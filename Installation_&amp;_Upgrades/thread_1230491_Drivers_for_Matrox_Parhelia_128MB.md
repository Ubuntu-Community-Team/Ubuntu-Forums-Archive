---
title: "Drivers for Matrox Parhelia 128MB"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by Lubelaczek on 2009-08-03
Hi,
I just instaled Ubuntu 9.04 and do everything for very first time and never had a chance experience work with Linux operated machine before. My computer has Matrox Parhelia 128MB (Dual Head) and I try to make it work as good as possible. However... Here is my problem when I try to install driver downloaded from Matrox website:

root@tmstas:~# /home/tmstas/Desktop/mtxdriver-installer-x86_32-1.4.6.run
Please, enter the directory to extract the files [/root/] /tmp/
Creating directory /tmp//matroxdriver-x86_32-1.4.6
Verifying archive integrity... All good.
Uncompressing Matrox Parhelia Driver..................................................................................................................................................................................................


========================================
   Matrox Linux Driver Install Script   
========================================

 Installation package v1.4.6

 Refreshing ld database
 Installed mtx_drv.so is the same file as the installer
 version, not installing.

 Installed v4l_drv.so is the same file as the installer
 version, not installing.

 Messages are being logged in file /tmp/make.log,
 this might take some time.

 Compiling mtx.ko ...
  ERROR: There has been an error compiling the kernel module. 
       A log file has been created in the file /tmp/make.log

Now, I don't post this log yet since some of you may have an quick idea what might be a problem. If you can help me I'll be more than happy but if the log is necessary to better understand what is happening I'll post it later.

---

### Post by Mark Phelps on 2009-08-04
This is a common misconception that folks have when first coming over from MS Windows -- that you get a generic driver installed initially and then you have to hunt down and install a driver specific to your video card/chip.

In Ubuntu, this second part is done as part of the installation.  The only difference is when there are "restricted" drivers available from Nvidia or AMD/ATI that are not automatically installed.

The log indicates that the Matrix driver is already installed -- which must be the case because, otherwise, you would not be seeing a graphical desktop.

---

### Post by Lubelaczek on 2009-08-04
Yes, you are 110% right. Entering to Ubuntu world with WinXP baggage is terrible. However I am old enough to have some DOS experience and hope that will help me.
After starting this thread I managed to install file (d/l from Matrox website) with almost 100% success. The problem was in xorg.conf file. Not created properly. Actually not created at all. File was empty. I did try to simple use listing found somewhere else. Partially did work, I was able to change refresh rate, resolution. Also prior installation  screen savers were not even close to smooth animations, jerky. After this installation they were noticeable faster and quite smooth. However still nothing in Hardware Drivers, pointer was split in two places and had shadow-like ghost. Basically, it was working much faster but freezing while I tried to look through all screen savers. It may sound lame but I really want to bring back to life this black, empty screen next to one I'm using right now. Currently visual effects are non existent and the way it works is not even close to possibilities that are hidden in this card. 
There must be out there someone who did this and it works fine for him/her. Please help.

---

### Post by merlinus on 2009-08-04
This may be useful:

[http://forum.tuxx-home.at/](http://forum.tuxx-home.at/)

And fwiw, I ditched matrox for nvidia.  Installing drivers and configuring them is a no-brainer directly from ubuntu, compared to jumping through hoops with matrox.

---

### Post by Lubelaczek on 2009-08-06
Thank you. I did manage to get second display to work. However it is a BIG issue for me how the cursor looks (see attached) Obviously I am far from being able to configure xorg.conf myself. Unless it is easy and some stubborn gay as myself will help me, share his/her knowledge how to make it work. It is simple, I can not afford any new ¨toy¨ for this long obsolete workstation. Also I have big library of video clips that need Parhelia along with it´s sister RT.X.100. As long as they are not ready to burn onto DVD I am married to Parhelia. Sad but true.
I have a dilemma which driver to use 1.4.6 or 1.4.7 (32-bit version). All tutorials I see are referring to 1.4.6. Is it only (1.4.7) beta?

---

