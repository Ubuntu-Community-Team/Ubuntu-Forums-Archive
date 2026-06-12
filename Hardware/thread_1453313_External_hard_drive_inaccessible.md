---
title: "External hard drive inaccessible"
date: 2010-04-13
forum: Hardware
---

### Post by DryGrain on 2010-04-13
I recently tried to update my backup media drive, a 500GB seagate external. When I plugged it in to my netbook, I noticed it did not mount automatically. When I tried to access it in GNOME, it crashed nautilus as soon as I tried to open it (or right-click "Properties"). I was able see the files via terminal and the 'ls' command, but could not open any of the files. I have tried restarting with the USB cable plugged in, and I also tried the same thing on another laptop to no avail.

When I check the System Monitor I see that the filesystem type for the drive in question is 'fuseblk', rather than say ext3 or fat. It appears that my files are still there, but inaccessible.

An update, since creating this post, after unplugging and replacing the USB cable again, I see that the drive was not mounted to /media/external at all, and did not show up in the 'Filesystems' tab of the System Monitor.

What can be done? Should I just format it to ext3 and replace the backup? Or can that be avoided?

---

### Post by sxmaxchine on 2010-04-13
dont know how to fix the problem but i would just try formsting the device however if you want or need files i wouldnt listen to my advice

---

### Post by DryGrain on 2010-04-13
I do have other backups of the files, I was hoping to format as a last resort and maybe gain some insight as to why this is happening.

What is the syntax to reformat a drive as ext3?

---

