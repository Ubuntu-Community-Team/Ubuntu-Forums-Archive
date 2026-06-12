---
title: "can't get ide tape drive working"
date: 2005-12-03
forum: General Help
---

### Post by david-texas on 2005-12-03
Hello,
 I just installed 5.10 and I can't get my Seagate stt20000A ide tape drive to work. I looked in messages and saw where it found it at hdd but I can't see any stx in /dev/ and I can't access it with mt command. I think I added the hdd=ide-scsi line to menu.lst in grub but as there is no clear examples of this who knows. I wouldn't realy care but I had just backed up Home on the server (running fedora core 3) which had my banking info in it. Just before I wiped and loaded ubuntu. I would realy like to get that stuff back.

---

### Post by Lambert on 2005-12-04
See if you have a node htX

> The first IDE tape drive.  Subsequent drives are 	    numbered ht1 etc.  They are character 	    devices on major node 37 and start at minor node 0 for 	    ht0 1 for ht1 	    etc.  If you where to create this device by hand using mknod you would do:
 
 # mknod /dev/ht0 c 37 0


---

### Post by david-texas on 2005-12-04
Well I tried manual adding the ht0 but I am not shure it saw the drive when I did a mt status it didn't know that there was a tape in. So I thought I would reboot but after I logged back in ht0 was gone. I have just removed the ide-scsi line from my /boot/grub/menu.lst and will wait for some more help (or I will load fc3/4 back on and move the data off to floppy or cd)

---

