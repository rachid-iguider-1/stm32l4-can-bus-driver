# 🚗 Driver CAN Bus Bare-Metal (CMSIS) pour STM32L4

Implémentation bas niveau d'un pilote de périphérique **bxCAN (Controller Area Network)** pour microcontrôleurs STM32 (série STM32L4 / STM32F4) en langage **C (Bare-Metal)** sans couche d'abstraction HAL/LL.

Ce driver gère l'initialisation matérielle des GPIOs avec fonctions alternatives, la configuration du contrôleur CAN (Bit Timing, modes Loopback/Silent), le filtrage d'identifiants, ainsi que la transmission et réception de trames de données.

---

## 🛠️ Caractéristiques et Périphériques

* **Accès Registres Directs (CMSIS) :** Manipulation explicite des registres `MCR`, `BTR`, `TSR`, `RIR`, `RF0R/RF1R` et `FMR`.
* **Multiplexage GPIO :** Support des options de remappage des broches :
  * `PA11 / PA12` (AF9)
  * `PB8 / PB9` (AF9)
  * `PD0 / PD1` (AF9)
* **Modes de Fonctionnement :** Support des modes Normal, Loopback (Bouclage) et Silent (Écoute seule).
* **Gestion des Filtres :** Configuration dynamique des filtres 16 bits / 32 bits en mode Masque ou Liste.
* **Emission / Réception :** 
  * Gestion des 3 Mailboxes d'émission avec vérification de disponibilité.
  * Réception FIFO 0 et FIFO 1 avec libération automatique des boîtes de réception (`RFOM`).

---

## 📁 Architecture du Code

```text
.
├── inc/
│   └── can.h        # En-tête : Définitions des structures, énumérations et prototypes
├── src/
│   └── can.c        # Implémentation : Configuration registres et fonctions E/S
└── README.md        # Documentation du projet
