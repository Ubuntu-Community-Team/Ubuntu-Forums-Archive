---
title: "Plantronics USB Headset : volume controller problem"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by filipebrandao_ on 2007-03-25
Here is my problem:

If i press the "volume up" or "volume down" of my headset buttons it changes the Bass volume instead of PCM volume! Same happens with my keyboard media keys.

how can i fix this problem?

---

### Post by Slarty Bardfast on 2007-04-03
I'm having the same issue. I think on a previous install I fixed it with gconf-editor but I never write these things down :confused: 

I'm guessing there's a way to re-map the buttons so they change a different slider on the mixer? I'm using a Plantronics Gamecon Pro (I'm at work, I think that's the name of it) and when I hit the volume buttons on it it changes the master volume but does not affect the sound level at all. Although i've set the default sound card as the headset I think this is just changing the volume on my integrated sound card..... Hmmmm If I figure it out I'll post an answer

---

### Post by khughitt on 2007-10-21
I'm having similar trouble issues with the volume buttons on the headset wire. Initially, the buttons changed the volume for the wrong device-- Instead of controlling the volume of the headset,** USB Device 0x47f:0cx001 (Alsa Mixer)**, it instead controlled the volume of the integrated sound card, **Intel ICH5 (Alsa Mixer)**.

I found [a fix on launchpad ]("https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/77105") (go to system--> sound, and you can select device to control from there). This may help with your problem.

Now however I have a different problem. Although the headset volume controls now control the USB Audio device volume, pressing the "volume up/down" buttons are very inconsistent. Pressing "volume up" several times, the volume will go up some, then back down, and occasionally only go up  in one earphone and not the other. Anyone else run into this?

---

### Post by filipebrandao_ on 2007-10-24
> **pwnedd said:**
> 

Now however I have a different problem. Although the headset volume controls now control the USB Audio device volume, pressing the "volume up/down" buttons are very inconsistent. Pressing "volume up" several times, the volume will go up some, then back down, and occasionally only go up  in one earphone and not the other. Anyone else run into this?


same here :(

---

### Post by khughitt on 2007-10-24
> **filipebrandao_ said:**
> same here :(

There is [a launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/155109") related to the problem we are having now. It might be helpful if you provided some information about your set-up there.

---

### Post by filipebrandao_ on 2007-10-25
> **pwnedd said:**
> There is [a launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/155109") related to the problem we are having now. It might be helpful if you provided some information about your set-up there.

Done. Thanks for reporting :P

---

### Post by dubcat on 2008-02-19
It's a gnome problem.

If you run alsamixer in a terminal window you can adjust the volume no problem.  Just type alsamixer -c <number of your usb device>.  For me this was alsamixer -c 1.  Now use cursor arrows to control volume.

---

