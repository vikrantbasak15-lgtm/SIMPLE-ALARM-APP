# Alarm Studio (WakeOS)

A mobile-first alarm clock that runs in the browser. It is a single HTML file with no build step and no dependencies. It includes alarms, a sleep planner, a countdown timer and a stopwatch.

## Features

- **Alarms**: create, edit, delete and switch alarms on or off. Each alarm has a time, label, sound, repeat days and a dismiss mode. Sort the list earliest-first or latest-first.
- **Real ringing**: when an alarm's time arrives, a full-screen alert appears with a looping tone and vibration (on devices that support it). You can **Snooze** for 5 minutes or **Dismiss**.
- **Repeat days**: pick any days of the week. An alarm with no days is one-time and switches itself off after ringing.
- **Four sounds**, all generated in the browser with the Web Audio API (no audio files):
  - Solar Rise: a warm rising arpeggio
  - Forest Air: a soft pad with bird-like chirps
  - Pulse Max: loud, urgent beeps
  - Study Bell: a clean bell
- **Dismiss modes**: the Math challenge asks you to solve a multiplication problem before the alarm stops. See [Known limitations](#known-limitations) for the other modes.
- **Sleep planner**: set a wake time and sleep goal to get a recommended bedtime. One tap creates a bedtime reminder alarm.
- **Timer**: a countdown with quick presets (5, 15, 25, 45, 60 and 90 minutes). It rings when it finishes.
- **Stopwatch**: start, pause, reset and lap timing.
- **Light and dark theme**: use the toggle in the top bar.

## Getting started

1. Download `mobile-alarm-app.html`.
2. Open it in any modern browser (Chrome, Edge, Safari, Firefox). On a phone, open it in the browser or add it to your home screen.
3. **Tap anywhere once.** Browsers block audio until you interact with the page, so this unlocks sound. The note under the alarm list changes to "Sound is ready" when it works.
4. Add an alarm from the **Create** tab and leave the page open.

You can also host the file anywhere that serves static files, such as GitHub Pages or Netlify.

## Using the app

| Tab | What it does |
| --- | --- |
| Alarms | See, toggle, edit, preview and sort your alarms. Shows the next alarm and its morning flow. |
| Sleep | Set your wake time and sleep goal, see your recommended bedtime, and create a bedtime alarm. |
| Timer | Countdown timer with presets, plus the stopwatch with laps. |
| Create | Add a new alarm and choose its sound from the sound picker. |

Tap **Preview sound** on any alarm, or **Preview tone** on the Create tab, to hear a sound before you rely on it.

## Data and storage

Alarms and the sleep plan are saved in your browser's `localStorage` under `alarmStudio.alarms` and `alarmStudio.sleep`. Nothing is sent to a server. Clearing your browser data removes your alarms. The theme choice is not saved and resets to dark on reload.

## Known limitations

- **The page must stay open.** A web page cannot ring when it is closed, in a background tab that the browser has suspended, or on a locked phone (especially on iOS). For a wake-up alarm you can fully rely on, you would need a native app or a PWA with notifications.
- **Shake phone and Scan QR** need device sensors and a camera flow that this page does not implement. Alarms set to those modes show a plain Dismiss button.
- **Morning flow** (lamp, smart home) is a visual outline only. It does not control any devices.
- The font (Satoshi) loads from Fontshare. If you are offline, the app falls back to your system font.

## Customizing

Everything is in the one file:

- **Sounds**: edit the `CYCLES` object in the `<script>` section. Each sound is a short function that schedules oscillator notes.
- **Timer presets**: edit the `PRESETS` array.
- **Colors and spacing**: change the CSS variables at the top of the `<style>` block (`--color-primary`, `--radius-*`, `--space-*`).
- **Snooze length**: change `5*60000` in the snooze button handler.

## Tech

HTML, CSS and vanilla JavaScript. It uses the Web Audio API for sound, the Vibration API where available, and `localStorage` for saving data.
