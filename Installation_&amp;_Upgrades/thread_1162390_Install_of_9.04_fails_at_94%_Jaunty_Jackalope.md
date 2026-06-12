---
title: "Install of 9.04 fails at 94% Jaunty Jackalope"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by hal8000 on 2009-05-17
The live CD of Jaunty boots and works correctly. However chosing the install icon from live environment or the install option booting from the CD always fails at 94%.

After progress bar reaches 94% the screen displays a few lines of text in console mode, starting gnome and then asks me to log in, however the new user ID is never created and I am logged in as user ubuntu automatically.

I have a multi boot linux, so can access the failed Ubuntu install. What I find is that Ubuntu never installs grub and also the Ubuntu kernel, initial ramdisk and grub/meny.lst are never created.


Fortunately I also have a laptop and Jaunty has sucessfully installed, so I will be copying the kernel, ramdisk and menu.lst file to my desktop to see if I can complete the installation. This also happened with 8.10, 8.04 installed successfully on my dekstop.

Desktop Specs
Asus P4P800
Intel P4 2.8GHz
1G RAM
Nidia 7600GTS
Maxtor 160G  IDE
Fujitsu 160G SATA

I am installing Ubuntu on the SATA drive, which has two primary partitions of ntfs and hfsplus. All other partitions are linux partitions.
The / and /home partitions seem to be filled except for the Ubunti kernel.
Not sure yet wheter this is caused by the mac filesystem or some other problem
Thanks in advance for help, if I solve this will post a solution.

---

### Post by hal8000 on 2009-05-28
Got this working with the alternate install CD (32bit) version.

---

