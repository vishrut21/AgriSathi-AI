# Software Requirements Specification (SRS)
# AgriSathi – AI Farmer Assistant

**Version:** 1.0  
**Date:** February 14, 2026  
**Prepared by:** AgriSathi Development Team

---

## 1. Introduction

### 1.1 Purpose
This Software Requirements Specification (SRS) document provides a complete description of the AgriSathi AI Farmer Assistant system. It defines the functional and non-functional requirements for an AI-based multilingual assistant designed specifically for Indian farmers. This document is intended for developers, project managers, testers, and stakeholders involved in the development and deployment of the system.

### 1.2 Scope
AgriSathi is a mobile-first AI assistant that empowers Indian farmers with:
- Real-time weather forecasts and agricultural advisories
- Crop management recommendations based on local conditions
- Pest and disease identification using image recognition
- Information about government schemes and subsidies
- Voice-based interaction in multiple Indian languages
- Offline functionality for areas with limited connectivity

The system aims to bridge the digital divide by providing accessible, actionable agricultural intelligence to farmers with low digital literacy.

### 1.3 Definitions and Acronyms

| Term | Definition |
|------|------------|
| AI | Artificial Intelligence |
| API | Application Programming Interface |
| GPS | Global Positioning System |
| IMD | India Meteorological Department |
| ML | Machine Learning |
| NLP | Natural Language Processing |
| SMS | Short Message Service |
| SRS | Software Requirements Specification |
| UI | User Interface |
| UX | User Experience |
| ASR | Automatic Speech Recognition |
| TTS | Text-to-Speech |
| PWA | Progressive Web Application |

---

## 2. Overall Description

### 2.1 Product Perspective
AgriSathi is a standalone mobile application that integrates with external services including:
- Weather data providers (IMD, private weather APIs)
- Government databases for scheme information
- Cloud-based AI/ML models for image recognition
- SMS gateways for offline notifications
- Location services for geo-specific recommendations

The system operates in a client-server architecture with offline-first capabilities.

### 2.2 User Classes

#### 2.2.1 Farmers (Primary Users)
- **Characteristics:** Low to moderate digital literacy, primary language is regional Indian language, limited smartphone experience
- **Needs:** Simple voice-based interface, visual guidance, offline access, vernacular language support
- **Frequency:** Daily usage for weather checks, periodic for crop advisory

#### 2.2.2 Agricultural Extension Officers
- **Characteristics:** Moderate to high digital literacy, field workers supporting multiple farmers
- **Needs:** Bulk advisory distribution, farmer analytics, regional insights
- **Frequency:** Regular usage for monitoring and support

#### 2.2.3 System Administrators
- **Characteristics:** Technical staff managing the platform
- **Needs:** System monitoring, user management, content updates, analytics dashboard
- **Frequency:** Continuous monitoring and periodic maintenance

#### 2.2.4 Government Officers
- **Characteristics:** Policy makers and agricultural department officials
- **Needs:** Usage analytics, impact assessment, scheme reach metrics
- **Frequency:** Periodic reporting and analysis

### 2.3 Operating Environment
- **Client Side:**
  - Android 8.0+ and iOS 12+ devices
  - Low-end smartphones (1GB RAM minimum)
  - Screen sizes: 4.5" to 6.5"
  - Intermittent internet connectivity (2G/3G/4G)
  
- **Server Side:**
  - Cloud infrastructure (AWS/Azure/GCP)
  - Linux-based servers
  - Containerized microservices architecture
  - CDN for content delivery

### 2.4 Design Constraints
- Must function on devices with limited processing power (entry-level smartphones)
- Application size must not exceed 50MB for initial download
- Must work with bandwidth as low as 64 kbps
- Voice recognition must handle noisy rural environments
- UI must be navigable without text literacy
- Must comply with Indian data protection regulations

### 2.5 Assumptions and Dependencies
- Users have access to smartphones with camera and microphone
- Basic GPS functionality is available on user devices
- Government APIs for scheme data remain accessible
- Weather data providers maintain service availability
- Users consent to location access for personalized services
- Internet connectivity available at least once per week for sync

---

## 3. Functional Requirements

### 3.1 Weather Forecast Module

#### FR-WF-001: Real-Time Weather Data
**Priority:** High  
**Description:** System shall provide current weather conditions based on user location.

**Requirements:**
- Display temperature, humidity, wind speed, and rainfall probability
- Update weather data every 3 hours when online
- Cache last 7 days of weather history
- Show weather alerts and warnings prominently

