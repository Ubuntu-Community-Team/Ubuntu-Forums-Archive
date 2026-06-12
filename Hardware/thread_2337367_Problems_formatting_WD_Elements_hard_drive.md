---
title: "Problems formatting WD Elements hard drive"
date: 2016-09-17
forum: Hardware
---

### Post by roc-humet on 2016-09-17
Hello, I'm new to the forums so please forgive me if I'm posting in the wrong place!

I have a WD Elements hard drive and when I wanted to burn the Ubuntu Gnome iso file in a USB stick I chose the wrong option. I chose the hard drive, so all it content was formated. When I installed the Ubuntu Gnome, I tried to delete all files in the hard drive to put new ones, but I couldn't because it was in read-only mode.

I formatted it in NTFS (and then ext4) with the Disks application, but it didn't work. The files of the iso file were gone, but it was still in read-only mode. This is my first problem.

My second problem is related to the first one: the desktop doesn't boot if the hard drive is not connected. The OS boots normally, but then, before the login screen, the terminal in root mode appears saying "Welcome to emergency mode!". If I try to start the desktop enviroment with "startx", it seems that it tries to start it because the screen turns black, but then it goes back to the terminal.

I have a Lenovo ideapad z370 with Ubuntu Gnome 16.04.1.

As you may have noted, I'm not a native English speaker, but I hope that won't be a problem! :)

---

### Post by Bucky Ball on 2016-09-17
Welcome. Lets try moving it to ***Hardware*** for now. Hopefully the following may be all you need ...

If you're wanting to resize the drive you are running the OS from, yes, it will be read only. Impossible to do, in fact.

You need to boot from the Ubuntu install media (you may need to make a USB or DVD to do this bit as it doesn't sound like you have either), choose 'Try Ubuntu' and when at a desktop, launch Gparted. Do what you like there as all partitions will be unmounted, including the / partition where you have Gnome installed, and you can resize partitions to heart's content. You can also do some severe breakage so be careful in there. ;)

Good luck.

---

### Post by roc-humet on 2016-09-17
> **Bucky Ball said:**
> If you're wanting to resize the drive you are running the OS from, yes, it will be read only. Impossible to do, in fact.

I may have expressed myself in the wrong way. The OS is installed in the laptop and it boots "normally" without the hard drive connected until the login screen (which doesn't show). The hard drive is completely empty (everything was removed when I formatted it), so I can't be running anything from there.

---

### Post by roc-humet on 2016-09-17
I fixed the problem. The problem was that for some reason Ubuntu was trying to mount the hard disk while booting.

I fixed the issue editing the file /etc/fstab and commenting the line of the hard drive.

---

### Post by Bucky Ball on 2016-09-17
Well done and good news. Could you please mark the thread as 'solved' to help others. Use Thread Tools at top right of page or see link in my signature.

---

