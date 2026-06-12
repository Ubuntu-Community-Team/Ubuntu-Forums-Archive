---
title: "Cant Install"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by Corrupt on 2005-07-19
Hey,

I am trying to install this version but it wont work, i get through the language options, keyboard settings fine but then it says it cant detect a cdrom (and i am booting off a cd rom). It then asks me to do somthing with the drivers and "if you are using a weird cdrom drive to insert the floppy disc. well i dont have a floppy disc but i am running a LG DVD-RW. my boss thinks it might be because i am running a SATA HD as he was able to install it fine on his pc which has a dual layer dvd player but an ide HD,  do you guys have any ideas

---

### Post by mad_scientist03 on 2005-07-19
How is the CD-ROM connected to the motherboard? Typically, you have two IDE ports on the motherboard. The master hard drive takes the master postiion on one IDE cable that then goes to the primary IDE port on the motherboard, and the CD-ROM drive takes the master position on the second IDE cable that then goes to the secondary IDE port on the motheboard.

Is that how your setup is arranged? Do the hard drive and CD-ROM drive share the same IDE cable? What are the jumper settings on your CD-ROM (look at the back of the drive where the IDE cable connects)?

Just in case you aren't sure, the IDE cables are the (usually gray) ribbon cables that run between the hard drive or CD-ROM and the motherboard. The primary IDE port on the motherboard usually has a blue plastic polarized shroud.

---

### Post by Corrupt on 2005-07-19
ok what i am running is my sata 200g on port 0, i have my cdrom in ide1 (the primary one) and my floppy in well where it usally goes.

---

### Post by Corrupt on 2005-07-23
ok i was left with no choice and had to try another os (mandrake 9.0) but it said that it could not format hda5 of my harddrive. does anyone know what this is

---

### Post by Civil on 2005-07-24
I am having the same problem getting Hoary to install on my new box.  I also have a SATA drive plugged into the serial SATA port, and a DVD ROM installed on the only available IDE slot for optical drives.  This would correspond to the secondary IDE port, but the primary IDE is an UltraIDE slot (X-WIDE).

I put the Install CD in the optical drive, and it boots off the disk like it should.  I also get to the keyboard setting when it craps out.  I tried another distro, and noticed that the DVD-ROM drive is mounting as hda and the SATA hard drive is mounting as hdc.

My guess is that the installer is looking for the CD on a drive other than hda.

Is there any work-around for this?  Maybe using the Live CD to partition part of the hard drive to hold the ISO and trying to mount it??

Any help/thoughts would be greatly appreciated.

Thanks,
Rich

---

### Post by marcovanbeek on 2005-08-13
Hi,

I don't know if this is the same issue, but we had something similar until we plugged in a standard IDE drive as well. After that the CDRom was found and the install was completed. We have a 4TB partitioning problem so the box has been re-installed a number of times, but I am pretty sure you don't have to use the IDE drive, just have it in the chain (we had it on the same IDE channel).

Regards,

Marco

UPDATE: It would appear that the issue is that the CDROM needs to be hooked up as a slave, not a master. You don't need the IDE hard drive.

---

