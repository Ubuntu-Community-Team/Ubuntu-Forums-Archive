---
title: "ubuntu under windows"
date: 2008-08-31
forum: General Help
---

### Post by simons-photography on 2008-08-31
could someone explain about the option of installing ubuntu under windows ? what exactly happens ?

also I've tried both i386 and AMD64 versions and both copy all the files from the CD to the hard drive and then say that the cd is in use and it can't continue shall I cancel or retry ? if I select retry is just starts copying all the files again, I'm on windows XP pro

---

### Post by whaxx0r on 2008-08-31
You specify only the first user's account. It doesn't do the partition stuff, so you must create 2 partitions before installing. One with ext3 file system and one with linux-swap.

Then, after the installation is complete, you reboot your computer. It gives you the GRUB menu and Ubuntu is installed.

---

### Post by simons-photography on 2008-08-31
erm this is sort of installing itself in a windows folder the option on the CD's menu say install and uninstall ubuntu under windows like any other program. I select that I want to use 30 GB for the instaltion and the folder createdis 30 GB in size despite just having the CD contents in it its like its going to be emulated under windows or something

---

### Post by pfdevil on 2008-08-31
Explore your ubuntu cd and use wubi to install ubuntu

---

### Post by simons-photography on 2008-08-31
yes but I'm asking "what will actually happen" I don't want to do something I won't be happy with later

---

### Post by Dutch70 on 2008-08-31
It can be installed and uninstalled like any other program in windoze. That is its purpose.

Dutch

---

### Post by drs305 on 2008-08-31
> **simons-photography said:**
> yes but I'm asking "what will actually happen" I don't want to do something I won't be happy with later

With a wubi install, you insert the LiveCD once you are in Windows. As you begin the install you will be asked what size you want to reserve. You cannot change the size later. I think my choices were between 4-20 GB. It will then install wubi into a folder called "Ubuntu". There is no partitioning - only the Ubuntu folder - set to the size you designated during the install. All settings, info and files are installed in the single file 'Ubuntu/disks/root.disk'.

When you boot into Windows after the install, the Windows boot loader (not grub menu) will ask if you want to start Windows or Ubuntu.

If you decide to uninstall wubi, there is an Uninstall_Ubuntu.exe file or you can remove it via the Control Panel's Add/Remove applet.

---

