---
title: "Mounting iPod ..."
date: 2008-10-25
forum: General Help
---

### Post by pmooney78 on 2008-10-25
I can't get my iPod to mount automatically. Alas, it works OK when I reboot into Windows, so I know it's not a hardware problem. Here's what I've currently got in /etc/fstab:

LABEL=CROISSANT /mnt/Croissant vfat async,users,rw,auto,gid=100 0 0

Yes, it's really a vfat iPod. Yes, the volume label is "Croissant." Yes, this is what's reported for the label when I run "sudo udevadm info --export-db". I can't figure out what else to do. 

I'm running Xubuntu 8.04 on a Pentium III 550 MHz with 384 MB of RAM. Any advice is helpful.

---

### Post by pmooney78 on 2008-10-30
Figured it out. I just changed the entry in /etc/fstab so the first column reads LABEL=Croissant (instead of LABEL=CROISSANT) and it seems to work now. Even though udevadm info reports it in all caps, that's apparently not correct.

---

