---
title: "Deleting ubuntu broke my eee?"
date: 2008-09-28
forum: Hardware
---

### Post by ZankerH on 2008-09-28
So I've tried installing ubuntu-eee on my new netbook. I've set aside a half of the 16gb SSD for it, keeping the rest of the default xandros installation intact. Dual booting worked fine, until I've decided I prefer shorter boot times and stable networking, so I've decided to delete ubuntu by deleting it's partitions and extending the Xandros ones back across the entire disk. Now, when I try to boot, I get a GRUB error 22.

Did I just become a proud owner of a $400 brick?

---

### Post by rsambuca on 2008-09-28
You will just need to re-install grub to the MBR using a liveCD or live USB stick.  Error 22 means that grub is loading, but is looking for the menu.lst file on a partition that no longer exists.  If you have a live USB stick, just open a terminal and re-install grub, but point it to the original Xandros partition.

---

### Post by ZankerH on 2008-09-28
Unfortunately, I'm unable to enter the boot menu by pressing esc. I still go immediately to the grub error screen.

---

### Post by ZankerH on 2008-09-28
OK, a little update: I'm able to get into BIOS by holding F2 during startup, but no matter how I change the boot device priority, I still end up with the GRUB error.

---

### Post by ZankerH on 2008-09-28
When I set removable media as the first boot device and disabled the SSD boot option, I get the following error, with my flash drive inserted:

Reboot or Select proper Boot device
or Insert Boot Media in selected Boot device and press a key

---

### Post by rsambuca on 2008-09-28
You need to use a bootable Live USB stick for this.  What distro is on the USB stick?

---

### Post by Stardust85 on 2008-11-11
I have the same problem. I have eeebuntu on my kingston 4GB flash created by isotostick.sh. It boots on my desktop PC. So the problem will be maybe in bios? I'm gonna look for flashing bios... And what is really strange, I managed to boot Damn Small Linux on the same eee but with a smaller flash (128MB)

---

### Post by mylo9000 on 2008-11-11
i don't know if this works on all of the asus eee pc models, but when i turn on my eee the eee bios screen comes up (gray screen with eee on it). i then press <esc> once when the bios finishes loading i get a menu with one time boot device options. i select my usb pendrive (kingston data traveler) and it boots from that device.

maybe it'll work for you. 
worth a shot.

---

### Post by Stardust85 on 2008-11-11
I tried this and it really works! :) thank you very muuch. I don't know if it is because I flashed to the newest version of bios... (in Xandros easy gui: Settings -> Add/Remove applications...)

---

### Post by Stardust85 on 2008-11-11
So it worked... And then I restarted and it didn't work again. And then I found out the trick: you have to totally power off your eee, then unplug the AC cable, wait for more than 5 seconds, connect it again and then turn it on and press Esc and it will work

---

### Post by mylo9000 on 2008-12-18
i've read around the web that some people need to pulse the <esc> key while the bios loads to get a consistent one-time-boot menu. i guess not all hardware is created equal.

i'm glad you have a way do get it to work tho.\\:D/

---

