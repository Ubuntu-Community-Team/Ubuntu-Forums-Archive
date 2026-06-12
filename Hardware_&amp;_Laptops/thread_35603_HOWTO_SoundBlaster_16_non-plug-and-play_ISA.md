---
title: "HOWTO: SoundBlaster 16 non-plug-and-play ISA"
date: 2005-05-19
forum: Hardware &amp; Laptops
---

### Post by StarkD on 2005-05-19
Hi everyone!

I've been using Ubuntu for a couple of weeks and I'm happy to contribute with a little how to. I've tried many different solutions from this forum and with this solution you can play several sounds at the same time. The problem is the "killall esd"-part. snd-sb16 is a ALSA sound driver and only GNOME freezez, both KDE and XFCE works fine.

1. Assumes that your card is set to standard I/O

2. $ sudo gedit /etc/modules
add the line:
snd-sb16

3. $ sudo gedit /etc/modprobe.d/snd-sb16
add the line:
options snd-sb16 isapnp=0

4. Make sure that ESD is chosen as the audio output at System -> Preferences -> 
Multimedia Systems Selector

5. Reboot

6. Login with your user account

7. When GNOME freezes press Ctrl + Alt + F1

8. Login with your user account

9. $ killall esd

10. $ logout

11. Ctrl + Alt + F7



ALTERNATIVE

The difference with this solution is sb which is a old OSS sound driver instead of the new snd-sb16 ALSA sound driver. This one worked fine for me until I installed my all-in-one HP PSC 950, then the sound got really twisted.

1. $ sudo gedit /etc/modules
add the line:
sb io=0x220 irq=5 dma=1 dma16=3

2. Reboot

3. If it doesn't work reinstall everything in synaptic that contains oss, alsa, esd and sound.

---

