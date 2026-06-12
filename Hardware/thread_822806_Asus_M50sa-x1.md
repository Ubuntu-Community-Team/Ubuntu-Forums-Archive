---
title: "Asus M50sa-x1"
date: 2008-06-08
forum: Hardware
---

### Post by wasutton3 on 2008-06-08
i have ubuntu hardy heron 64 bit running on an asus m50 laptop
u have solved the other problems (brightness, webcam, fingerprint, etc)
but i cannot seem to get the sound to stop playing out of the speakers when i plug in headphones. any ideas?

(by the way, to configure the extra keys on laptops, i have found that keytouch is very effective)

---

### Post by 1nxr0x on 2008-07-23
Sorry I can't help you, but can you please tell me how to fix the ambient light sensor screen brightness problem? None of the supposed fixes that I've found work, or stay after reboot.

---

### Post by hotweiss on 2009-01-10
> **wasutton3 said:**
> i have ubuntu hardy heron 64 bit running on an asus m50 laptop
u have solved the other problems (brightness, webcam, fingerprint, etc)
but i cannot seem to get the sound to stop playing out of the speakers when i plug in headphones. any ideas?

(by the way, to configure the extra keys on laptops, i have found that keytouch is very effective)

A) First we’ll have to edit the ALSA configuration file via terminal:
sudo nano /etc/modprobe.d/alsa-base

B) Scroll down to the bottom and add this line:
options snd-hda-intel model=haier-w66

C) Hit Ctrl-O to save and then Ctrl-X to exit.

D) Reboot and your speakers will now automatically mute when you plug your headphones in.

---

