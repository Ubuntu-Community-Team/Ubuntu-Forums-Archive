---
title: "Ubuntu Software RAID Install Partitioning"
date: 2005-07-12
forum: Hardware &amp; Laptops
---

### Post by firefly2442 on 2005-07-12
Hello.  I am trying to setup an old computer with four 9 GB SCSI drives in a software RAID.  When I load the installer I setup each drive as being a RAID and then created a multi disk device that contains all four drives.  This creates a new RAID entry on the partition screen totaling 36GB.  So this is where I figured I need to install Ubuntu.  When I setup to automatically partition this RAID and format it gives me an error right at the end that it cannot format.  I'm assuming that this might have something to do with it being confused as to where the boot loader is possibly?  Is there some step that I might have missed?  Thank you for the help. :)

---

### Post by firefly2442 on 2005-07-15
Do I have to setup one of the drives as the "/" drive with a swap partition and so on and then use the other drives and create a RAID?  Do I have to setup the RAID after I install Ubuntu?

---

### Post by OzPhoenix on 2005-07-18
Did you ever get this sorted? I'm currently having a simiar problems (two 80GB SATA drives - but the rest the same). Love to know what I need to do.

---

### Post by firefly2442 on 2005-07-18
Hey, I got it working but sadly not with Ubuntu.  There must be some error in the Ubuntu partition section.  I did the same setup that I tried on Ubuntu under an old Mandrake 9 install and it worked under Mandrake.  I would submit a bug report but I'm not sure what the specifics of it entail.  There was no console error or anything.  It was not specific at all.  Apparently you cannot have the "/" on the RAID.  What I did was setup one drive as the "/" and swap sections and then create a RAID with the other drives and use the RAID for the "/home" section.  Anyway, hope you get it sorted out. :)

---

### Post by OzPhoenix on 2005-07-18
Thanks for replying.

Yup, last night I tried numerous things and got nothing wokring. Thinking tonight I'll install a third drive and (like you mentioned) set that up as / and then set my current two drives as a RAID for my /file-share.

Man, if that doesn't work I'll be pretty annoyed. I find the thing that is most annoying is the fact that the installer makes it look like you should be able to do it!!!

Anyway, thanks again, more playing tonight,
OP.

---

### Post by snoochems on 2005-08-01
Just another thread about installing ubuntu on raid, with no replies that help.

---

### Post by Yagisan on 2005-08-01
The fact is in attempting to speed up the boot process for "desktop" users the timing of the RAID initialisation gets stuffed. See this bug for how I got RAID to work. [http://bugzilla.ubuntu.com/show_bug.cgi?id=4944#c6](http://bugzilla.ubuntu.com/show_bug.cgi?id=4944#c6)

---

### Post by firefly2442 on 2005-10-11
The RAID issue seems to be fixed with the new breezy pre-release.  I installed it and everything is working fine. :)

---

