---
title: "SATA + IDE Help"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by Anti-Hero on 2007-07-29
I currently have 7.04 installed on a SATA drive, and some backed up files installed on an IDE drive.  (ext3 FS) When I hook up the IDE and boot, I get a GRUB error 22.  Its trying to boot from the IDE I believe.  I have checked the BIOS thoroughly and cannot find any specific section to specify SATA.  The only config option is boot order / priority.  

Any suggestions?

---

### Post by kyphi on 2007-07-29
There should be an option in the BIOS to treat drives as IDE or AHCI=Advanced Host Controller Interface for SATA drives.

When you say 'hook up' the IDE drive and then boot' do you mean that you have it disconnected normally?  Is it an external drive?  If so, then the answer is simple: do not boot with storage peripherals attached.

SATA and IDE drives generally do not mix well since each uses a different controller on the motherboard.

---

### Post by Anti-Hero on 2007-07-29
Thanks for the reply.  It is an internal driver that I used to backup a lot of media stuff.  I am connecting it to the primary IDE port  on the MB.  Then I want to copy the files off and disconnect it.  It worked before, that's how I backed up the media.

Then I reinstalled ubuntu as the first install was more of a test for this HW, and too see if it's media abilities were up to par.

---

### Post by kyphi on 2007-07-29
The only solution that I can think of is to make a change in the BIOS so that the IDE storage drive is not part of the bootup chain.

Since there are several versions of BIOS I am not in a position to advise you on how to accomplish that.  You might get the information from the BIOS manufacturer or from your motherboard handbook.

Did you reinstall Ubuntu with the IDE drive in place?

---

### Post by dabl on 2007-07-29
> **Anti-Hero said:**
> 

 When I hook up the IDE and boot, I get a GRUB error 22.  Its trying to boot from the IDE I believe.

Any suggestions?



Yep, stop doing this!

:)  (sorry, I couldn't help myself)

You really don't want to be trying this game of disconnecting hard drives, installing stuff on the remaining drive,  then connecting the other drive and seeing what it will do to your Linux system. Pass the word -- there are like 3 posts per day from people with screwed-up systems caused by doing this.

OK, if you will download the ISO image and make yourself a GParted Live CD, then you should be able to turn OFF the boot flag on the bootable partition on that IDE drive.  Get it here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

With only your problem IDE drive connected to your computer, boot the GParted Live CD, look at the partitions of your IDE drive, find the one that has the boot flag set, and un-set it, so there are no bootable partitions.

Now hook back up your SATA drive, restart the computer, go into BIOS and set the boot sequence so the SATA drive is BEFORE the IDE drive, if possible (it's not always possible).

If this doesn't work, you are going to have to find another way to backup your data off that IDE drive.

Next time you try this, fdisk your IDE drive BEFORE you install Ubuntu, then install Ubuntu on your SATA drive WITH the IDE drive connected, THEN partition and format your IDE drive, THEN mount it, and you'll be fine. :)

---

### Post by logos34 on 2007-07-29
I think it's trying to boot from the ide drive--the minute you connect it the bios puts it first in the boot order.  Somewhere in the Bios there should be a subsection for hard disk boot priority--after you connect the ide make sure the sata is listed first and the ide listed second and/or disabled.

Or you could just install grub to the ide MBR too so that ubuntu boots via grub on either disk.

---