#### FR-WF-002: 7-Day Forecast
**Priority:** High  
**Description:** System shall provide weather predictions for the next 7 days.

**Requirements:**
- Display daily high/low temperatures
- Show rainfall predictions with probability percentages
- Include agricultural-specific metrics (soil moisture prediction, evapotranspiration)
- Provide voice narration of forecast in user's language

#### FR-WF-003: Weather-Based Alerts
**Priority:** High  
**Description:** System shall send proactive alerts for critical weather events.

**Requirements:**
- Push notifications for extreme weather (storms, heatwaves, frost)
- SMS fallback when app is not active
- Customizable alert thresholds
- Agricultural impact assessment with each alert

### 3.2 Crop Advisory System

#### FR-CA-001: Crop Selection Guidance
**Priority:** High  
**Description:** System shall recommend suitable crops based on location, season, and soil type.

**Requirements:**
- Input: Location, soil type, season, available resources
- Output: Ranked list of suitable crops with expected yield
- Consider market prices and demand trends
- Provide crop rotation suggestions

#### FR-CA-002: Crop Calendar
**Priority:** Medium  
**Description:** System shall provide stage-wise crop management timeline.

**Requirements:**
- Sowing to harvesting timeline with key activities
- Reminders for irrigation, fertilization, and pest control
- Adjust recommendations based on actual weather
- Support for 50+ major crops grown in India

#### FR-CA-003: Fertilizer Recommendations
**Priority:** High  
**Description:** System shall suggest optimal fertilizer application.

**Requirements:**
- Calculate NPK requirements based on crop and soil
- Recommend organic and chemical fertilizer options
- Provide application timing and quantity
- Cost estimation for recommended fertilizers

#### FR-CA-004: Irrigation Advisory
**Priority:** High  
**Description:** System shall provide irrigation scheduling guidance.

**Requirements:**
- Calculate water requirements based on crop stage and weather
- Suggest optimal irrigation timing
- Support drip, sprinkler, and flood irrigation methods
- Water conservation tips

### 3.3 Pest & Disease Detection

#### FR-PD-001: Image-Based Identification
**Priority:** High  
**Description:** System shall identify pests and diseases from crop images.

**Requirements:**
- Accept images from camera or gallery
- Process images using AI/ML models
- Identify 100+ common pests and diseases
- Provide confidence score for identification
- Work with images taken in varying light conditions

#### FR-PD-002: Treatment Recommendations
**Priority:** High  
**Description:** System shall suggest treatment options for identified issues.

**Requirements:**
- Provide organic and chemical treatment options
- Include application methods and safety precautions
- Estimate treatment costs
- Link to video demonstrations when available

#### FR-PD-003: Pest Alert System
**Priority:** Medium  
**Description:** System shall alert users about pest outbreaks in their region.

**Requirements:**
- Crowdsource pest sighting data
- Generate regional pest alerts
- Preventive measures for predicted outbreaks
- Integration with agricultural department data

### 3.4 Government Scheme Guidance

#### FR-GS-001: Scheme Discovery
**Priority:** High  
**Description:** System shall help farmers discover applicable government schemes.

**Requirements:**
- Database of central and state schemes
- Filter schemes by eligibility criteria
- Display scheme benefits, documents required, and application process
- Support for 20+ Indian states

#### FR-GS-002: Application Assistance
**Priority:** Medium  
**Description:** System shall guide farmers through scheme application process.

**Requirements:**
- Step-by-step application guidance
- Document checklist
- Link to official application portals
- Track application status where possible

#### FR-GS-003: Subsidy Calculator
**Priority:** Medium  
**Description:** System shall calculate potential subsidy amounts.

**Requirements:**
- Input: Land size, crop type, equipment needs
- Output: Estimated subsidy amount
- Compare multiple schemes
- Update calculations based on latest scheme rules

### 3.5 Voice Interaction System

#### FR-VI-001: Voice Input
**Priority:** High  
**Description:** System shall accept voice commands in multiple Indian languages.

**Requirements:**
- Support for Hindi, English, Tamil, Telugu, Marathi, Bengali, Gujarati, Kannada, Malayalam, Punjabi
- Handle rural accents and dialects
- Function in noisy environments (farm settings)
- Provide visual feedback during voice recognition

#### FR-VI-002: Voice Output
**Priority:** High  
**Description:** System shall provide voice responses using text-to-speech.

**Requirements:**
- Natural-sounding voice in user's selected language
- Adjustable speech rate
- Ability to repeat last response
- Pause/resume functionality

