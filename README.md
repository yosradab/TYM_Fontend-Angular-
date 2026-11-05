# TYM — Train Your Mind · Frontend Angular

Interface web de la plateforme **Train Your Mind (TYM)** : les clients trouvent un spécialiste (coach, formateur), réservent des séances et des ateliers, paient en ligne et échangent par chat. Un back office permet à l'administrateur de piloter la plateforme.

Projet de fin d'études (PFE, 2023). L'API Spring Boot est ici : [TYM_Backend-SpringBoot-](https://github.com/yosradab/TYM_Backend-SpringBoot-).

## Fonctionnalités

### Front office (`/user`, `/workshop`, `/Client`)
- Inscription par rôle (client, spécialiste, admin), connexion **JWT**, code de vérification, mot de passe oublié et mise à jour
- Espace spécialiste : profil, **portfolio**, dépôt de CV, **agenda** (FullCalendar)
- Liste des **ateliers** et **réservation** de séances, avec confirmation
- **Paiement Stripe** au moment de la réservation
- Génération de **QR codes**
- Envoi et réception d'e-mails, désinscription de la newsletter
- Filtrage des mots inappropriés dans les messages

### Back office (`/admin`)
- Tableau de bord avec **statistiques** (Chart.js)
- Gestion des utilisateurs et des spécialistes : création, liste paginée, détails
- Gestion des **réservations**, des **contrats** (liste, détails, statistiques, export **PDF** avec jsPDF) et des offres
- **Chat** en temps réel (WebSocket) et messagerie e-mail

## Stack technique

| Élément | Technologie |
|---|---|
| Framework | Angular 15, TypeScript 4.9 |
| UI | Angular Material, Bootstrap 5 |
| Agenda | FullCalendar, angular-calendar, Syncfusion Calendars |
| Graphiques | Chart.js |
| Paiement | Stripe.js |
| Auth | @auth0/angular-jwt, ngx-cookie-service |
| Autres | jsPDF, angularx-qrcode, ngx-pagination, Moment.js, RxJS |

## Structure

```
src/app/
├── frontOffice/   # Pages utilisateur (inscription, profil, agenda, paiement, ateliers…)
├── backOffice/    # Pages admin (dashboard, stats, contrats, chat, mails…)
├── services/      # Appels HTTP vers l'API Spring Boot + WebSocket
├── models/        # Interfaces TypeScript (User, Booking, Workshop, Contract…)
└── app-routing.module.ts
```

## Lancer le projet

Prérequis : Node.js 16 ou 18, Angular CLI 15, et le [backend](https://github.com/yosradab/TYM_Backend-SpringBoot-) démarré sur `http://localhost:8075`.

```bash
npm install
npm start          # ng serve → http://localhost:4200
```

Build de production :

```bash
npm run build      # sortie dans dist/
```

La configuration (clés Stripe, etc.) se trouve dans `src/environments/`.

## Auteur

**Yosra Dab** — Ingénieure logiciel Full Stack · [Portfolio](https://yosradab.vercel.app) · [GitHub](https://github.com/yosradab) · [LinkedIn](https://linkedin.com/in/yosradab)
