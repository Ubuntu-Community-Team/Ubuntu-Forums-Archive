---
title: "cannot boot installation disk"
date: 2006-02-07
forum: Installation &amp; Upgrades
---

### Post by hollowhead on 2006-02-07
I downloaded the ubantu iso file (ubuntu-5.10-install-i386.iso) burn't it onto the RW CD using the built in XP software.  After changing the bios settings so that this machine boots from the cd first I tried to see if it would boot.  It doesn't where am I going wrong?

---

### Post by Robgould on 2006-02-07
probably a corrupt .iso.  Just a guess, but if you feel confident that the disk should boot and it does not, then you probably had an error downloading or burning the .iso.  Did you use the checksum to verify it?

---

### Post by hollowhead on 2006-02-07
Thanks for your reply. No how I do that given I am not allowed or able to install any software on this machine?

---

### Post by hashimoto on 2006-02-07
As far as I know, XP's own burning software is not able to burn images (iso-files) as images, but burns them as data files. That won't do. You will need a software that can burn image files.

You can check md5sum with a little command prompt program that you can get from here: [http://www.etree.org/cgi-bin/counter.cgi/software/md5sum.exe](http://www.etree.org/cgi-bin/counter.cgi/software/md5sum.exe)
And it won't need admin rights on XP.

---

### Post by Robgould on 2006-02-07
Why can't you install anything?  Why would install a completely seperate operating system on a computer that is not yours and you don't have girhts too?  I am confused now.  Where are you going to stall Ubuntu?  Did you free up partition space?  The chance is small, but there is a chance that you could erase data installing Ubuntu.  Even if you install it right, you overwrite the computers mater boot record.  Windows will not boot the same.  If you do not have rights to the computer, do not install Ubuntu.  It will not go unnoticed by you administrator.
 
That being said...this thread should help you
 
[http://www.ubuntuforums.org/showthread.php?t=101533&highlight=verify+checksum]("http://www.ubuntuforums.org/showthread.php?t=101533&highlight=verify+checksum")

---

### Post by hollowhead on 2006-02-07
I don't want to install it at work just boot into the installation process to see if the burn has worked and abortthe installation process which you can do. I want to install it it on laptop A wise precuation as it happens...  

I did some research about the checksum and iso's and downloaded the XP shell extension burner.  Cannot install it cannot copy mdsum5 to correct dirs here (don't have rights) copied it to another folder tried running it.  Momentarily a dos window (I think its so fast) appears then dissappears.  Question at home I have slow dialup can I take the iso home on a CD and bung it on linux/windows check and reburn it or will it be corrupted in its burn onto the CD?

---

### Post by Robgould on 2006-02-07
You can burn it on a cd as a file....an iso is a compressed image....you can burn the .iso file on the disk jsut like you downloaded it.

---

