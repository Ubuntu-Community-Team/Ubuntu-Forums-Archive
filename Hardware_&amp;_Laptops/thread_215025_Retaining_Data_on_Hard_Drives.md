---
title: "Retaining Data on Hard Drives"
date: 2006-07-13
forum: Hardware &amp; Laptops
---

### Post by Burgresso on 2006-07-13
I'm considering adding another harddrive to my system; I've got a IDE setup. I'd have two.

Is it possible to have one retain information and data when I (re)install Linux distros? 

Every once in a while I like to try new distros but it would be nice if I could retain my data on one drive so I don't have to backup data - like files and stuff - on DVD or CD just to test drive a new distro for a while. Any advice or wisdom I should now about?

Thanks very much,

Burgresso

---

### Post by Landoln on 2006-07-13
There are several ways you could go about this.  I usually set my hard drives up into several partitions, putting /home on a seperate partition from / so if I have to reinstall I can do so without losing any of my personal files.  I'm not sure about how exactly you would go about it with (k/x)ubuntu, but I know if you do the manual partitioning during setup you can opt to not format a partition for mounting.  So you could specify, for example, that you want to use /dev/hda3 for /home, but not format it, preserving your data.  

If you don't already have the seperate partitions, You may be able to simply boot into the live cd, delete any files on the hard drive you don't want to keep (for example, everything except /home, and then reinstall on that same partition without reformatting. I would guess that it would keep all of the files that you have in /home in tact, but I haven't tried it, so no guarantees.  

Since you have two hard drives, you could simply mount the one with the files you wish to keep either on your /home directory, or more likely someplace else (like /media/SecondDrive). Then when you're installing you can either specify that you want to mount /dev/hdb1 (or whatever it is) there, or wait until everything is installed, ignoring that second drive during the install, and modify your fstab manually.  

I hope this helps.

---

### Post by Burgresso on 2006-07-16
Landoln,

Thank you; I appreciate your reply very much.

Is there any significance to the naming of hard drives and partitions - as in hdb1 and hda1?

Thank again,

burgresso

---

### Post by Landoln on 2006-07-17
> **Burgresso said:**
> 
Is there any significance to the naming of hard drives and partitions - as in hdb1 and hda1?

Your master hard drive is most likely hda.  The first partition on that drive is hda1, the second partition is hda2, etc.   Your second drive is hdb, the first partition that that drive is hdb1, and so on.

---

