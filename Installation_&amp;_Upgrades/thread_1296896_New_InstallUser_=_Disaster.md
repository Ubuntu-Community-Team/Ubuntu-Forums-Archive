---
title: "New Install/User = Disaster"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by Twinny on 2009-10-21
Hello everyone:
I'm am BRAND new to Ubuntu and have embarked on taking an older Toshiba Qosimo laptop away from Microsoft XP land to Ubuntu 9.04.  I downloaded the image from U Minn server and burned the CD OK.  Installed the opsys with single boot only (knowing it would erase XP and all contents).  

When I went to have the OS boot from the hard disk for the first time, it began the start-up sequence, but then terminated with about 8 hours (and running) of error message of the flavor EXT3 fs error -- get_inode_loc. . . .  something something.  System never booted from hard drive at all.

Can anyone tell me where to begin?  My children are beginning to think Dad is WAY over his head. . . .

The Qosmio has two physical drives, and then BIOS is set to boot off the drives.

Thanks for any help in advance.

Twinny

---

### Post by linux-hack on 2009-10-21
try this command : fsck /dev/sdaX (You HDD)

look in here [http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html](http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html)

---

### Post by Twinny on 2009-10-21
> **boogy9 said:**
> try this command : fsck /dev/sdaX (You HDD)

look in here [http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html](http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html)


I actually tried that already and got a one line response that said "clean" and some detail about sectors.  I had seen that command on some of the other posts.

---

### Post by Ravernomina on 2009-10-21
try a SMART test. Maybe the drive is dieing. Also a Reinstall would not hurt at all. This time install it with EXT4. Good luck 

      Ravernomina

---

### Post by Twinny on 2009-10-21
> **Ravernomina said:**
> try a SMART test. Maybe the drive is dieing. Also a Reinstall would not hurt at all. This time install it with EXT4. Good luck 

      Ravernomina

Sounds promising.  How do I do that (SMART test)?  How do I do ext4 versus 3, don't remember an option in install that allowed for a selection like that.

Thanks again for the help.

Twinny

---

### Post by Ravernomina on 2009-10-21
> **Twinny said:**
> Sounds promising.  How do I do that (SMART test)?  How do I do ext4 versus 3, don't remember an option in install that allowed for a selection like that.

Thanks again for the help.

Twinny

U need an OS to Run a smart test.

Install windows again if you can then find your hard drive maker. They Usually have testing utilities. Run an extended test to see if your Hard drive is ok. EXT4 is the next FS that makes EXT3 Obsolete. Its faster better and stronger basically. You can format the disk with Gparted to get an EXT4 Disk.

---

### Post by dhavalbbhatt on 2009-10-21
Were you able to run Ubuntu using LiveCD? Also, provide more information about the ISO image that you burned - is it 32bit or 64bit, more information about your hardware (other than just the name) will also help.

---

### Post by Twinny on 2009-10-23
> **dhavalbbhatt said:**
> Were you able to run Ubuntu using LiveCD? Also, provide more information about the ISO image that you burned - is it 32bit or 64bit, more information about your hardware (other than just the name) will also help.

Ok, problem solved.  Apparently, there was a problem with the hard drive, a whole collection of bad sectors.  The Qosmio had a second drive and I just installed the image to it and voila!  It works very well.  Was able to get printers, wireless, and sound card to work automatically.  Had some struggles with adobe flash, but eventually got it to work as well.  Awesome image.  First exposure to OO and it is WAY impressive.  

Thanks for the help and guidance, all!

Twinny

---

