---
title: "Error 18 after fresh install from CD"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by chkneater on 2009-10-26
I just did a fresh install of 9.04 from CD.  The ISO and CD are good.  The install goes fine but just before the computer shuts down for reboot, I/O error fills the screen. And then when it restarts it gets to the grub menu and stalls with "error 18".  I'm going to try to reinstall and reformat.  Any other ideas?

---

### Post by chkneater on 2009-10-26
Reinstalling didn't help, still getting error 18.  I checked the bios and there are no options to switch the LBA on the hard drive.  It's a Maxtor 300GB.

---

### Post by chkneater on 2009-10-27
I fixed the issue and installed 9.04.  I had to reformat and do a manual partion on the entire disk.  I had to make sure that instead of being SDA1, SDA5, and SDA6 to make the partions SDA1,2,and 3.  I couldn't change this in Gparted which is why I had to reformat.  SDA1 I made only 2 Gbs.  Also I set the mount point to /boot.  I could have made it smaller but I wanted to leave room for changes I guess. I made sure that SDA1 was a PRIMARY partion, all partions have to be PRIMARY and NOT logical (the second issue I had to fix).  SDA2 I made 5 Gb for the swap file.  SDA 3 I set for /ext3 and used the rest of the disk space on it.  I set the mount point to / and made sure it was PRIMARY not logical.  

I was able to figure this out from this thread. 

[https://answers.launchpad.net/ubuntu/+source/grub/+question/74437](https://answers.launchpad.net/ubuntu/+source/grub/+question/74437)

 It didn't apply directly to me because it was about dual booting with Windows where I just did a fresh install with just Jaunty.  The problem I was having was that my bios wasn't able to recognize the SDA5 and SDA6 partions, so changing the size of the boot partion and having it set for primary, and then the same for the swap partition and the file system partion.  Only thing is I don't know if I remembered to turn the swap file on when I formatted it?  Does anyone know about that?

---

