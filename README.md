# Servd - AI-Powered Recipe Platform

> **Turn your leftovers into masterpieces** 🍳

Servd is a modern, AI-powered recipe discovery and meal planning application that helps you reduce food waste and simplify meal preparation. Upload a photo of your pantry, and our intelligent system will suggest delicious recipes using what you already have.

## ✨ Features

### 🤖 AI-Powered Features
- **Smart Pantry Scanning**: Upload photos of your fridge/pantry and our AI automatically identifies ingredients
- **AI Recipe Generation**: Get complete, personalized recipes with detailed instructions, nutritional info, and chef's tips
- **Intelligent Recommendations**: Receive meal suggestions based on your available ingredients
- **Ingredient Substitutions**: Alternative ingredients included in every generated recipe

### 🍽️ Recipe Discovery
- **Extensive Recipe Database**: Browse 1000+ recipes from TheMealDB
- **Filter by Category**: Breakfast, lunch, dinner, snacks, and desserts
- **Filter by Cuisine**: 22+ cuisines including Italian, Asian, Mediterranean, and more
- **Recipe of the Day**: Daily featured recipe recommendations

### 📚 Personal Cookbook
- **Save Favorites**: Create a personalized collection of your favorite recipes
- **PDF Export**: Download recipes for offline access
- **Detailed Nutrition Info**: Calories, protein, carbs, and fat breakdown
- **Prep Time Tracking**: Cook time and serving size information

### 🔐 User Accounts & Subscriptions
- **Secure Authentication**: Powered by Clerk with OAuth and multi-factor authentication
- **Two Subscription Tiers**:
  - **Free (Sous Chef)**: 10 pantry scans/month, 5 AI recommendations/month
  - **Pro (Head Chef)**: $7.99/month - unlimited scans, unlimited AI recipes, priority support

### 🛡️ Security & Performance
- **Rate Limiting**: Arcjet protection with token bucket algorithm
- **Bot Detection**: Automatic bot protection and WAF shield
- **Image Optimization**: Fast loading with automatic image optimization
- **Server-Side Caching**: Optimized response times

## 🛠️ Technology Stack

