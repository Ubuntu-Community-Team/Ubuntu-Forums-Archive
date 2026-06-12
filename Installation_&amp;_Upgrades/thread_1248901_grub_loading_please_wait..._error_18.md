---
title: "grub loading please wait... error 18"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by ATK on 2009-08-24
first off i have 2 computers, both of which have the option to enable "USB Boot" in the BIOS. i used my first computer to install xubuntu 8.10 onto my 2Gb flash drive from the live CD. i did a full install, i did not make an install disk. before i installed xubuntu i unplugged both of the internal HDDs so i couldnt mess them up at all. the install worked fine, i made sure to install the boot loader on the flashdrive. when i was done i powered down, plugged the HDDs back in, restarted and with a few changes to the BIOS settings i was able to boot from the flash drive. a short while later i put the flashdrive in my second computer, changed some BIOS settings and restarted the computer. the computer tries to boot from the flashdrive but i get this message 

GRUB loading, stage1.5.
GRUB loading, please wait...
Error 18

also, in the BIOS settings for both computers the flashdrive is listed as a hard drive, i thought it would be a removeable device but im not sure. i dont know if this matters at all. any suggestions?
Thanks, ATK

---

### Post by philcamlin on 2009-08-24
this may turn out to be a variant of the problem I struggled with. Here's what I did:

1. Set the drive up in LBA mode in the BIOS. That should give disk geometry data with 255 Heads, probably 63 sectors.

2. Install Ubuntu normally. Never mind the /boot partition at the beginning.

3. After the core is installed, Ubuntu reboots the machine. At this point, I set the BIOS settings to "Normal" which gave my 4GB drive a disk geometry of about 8800 cylinders, 15 head, and 63 sectors. It rebooted the machine and...

4. GRUB started up fine and the Ubuntu installation finished.

If this does work I really don't know why. But I'd love to know what kind of hard drive you have and what your LBA and Normal disk geometry was.

Best of luck!

---

### Post by ATK on 2009-08-24
like i said, i installed xubuntu on a 2gig flash drive, my HDD should not matter at all

---

### Post by louieb on 2009-08-24
Sounds like a flaky BIOS in the 2nd computer.  Error 18 usually means GRUB or whatever it trying to boot is too far from the start of the drive to be read. 
That limit used to be about 8GB.  BIOS has improved modern BIOS has a limit in the 100s of GB.  How old is the 2nd pc?

[This is what Herman says about error 18]("http://members.iinet.net.au/%7Eherman546/p15.html#18") 

Since its just 2GB drive none of normal error 18 reasons or there fix apply.  

Not much help - about all I could suggest is try to find the BIOS update for your motherboard.

---

### Post by ATK on 2009-08-25
i found a sticker on the back of the 2nd computer that says the model number and then
MN04/02
im assuming that means minnesota, april, 2002

---

### Post by ATK on 2009-08-25
another quick question, if i were to make a boot partition at the beginning of the drive, what should the other partition be? just / ? or do i need it to be /home or something like that?
Thanks, ATK

---

### Post by ATK on 2009-08-26
nvrmd, figured this one out

---

### Post by Bigfootmech on 2009-08-28
> **philcamlin said:**
> this may turn out to be a variant of the problem I struggled with. Here's what I did:

1. Set the drive up in LBA mode in the BIOS. That should give disk geometry data with 255 Heads, probably 63 sectors.

2. Install Ubuntu normally. Never mind the /boot partition at the beginning.

3. After the core is installed, Ubuntu reboots the machine. At this point, I set the BIOS settings to "Normal" which gave my 4GB drive a disk geometry of about 8800 cylinders, 15 head, and 63 sectors. It rebooted the machine and...

4. GRUB started up fine and the Ubuntu installation finished.

If this does work I really don't know why. But I'd love to know what kind of hard drive you have and what your LBA and Normal disk geometry was.

Best of luck!

This... actually worked :O. Thank you :D.

All I did was swap the boot order to have normal HDDs first, then Removables, then CD and no error.

PS: For side information (people searching or whatever), I tried to make a bootable USB (16GB), the first one didn't succeed, but the second time I did a clean install on the USB - it wouldn't let me do this the first time so I followed a guide to making a flash drive instead of a live cd.

Anyway after the second install I could only get into the ubuntu bootable stick by having a CD and going to 'boot from first hard drive' on the main menu otherwise GRUB would complain about error 18. Change the boot order and it works :S. No error no problems.

---

### Post by ATK on 2009-09-05
well i tried flashing the BIOS on my 2nd computer, i think this would have solved my problem. i downloaded the BIOS update straight form the intel website but for some odd reason it wont put it on my floppy, so i guess i just wont use my xubuntu flashdrive in that computer. thanks to all who posted.
ATK

---

