---
title: "Transfer files from Ubuntu to Windows"
date: 2008-09-16
forum: General Help
---

### Post by brianlawrence15 on 2008-09-16
Hi im fairly new to Ubuntu and Linux. I have a windows xp and ubuntu hardy heron 8.04 dual boot. im wondering if there is a way i can take files i downloaded on ubuntu and transfer them to the windows partition or vice versa. thanks for the help.

---

### Post by quibbler on 2008-09-18
> **brianlawrence15 said:**
> Hi im fairly new to Ubuntu and Linux. I have a windows xp and ubuntu hardy heron 8.04 dual boot. im wondering if there is a way i can take files i downloaded on ubuntu and transfer them to the windows partition or vice versa. thanks for the help.
Look in Synaptic Package Manager for ntfs-conf
and install it.
You will find it under System tools.
With it you can turn off and on read-write for your win xp 
partition. You can then in nautilus just copy and delete as
you please.

Regards quibbler

---

### Post by RobOrr on 2008-09-18
If you're new to the wonders of ubuntu here's a further couple of tips - nautilus is the equivalent of windows explorer. i was using it for weeks without knowing the name! Also, because Microsoft is the jealous ex girlfriend, windows refuses to admit ext2 or 3 (the file systems of linux) so you have to copy the stuff from inside ubuntu, not windows.

---

### Post by mb_webguy on 2008-09-18
However, the best way to set up a dual-boot system is to put each operating system on a partition just large enough for the OS and some room to install software (which is about 8GB for Ubuntu, 15GB for Windows XP, and 25GB for Vista), then have a tiny (<1GB) ext3 partition for your Ubuntu /home directory and a big NTFS partition using up the rest of your drive for storing your files.

You would put shortcuts and symbolic links to make sure that your Windows user folder and your Ubuntu home directory pointed to the same places (e.g. "My Music" in Windows and "/home/dave/Music" both point to the Music folder on the shared NTFS parition).  That way, you don't waste space by having one set of files for Windows and another for Ubuntu, and you don't waste time transferring files back and forth between operating systems.

---

