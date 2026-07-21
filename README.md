# 🕵️‍♂️ Mr. White (Frontend)

Benvenuto nel frontend di **Mr. White**, un gioco interattivo di deduzione sociale basato su ruoli e parole segrete. Questa interfaccia permette ai giocatori di connettersi a stanze in tempo reale, scoprire le proprie identità e votare per scovare Mr. White!

## 🏗️ Tech Stack

Il progetto è sviluppato con tecnologie moderne per garantire un'esperienza utente fluida e reattiva:

| Categoria | Tecnologia |
| :--- | :--- |
| **Framework** | Next.js 16 (App Router) + React 19 |
| **Styling** | Tailwind CSS v4 |
| **State Management** | Redux Toolkit (`@reduxjs/toolkit`) |
| **Comunicazione Real-time** | SignalR Client (`@microsoft/signalr` v10) |
| **Icone** | Lucide React |
| **Linguaggio** | TypeScript |

## 🎮 Flusso di Gioco e Funzionalità

L'interfaccia gestisce l'intero ciclo di vita di una partita, sincronizzato in tempo reale tramite SignalR con il backend:

1. **Home (`/`)**: Inserisci il tuo nome e unisciti a una stanza esistente o creane una nuova.
2. **Lobby**: Sala d'attesa per radunare tutti i giocatori prima di iniziare.
3. **Assegnazione Ruoli**: Visualizzazione della carta segreta. Scopri se sei un **Civile** (con la parola segreta) o **Mr. White** (all'oscuro della parola).
4. **Fase di Discussione (Talking)**: I giocatori si alternano per fornire un indizio sulla propria parola.
5. **Votazione (Voting)**: Ogni giocatore vota la persona che sospetta essere Mr. White.
6. **Rivelazione (Revelation)**: Viene svelato l'esito della votazione e l'identità dell'eliminato.
7. **Fine Partita (End Game)**: Schermata riepilogativa con i vincitori e l'opzione per rigiocare.

## ⚙️ Prerequisiti

- **Node.js**: v20+ (il progetto utilizza Node 24 in produzione)
- Il **[Backend di Mr. White](https://github.com/roberto-ingenito-home-lab/mr-white-backend)** in esecuzione e accessibile.

## 🚀 Setup e Sviluppo Locale

1. Clona la repository e installa le dipendenze:
   ```bash
   npm install
   ```

2. Configura le variabili d'ambiente. Crea un file `.env.local` nella root del progetto:
   ```env
   # Sostituisci con l'URL effettivo del tuo backend
   NEXT_PUBLIC_API_URL=http://localhost:5000
   ```

3. Avvia il server di sviluppo:
   ```bash
   npm run dev
   ```
   L'applicazione sarà disponibile all'indirizzo `http://localhost:3000`.

## 🐳 Deployment con Docker

Il progetto è fornito di un `Dockerfile` multi-stage ottimizzato (basato su `node:24-slim` e output `standalone` di Next.js) per un facile deployment nei container.

Per buildare e lanciare l'immagine localmente:

```bash
# Build dell'immagine passando l'URL del backend come argomento
docker build --build-arg NEXT_PUBLIC_API_URL=https://api.tuodominio.com -t mr-white-frontend .

# Esecuzione del container sulla porta 3000
docker run -p 3000:3000 -d mr-white-frontend
```

---

## 🔗 Progetti Correlati

- [Mr. White Backend](https://github.com/roberto-ingenito-home-lab/mr-white-backend) — API .NET Core + SignalR
- [Homelab Infrastructure](https://github.com/roberto-ingenito-home-lab/server-raspberry-pi) — Infrastruttura server e deployment Docker
