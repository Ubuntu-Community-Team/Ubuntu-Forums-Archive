---
title: "new 8.10 server install vs Dell Utility Partition"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by brown705 on 2009-04-09
Disclaimer: I'm pretty much a Linux newbie...maybe a 2 on a scale of 1 to 10.

I am trying to boot into a new 8.10 Server install on a Dell PowerEdge 2650 with RAID 1 (mirror).  I went into the RAID management, deleted the container, wiped the drives, created a new container and mirrored the two drives, giving me only one drive.  I then installed the Dell Utility Partition so I could run diagnostics and such.  No errors were found.

I then booted to my 8.10 server CD and installed using the "use the REST of the free space for Ubuntu" option, thinking this would leave the Dell Utility Partition intact.  The install completed without issue.  I removed the CD and restarted, and the system boots right into the Dell Utility Partition without giving me any option to boot into Ubuntu Server.  

Is there some way I can boot into Ubuntu without having to somehow wipe out the Dell Utility Partition?  If not, can I remove the Dell Utility Parition without having to wipe everything and reinstall Ubuntu Server?

Thanks in advance,
Michael

---

### Post by Sam Lars on 2009-04-10
It sounds like the bootloader did not get installed as it should have been...
You could try booting to a CD and following the instructions [here]("https://help.ubuntu.com/community/GrubHowto#Command%20line").

---

### Post by brown705 on 2009-04-16
> **Sam Lars said:**
> It sounds like the bootloader did not get installed as it should have been...
You could try booting to a CD and following the instructions [here]("https://help.ubuntu.com/community/GrubHowto#Command%20line").

Sam,

I tried this from the Rescue option on the 8.10 Server CD and got nowhere.  When I tried to run the "find" operation on any partition it told me "not found".  I then booted to a 7.10 Live CD, opened Terminal, and followed the directions.  The "find" still gave a "Error 15: file not found" error.

When in the 7.10 Live CD environment, I ran GParted.  Please see the attached screenshot.  I don't think it makes a difference, but this is all running on two 33.6 GB SCSI disks that are mirrored from the Dell PERC RAID controller.  You can see that I first installed the Dell Utility Partition (sda1) and then 8.10 Server using the remaining portion of the mirror (sda5) by creating the extended partition (sda2).

When I open Computer and navigate to disk/boot/grub, I do see "stage1" and other files there.

The directions from the link you gave said to type "root (hdX,Y), where X and Y are the hard disk and boot partition for Ubuntu.  I know Ubuntu is in /dev/sda5, but how do I address this to install Grub?

Thanks for your help.
Michael

---

### Post by Sam Lars on 2009-04-16
I believe you would change it like this:

a=1
b=2
c=3 etc.

1=0
2=1
3=2 etc.

So sda5 would be hd0,4
That seems to be how mine corresponds.

---

### Post by brown705 on 2009-04-17
> **Sam Lars said:**
> I believe you would change it like this:

a=1
b=2
c=3 etc.

1=0
2=1
3=2 etc.

So sda5 would be hd0,4
That seems to be how mine corresponds.

Sam, I really appreciate your help.  Unfortuantely, I still have not been able to get this working.  Within GRUB (as sudo) I can do "root (hd0,4)" without getting an error, but when I try to do "setup (hd0,4)" I get "Error 2: Bad file or directory type" (see screenshot).  My other screenshot shows /boot/grub/stage1 does indeed exist.  I tried doing the root and setup commands on other partitions, but they all gave either mounting errors or the same Error 2 message.

Any other ideas?  I'm about ready to just say screw it and forget about the Dell Utility partition and wipe the whole thing for a reinstall.

Thanks,
Michael

---

### Post by Sam Lars on 2009-04-17
I think this is related to the problem you had with the find command... it should tell you where to run the setup command.
It might be better to do a clean install of Ubuntu and then try installing the Utility partition...

---

### Post by brown705 on 2009-04-22
> **Sam Lars said:**
> I think this is related to the problem you had with the find command... it should tell you where to run the setup command.
It might be better to do a clean install of Ubuntu and then try installing the Utility partition...

Sam,

Thanks for all your help.  I reinstalled using the entire available space, and when I restarted, I got the "Bad PBR signature" error.  I did some Googling and saw it to be a common issue, particularly on Dell servers.  I ran a rescue from CD and reinstalled grub to hd0, and that did the trick.  I'm in the server (finally).

Thanks again!
Michael

---