#### FR-VI-003: Conversational Interface
**Priority:** Medium  
**Description:** System shall support natural conversation flow.

**Requirements:**
- Context-aware responses
- Handle follow-up questions
- Clarification prompts for ambiguous queries
- Conversation history for current session

### 3.6 Multilingual Support

#### FR-ML-001: Language Selection
**Priority:** High  
**Description:** System shall support 10+ Indian languages.

**Requirements:**
- Language selection during onboarding
- Easy language switching from settings
- Consistent translation across all features
- Support for regional language scripts

#### FR-ML-002: Content Localization
**Priority:** High  
**Description:** All content shall be available in supported languages.

**Requirements:**
- UI text, labels, and messages
- Advisory content and recommendations
- Government scheme information
- Help documentation and tutorials

### 3.7 Location-Based Services

#### FR-LB-001: Automatic Location Detection
**Priority:** High  
**Description:** System shall detect user location for personalized services.

**Requirements:**
- GPS-based location detection
- Manual location entry option
- Village/district/state level granularity
- Location-based content filtering

#### FR-LB-002: Regional Customization
**Priority:** High  
**Description:** System shall customize content based on user's region.

**Requirements:**
- Region-specific crop recommendations
- Local weather data
- State-specific government schemes
- Regional pest and disease patterns

### 3.8 Offline Mode

#### FR-OF-001: Offline Data Access
**Priority:** High  
**Description:** System shall provide core functionality without internet.

**Requirements:**
- Cache last 7 days of weather data
- Store crop advisory for user's selected crops
- Offline access to saved pest/disease information
- Local storage of user's farm data

#### FR-OF-002: Data Synchronization
**Priority:** High  
**Description:** System shall sync data when connectivity is restored.

**Requirements:**
- Automatic background sync
- Conflict resolution for offline changes
- Sync status indicator
- Manual sync trigger option

#### FR-OF-003: Offline Voice Recognition
**Priority:** Medium  
**Description:** System shall support basic voice commands offline.

**Requirements:**
- On-device speech recognition for common commands
- Limited vocabulary mode for offline use
- Automatic switch to online mode when available
- Offline command library for navigation

---

## 4. Non-Functional Requirements

### 4.1 Performance Requirements

#### NFR-PF-001: Response Time
- Voice recognition response: < 2 seconds
- Image processing for pest detection: < 5 seconds
- Weather data refresh: < 3 seconds
- Page load time: < 2 seconds on 3G connection

#### NFR-PF-002: Throughput
- Support 100,000 concurrent users
- Handle 1 million API requests per hour
- Process 10,000 image uploads per hour

#### NFR-PF-003: Resource Usage
- App memory footprint: < 150MB
- Battery consumption: < 5% per hour of active use
- Data usage: < 10MB per day with normal usage
- Storage: < 200MB including cached data

### 4.2 Scalability

#### NFR-SC-001: User Scalability
- System shall scale to support 10 million registered users
- Horizontal scaling for increased load
- Auto-scaling based on demand patterns

#### NFR-SC-002: Geographic Scalability
- Support deployment across all Indian states
- Regional data centers for reduced latency
- CDN integration for content delivery

### 4.3 Security

#### NFR-SE-001: Data Protection
- End-to-end encryption for sensitive data
- Secure storage of user credentials
- Compliance with Indian data protection laws
- Regular security audits

#### NFR-SE-002: Authentication
- Phone number-based authentication
- OTP verification
- Biometric authentication support (fingerprint/face)
- Session timeout after 30 minutes of inactivity

#### NFR-SE-003: Privacy
- User consent for data collection
- Anonymized analytics data
- Option to delete user account and data
- No sharing of personal data with third parties without consent

### 4.4 Usability

#### NFR-US-001: Ease of Use
- First-time users shall complete onboarding in < 5 minutes
- Core features accessible within 3 taps/voice commands
- Visual icons for illiterate users
- Consistent navigation patterns

#### NFR-US-002: Accessibility
- Support for screen readers
- High contrast mode for visibility
- Large touch targets (minimum 44x44 pixels)
- Voice-first design for low literacy users

#### NFR-US-003: Learning Curve
- Interactive tutorial on first launch
- Contextual help throughout the app
- Video tutorials in regional languages
- Helpline number for support

### 4.5 Reliability

#### NFR-RE-001: Availability
- System uptime: 99.5% (excluding planned maintenance)
- Graceful degradation when services are unavailable
- Offline mode ensures core functionality always available

