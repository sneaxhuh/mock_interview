# Mock Interview Platform - Prepify

Prepify is an AI-powered mock interview platform that helps candidates prepare for technical interviews through realistic simulations. The platform uses voice interaction, AI-generated questions, and personalized feedback to create an authentic interview experience.

## Features

- **Voice-Based Interviews**: Conduct interviews using your microphone for a natural conversation experience
- **AI Interviewers**: Choose between different AI interviewers (Matthew or Ruth) with distinct personalities
- **Customizable Interviews**: Tailor interviews based on your resume and job descriptions
- **Real-Time Transcription**: Uses AWS Transcribe to convert speech to text
- **AI-Powered Questions**: Gemini AI generates relevant technical and behavioral questions
- **Voice Synthesis**: AWS Polly converts AI responses to natural-sounding speech
- **Performance Analysis**: Get detailed feedback and a performance report at the end of the interview

## Architecture

The application consists of two main components:

### Frontend (React)
- Built with React and Material-UI for a responsive user interface
- Real-time communication with backend using Socket.IO
- WebRTC for microphone access and audio recording
- Audio playback functionality for interviewer responses

### Backend (Node.js/Express)
- RESTful API with WebSocket support for real-time communication
- AWS services integration:
  - AWS Transcribe for speech-to-text conversion
  - AWS Polly for text-to-speech synthesis
  - AWS S3 for audio file storage
- Gemini AI integration for generating interview questions and feedback
- FFmpeg for audio format conversion

## Prerequisites

Before you begin, ensure you have the following installed:
- Node.js (v14 or higher)
- npm (v6 or higher)
- AWS account with configured credentials
- Google Gemini API key

## Setup

### Environment Variables

Create a `.env` file in the root directory with the following variables:

```env
# AWS Credentials
ACCESS_KEY=your_aws_access_key
SECRET_KEY=your_aws_secret_key
BUCKET_NAME=your_s3_bucket_name

# Gemini API Key
GEMINI_API_KEY=your_gemini_api_key
```

### Backend Setup

1. Navigate to the backend directory:
   ```bash
   cd back-end
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the server:
   ```bash
   node index.js
   ```
   The backend server will start on port 5001.

### Frontend Setup

1. Navigate to the frontend directory:
   ```bash
   cd front-end
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the development server:
   ```bash
   npm start
   ```
   The frontend will start on port 3000.

## Usage

1. Start both the frontend and backend servers
2. Open your browser and navigate to `http://localhost:3000`
3. Enter your resume and a job description
4. Select an interviewer
5. Click "Submit Application" to begin the interview
6. Use the record button to answer questions
7. At the end of the interview, click "End Interview" to receive your feedback report

## How It Works

1. **Interview Setup**: Users provide their resume and a job description to customize the interview
2. **Audio Recording**: The frontend captures audio using the browser's microphone
3. **Speech Processing**: Audio is sent to the backend, converted to WAV format, and uploaded to AWS S3
4. **Transcription**: AWS Transcribe converts speech to text
5. **AI Interaction**: Transcribed text is sent to Gemini AI, which generates relevant responses
6. **Voice Synthesis**: AI responses are converted to speech using AWS Polly
7. **Audio Playback**: The frontend plays the interviewer's response
8. **Performance Analysis**: At the end of the interview, Gemini generates a detailed performance report

## Technologies Used

### Frontend
- React
- Material-UI
- Socket.IO Client
- WebRTC

### Backend
- Node.js
- Express
- Socket.IO
- AWS SDK (S3, Transcribe, Polly)
- FFmpeg
- Gemini AI SDK

## Project Structure

```
mock_interview/
├── back-end/
│   ├── index.js          # Main server file
│   ├── package.json      # Backend dependencies
│   └── ...               # Other backend files
├── front-end/
│   ├── src/
│   │   ├── components/   # React components
│   │   ├── pages/        # Page components
│   │   ├── constants.js  # Application constants
│   │   └── App.js        # Main App component
│   ├── package.json      # Frontend dependencies
│   └── ...               # Other frontend files
└── README.md             # This file
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a pull request

## License

This project is licensed under the MIT License.