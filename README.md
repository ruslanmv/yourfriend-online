# YourFriend.online - AI Chatbot

YourFriend.online is a next-generation AI chatbot designed to be your digital companion. This open-source project is in active development and welcomes contributions from the community.

Developed by [ruslanmv.com](https://ruslanmv.com), YourFriend.online leverages cutting-edge AI and database technologies to deliver an intelligent, context-aware conversational experience.

## 🚀 Tech Stack

- **Next.js** - Frontend & Backend framework
- **MongoDB Atlas** - Database & Vector Store
- **OpenAI API** - AI-powered chat interactions
- **Tailwind CSS** - Modern styling
- **Netlify** - Deployment platform
- **Apideck Components** - UI notifications and modals

## 🌍 One-Click Deployment

Deploy the chatbot instantly on **Netlify**:

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/mongodb-developer/netlify-mongodb-nextjs-ai-chatbot)

### Environment Variables:
Ensure you set the required variables before deployment:
```bash
OPENAI_API_KEY=your_openai_api_key
MONGODB_ATLAS_URI=your_cluster_connection_string
MONGODB_DATABASE=your_source_documents_database
MONGODB_SOURCE_COLLECTION=your_embedded_collection
```

## 📌 Getting Started

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-repo/yourfriend-online.git
   cd yourfriend-online
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Set up environment variables**:
   Create a `.env.local` file and add:
   ```bash
   OPENAI_API_KEY=your_openai_api_key
   MONGODB_ATLAS_URI=your_cluster_connection_string
   MONGODB_DATABASE=your_source_documents_database
   MONGODB_SOURCE_COLLECTION=your_embedded_collection
   ```

4. **Run the development server**:
   ```bash
   netlify dev
   ```

5. **Open in browser**:
   Navigate to `http://localhost:8888` to start chatting!

## 🛠 Setting Up MongoDB Atlas

1. **Create or use an existing Atlas Cluster**:
   - Ensure IP whitelisting is configured
   - Retrieve your MongoDB connection string

2. **Import Data for Vector Store**:
   - Follow the [data ingestion guide](src/data_ingestion/INSTALL.md)
   - Alternatively, import the provided JSON file:
     ```bash
     /src/data_ingestion/netlify_chat_demo.context.json
     ```

3. **Create Atlas Vector Index**:
   ```json
   {
     "fields": [
       {
         "type": "vector",
         "path": "embedding",
         "numDimensions": <NUMBER>,
         "similarity": "cosine"
       }
     ]
   }
   ```

## 🔧 Customization

### Changing AI Model
The chatbot currently uses `gpt-3.5-turbo`. To switch to `GPT-4` (if available), edit the `createMessage` function in `/src/pages/api/createMessage.ts`:

```typescript
const body = JSON.stringify({
  messages,
  model: 'gpt-4', // Change from 'gpt-3.5-turbo'
  stream: false
});
```

### UI & Styling
Modify styles in:
- `/src/styles/tailwind.css`
- `/src/styles/globals.css`

### Core Chat Functionality
Located in:
- `/src/utils/sendMessage.ts`
- `/src/utils/useMessages.tsx`

## 🚢 Deploying to Production

Use the **Netlify CLI** to deploy:
```bash
netlify deploy --prod
```

## 🤝 Contributing
This project is open-source and welcomes contributions! Feel free to submit pull requests or open GitHub issues.

---

💡 *YourFriend.online – More than just a chatbot, it's your AI companion!*

