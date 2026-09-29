```markdown
# 🎵 Sonus

### Your music. Your library. Your listening history.

**Sonus** is a cross-platform music player and personal listening analytics platform built with Flutter.

Rather than treating a local music library as just a collection of audio files, Sonus is designed to build a persistent music ecosystem around it — combining library management, playback, metadata, listening history, personal charts, analytics, and cloud-backed user data.

> 🚧 **Sonus is currently under active development.**
>
> The application is being actively developed and refined. This repository serves as the public showcase and documentation hub for the project. The production source code is maintained privately.

---

## ✨ Features

### 🎧 Music Playback

Sonus includes a dedicated playback system designed to provide consistent playback state throughout the application.

Current functionality includes:

- Audio playback and seeking
- Play/pause controls
- Previous and next track navigation
- Playback queue management
- Repeat behavior
- Track transitions
- Persistent Now Playing state
- Audio session management
- Integration between playback and listening analytics

---

### 💿 Local Music Library

Users can import and organize locally stored music while Sonus maintains structured relationships between the underlying media and its metadata.

The library system handles:

- Tracks
- Albums
- Artists
- Album artwork
- Audio metadata
- Local media references
- Lyrics
- Library search
- Metadata editing
- Persistent library storage

Imported music is processed into Sonus's internal data model rather than being treated as a simple list of files.

---

### 📊 Listening Analytics

Sonus records actual playback activity to build a persistent history of a user's listening behavior.

The analytics system is designed around a simple principle:

**Playback Events → Qualified Listens → Derived Statistics → Insights**

This allows listening statistics to be calculated from historical playback data instead of relying on disconnected counters maintained by individual screens.

Analytics infrastructure supports data such as:

- Track listening history
- Artist listening activity
- Album listening activity
- Play counts
- Listening duration
- Historical trends
- Ranked listening data
- Time-based statistics

---

### 📈 Personal Music Charts

Listening activity feeds into a custom chart system that transforms personal listening history into ranked music charts.

The chart architecture supports:

- Ranked tracks
- Ranked artists
- Ranked albums
- Historical chart snapshots
- Previous positions
- Position movement
- Peak positions
- Chart longevity
- Chart history
- Notable chart moments

The goal is to give users their own evolving music charts based entirely on how they actually listen.

---

### 🏠 Personalized Home Experience

Sonus includes a data-driven Home experience built from the user's library and listening activity.

Home content can surface personalized information derived from:

- Recently played music
- Listening activity
- Library data
- Artists and albums
- Personal rankings
- Historical listening behavior

This allows the application to become increasingly personalized as the user's listening history grows.

---

### 📝 Lyrics

Sonus supports lyrics as part of the music library and playback experience.

Lyrics can be associated with tracks and surfaced alongside playback, allowing lyric data to remain connected to the user's local music collection.

---

### 🔎 Library Search

A dedicated search architecture allows users to navigate larger music libraries without manually browsing through their entire collection.

Search is integrated with Sonus's underlying library repositories rather than operating as a standalone UI filter.

---

### ☁️ Accounts & Cloud Infrastructure

Sonus includes account and synchronization infrastructure designed to eventually allow user data to persist beyond a single installation.

Current infrastructure includes:

- Google authentication
- Supabase integration
- User identity management
- Cloud-backed data synchronization
- Local/cloud data coordination

The application remains local-first while cloud functionality is progressively expanded.

---

## 🧠 Architecture

Sonus uses a **feature-oriented layered architecture** intended to keep UI, business logic, persistence, and external services separated as the application grows.

```text
                         ┌─────────────────────┐
                         │      Flutter UI     │
                         │   Pages & Widgets   │
                         └──────────┬──────────┘
                                    │
                         Controllers / Scopes
                                    │
                         ┌──────────▼──────────┐
                         │ Application Services│
                         │ & Feature Logic     │
                         └──────────┬──────────┘
                                    │
                         Domain / Repositories
                                    │
                 ┌──────────────────┴──────────────────┐
                 │                                     │
        ┌────────▼────────┐                   ┌────────▼────────┐
        │ Local Persistence│                  │ Cloud Services   │
        │ SQLite / DAOs    │                  │ Supabase / Auth  │
        └─────────────────┘                   └─────────────────┘
