---
title: "Moving system folders from one hard drive partition to another"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by ricky22 on 2009-02-19
Hey,

I reinstalled Ubuntu recently (8.10), and used this opportunity to create three additional 10GB partitions, where I would like to install and try out different operating systems (Solaris, Nexenta, BSD etc.). Unfortunately, the Ubuntu installer wouldn't let me create those unless I selected "mount points" for them from a few available options. I didn't know what exactly that meant at that time, and selected /boot, /tmp and /var. It turns out that now my system folders boot, tmp and var were installed on one 10GB partition each. Is it possible to copy them to my main Linux partition, to free those three so I can format them and install other systems? I really appreciate your help, cheers!

Patrick

---

### Post by durand on 2009-02-19
For /tmp and /var, you just need to copy them to your main partition and then edit /etc/fstab and comment out the lines(# at the start of the line) to prevent those partitions from being mounted. 

For /boot, it is a bit more complicated. You need to copy the folder across and then you will need to fix grub somehow because it will be looking for the config file in a partition that doesn't exist. Maybe someone else will be able to help you with this but I'm not so sure...

Don't try anything out until you know exactly what you're doing.

---

### Post by ricky22 on 2009-02-19
Hey, 
Thanks vm for the quick reply. How do I copy folders between partitions? They aren't shown anywhere with little hard disk icons as in Windows. As for /boot, I guess it's just the matter of editing /boot/grub/menu.lst, right? Again, thanks for your help!
Patrick

---

### Post by durand on 2009-02-19
They won't be displayed as icons because they are being mounted as part of the main partition.

Press Alt+F2, type in gksudo nautilus and type in your admin password. Then go to / and create 3 folders. /tmp_new /var_new and /boot_new. Then copy everything from /tmp into /tmp_new and so on. **Don't delete the original partitions!** Press Ctrl+H to show all files, including hidden files first so that nothing is missed out. You should also compare the folder permissions for the original and the new folders.

Then you will need to use a live cd or another linux distro to do the rest since you are changing fundamental parts of the system and it cannot run without them.

In the live cd, go to Places>Computer and double click on the root partition. /tmp should be empty inside it. You can then delete that folder and rename /tmp_new to /tmp. Repeat this for the other folders. Then edit /etc/fstab in your root partition and comment out the mount lines for /var and /tmp. That should really be it.

The only problem is that I have no idea how to make that work for /boot. I think that grub-install needs to be run but you really need input from others before doing anything like this. Oh and take backups!

---

### Post by ricky22 on 2009-02-19
I followed your advice and freed two partitions. I think I'm fine with these for now, if I need the /boot partition, I think similar procedure, and then fixing MBR and GRUB with Super Grub Disk should work. That was very helpful, cheers!

---

### Post by ricky22 on 2009-02-19
Problem solved! I moved the content of /boot to the main partition in the same way as the other two, then restarted system with live CD in the drive, chose the option to boot from hard disk and ran 

grub-install /dev/sda1

I'm going to try out OpenSolaris on one of my newly freed partitions, the live CD looks really cool, somewhat familiar but different. Thanks for the help!

---

### Post by durand on 2009-02-20
Wow, thats great! Have fun :D

---

### Post by ricky22 on 2009-02-22
That didn't go very well I'm afraid... Installing OpenSolaris destroyed my Windows partition and my Ubuntu /boot partition, so I had to reinstall both. In case anyone wants to give it a go, the problem is, Solaris does not recognise extended partitions. Before installing it, make sure you only have primary partitions on your disk. Also, Linux GRUB does not read Solaris' ZFS file system (the work on that is in early stages), so for dual boot you will need to use OS's GRUB instead. Before installing OS, you need to copy the Ubuntu entry from /boot/grub/menu.lst, then, after installation, paste it into OS's menu.lst. Here are the links that describe in more detail how to do this:

[http://opensolaris.org/os/community/documentation/reviews/Dual_Boot_Install_Doc_Plan/Dual-Booting-OpenSolaris-with-Ubuntu-Linux/](http://opensolaris.org/os/community/documentation/reviews/Dual_Boot_Install_Doc_Plan/Dual-Booting-OpenSolaris-with-Ubuntu-Linux/)

[http://wikis.sun.com/display/OpenSolaris/OpenSolaris0811InstallationFAQ](http://wikis.sun.com/display/OpenSolaris/OpenSolaris0811InstallationFAQ)

Q: Why would someone want to install OpenSolaris if Ubuntu is so great?
A: Ubuntu wouldn't be so great if there were no Unix before it. Standing on the shoulders of giants, or something like that;-)

---

### Post by durand on 2009-02-23
Aww :( Well, I really hope it wasn't something I said. What's OpenSolaris like?

---

### Post by ricky22 on 2009-02-23
No, absolutely not, it was just me installing a new OS for the first time, and not caring to read a single howto, just popped the CD in the drive... 

OpenSolaris seems cool so far, it uses GNOME desktop, so looks familiar. There is a project to port Ubuntu packages to it - [http://www.nexenta.org/](http://www.nexenta.org/)

Hardware support is an issue, and it requires more RAM than Linux. Anyway, live CD is available here:

[http://opensolaris.org/os/downloads/](http://opensolaris.org/os/downloads/)

Enjoy :-)

---

### Post by durand on 2009-02-24
I'll definitely give it a go. Thanks for the links!

---

### Post by ricky22 on 2009-03-08
If this isn't cool I don't know what is...

---

### Post by ricky22 on 2009-03-08
If you just want to try it out, it's worth installing it in VirtualBox. I have never tried virtualisation before, and I was genuinely surprised how ridiculously easy it was. And that's after years of struggling with Wine... For those interested:

[http://dlc.sun.com/osol/docs/content/IPS/virtualbox.html](http://dlc.sun.com/osol/docs/content/IPS/virtualbox.html)

...and a general VirtualBox guide:

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by ricky22 on 2009-03-08
P.S. By Wine I meant the compatibility layer software, I have my drinking totally under control ;)

---

### Post by durand on 2009-03-08
That looks pretty cool :D I use vbox a bit but I don't really like virtualising. I'll probably try opensolaris when my dell laptop arrives.

---

