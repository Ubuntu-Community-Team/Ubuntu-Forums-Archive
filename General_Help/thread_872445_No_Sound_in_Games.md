---
title: "No Sound in Games"
date: 2008-07-28
forum: General Help
---

### Post by Unanimated on 2008-07-28
Okay, here's my problem.

I was playing World of Padman, when it suddenly crashed. I had forgotten to turn off Visual Effects. After messing around with the arrow keys after pressing Ctrl + Alt + Delete, I finally hit Shut Down (my mouse wasn't moving, for some reason). My computer shut down, and I turned it back on and logged in again. I went to open Tremulous, and there was no sound at all. I opened World of Padman and PulseAudio, set WOP to windowed mode and looked on PA to see if there was an input. Nothing showed up. I closed WOP and went to a thread that told me how to set it up, and now I get sound from flash movies. However, whenever I run a game, there is still no sound. I can't use the terminal command that sets up a program for PulseAudio because I installed most of my games manually, and we all know that Frets On Fire is really bad from the repos. Can someone help?

Things were working perfectly up until WOP crashed.

---

### Post by iaculallad on 2008-07-28
> **Unanimated said:**
> Okay, here's my problem.

I was playing World of Padman, when it suddenly crashed. I had forgotten to turn off Visual Effects. After messing around with the arrow keys after pressing Ctrl + Alt + Delete, I finally hit Shut Down (my mouse wasn't moving, for some reason). My computer shut down, and I turned it back on and logged in again. I went to open Tremulous, and there was no sound at all. I opened World of Padman and PulseAudio, set WOP to windowed mode and looked on PA to see if there was an input. Nothing showed up. I closed WOP and went to a thread that told me how to set it up, and now I get sound from flash movies. However, whenever I run a game, there is still no sound. I can't use the terminal command that sets up a program for PulseAudio because I installed most of my games manually, and we all know that Frets On Fire is really bad from the repos. Can someone help?

Things were working perfectly up until WOP crashed.

Try installing the sound wrapper for non-Free flash plugin:

```
sudo apt-get install libflashsupport
```

---

### Post by Unanimated on 2008-07-28
That seems to have done it. Thanks!

---

### Post by Unanimated on 2008-07-28
Ok, nevermind--there only seems to be sound in these games when Amarok is running, and when I close them when it isn't, they crash, forcing me to do a hard reset on my computer. Tremulous is stubborn and won't let my cursor out of the screen, so I can't really do anything. Also, when Amarok isn't running, there's no sound, but it closes immediately, at least in World of Padman.

---

