---
title: "Second Optical Drive(DVD) not working"
date: 2005-03-31
forum: Hardware &amp; Laptops
---

### Post by ardvark on 2005-03-31
I've added a DVD drive after loading Warty. I couldn't access it at all. At least 1 thread mentioned disabling that drive in Bios, so I tried that. I now show a /dev/hdc (for the CDROM) and a /devhda (for the DVD), Warty created both sybolic links for CDROM and DVD pointing to /dev/hda. So I deleted the incorrect one and made a new link for CDROM. which made the CDROM operational again. The first problem is as soon as I reboot, it goes back to having both links pointing to the same device. The second problem, even with the liinks corrected, /dev/hda (for the DVD) is not mounted.  FSTAB shows /dev/hdc mounted as /media/CDROM, but there is no /media/DVD file to mount to. Should there have been a /media/DVD created somehow?? The DVD drive does show up in Totem as a drive to use, so at least some part of Warty is seeing it.

---

### Post by Juergen on 2005-04-01
To me it seems the udev configuration assumes you have only one cdrom/dvd.

Try to change the file /etc/udev/cdsymlinks.sh where it says 'echo cdrom dvd' to only be 'echo dvd'

I don't know how this would work if you had more than one dvd or more than one cdrom, though. 
If you fully understand this udev-stuff, please tell me :-)

I don't think it creates a /media/dvd dir automatically, so create it and add the entry to fstab manually

---

### Post by ardvark on 2005-04-01
Thanks for the reply & help. I'll list what I did in case someone else has this problem. I first went to the /media directory and created a directory called dvd0. Then I created a symbolic link   ln -s dvd0 dvd. I then edited /etc/fstab and added the line

/dev/hda    /media/dvd0   udf,iso9660   rw,user,auto   0  0

Next I went to /dev and removed the incorrect symbolic link which had CDROM linked to /dev/hda, and created a new symbolic link making CDROM linked to /dev/hdc.
Last, I made the change to /etc/udev/cdsymlinks.sh that was suggested above. After rebooting, I still have the correct symbolic links and I can access both CD and DVD. I can't watch a DVD movie yet, but that, so far, appears to be something missing in TOTEM.

Thanks again fot the help.

---

