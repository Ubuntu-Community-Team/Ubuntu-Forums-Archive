---
title: "Troubles with default ALSA card"
date: 2005-11-29
forum: General Help
---

### Post by amarra on 2005-11-29
Dear Ubuntoers,

I've a trouble with my Kubuntu Breezy. Sometimes the KDE sound server doesn't start, giving the following message:

[FONT=Courier New][I]Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for playback (No such file or directory)
The sound server will continue, using the null output device.[/I]

I've a VIA 8237 motherboard integrated sound card and an USB webcam (Logitech QuickCam Zoom, with an integrated microphone)
I suspect that the problem arises because Ubuntu on boot sometimes swaps the order of the two detected sound devices, and when the USB sound card (the webcam) is identified as sound card 0 in ALSA, then KDE fails on loading the sound system (that's right, since the webcam is an INPUT device, it cannot be used as a playback device).
Default card in ALSA is 0.

How can I solve this problem? There is a way to fix the sound device order in ALSA?

Thanks.
[/FONT]

---

### Post by amarra on 2005-11-30
Nobody can help me?

Bye

---

