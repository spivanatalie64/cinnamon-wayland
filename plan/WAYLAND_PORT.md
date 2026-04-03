# Cinnamon Wayland Porting Plan

This document outlines the tasks required to fully port Cinnamon to Wayland.

## Core Components

- [ ] **Muffin (Window Manager)**: Ensure Muffin has full Wayland support (forked from Mutter).
- [ ] **Cinnamon Shell (C code)**:
    - [ ] Handle input regions in Wayland (`cinnamon-global.c`).
    - [ ] Port Tray Manager to support Wayland (StatusNotifierItem).
    - [ ] Port any other X11-specific code in `src/`.
- [ ] **Cinnamon Shell (JS code)**:
    - [ ] Support restarts in Wayland (currently disabled).
    - [ ] Enable gestures in Wayland.
    - [ ] Port Applets to Wayland (if they use X11 specific features).
    - [ ] Fix `ScreenShield` and `BackupLocker` for Wayland.
- [ ] **XWayland**: Ensure seamless integration for X11 apps.

## Specific Tasks

### 1. Tray Manager / System Tray
Cinnamon's current Tray Manager is X11-only.
- [ ] Implement a StatusNotifierItem (SNI) watcher and host in Cinnamon.
- [ ] Update `statusIconDispatcher.js` to work on Wayland using the new SNI implementation.

### 2. Input Handling
- [ ] Port `cinnamon_global_set_stage_input_mode` and `cinnamon_global_set_stage_input_region` to Wayland.
- [ ] Enable gestures in `js/ui/gestures/gesturesManager.js`.

### 3. Session Management
- [ ] Improve `cinnamon-wayland.session`.
- [ ] Handle Cinnamon restarts in Wayland (requires Muffin/Mutter support for state preservation or quick restart).

### 4. Extensions and Applets
- [ ] Audit extensions for X11 dependencies.
- [ ] Provide Wayland-compatible alternatives for common X11-only features.

## Progress Tracking
- 2026-03-10: Initial research and plan creation.
