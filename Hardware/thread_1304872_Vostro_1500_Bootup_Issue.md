---
title: "Vostro 1500 Bootup Issue"
date: 2009-10-29
forum: Hardware
---

### Post by Mr_Congeniality on 2009-10-29
Ok, I just installed from the live cd and booted up into my partition, and my screen is constantly blinking black and back to a terminal and I can't log in or anything, I think it has something to do with the graphics driver.

How can I install restricted graphics drivers for my NVIDIA 8600 card on my laptop without using X?

---

### Post by Mr_Congeniality on 2009-10-29
By the way, dpkg-reconfigure xserver-xorg does nothing.  Doesn't even load up a reconfiguerer.  I looked at my xorg config and it things the nvidia driver is already installed, which it is not.

---

### Post by Mr_Congeniality on 2009-10-29
Any other users who suffer from this issue who have wired ethernet connections, you should try this.

Boot up into recovery mode, select netroot as your means of recovery.
The command prompt will come up.

type in "sudo apt-get install nvidia-glx-185"
once everything is downloaded and installed, do "sudo nvidia-xconfig".

If anyone knows how to configure a wireless connection with just the terminal, can you possibly help out?

---

