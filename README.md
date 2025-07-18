# Campus Hub - A Next.js, Firebase, and Genkit Application

This is a Next.js application built with Firebase for backend services (Authentication, Firestore) and Genkit for AI-powered features. This guide provides instructions on how to set up, run, and deploy the project to Vercel.

## Features

- **Event Management:** Create, view, and filter upcoming and past events.
- **User Authentication:** Sign up, log in (email/password, Google, guest), and manage user profiles.
- **AI-Powered Features:**
  - Generate event details from a simple text description.
  - Chatbot to answer questions about campus events and resources.
  - Analytics dashboard with AI-generated summaries of event data.
- **Real-time Interaction:** RSVP for events, see participant lists, and check in users with a QR code scanner.
- **Gamification:** Earn points and badges for participating in events.

## Tech Stack

- **Framework:** Next.js (with App Router)
- **UI:** React, ShadCN UI, Tailwind CSS
- **Backend & Database:** Firebase (Authentication, Firestore, Storage)
- **Generative AI:** Google AI via Genkit
- **Deployment:** Vercel

---

## Getting Started

### 1. Prerequisites

- [Node.js](https://nodejs.org/) (v18 or later)
- [Vercel CLI](https://vercel.com/docs/cli)
- A Firebase project with Authentication, Firestore, and Storage enabled.
- A Google Cloud project with the "AI Platform" API enabled to get a `GOOGLE_API_KEY` for Genkit.

### 2. Set Up Environment Variables

This project requires several environment variables to connect to Firebase and Google AI services.

Create a `.env.local` file in the root of your project and add the following variables. Replace the placeholder values with your actual project credentials.

```env
# Firebase Configuration
NEXT_PUBLIC_FIREBASE_API_KEY=YOUR_FIREBASE_API_KEY
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=YOUR_FIREBASE_AUTH_DOMAIN
NEXT_PUBLIC_FIREBASE_PROJECT_ID=YOUR_FIREBASE_PROJECT_ID
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=YOUR_FIREBASE_STORAGE_BUCKET
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=YOUR_FIREBASE_MESSAGING_SENDER_ID
NEXT_PUBLIC_FIREBASE_APP_ID=YOUR_FIREBASE_APP_ID

# Genkit (Google AI) Configuration
GOOGLE_API_KEY=YOUR_GOOGLE_AI_API_KEY
```

You can find your Firebase credentials in your Firebase project settings. The `GOOGLE_API_KEY` can be generated from your Google Cloud Console.

### 3. Install Dependencies and Run Locally

First, install the project dependencies:
```bash
npm install
```

Next, run the development server:
```bash
npm run dev
```
The application will be available at `http://localhost:9002`.

---

## Deployment to Vercel

Follow these steps to deploy your application to Vercel.

### 1. Install Vercel CLI

If you haven't already, install the Vercel CLI globally:
```bash
npm i -g vercel
```

### 2. Log in to Vercel

Log in to your Vercel account through the CLI. This will link your local machine to your Vercel account.
```bash
vercel login
```

### 3. Add Environment Variables to Vercel

Your project's environment variables must also be available to Vercel during the build and runtime process.

Add each variable from your `.env.local` file to your Vercel project. For each key-value pair, run the following command, replacing `KEY` and `VALUE` accordingly.

**Important:** Note the `NEXT_PUBLIC_` prefix for Firebase keys.

```bash
vercel env add NEXT_PUBLIC_FIREBASE_API_KEY YOUR_FIREBASE_API_KEY
vercel env add NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN YOUR_FIREBASE_AUTH_DOMAIN
vercel env add NEXT_PUBLIC_FIREBASE_PROJECT_ID YOUR_FIREBASE_PROJECT_ID
vercel env add NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET YOUR_FIREBASE_STORAGE_BUCKET
vercel env add NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID YOUR_FIREBASE_MESSAGING_SENDER_ID
vercel env add NEXT_PUBLIC_FIREBASE_APP_ID YOUR_FIREBASE_APP_ID
vercel env add GOOGLE_API_KEY YOUR_GOOGLE_AI_API_KEY
```

After adding the variables, you can verify they were added correctly by running `vercel env ls`.

### 4. Deploy the Project

Once your environment variables are set, you can deploy the project.

For your first deployment, run:
```bash
vercel
```
The CLI will guide you through linking the local directory to a new or existing Vercel project.

For subsequent deployments from the project directory, you can simply run:
```bash
vercel --prod
```
This command will build your Next.js application and deploy it to a production URL on Vercel. Vercel will automatically use the `vercel.json` file and Next.js framework defaults for a seamless deployment.
