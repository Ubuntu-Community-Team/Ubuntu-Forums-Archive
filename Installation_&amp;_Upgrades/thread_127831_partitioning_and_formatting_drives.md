---
title: "partitioning and formatting drives"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by krick on 2006-02-09
As a disclaimer, I've been building windows based systems for myself, friends, and family since the early 90's so I know my way around windows, however, this is my first real experience with linux (except hacking my series 1 TiVo).

I'm attempting to set up a box with Ubuntu for work.

I plan to use it primarily as a SubVersion server.

Anyway, my hardware setup has a 40GB IDE drive, which is the primary boot drive.  I also have a 3Ware 8006-2LP SATA RAID card connected to 2 100GB drives (mirrored) which will be use to store data for SubVersion.

I installed ubuntu once already but I hadn't formatted my RAID mirror.  When I got to the ubuntu desktop, I could see my RAID mirror but there weren't any partitions and I couldn't find any way to create or format them.

So I booted with a Western Digtal boot CD, blew away the partitions, reformatted both drives with FAT32, and reinstalled ubuntu.

During the install process, there is some sort drive configuration step that wasn't very clear to me (it wasn't clear the first time either).  It asked me which drive to install to.  That part is obvious.  However, I don't understand the options and if it's partioning and reformatting the drive or not.  When you install Windows 2000 on an existing FAT32 formatted drive, it asks if you want to blow away the partitions and reformat with NTFS or keep the existing FAT32 even though its not optimal for Win2K.  I just want to make sure that the ubuntu installer is doing whatever is "optimal" and not just using my existing FAT32 partitions.

So basically, I guess I'm asking two things:

1) What is the "optimal" choice for configuring the boot drive.

2) How do I partition / format additional drives from the ubuntu desktop?

I guess another question might be... Should I have installed Kubuntu instead?  I hear that it's better for power users.  Maybe it would let me actually partition and format a drive.

---

### Post by krick on 2006-02-09
And the plot thickens.

I'm at the ubuntu desktop and I open the "Disks Manager" application.

When I select my 100GB mirror, and click on the partitions tab, there's one partition with "Windows Virtual FAT" filesystem.

So just out of curiosity, I click the "Format" button to see where it takes me.

When I click the "Cancel" button to leave the format dialog without changing anything, I get this...

[IMG]http://files.3feetunder.com/Screenshot-Error.png[/IMG]

Clicking the "Inform Developers" button turns out to be useless because "disks-admin" or "Disks Manager" do not appear in the list of applications you can submit bugs on.

---

### Post by phyziks on 2006-02-18
Same thing happens to me.

---