```

Major features are separated into combinations of:

**Presentation**  
Flutter pages, reusable widgets, visual state, and user interaction.

**Application**  
Controllers and services responsible for coordinating application behavior.

**Domain**  
Entities, repository contracts, models, and business rules.

**Data**  
SQLite DAOs, repository implementations, mappers, local persistence, and external service integrations.

This structure allows features such as playback, analytics, charts, importing, and synchronization to evolve without tightly coupling them to the UI.

---

## 🧩 Major Systems

Sonus is currently organized around several major feature areas:

```text
Sonus
│
├── Account & Authentication
├── Analytics
├── Artwork Management
├── Personal Charts
├── Home
├── Music Import
├── Library
├── Playback
├── Search
├── Settings
├── Application Shell
└── Cloud Synchronization
```

Each system owns its relevant application, domain, data, and presentation responsibilities.

---

## 🛠️ Tech Stack

| Area | Technology |
|---|---|
| Application | Flutter |
| Language | Dart |
| Local Database | SQLite / sqflite |
| State Management | Provider |
| Audio Playback | just_audio |
| Audio Sessions | audio_session |
| Authentication | Google Sign-In |
| Cloud Backend | Supabase |
| File Access | Storage Access Framework / File Picker |
| Media Processing | Audio metadata parsing |
| Identity | UUID-based entities |
| Testing | Flutter & Dart testing infrastructure |

---

## ⚙️ Engineering Highlights

### Local-First Data Model

Sonus is designed around persistent local data.

Library information, playback activity, analytics, and other application state can remain available independently of cloud connectivity.

---

### Event-Based Listening History

Listening statistics originate from actual playback activity.

Instead of allowing individual features to maintain separate play-count systems, Sonus records listening events and derives higher-level statistics from that historical data.

This creates a common source of truth for features such as:

- Home
- Listening analytics
- Personal charts
- Historical statistics

---

### Structured Import Pipeline

Music importing involves more than locating an audio file.

Sonus processes imported media into structured entities and coordinates information such as:

```text
Audio File
    ↓
Metadata Extraction
    ↓
Track Identity
    ↓
Artist / Album Relationships
    ↓
Artwork
    ↓
Library Persistence
```

This gives the rest of the application a consistent music model to work with.

---

### Separation of Playback and UI

Playback is not owned by an individual screen.

Instead, playback behavior is handled through dedicated application infrastructure so that the queue, player state, analytics, and UI can interact with the same playback system.

---

### Historical Chart Modeling

Personal charts are designed as historical data rather than temporary rankings.

Chart entries can retain information about movement and previous performance, enabling Sonus to represent how a user's listening habits change over time.

---

## 🧪 Testing

Sonus includes automated tests across major parts of the application rather than limiting testing to individual UI components.

Testing currently covers areas including:

- Database behavior and migrations
- Authentication
- User identity
- Music importing
- Library management
- Playback
- Listening analytics
- Artwork
- Personal charts
- Home
- Lyrics
- Search
- Settings
- Application shell behavior
- Synchronization

Testing is expanded alongside the application's feature set.

---

## 🚧 Development Status

Sonus is an ongoing independent software project.

Development currently focuses on expanding and refining:

- Playback behavior
- Listening analytics
- Personal charts
- Personalized Home content
- Library management
- Cloud synchronization
- Android integration
- UI/UX
- Performance
- Testing and release hardening

The visual interface is also undergoing continued development.

Screenshots and demonstrations will be added to this showcase once the UI reaches a representative design milestone.

---

## 🗺️ Project Direction

Sonus is being built toward a music experience where the application doesn't simply play a user's collection — it **understands the history of that collection.**

The long-term goal is to combine:

**Playback**

**Library Management**

**Listening History**

**Personal Analytics**

**Music Charts**

**Cross-Device Data**

into a single cohesive experience centered around the user's own music.

---

## 🔒 Source Availability

Sonus is actively developed in a **private source repository**.

This public repository exists as a project showcase and technical overview. The production source code is not publicly distributed while the application remains under active development.

---

## 👨‍💻 Developer

**Patrick Casseus Jr.**

Computer Science graduate student and software developer focused on application development, interactive user experiences, data-driven features, and software architecture.

---

*Built with Flutter & Dart.*
```
