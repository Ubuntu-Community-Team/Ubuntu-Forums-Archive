---
title: "Vista after Ubuntu install - possible on seperate HD's?"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by cknight on 2009-06-27
I've been having trouble installing Vista on my primary harddrive post Ubuntu install (see [this post]("http://ubuntuforums.org/showthread.php?t=1198198") for details).  For whatever reason, Vista just won't assign a drive letter to the NTFS primary partition I created for it.  No help yet, so I'm now looking into alternative solutions.

I do have a second hard drive installed.  Is it possible instead to put Vista on it and use the existing grub on the other drive to boot it?  If so, what are the complications?  Do I need to adjust the bios to boot off of the other hard disk?  Anything special to the installation of Vista procedure?

---

### Post by jprophet420 on 2009-06-27
> **cknight said:**
> I've been having trouble installing Vista on my primary harddrive post Ubuntu install (see [this post]("http://ubuntuforums.org/showthread.php?t=1198198") for details).  For whatever reason, Vista just won't assign a drive letter to the NTFS primary partition I created for it.  No help yet, so I'm now looking into alternative solutions.

I do have a second hard drive installed.  Is it possible instead to put Vista on it and use the existing grub on the other drive to boot it?  If so, what are the complications?  Do I need to adjust the bios to boot off of the other hard disk?  Anything special to the installation of Vista procedure?

Yes, you can do that. example:

c: has grub on boot sector, ubuntu on the partition.
d: has vista installed

set your bios to boot from drive "c:" and grub will take care of it. You will have to edit the grub.conf file to point the vista install, it will most likely be "00" for the ubuntu drive and "01" for for the windows drive.

I have had many installations of linux where there was no boot loader, i just used the bios (f10 in most cases) to select the installation at boot time.

---

### Post by cariboo on 2009-06-27
When you install Vista, especially after you installed Ubuntu. Vista will overwrite the mbr. To repair grub, have a look at this [thread=224351]howto[/thread].

---

### Post by jprophet420 on 2009-06-27
simply install vista with only one hard drive plugged in to avoid that. 

As a windows PC tech, I can tell you with 100% certainty that thats the best way to install Vista or XP even w/o an Ubuntu install.

---

### Post by cknight on 2009-06-27
> **jprophet420 said:**
> simply install vista with only one hard drive plugged in to avoid that. 

As a windows PC tech, I can tell you with 100% certainty that thats the best way to install Vista or XP even w/o an Ubuntu install.

Sounds like a plan, if I knew much about laptop harddrives :)  Is it easy enough to identify which hard drive to remove and then to remove it?

Also, does each drive have an MBR, but which is only used if the BIOS boots off of that drive?

---

### Post by cknight on 2009-06-27
> **jprophet420 said:**
> simply install vista with only one hard drive plugged in to avoid that. 

As a windows PC tech, I can tell you with 100% certainty that thats the best way to install Vista or XP even w/o an Ubuntu install.

Oh man, thanks so much for that advice.  Removing the primary hard drive was easy (and I even guessed correctly the first time as to which was the primary).  After that, installing Vista to the second hard drive was a cinch.  Didn't have to restore grub or anything (just change the HD boot order back to its original setting in the bios). The only panic moment was when my damn cat walked over the motherboard while I was re-installing the primary drive.  Ack!

---

