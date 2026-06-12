---
title: "Keyboard not working with jaunty alternate cd"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by rasca7 on 2009-04-25
Hi, i'm trying to install Jaunty from the alternate CD onto my Macbook 1,1. I have a grub2 bootloader and I use this parameters:
```
root=(hd0,6)
linux /vmlinuz root=/dev/ram0
initrd /initrd.gz
```
When it starts and reaches the select language screen, the keyboard doesn't work and I have to hard reset the mac. It works fine with the Intrepid alternate cd (same parameters), so I have no idea what's happening. Any clue?
If this is not the apropiate forum please move it, or tell me where should I post ir. Thank's to you all very much.

---

### Post by Spiritous on 2009-04-25
> **rasca7 said:**
> Hi, i'm trying to install Jaunty from the alternate CD onto my Macbook 1,1. I have a grub2 bootloader and I use this parameters:
```
root=(hd0,6)
linux /vmlinuz root=/dev/ram0
initrd /initrd.gz
```When it starts and reaches the select language screen, the keyboard doesn't work and I have to hard reset the mac. It works fine with the Intrepid alternate cd (same parameters), so I have no idea what's happening. Any clue?
If this is not the apropiate forum please move it, or tell me where should I post ir. Thank's to you all very much.

Use the Intrepid* alternative CD? You answered your own question

Edit: Typo

---

### Post by rasca7 on 2009-04-25
Thanks Spiritous.. But i would like to install Jaunty, not Intrepid. I've tried with Intrepid's vmlinuz and initrd, and Jaunty's ISO but it says (somewhere in the middle of the installation) the kernel version is incorrect, and that it might install the incorrect modules. Any ideas?

---

### Post by Yoghurt_LX on 2009-04-25
Installed Jaunty new from alternate Cd because upgrading Intrepid didn't work.
Now i have nearly every 2nd time i boot up to Jaunty a login screen, but no Keyboard or Mouse available.
Grub works fine and i can select, but somehow Jaunty does loose Keyboard and Mouse on the way to the login screen.
Have to reset and than it works.

Guess Intrepid will be my future since provided NVidia drivers doesn't work too.

---

