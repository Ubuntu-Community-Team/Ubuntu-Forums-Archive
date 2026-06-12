---
title: "how-to: Ubuntu 5.10 on IBM Thinkpad T43"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by RdM on 2006-10-24
I wanted to run the Ubuntu 5.10 -Breezy Badger on this laptop. I have read several guides  about this, but since none of them matched my system and linux distribution exactly, i wrote this guide.

**Specification**
The Thinkpad T43 come in many different versions, and the specifications for 1871-12G is as follows:

Processor:	Intel Pentium M 730
Memory:	256 Mb / 2 Gb
Grapics:	Intel Graphics Media Accelerator 900
Hardisk:	40 Gb


**Get started**
The first thing you need to do is to create the rescue discs. This is extremely important since it's the only way to get back the system to factory settings!

**Disk layout**
My IBM came with a 40 Gb hard drive. As you can see below there are two partitions. 
The first one is a 35 GB NTFS partition containing Windows XP and the second one is a 4 GB IBM rescue partion.
-----------------------------------------------------------------------------------------
Disk /dev/sda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4642    35093488+   7  HPFS/NTFS
/dev/sda2            4643        5167     3969000   12  Compaq diagnostics
-----------------------------------------------------------------------------------------

_Partitioning_
Since the harddrive is relatively small, i decided to get rid of windows, and use linux exclusively only on this machine. If you want to keep the existing windows partition you can resize it, and add the linux partitions during installation.
After partitioning the disklayout looked like this:
-----------------------------------------------------------------------------------------
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         124      995998+  82  Linux swap / Solaris
/dev/sda2             125        1948    14651280   83  Linux
/dev/sda3            1949        4864    23422770    5  Extended
/dev/sda5            1949        4864    23422738+  83  Linux
-----------------------------------------------------------------------------------------

**Add repositories**
In order to follow this guide you need to update your repositories. 
Execute the following commands in a terminal, in order to do this:

> sudo vi /etc/apt/sources.list
Add the repositories 'universe' and 'multiverse' to the first line, so it looks someting like this:
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

- Save and exit the file.

Now, update your repositories by enter the following:
#sudo apt-get update

Enable the TrackPoint scroll button
To use the blue middle TrackPoint button as a scroll wheel, In a terminal, enter these commands:
> 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
sudo vi /etc/X11/xorg.conf
In the editor, find the section headed Section “InputDevice” / Identifier “Configured Mouse” add the following lines above the “EndSection” line:

Option    "EmulateWheel"        "true"
Option    "EmulateWheelButton"  "2"

Save the file. Logout, restart X with Ctrl-Alt-Backspace, and log in again.

**Enable On-Screen Display** (You probably don´t have to do this)
To get the on-screen display working, in a terminal, enter these commands:
> 
sudo apt-get install tpb
sudo adduser [username] nvram

Logout, restart X (with Ctrl-Alt-Backspace), and log in again. -Works like a charm!

**Summary **
_Works instantly:_
Network (wireless & cable), sound, hibernate, sleep (suspend to ram), Thinkpad buttons (volume, brightness etc.), touchpad, trackpoint, thinklight.
[U]
Works after a little tweaking:[/U] 
Middle button scrolling, ThinkPad Buttons OSD

_Have not tried:_
Internal modem

_Don't work:_
IBM Rescue and Recovery Partition. **[COLOR="Red"]Make sure you create recovery cd:s[/COLOR]**

---