#### NFR-RE-002: Fault Tolerance
- Automatic retry for failed network requests
- Local caching to prevent data loss
- Error recovery without app restart
- Backup systems for critical services

#### NFR-RE-003: Data Integrity
- Validation of all user inputs
- Checksums for data synchronization
- Regular database backups
- Transaction rollback on failures

### 4.6 Maintainability

#### NFR-MA-001: Code Quality
- Modular architecture for easy updates
- Comprehensive code documentation
- Automated testing coverage > 80%
- Version control and CI/CD pipeline

#### NFR-MA-002: Updates
- Over-the-air updates for content
- Backward compatibility for 2 previous versions
- Staged rollout for major updates
- Rollback capability for failed updates

---

## 5. External Interface Requirements

### 5.1 User Interface Requirements

#### UI-001: Mobile Application Interface
- **Platform:** Android and iOS native apps
- **Design:** Material Design (Android), Human Interface Guidelines (iOS)
- **Orientation:** Portrait mode primary, landscape support for media
- **Navigation:** Bottom navigation bar with 4-5 main sections
- **Color Scheme:** Agriculture-themed (greens, browns, blues)
- **Typography:** Large, readable fonts (minimum 16sp for body text)

#### UI-002: Voice Interface
- **Activation:** Wake word ("Hey AgriSathi") or button press
- **Feedback:** Visual waveform during listening
- **Confirmation:** Voice and visual confirmation of understood commands
- **Error Handling:** Clear error messages with retry options

#### UI-003: Key Screens
- Home Dashboard (weather, alerts, quick actions)
- Crop Advisory (calendar, recommendations)
- Pest Detection (camera interface, results)
- Government Schemes (search, filter, details)
- Profile & Settings (language, location, preferences)

### 5.2 Hardware Interface Requirements

#### HW-001: Camera
- Access to device camera for pest/disease detection
- Support for both front and rear cameras
- Minimum resolution: 5MP
- Auto-focus and flash control

#### HW-002: Microphone
- Access to device microphone for voice input
- Noise cancellation support
- Audio recording for voice messages

#### HW-003: GPS
- Access to location services
- Support for GPS, GLONASS, and network-based location
- Background location updates for weather alerts

#### HW-004: Storage
- Access to device storage for offline data
- SD card support for extended storage
- Minimum 100MB free space required

### 5.3 Software Interface Requirements

#### SW-001: Weather API Integration
- **Provider:** IMD, OpenWeatherMap, or equivalent
- **Protocol:** REST API over HTTPS
- **Data Format:** JSON
- **Update Frequency:** Every 3 hours
- **Endpoints:** Current weather, forecast, alerts

#### SW-002: Government Database Integration
- **Source:** National/State agricultural portals
- **Protocol:** REST API or web scraping (as available)
- **Data Format:** JSON/XML
- **Update Frequency:** Daily
- **Content:** Scheme details, eligibility, application process

#### SW-003: AI/ML Model Services
- **Pest Detection:** TensorFlow Lite or PyTorch Mobile
- **Deployment:** On-device and cloud-based models
- **Model Format:** TFLite, ONNX
- **Update Mechanism:** Over-the-air model updates

#### SW-004: SMS Gateway
- **Provider:** Twilio, MSG91, or equivalent
- **Protocol:** REST API
- **Purpose:** OTP, alerts, offline notifications
- **Rate Limit:** 10,000 messages per day

#### SW-005: Analytics Platform
- **Tool:** Firebase Analytics, Mixpanel, or equivalent
- **Data:** User behavior, feature usage, crash reports
- **Privacy:** Anonymized data only
- **Compliance:** GDPR and Indian data protection laws

### 5.4 Communication Interface Requirements

#### COM-001: Network Protocols
- **HTTP/HTTPS:** For API communication
- **WebSocket:** For real-time updates
- **MQTT:** For IoT sensor integration (future)

#### COM-002: Data Formats
- **JSON:** Primary data exchange format
- **Protocol Buffers:** For efficient mobile communication
- **Image Formats:** JPEG, PNG (compressed)

#### COM-003: API Standards
- RESTful API design
- OAuth 2.0 for authentication
- Rate limiting: 1000 requests per hour per user
- API versioning (v1, v2, etc.)

---

## 6. System Features (Use Case Style)

### 6.1 Use Case: Check Weather Forecast

