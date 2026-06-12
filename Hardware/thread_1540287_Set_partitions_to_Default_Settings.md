---
title: "Set partitions to Default Settings"
date: 2010-07-27
forum: Hardware
---

### Post by Femster88 on 2010-07-27
Is there a way to restore my partitions to their original settings with Windows 7. I was trying to install Ubuntu but i need to Start from the top bc i messed up...Im using a Hp Pavilion dm4-1065dx...****

---

### Post by mandazi on 2010-07-27
> **Femster88 said:**
> Is there a way to restore my partitions to their original settings with Windows 7. I was trying to install Ubuntu but i need to Start from the top bc i messed up...Im using a Hp Pavilion dm4-1065dx...
I have a hp pavilion dm4-1060us.  Very similar to what you have I think.

I had to order the Recovery CD from HP.  It's 15 bucks including shipping and handling.

---

### Post by ks07 on 2010-07-27
It depends how you messed it up. Don't order any cds yet, instead give us some more details.

Also, boot from the live cd and do ```
sudo fdisk -l
``` in the terminal and post the output here. Thanks. :p

---

### Post by Femster88 on 2010-07-27
I went to Prepare disk space and went to Manually Specify my partitions...i then went to change the size of device: /dev/sda2 from 480Gb to 320Gb...when i did that it left me with 160Gb of free space... i then attempted to move forward but it denied me... i then went back to change the same device back to 480Gb...after that i believe i hit revert and then quit the installation...from then on, when i started up my labtop, it would go straight to the recovery system setup, but it would not allow me to recover any things...two error codes would pop up...0xE0EF0009 Null input string and code error 0xe0ef0003

---

### Post by ks07 on 2010-07-28
> **Femster88 said:**
> I went to Prepare disk space and went to Manually Specify my partitions...i then went to change the size of device: /dev/sda2 from 480Gb to 320Gb...when i did that it left me with 160Gb of free space... i then attempted to move forward but it denied me... i then went back to change the same device back to 480Gb...after that i believe i hit revert and then quit the installation...from then on, when i started up my labtop, it would go straight to the recovery system setup, but it would not allow me to recover any things...two error codes would pop up...0xE0EF0009 Null input string and code error 0xe0ef0003
Hmmm... If you canceled and quit the installation before changing the partitions then nothing should have changed, and your PC should still work fine.

Anyway, could you boot from the CD, choose try Ubuntu without installing (owtte) and then follow the instructions at [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) to give us a look at your system. Remember to use code tags! :popcorn:

---

