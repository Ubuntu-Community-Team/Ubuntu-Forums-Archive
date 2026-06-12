---
title: "Snag following the RAID1 HowTo"
date: 2010-03-14
forum: Hardware
---

### Post by shortmort37 on 2010-03-14
I'm trying to follow the HOWTO for setting up a RAID1, here:

[http://ubuntuforums.org/showthread.php?t=1027240](http://ubuntuforums.org/showthread.php?t=1027240)

I ran into a snag -- but, maybe not.  I'd like for someone to tell me it's OK to enter "y" and proceed.  Here's the snag, posted at the end of the instructions, but yet no reply:

> OK -- I've decided to take the plunge, and work through these steps (except for RAIDing the swap partition; I'm foregoing that). Everything is going fine, until I get to this part:

[QUOTE]We need to put a file system onto the root partition of our new RAID 1 array. I use reiserfs so the command is 

     Code:
     sudo mkreiserfs -l root_raid1 /dev/md0 
When I do this, I get:

> ...
Guessing about desired format.. Kernel 2.6.31-20-generic-pae is running.
Format 3.6 with standard journal
Count of blocks on the device: 122095984
Number of blocks consumed by mkreiserfs formatting process: 11938
Blocksize: 4096
Hash function used to sort names: "r5"
Journal Size 8193 blocks (first block 1)
Journal Max transaction length 1024
inode generation number: 0
UUID: ca82295e-1427-494c-b576-a19abf527e28
LABEL: root_raid1
ATTENTION: YOU SHOULD REBOOT AFTER FDISK!
ALL DATA WILL BE LOST ON '/dev/md0'!Huh? What fdisk? That step was 10 steps back; and I did reboot. Or, is this a warning that after mkreiserfs invokes fdisk, I should reboot?

This is a scary warning I didn't anticipate. Sorry to sound like such a noob, but I'm not proceeding until someone tells me I'm not going to lose my drive...
[/QUOTE]

Dan

---

### Post by Fafler on 2010-03-14
I think it's just trying to tell you that IF you have run fdisk, you should reboot first. If you just created your array, there isn't any data too loose anyway. Go for it. Good luck ;)

---

### Post by shortmort37 on 2010-03-14
Well, that seemed to go OK -- thanks for the advice.  Now, I'm at this point:

> Update /mnt/mirror/boot/grub/menu.lst to boot from /dev/md0. You will also want to turn on the grub menu and make a few other small changes. Below are examples of the new lines for the grub menu just scroll through the file changing them as you go. The lines below are the changed lines with the new values.

Ain't got no ...boot/grub/menu.lst -- ain't got no grub, neither!  So I install it with Synaptic (which claims I need to deinstall grub-pc, which I do) -- and look for menu.lst again.  Ain't there.

What am I missing?

Dan

---