**Actor:** Farmer  
**Precondition:** User has installed app and granted location permission  
**Main Flow:**
1. User opens app or says "Hey AgriSathi, what's the weather?"
2. System detects user location
3. System retrieves current weather and 7-day forecast
4. System displays weather information with agricultural insights
5. System provides voice narration in user's language

**Alternative Flow:**
- If offline, system displays cached weather data with timestamp
- If location unavailable, system prompts for manual location entry

**Postcondition:** User receives weather information relevant to farming activities

### 6.2 Use Case: Identify Pest or Disease

**Actor:** Farmer  
**Precondition:** User has camera access enabled  
**Main Flow:**
1. User navigates to pest detection feature
2. User captures image of affected crop
3. System processes image using AI model
4. System identifies pest/disease with confidence score
5. System displays treatment recommendations
6. User can save result for future reference

**Alternative Flow:**
- If confidence score < 70%, system suggests consulting expert
- User can upload multiple images for better accuracy
- System provides option to report misidentification

**Postcondition:** User receives actionable treatment guidance

### 6.3 Use Case: Get Crop Advisory

**Actor:** Farmer  
**Precondition:** User has completed profile with crop and land details  
**Main Flow:**
1. User asks "What should I do for my wheat crop today?"
2. System retrieves user's crop information
3. System considers current crop stage, weather, and season
4. System generates personalized advisory
5. System delivers advisory via voice and text
6. System sets reminders for upcoming activities

**Alternative Flow:**
- User can browse crop calendar for full season view
- User can request specific advice (irrigation, fertilizer, etc.)

**Postcondition:** User receives timely, actionable crop management advice

### 6.4 Use Case: Discover Government Schemes

**Actor:** Farmer  
**Precondition:** User has completed basic profile  
**Main Flow:**
1. User navigates to government schemes section
2. System filters schemes based on user's profile (location, crop, land size)
3. System displays list of applicable schemes
4. User selects a scheme for details
5. System shows benefits, eligibility, documents, and application process
6. User can bookmark scheme or start application

**Alternative Flow:**
- User can search schemes by keyword
- User can view all schemes without filtering
- System notifies user of new schemes matching their profile

**Postcondition:** User discovers relevant government benefits

---

## 7. Data Requirements

### 7.1 User Data

| Data Element | Type | Description | Storage |
|--------------|------|-------------|---------|
| User ID | UUID | Unique identifier | Cloud DB |
| Phone Number | String | Primary authentication | Encrypted |
| Name | String | User's name | Cloud DB |
| Location | Geo-coordinates | Farm location | Cloud DB |
| Language Preference | Enum | Selected language | Local & Cloud |
| Crops | Array | Crops being grown | Cloud DB |
| Land Size | Float | Farm area in acres | Cloud DB |
| Soil Type | Enum | Soil classification | Cloud DB |

### 7.2 Weather Data

| Data Element | Type | Description | Retention |
|--------------|------|-------------|-----------|
| Temperature | Float | Current/forecast temp | 30 days |
| Humidity | Float | Relative humidity % | 30 days |
| Rainfall | Float | Precipitation in mm | 90 days |
| Wind Speed | Float | Wind speed in km/h | 30 days |
| Weather Alerts | String | Warning messages | 7 days |

### 7.3 Crop Advisory Data

| Data Element | Type | Description | Update Frequency |
|--------------|------|-------------|------------------|
| Crop Name | String | Crop identifier | Static |
| Growth Stages | Array | Stage definitions | Quarterly |
| Activity Calendar | JSON | Stage-wise activities | Quarterly |
| Fertilizer Schedule | JSON | NPK recommendations | Quarterly |
| Pest Susceptibility | Array | Common pests by stage | Monthly |

### 7.4 Pest & Disease Database

| Data Element | Type | Description | Size |
|--------------|------|-------------|------|
| Pest ID | UUID | Unique identifier | - |
| Pest Name | String | Common & scientific name | - |
| Images | Array | Reference images | 5-10 per pest |
| Symptoms | Text | Visual indicators | - |
| Treatment | JSON | Organic & chemical options | - |
| Affected Crops | Array | Susceptible crops | - |

### 7.5 Government Schemes Data

| Data Element | Type | Description | Update Frequency |
|--------------|------|-------------|------------------|
| Scheme ID | UUID | Unique identifier | - |
| Scheme Name | String | Official name | - |
| State | Enum | Applicable state(s) | - |
| Eligibility | JSON | Criteria details | Monthly |
| Benefits | Text | Scheme benefits | Monthly |
| Documents | Array | Required documents | Monthly |
| Application URL | String | Official portal link | Monthly |

