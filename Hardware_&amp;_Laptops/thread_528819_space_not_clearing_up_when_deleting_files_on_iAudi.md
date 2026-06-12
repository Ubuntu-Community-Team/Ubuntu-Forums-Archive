---
title: "space not clearing up when deleting files on iAudio X5L"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by wickstopher on 2007-08-18
I have an iAudio X5L DMP, and have recently run into a problem when deleting files from the device.  Linux doesn't seem to be making the space re-available upon deletion.  The space is registered on the device itself, and it shows when i connect the device in my WinXP partition.  This occurs when deleting the files from the GUI.  I am right-clicking, deleting, and then emptying the trash.  It also occurs if I delete the files via the firmware UI.  if I rm the files via the command line, the space gets cleared up.  I'm very curious as to why this is happening and if there is any way I can fix the problem.  Thanks very much!

---

### Post by wickstopher on 2007-08-21
a little bumpitty-bump.

---

### Post by Soarer on 2007-08-21
I have an X5 too. Because it is mounted via the USB, the deleted files go, not into your desktop trash can, but into a .trash (or maybe .Trash) directory on the device itself. Thus deleting files just moves them into .trash and frees no space at all. Because the folder starts with a '.' it is a hidden folder which you don't *normally* see.

With the X5 open in Nautilus (file manager) hit <ctrl>H to view hidden files and you will see .trash. Empty that & you're good to go.

The command 'rm' bypasses the trash can so doesn't give this effect.

---

### Post by wickstopher on 2007-08-22
I knew about the .Trash directory.  The files weren't going there...I was emptying the trash, and they were gone, nowhere to be found, no hidden files/directories, nothing.  But recently, the drive has been functioning normally again.  Just a little bump in the road.  Right-click, delete, empty trash, and the space frees up immediately.  Don't know what was going on there for a minute (and there's still about 400MB on the drive that aren't being seen by linux.  Go figure.)

---

### Post by johnny_5 on 2008-01-17
ahhhh... bump bump bump.

I have the same promblem running Debian off of a Flash drive.
Help?

My 1.2Gb ext2 partition has become 825mb, and it's virtually empty?

---

### Post by johnny_5 on 2008-01-17
for anyone else with similar problems.

sudo apt-get xdiskusage

sudo xdiskusage

see where it put it all. Delete those files as root from command line.

Tada.

---

