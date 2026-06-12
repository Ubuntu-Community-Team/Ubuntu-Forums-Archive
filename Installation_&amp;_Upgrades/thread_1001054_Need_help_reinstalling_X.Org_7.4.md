---
title: "Need help reinstalling X.Org 7.4"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by Verdugo on 2008-12-03
Can someone help me reinstall xserver 7.4? I had upgraded to a beta version of 8.10 and it messed up the xorg.conf because I have an ati video card. I had read that I needed to downgrade xserver at the time to one that was supported. I was able to remove xorg 7.4 but since can't access the internet from the root shell I don't know how to reinstall xorg from the live cd. I would greatly appreciate any help on this because I don't want to resort to a full reinstall of Ubuntu.  Basically, I can only access the shell from the recovery mode. Thank you to anyone that attempts to help me.

---

### Post by Partyboi2 on 2008-12-03
You could try booting the live cd and using chroot to install xorg. This would require you having a working internet connection while using the live cd.
Open a terminal (Applications>Accessories>Terminal)
```
sudo mount /dev/sda1 /mnt 
``` *change /dev/sda1 to correct one, if not sure  check the output to ```
sudo fdisk -l
``` or post results.
Then chroot
```
sudo chroot /mnt
```Followed by```
sudo apt-get update
``````
sudo apt-get install xorg
```then unmount and reboot.
```
 sudo umount /dev/sda?
```

---

### Post by Verdugo on 2008-12-04
Thank you for responding. I had found this solution on another thread right before you had replied and it worked. Thanks again for your help.

---