---

## 8. Legal and Compliance Requirements

### 8.1 Data Protection
- Compliance with Information Technology Act, 2000
- Adherence to Digital Personal Data Protection Act, 2023
- User consent for data collection and processing
- Right to data portability and deletion
- Data localization as per Indian regulations

### 8.2 Agricultural Regulations
- Compliance with Pesticides Act, 1968 for chemical recommendations
- Adherence to Fertilizer Control Order, 1985
- Alignment with Ministry of Agriculture guidelines
- Disclaimer for advisory content (not a substitute for expert consultation)

### 8.3 Intellectual Property
- Proper licensing for third-party APIs and services
- Attribution for open-source components
- Copyright protection for original content
- User-generated content ownership and usage rights

### 8.4 Accessibility Compliance
- Compliance with Rights of Persons with Disabilities Act, 2016
- WCAG 2.1 Level AA standards for digital accessibility
- Voice-first design for users with visual impairments

### 8.5 Terms of Service
- Clear terms of use and privacy policy
- Liability limitations for advisory accuracy
- User responsibilities and acceptable use
- Dispute resolution mechanism

---

## 9. Future Enhancements

### 9.1 Phase 2 Features (6-12 months)
- **Marketplace Integration:** Direct connection to buyers and mandis
- **Financial Services:** Crop insurance, loans, and credit scoring
- **Community Forum:** Farmer-to-farmer knowledge sharing
- **IoT Integration:** Support for soil sensors and weather stations
- **Drone Integration:** Aerial crop monitoring and analysis

### 9.2 Phase 3 Features (12-24 months)
- **Blockchain Traceability:** Farm-to-fork supply chain tracking
- **AI Yield Prediction:** Machine learning-based harvest forecasting
- **Precision Agriculture:** GPS-guided farming recommendations
- **Water Management:** Smart irrigation system integration
- **Carbon Credit Tracking:** Sustainable farming incentives

### 9.3 Technology Roadmap
- **AR Features:** Augmented reality for pest identification
- **Satellite Imagery:** Integration with remote sensing data
- **Edge AI:** Advanced on-device machine learning
- **5G Optimization:** Enhanced features for high-speed connectivity
- **Wearable Integration:** Smartwatch companion app

---

## 10. Constraints and Limitations

### 10.1 Technical Constraints
- Limited processing power on entry-level devices
- Intermittent network connectivity in rural areas
- Varying quality of user-captured images
- Accuracy limitations of AI models
- Dependency on third-party data sources

### 10.2 Business Constraints
- Budget limitations for cloud infrastructure
- Cost-effective deployment requirement
- Free tier for farmers (monetization through partnerships)
- Limited resources for 24/7 support
- Phased rollout across states

### 10.3 User Constraints
- Low digital literacy among target users
- Language diversity across regions
- Resistance to technology adoption
- Limited smartphone penetration in some areas
- Concerns about data privacy

### 10.4 Regulatory Constraints
- Compliance with agricultural advisory regulations
- Restrictions on pesticide recommendations
- Data localization requirements
- Government approval for scheme information
- Liability for incorrect advice

---

## Appendix A: Supported Languages

1. Hindi (हिन्दी)
2. English
3. Tamil (தமிழ்)
4. Telugu (తెలుగు)
5. Marathi (मराठी)
6. Bengali (বাংলা)
7. Gujarati (ગુજરાતી)
8. Kannada (ಕನ್ನಡ)
9. Malayalam (മലയാളം)
10. Punjabi (ਪੰਜਾਬੀ)
11. Odia (ଓଡ଼ିଆ) - Future
12. Assamese (অসমীয়া) - Future

---

## Appendix B: Supported Crops (Initial Release)

**Cereals:** Rice, Wheat, Maize, Bajra, Jowar  
**Pulses:** Chickpea, Pigeon Pea, Lentil, Green Gram, Black Gram  
**Oilseeds:** Groundnut, Soybean, Mustard, Sunflower, Sesame  
**Cash Crops:** Cotton, Sugarcane, Jute, Tea, Coffee  
**Vegetables:** Tomato, Potato, Onion, Cabbage, Cauliflower  
**Fruits:** Mango, Banana, Citrus, Grapes, Pomegranate  
**Spices:** Turmeric, Chili, Coriander, Cumin, Ginger

---

## Document Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Product Manager | | | |
| Technical Lead | | | |
| QA Lead | | | |
| Stakeholder | | | |

---

**End of Document**
