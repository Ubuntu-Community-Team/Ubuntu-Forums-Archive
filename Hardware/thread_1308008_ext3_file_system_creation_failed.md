---
title: "ext3 file system creation failed"
date: 2009-10-31
forum: Hardware
---

### Post by mjp29 on 2009-10-31
I have a hard drive my Uncle gave me that we think works.  However, when trying to install either Ubuntu or Kubuntu from a live cd at about 5% into the install the message:

"The ext3 file system creation in partition #1 of SCSI 1 (0,0,0) (sda) failed"

Is there any possibility, other than the HD is bad, that something else could cause this?  Perhaps one of the jumper switches in the wrong place?

---

### Post by paulisdead on 2009-10-31
Could be a bad scsi card or cable, but it very well could be the drive.  Who made it?  You should see if the manufacturer has a bootable test cd you can run on it.  If there isn't one, try seatools, it works on pretty much any drive, but it might not support your scsi controller.

*edit* duh, it's probably a sata drive.  Wasn't quite fully awake there, and was forgetting it treats sata as scsi.  So ya you should be able to get a manufacturer's bootable test cd and run it.

---

### Post by mjp29 on 2009-10-31
> **paulisdead said:**
> Could be a bad scsi card or cable, but it very well could be the drive.  Who made it?  You should see if the manufacturer has a bootable test cd you can run on it.  If there isn't one, try seatools, it works on pretty much any drive, but it might not support your scsi controller.

*edit* duh, it's probably a sata drive.  Wasn't quite fully awake there, and was forgetting it treats sata as scsi.  So ya you should be able to get a manufacturer's bootable test cd and run it.

I just noticed that the jumper (whatever you call it) is in a different place than the one on the drive i took out.  I'll try to move the jumper and see if that does anything.  If not, I'll put the 20 gig hd back in the machine - the one i was trying to replace it with was a 320 gig western digital.

---

### Post by mjp29 on 2009-10-31
Switching the jumper to what the HD was like did not help.  Still same error.  The original jumper on the 20 gig HD that came out of the Dell worked and was in the 3rd from the powersupply which I think is the "Enable cable select" jumper position.  The 320 gig HD that I thought I pop in there from an IBM computer was in the 1st position closest to the power supply which is probably the "Limit drive capacity to 32 Gbytes" position.

I thought that putting the 320 gig HD in the "Enable cable select" jumper position it would then work.  But again, the same exact failure of the ext3 file system creating error.  This occurs at about 5% after partitioning and installation is occurring.

Odd thing is, upon bootup from the live Ubuntu cd, I had it check the 320 gig HD and it reported there were no problems with the HD.

?  Could it be the HD is still bad even though live cd checking it reports the HD is ok ?

---

### Post by mjp29 on 2009-10-31
I have the install disk for a new netbook (has windows xp) and I have the install disk for a new Dell (has windows vista).

Could perhaps either of these help me get the drive working?

Ubuntu live cd checks the disk (at my choosing upon boot from cd) and reports no problems with this HD.  I'm not ready yet to give up on a 320 gig hard drive and put the 20 gig hd back in it.

---

### Post by cariboo on 2009-10-31
I would suggest you go to the manufacturers web site and download and use their diagnostic tools on the drive to make sure it is OK.

I have never had much luck using cable select, set it either to a master if it is on it's own cable, or a slave if it is sharing the cable with another hard drive.

---

### Post by mjp29 on 2009-10-31
> **cariboo907 said:**
> I would suggest you go to the manufacturers web site and download and use their diagnostic tools on the drive to make sure it is OK.

I have never had much luck using cable select, set it either to a master if it is on it's own cable, or a slave if it is sharing the cable with another hard drive.

I tried it in master mode - there isn't another hd but i'll try it in slave mode too.

It's a Dell and it has no OS on the HD now - is there a way to go to dell.com and download something that ubuntu can run to test it?
I tried booting off of a windows xt (netbook) and a windows vista (newer laptop) os disk.  But it wouldn't boot.  I was doing an f12 and selecting boot from cd drive (is there another way to force it to boot, i think i read somewhere holding down a right mouse key or the c key or something)

---

### Post by mjp29 on 2009-10-31
I was just looking at an old drive pulled from an iMac or g4 cube years ago.  Curious that it has 2 jumpers.  One in master with another jumper between the bottom of the two next to it.  Ever seen anything like this?

Also, the one that came out of Dell is "ATA" - is that the same as IDE I'm trying to replace it with?

fyi: It always stops at 5% into partion formatting with ubuntu live cd during install.

---

### Post by Bartender on 2009-10-31
Do you have a high level of confidence in the CD you're using?

---

### Post by mjp29 on 2009-10-31
I think it is just a bad HD.

I took an old 20 gig hd that had been sitting around that came out of an old Mac and it is installing fine.  

So both the 20 gig hd worked that I took out, and a different 20 gig HD I just put in both work in it.

Unless there is some limitation on size (the HD I was trying to put into it was 320 gigs), then I can only conclude that the 320 gig hd is just bad.

Any thoughts?

---

### Post by cariboo on 2009-10-31
It may be a limitation of the computer, I recently helped someone who had the same problem with a large drive. It seems the the primary ide channel was limited to 32Gb, but the secondary saw the full drive size.

There should be a label on the drive, showing where the jumper should be for different modes

---

### Post by mjp29 on 2009-11-01
> **cariboo907 said:**
> It may be a limitation of the computer, I recently helped someone who had the same problem with a large drive. It seems the the primary ide channel was limited to 32Gb, but the secondary saw the full drive size.

There should be a label on the drive, showing where the jumper should be for different modes


Were you able to get the larger drive to work on the computer you were helping with?  Perhaps you set the drive to secondary drive mode with the jumper switches somehow or another mode?

It just doesn't seem logical to me that a primary ide channel would be limited to 32GB.  Good grief, that isn't much size for a HD.  Surely there is a workaround - ?

---