### Frontend
- **Framework**: [Next.js 16.1](https://nextjs.org/) - React framework for production
- **React**: 19.2 - UI library
- **Styling**: [Tailwind CSS 4](https://tailwindcss.com/) - Utility-first CSS framework
- **Authentication**: [Clerk](https://clerk.com/) - User authentication and management
- **UI Components**:
  - [Radix UI](https://www.radix-ui.com/) - Unstyled, accessible components
  - Custom shadcn-inspired components
  - [Lucide React](https://lucide.dev/) - Beautiful icon library
- **Image Handling**: Next.js Image optimization with Unsplash integration
- **File Upload**: React Dropzone for drag-and-drop support
- **PDF Export**: [@react-pdf/renderer](https://react-pdf.org/) - PDF generation
- **Notifications**: [Sonner](https://sonner.emilkowal.ski/) - Toast notifications
- **Security**: [Arcjet](https://arcjet.com/) - WAF and rate limiting
- **Themes**: [next-themes](https://github.com/pacocoursey/next-themes)
- **Build**: [SWC](https://swc.rs/) - Fast JavaScript compiler

### Backend
- **CMS**: [Strapi 5.33](https://strapi.io/) - Headless CMS with REST API
- **Database**: [PostgreSQL](https://www.postgresql.org/) - Reliable relational database
- **Runtime**: Node.js 20.0 - 24.x
- **API**: RESTful API with Strapi content types

### External APIs
- **[Google Gemini](https://ai.google.dev/)**: AI-powered image analysis and recipe generation
- **[TheMealDB](https://www.themealdb.com/)**: Free recipe database with 1000+ recipes
- **[Unsplash](https://unsplash.com/)**: High-quality recipe images

## 🚀 Getting Started

### Prerequisites
- Node.js 20.0 or higher
- PostgreSQL database
- Google Gemini API key
- Unsplash API key (optional for image optimization)
- Clerk account

### Installation

1. **Clone the repository**
```bash
git clone <repository-url>
cd AI-Recipe-Platform
```

2. **Setup Frontend**
```bash
cd frontend
npm install
```

3. **Setup Backend**
```bash
cd backend
npm install
```

4. **Environment Variables**

Create `.env.local` in the `frontend` directory:
```env
NEXT_PUBLIC_STRAPI_URL=http://localhost:1337
STRAPI_API_TOKEN=<your-strapi-token>
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=<your-clerk-key>
CLERK_SECRET_KEY=<your-clerk-secret>
GEMINI_API_KEY=<your-gemini-api-key>
UNSPLASH_ACCESS_KEY=<your-unsplash-key>
ARCJET_KEY=<your-arcjet-key>
```

Create `.env` in the `backend` directory:
```env
DATABASE_URL=postgresql://user:password@localhost:5432/servd
JWT_SECRET=<your-jwt-secret>
ADMIN_JWT_SECRET=<your-admin-jwt-secret>
NODE_ENV=development
```

5. **Start Development Servers**

Frontend:
```bash
cd frontend
npm run dev
```

Backend:
```bash
cd backend
npm run develop
```

Visit `http://localhost:3000` for the frontend and `http://localhost:1337` for the backend admin panel.

## 📁 Project Structure

```
AI-Recipe-Platform/
├── frontend/                      # Next.js React application
│   ├── app/
│   │   ├── (auth)/               # Authentication pages (sign-in, sign-up)
│   │   ├── (main)/               # Main application routes
│   │   │   ├── dashboard/        # Recipe discovery hub
│   │   │   ├── pantry/           # Pantry management
│   │   │   ├── recipe/           # Single recipe viewer
│   │   │   └── recipes/          # Recipe browsing (category, cuisine)
│   │   ├── layout.js             # Root layout with providers
│   │   └── page.js               # Landing page
│   ├── components/               # React components
│   ├── actions/                  # Server actions (API integration)
│   ├── lib/                      # Utilities and helpers
│   ├── hooks/                    # Custom React hooks
│   ├── public/                   # Static assets
│   └── package.json
└── backend/                       # Strapi CMS
    ├── src/
    │   ├── api/                  # Content types (Recipe, Pantry, SavedRecipe)
    │   ├── extensions/           # Extended features
    │   └── index.js              # Server entry point
    ├── config/                   # Configuration
    ├── database/                 # Database migrations
    └── package.json
```

## 🎯 Key Workflows

### 1. Pantry Scanning
- User uploads/takes a photo
- Gemini Vision API analyzes the image
- Identified ingredients saved to user's pantry
- Rate-limited based on subscription tier

### 2. AI Recipe Generation
- User requests a recipe
- System checks database for existing recipe
- If not found, Gemini generates personalized recipe
- Unsplash fetches corresponding recipe image
- Recipe saved to database for future reference

### 3. Recipe Discovery
- Browse TheMealDB with category/cuisine filters
- View detailed recipe information
- Save favorites to personal cookbook
- Export as PDF for offline access

### 4. Subscription Management
- Powered by Clerk's subscription system
- Features unlock based on tier
- Usage tracked per user

## 🎨 Design Philosophy

- **Design System**: Neobrutalism with bold, high-contrast UI elements
- **Color Scheme**: Stone grays with orange (#ff6600) accents
- **Mobile-First**: Fully responsive design optimized for mobile
- **Accessibility**: Semantic HTML, ARIA attributes, keyboard navigation
- **Performance**: Optimized images, server-side caching, efficient API calls

## 📊 Data Models

### Recipe
- Title, description, cuisine, category
- Ingredients with quantities and categories
- Step-by-step instructions with tips
- Cooking times, servings, nutrition info
- Chef's tips and ingredient substitutions
- Author and visibility settings

### Pantry Item
- Ingredient name and quantity
- Associated image
- Owner tracking

### Saved Recipe
- User-specific saved recipes
- Timestamp tracking

### User
- Synchronized between Clerk and Strapi
- Subscription tier management
- Related recipes, pantry items, and saved recipes

## 🔒 Security Features

- **Authentication**: Clerk with OAuth 2.0 and MFA support
- **Rate Limiting**: Arcjet token bucket algorithm per user
- **Bot Protection**: Automatic bot detection and blocking
- **WAF**: Web Application Firewall protection against common attacks
- **API Security**: JWT tokens and server-side validation
- **Image Optimization**: Secure image processing and optimization

## 📈 Performance Optimizations

- **Caching Strategy**: 24-hour recipe cache, 1-week category cache
- **Image Optimization**: Next.js Image component with automatic compression
- **Server Actions**: Efficient server-side data fetching
- **Database Indexing**: Optimized PostgreSQL queries
- **CDN**: Image delivery through Unsplash CDN

## 🚢 Deployment

### Frontend
The frontend is optimized for deployment on:
- Vercel
- Netlify
- Any Node.js hosting platform

### Backend
The backend runs on Strapi and can be deployed to:
- Strapi Cloud
- Heroku
- Railway
- Self-hosted servers

## 📚 API Documentation

### Key Endpoints
- `GET /api/recipes` - Fetch recipes
- `POST /api/recipes` - Create new recipe
- `GET /api/pantry-items` - Fetch user's pantry
- `POST /api/pantry-items` - Add item to pantry
- `GET /api/saved-recipes` - Fetch user's saved recipes
- `POST /api/saved-recipes` - Save a recipe

For complete API documentation, visit the Strapi admin panel at `http://localhost:1337/admin`

## 🤝 Contributing

We welcome contributions! Please feel free to submit a Pull Request.

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 💬 Support

For issues and feature requests, please open an issue on GitHub.

---

**Built with ❤️ to reduce food waste and inspire home cooks everywhere.**
