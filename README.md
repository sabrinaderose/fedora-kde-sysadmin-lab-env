# Fedora KDE SysAdmin Lab Environment

**Date:** 2025-07-27  
**Author:** [sabrinaderose](https://github.com/sabrinaderose)  
**Repository:** https://github.com/sabrinaderose/fedora-kde-sysadmin-lab-env  
**Category:** Homelab | Build | Configuration | Documentation  
**Related Certifications:** LPI Linux Essentials (Completed), Cisco CCNA (Upcoming), WGU B.S. Network Engineering & Security

---

## Objective

To build a clean, customizable Fedora KDE environment optimized for system administration, productivity, and homelab usage. This project tests usability, display behavior, and application layout configuration under Fedora 40 KDE Plasma, leading into future SSH-based home lab work with a Raspberry Pi.

---

## Environment & Tooling

### Hardware Used

- **Main System:** Custom desktop  
- **Primary Monitor:** DP-1 – 1920x1080 @ 144Hz (Main)  
- **Secondary Monitor:** HDMI-A-1 – 1080x1920 (Rotated)  
- **Input:** USB keyboard + mouse

### Software Environment

- **Operating System:** Fedora 42  
- **Kernel:** 6.x (default with Fedora 42)  
- **Desktop Environment:** KDE Plasma 6  
- **Display Manager:** SDDM  
- **Package Manager:** `dnf`, `flatpak`

---

## Step-by-Step Process

### Phase 1: Preparation

- Fedora 42 KDE installed as base environment.
- Display connected: primary via DP (landscape), secondary via HDMI (rotated to portrait).
- Verified output via `xrandr`.

### Phase 2: Configuration

- Custom layout created and saved as `displaylayoutsettings`.
- Multiple failed attempts to rotate HDMI-A-1 via `/etc/sddm/scripts/Xsetup`:
  ```sh
  xrandr --output HDMI-A-1 --primary --auto --rotate normal
  ```
  Resulted in distortion on lock screen (see screenshot).
- Script ultimately removed to restore visual integrity.
- KDE layout manager used instead to persist configurations.

#### Applications Installed

- KDE Essentials: Dolphin, Spectacle, Kate, Konsole, KRunner, Yakuake
- Developer Tools: Neovim, KDiff3, Ghostwriter, Filelight
- Layouts made for: Primary (Default), WGU Coursework, Home Lab Work
- Each layout has a unique wallpaper and functional use case

#### Panel Configuration

- Default bottom panel removed  
- Replaced with adaptive top bar for:
  - Activities
  - Clock
  - Status icons
- Final bottom panel added later to show open applications (task manager)
- Final setup screenshot: `finallayout.png`

### Phase 3: Testing

- Display tested through multiple reboots and sleep/wake cycles
- Identified screen corruption issue stemming from the SDDM `Xsetup` script
- KDE’s native layout manager and saved layout proved stable

### Phase 4: Troubleshooting

- **Issue:** Horizontal corruption on rotated monitor at lock screen  
  **Cause:** Incompatible or early execution of `xrandr` commands via SDDM's `Xsetup`  
  **Solution:** Removed script; used KDE layout manager only  
  **Outcome:** Stable and persistent configuration

---

## Analysis & Reflection

- Attempting to automate monitor rotation via `Xsetup` caused display corruption — KDE's internal config tools were more reliable.
- Sodium session manager presented unresolved conflicts when multiple rotated displays were involved.
- Display layout and system tools were successfully configured to support future sysadmin and homelab productivity workflows.

---

## Final Outcome

- Functional Fedora 42 KDE Plasma sysadmin desktop configured and themed  
- Productivity tools and layouts installed  
- Finalized for transition to SSH hardening with Raspberry Pi (see repo below)

---

## Screenshot Gallery (WIP)

- `finallayout.png`: Final desktop with bottom taskbar and top adaptive panel  
- Display corruption from SDDM/Xsetup: (refer to earlier captured image in documentation)  
- KDE layout arrangement panel screenshot (saved as `displaylayoutsettings`)  
- KRunner + Kate + Yakuake usage: [captured but not included here]

---

## Key Files and Scripts

- `displaylayoutsettings` – KDE Plasma saved monitor layout
- ❌ `/etc/sddm/scripts/Xsetup` – created and removed due to lockscreen corruption

---

## Interview/Resume Summary (STAR Format)

**S:** Needed a reliable and clean Fedora KDE environment for system admin home lab testing.  
**T:** Configure dual-display setup with rotation, KDE layouts, and essential productivity tooling.  
**A:** Installed and tested Fedora 40 KDE, handled display issues through system scripting, then migrated to KDE layout management.  
**R:** Finalized a stable sysadmin lab environment, documented for reproducibility and linked to future Raspberry Pi SSH hardening work.

---

## References & Resources

- https://wiki.archlinux.org/title/SDDM  
- https://wiki.archlinux.org/title/Xrandr  
- https://www.gnome-look.org/p/2163026 (KDE Splashscreen)  
- KDE Plasma Display Configuration Tool  
- KDE System Settings: Layouts, Panels, and Activities
