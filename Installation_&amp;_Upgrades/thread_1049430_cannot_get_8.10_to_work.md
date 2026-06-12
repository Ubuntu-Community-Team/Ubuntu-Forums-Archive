---
title: "cannot get 8.10 to work"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by merlin666 on 2009-01-24
I have been using Ubuntu for a few years, faithfully going from one version to the next. I was pleased with the easy transition from 7.10 to 8.04, and 8.04 worked very well for me with the exception of wireless connection. I hoped that 8.10 would remedy this shortcoming, and decided to go for the update. The following occurred: there was no GUI as gnome/xserver would not start. After removing the fglrx driver I was able to get into gnome, but it was a poor experience with several issues, such as no working arrow/cursor keys. After much experimenting, I lost access to xserver/gnome again, and searches through this forum did not yield any solutions to start it again, and I was advised that there is no "downgrade" path to go back to the excellent 8.04 configuration that I had before.

I decided to try a new installation (dual boot with XP) and downloaded and burnt the 8.10 install image to disc. I have not done this for years, so started with a manual partition etc3 set for a journaling file and / as mount point. I also added a generous logical partition for swap. The installation proceeded fine from there, until close to the end there was a fatal error stating that grub could not be installed. On reboot I get a boot menu that reflects my old configured menu.lst. When I select the linux kernel, I get to a login screen, but there is no keyboard or touchpad response. ctrl-alt-f2 goes to a terminal, and when I checked xorg.conf it shows empty headings. I am at a loss now. What is the proper way to a "clean" install that writes a fresh menu.lst and xorg.conf, and will still permit dual boot to XP?

---

### Post by lemming465 on 2009-01-25
The fglrx situation improved a bit with later updates, so if you can get into your fresh install and patch it current it may do better.  I'm not sure why the grub install failed; you can try fixing that by mounting your new root partition on a live CD and doing something like**sudo grub-install --root-directory=/dev/sda3 /dev/sda**, assuming your root partition got mounted at /media/sda3.  This assumes that /boot is a plain directory, not a mount point.  If the /media/sda3/boot/grub/menu.lst file doesn't have a clause for XP, you can add something like ```
title           Windows XO
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```
using your favorite text editor, such as gedit or nano or vim.  Edit as root (using sudo or gksu), of course.

Assuming that this gets you booting to at least a functional text console, the next thing to try is ```
sudo apt-get update; sudo apt-get upgrade; sudo reboot
``` followed by ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by merlin666 on 2009-01-26
Thanks, when reading through similar threads I noticed that the /etc3 needed to be formatted for a new install. This got rid of the old menu.lst etc and it seems that I'm up and running now. I have not tried yet to install a graphics driver, and have not found google earth in the synaptics list. will probably take a while for me to get to this.

---

