---
title: "Dell m4300 Nvidia Quadro FX 360M - HELLP?"
date: 2009-04-17
forum: Hardware
---

### Post by u.2 on 2009-04-17
Hi,
I have a Dell m4300 Nvidia Quadro FX 360M and I can't get the resolution to display as it was in windows.

The resolution in the BIOS is showing as 1280x800, but when running windows XP I had it at 1920x1200

I have tried editing the xorg.conf file, used the Nvidia-xconfig, nvidia-settings, and a ton of other things like editing the /etc/default/ restricted linux modules file with an entry I found on an nvidia forum.

Any ideas?  I found someone's posted x file here with the same laptop and that didn't do it.

I tried xrandr --newmod and --addmode yet still nothing.

I have no way to choose any other resolution aside from auto or manual 1280x800.
I know the bios info is wrong and if I reinstall windows it would go back to the higher option.

Any ideas?

---

### Post by need2knowlinux on 2009-05-30
Running M4300 w/Quadro FX 360M also. Just upgraded to 9.04 from 8.04. It is much better. Came across your thread looking for audio driver pkg for same. Audio goes from barely to whisper in 9.04. On your problem, Go to administration, hardware drivers, this is were you configure 3rd party and proprietary driver. NVIDIA is 3rd party. Had same issue when I 1st loaded Ubuntu. Follow the menu and it will go out and get the proper pkg for that device and install it. I am running 1920x1200. Good luck. Is your audio working OK? If so what device on m4300 and settings?

---

