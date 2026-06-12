---
title: "Disk usage analyser and df report different free space on external HD"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by jaydoubleyou on 2007-11-08
I have a 500GB external hard drive (formatted as FAT32). I've just moved a lot of files from here onto a Windows machine and have then connected it to my Ubuntu (Gutsy 64 bit) machine to move a 44GB folder to the external drive, only to be told there is not enough free space.
Disk Usage Analyser reports that I have used 154.3GB, which sounds about right. However, the status bar of the file browser shows 25.7GB free, which tallies with what df -h comes up with:
> /dev/sde1             466G  440G   26G  95% /media/EXTERNAL
There are no odd folders that might account for the missing 300GB - there is a Windows 'Recycled' folder, containing all of 66.5MB, and a 'System Volume Information' folder containing a mighty 131.3KB, but nothing else - even selecting 'show hidden folders' does not shed any further light. All I can think is that Ubuntu is counting the files that Windows has moved, but why don't they show up in the file browser or the Disk Usage Analyser, and more crucially, what can I do to make df -h and the file browser count the disk space correctly and let me move my folder? I've done a Google search and checked the threads that showed up when I put the title in to this post, but have drawn a blank. Any ideas?
Jason

---

### Post by jaydoubleyou on 2007-11-11
Further to the above, it appears it isn't specifically a Linux issue. I've just gone to back up my Windows laptop (prior to installing Linux) onto the drive using Norton Ghost and *that* is reporting just 25.7GB free space on the drive as well. My Computer in Windows reports 307GB free...

---

### Post by gangalee on 2007-11-12
slightly aside, what's the command-line name for this disk usage analyser?

---

