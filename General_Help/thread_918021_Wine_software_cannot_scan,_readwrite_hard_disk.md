---
title: "Wine software cannot scan, read/write hard disk"
date: 2008-09-12
forum: General Help
---

### Post by iampriteshdesai on 2008-09-12
I have used a data restore software using Wine and when I try to scan my HD for files I get an error saying need administrator previlegies.
Wat to do?

---

### Post by EmanresuusernamE on 2008-09-12
:( Very sketchy, you could run the command with sudo in front of it, but then you'd open yourself up to possible problems.

Goto the location of your "C" drive, right click on it and make sure it's permissions are read/writable to you.

---

### Post by cariboo on 2008-09-12
You can access your files using Nautilus. Hit Alt-F2 and enter the following:

```
gksu nautilus
```

enter your password when asked. This will open another Nautilus window with root access. 

Using wine for critical actions is not a very good way to do things as wine is not a complete clone of windows, and somethings may not work as expected.

If you search Synaptic Package Manager for backups you will find a large number of different backup programs. Find one that suits the way you do things and use it instead.

Jim

---

### Post by iampriteshdesai on 2008-09-12
I installed Bacula but couldn't find it any where in the menus.

---

### Post by EmanresuusernamE on 2008-09-12
System > Preferences > Main Menu
Look for it in there, and then add it to your menu.

---

### Post by EmanresuusernamE on 2008-09-12
Also, have you thought about using Clonezilla?  It's a great way to make complete backups/restores of your hard drives, and it's Linux based and free.

[QUOTE=iampriteshdesai]I have used a data restore software using Wine and when I try to scan my HD for files I get an error saying need administrator previlegies.
Wat to do?[/QUOTE]
What software are you trying to use anyways?

---

### Post by iampriteshdesai on 2008-09-12
I searched, but it isn't there. Guess I'll have to say bye bye to Avril.
Hell I lost 20 Mb worth of Emma Watson.

---

### Post by iampriteshdesai on 2008-09-12
I am using Undelete and restoration, but I get an error while scanning, authority required or something.

---

### Post by EmanresuusernamE on 2008-09-12
Do you have a windows partion you could boot to?  Or better yet, a friend who has a windows PC that you can use to restore the files?

---

### Post by iampriteshdesai on 2008-09-12
Unfortunately no. I completely erased the disk before installing, Hope it was a soft formatting.

---

### Post by EmanresuusernamE on 2008-09-12
Hate to tell you this, but I think you're screwed if you erased the disk and then put Ubuntu on it.  When you erase stuff, usually it just unlinks it from the file system, and it's recoverable, up until you put something over it.  If you erased your windows disk, and then put Ubuntu on it, there's isn't much that I know of personally to help you.  Windows and Ubuntu put most of the info needed for saving files in the beginning of the file allocation table.  If you've deleted it, and put the Ubuntu version over it.... it's pretty much gone.

Even if the data that you need isn't written over, most programs won't know how to recover it since the file allocation table is gone.

Is your computer really old, or fairly new? If it's fairly new, and you still have the reinstallation disks that came with your system, go buy a small USB thumb drive with at least 2 gigs (4 would probably be better if your computer came with a restoration partition) on it, remove the hard drive physically from your machine and put the USB drive in your computer.  Then insert the reinstallation disks in it, and resinstall Windows.  After you finish reinstalling windows to your USB drive, shutdown the computer and then put the hard drive back into the system.  Boot your computer, (make sure it's set to boot off of your USB drive) and then try and run your restoration programs.

---

### Post by iampriteshdesai on 2008-09-13
Ok

---

