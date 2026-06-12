---
title: "Software on second drive"
date: 2010-08-09
forum: Hardware
---

### Post by kooia on 2010-08-09
Hi everyone,

I'm pretty surprised with how fast the 100GB partition I set for Ubuntu is filling up.  So sometime, I'm going to get another hard drive and set it as FAT32.  But the thing is that most of the hard drive usage is programs.  An extra 1 TB isn't really going to help if I can't install programs on it.  So anyone, is there a way I can install programs on the second hard drive, especially if it's FAT32?  And I'm NOT going to use RAID... it's slow and inefficient.  

Also, I've never used a second hard drive, so can someone update me on all the info of what it's like and what all that master/primary slave/secondary slave stuff is all about.  And is it going to be ejectable (like when you dual boot with windows, you can view the other partition but when you're done you can click that ||> button.  And what does that do, power the hard disk down?)?

---

### Post by Fafler on 2010-08-09
Unless you are a experienced linux user i wouldn't recommend it. It's very much possible but takes some skill. But i'll bet you anything not all your 100 gb is used by applications, so what about moving some user data instead? You could get a new drive, split it two, one partition for Windows and one for Linux, format the Linux partition, move you current /home to it and modify fstab. That's probably the best way to go as trying this with /usr and other folders is more likely to fsck things up.

Also, i think Ubuntu has a filesystem cleanup tool somewhere. Atleast do a df -h && sudo apt-get clean && df -h from a terminal. It could free up quite a bit of space.

How old is your PC? Models from the last five years have SATA instead of IDE, so if you possible can, go for a SATA drive instead of a older IDE. SATA doesn't have any master/slave configuration. Just connect the drive to the next available connector on the motherboard and your'e ready to go. The eject button is just like the safe removal of hardware button in Windows.

---

### Post by kooia on 2010-08-10
Thanks for the info.  Yeah, I have SATA.  So thanks about that.  And of course, you're right about the software thing.  I bet that I do have enough space for all the programs.

---

