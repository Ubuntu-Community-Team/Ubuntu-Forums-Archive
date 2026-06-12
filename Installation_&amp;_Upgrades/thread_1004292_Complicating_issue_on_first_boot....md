---
title: "Complicating issue on first boot..."
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by ukulele_ninja on 2008-12-07
Literally just found a fix for a grub issue I was having (see thread about 'error 2'. The motherboard (ASUS M2N-Plus SLI Vista Edition) I have had an option in the bios that enabled an 'ASAP' drive that has something to do with Vista ready Boost. I disabled that and it got past the Grub error, but now I have a screen that says: 

'Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
     -Check rootdelay= (did the system wait long enough?)
     -Check root- (did the system wait for the right device?)
-Missing Modules (cat/proc/modules; 1s /dev)
ALERT! /dev/disk/by-uuid/0b74cbf5-f202-43cc-8484-7ea539dd0573 does not exist. Dropping to shell!


BusyBox ve1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) _[prompt here]

...after the Grub loads, where the splash screen should be.

I wouldnt even know where to begin addressing this one...

Its very late, ill pick up here in the morning hopefully somebody has a solution for this one. Thanks!

---

### Post by ukulele_ninja on 2008-12-07
*bump*

---

### Post by petteriIII on 2008-12-07
I have had the same error. With me it came because the UUID that is refetenced in /boot/grub/menu.lst and the UUID referenced in /etc/fstab didn't reference to the UUID of Ubuntu's partition. 
To correct the situation boot with live-CD and check the UUID:s in your disk by the command: sudo blkid    and cut the correct UUID from the list. Mount the partition in harddisk by command: sudo mount -t ext3 /mnt and give commands: gksudo gedit /mnt/boot/grub/menu.lst and: gksudo gedit /mnt/etc/fstab and paste the correct UUID into them in correct places.
- But then your PC may error in something else.

---

### Post by ukulele_ninja on 2008-12-07
> **petteriIII said:**
> I have had the same error. With me it came because the UUID that is refetenced in /boot/grub/menu.lst and the UUID referenced in /etc/fstab didn't reference to the UUID of Ubuntu's partition. 
To correct the situation boot with live-CD and check the UUID:s in your disk by the command: sudo blkid    and cut the correct UUID from the list. Mount the partition in harddisk by command: sudo mount -t ext3 /mnt and give commands: gksudo gedit /mnt/boot/grub/menu.lst and: gksudo gedit /mnt/etc/fstab and paste the correct UUID into them in correct places.
- But then your PC may error in something else.

Im really not sure what your telling me to do or how to cut the correct UUID, can you elaborate?, I should add its happening after the splash screen not before as I originally mentioned.

---

### Post by ukulele_ninja on 2008-12-07
Can I install an older version of Ubuntu and upgrade to 8.10? Im wondering if an older version might work better.

---

### Post by ukulele_ninja on 2008-12-07
gksudo gedit /mnt/boot/grub/menu.lst and: gksudo gedit /mnt/etc/fstab


when I do these Im gettin No such file or directory I/O errors

---

### Post by sdb2028 on 2008-12-07
Try this: 
gksudo gedit /boot/grub/menu.lst /etc/fstab
(dont use /mnt)

---

### Post by ukulele_ninja on 2008-12-07
what uuid do i need to put into the file? I assume the one that says its the boot one?

---

### Post by ukulele_ninja on 2008-12-07
sdb, heres whats in my fstab file using your suggestion:

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

The menu.lst file is empty

---

### Post by ukulele_ninja on 2008-12-07
Just tried installing mythbuntu and got the same error as before. Is it possible I have a bad HDD or something? Im so freaking fed up at this point :(

---

### Post by henrik65 on 2008-12-07
Sounds like my problem, I'm over in
[http://ubuntuforums.org/showthread.php?p=6325225](http://ubuntuforums.org/showthread.php?p=6325225)

---

### Post by ukulele_ninja on 2008-12-07
Went out and picked up a 500gig SATA HDD to replace the IDE one I was using, solved the problem! My other HDD must have been dying.

---

