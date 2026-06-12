---
title: "Is it possible to save debug logs onto a USB stick from a jaunty alternate install?"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by tghe-retford on 2009-04-25
I've been wishing to reinstall Jaunty afresh on my computer, however I have stumbled across a networking problem where DHCP, which used to work, no longer does on the alternate install. I install using a USB stick and I am wondering whether it is possible to save the debug files to the same USB stick? No matter what I have tried, I either get told that the installation step to save the debug files has failed or the directory does not exist.

I have tried the web option, but it can't be accessed through the network, and I don't have a floppy disk drive, so can't use that option either.

Thanks in advance.

---

### Post by tghe-retford on 2009-04-25
I managed to get it sorted eventually. I had to get a second USB stick, and then I switched to a command line using CTRL+ALT+F2. I first entered:

```
ls /dev/sd*
```
And then inserted the second USB stick. I used the same code again to see where the USB stick was assigned to. In my case, it was /dev/sdc1.

I then mounted the USB stick on /media/USB, which I created beforehand.
```
mkdir /media/USB
mount -t vfat /dev/sdc1 /media/USB
```
Once it was mounted, I could go back to the Debian installer using CTRL+ALT+F1, press escape to get the main menu, scroll down to save debug logs, selected the mounted file system option, and enter the location to save the files to /media/USB. When I got back to the desktop, the install folder which contained the debug logs was on the USB stick. :)

---

