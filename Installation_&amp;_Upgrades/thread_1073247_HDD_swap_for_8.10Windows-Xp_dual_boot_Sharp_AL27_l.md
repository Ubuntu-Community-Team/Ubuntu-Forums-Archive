---
title: "HDD swap for 8.10/Windows-Xp dual boot Sharp AL27 laptop"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by hopikrishnan on 2009-02-18
Many know that the Sharp Actius AL27 laptop ( AMD2700 64bit processor, 512RAM, 60GB hdd, RW-DVD) will soon lose its battery and become a desktop computer.  After about four years (only the first six months of real battery recharging !!) this laptop has seen dual boots with various linux versions.  All the while the original XP stayed in hda1.  This week I bought a new 160gb Seagate IDE harddrive for it.  Here is the procedure for the swap of the harddrives.  
1.  Take out the old drive and put it in an IDE-USB external case.  
2.  Put in the new drive and close the laptop panel.  Connect the power cord, (it has no battery!!) and start.  Go into BIOS.  The new drive is "seen" !!  Verify that the BIOS setup gives the CD drive the first priority for BOOT.
 3. Connect the USB drive to an USB port on the computer (there are four).  Make sure that the external drive and the computer are both sitting on a stable, vibration free spot on the floor.  
4. Open the CD-DVD and put in a live CD linux distribution.  I used Linux PC-OS 2007, which can launch the trackpad mouse in this Sharp laptop.  Ubuntu cannot.  (More on this later).  Do a CNTL-ALT-DEL to restart the computer.
5. when the live cd boots up and lets you login, login as ROOT.
6. Start the terminal and type in the command 'fdisk -l'   You should see your hda (no partitions) and the old drive named "sda" with all the things that are on it... the partitions for windows, linux etc..
7. Now use the instructions in the website below to make a clone of the old hdd (now called sda and sitting in the usb case) in the new hdd within the computer (now called hda).  The instructions call for typing the single line of code as root.
            dd if=/dev/sda of=/dev/hda
 [http://www.backuphowto.info/linux-backup-hard-disk-clone-dd](http://www.backuphowto.info/linux-backup-hard-disk-clone-dd)
8. I watched the command line for a while to make sure I hadnt made any spelling mistakes in the drive names.  Then pressed enter, watched the lights of both drives (inside and outside) go on and start to flicker for a few minutes.  Then went shopping for several hours.  
9. When I came back after about 3 hours, the cloning was done.  I shut down the computer, took away the live cd disc as it got ejected and when it finally shutdown, pulled off the external usb drive.  
10. When I restarted the computer, it started as if nothing had happened and went right into the grub screen and booted into the default OS - the ubuntu 8.10, 64bit version.  
   The trackpad was dead again.  I had to connect an external usb mouse and found everything to be as good as it was.  Except now I have gobs of free space in that drive.  
   I am planning to move the home folder to the windows partition and reinstall the Ubuntu 8.10 anew with new (larger) partition for the /home folder.  
   It is a pity that my trackpad mouse of this Sharp Actius AL 27 doesnt work under Ubuntu, whereas my wireless doesnt work under the PC-OS.  And my HP-PSC-all-in-one doesnt scan using xsane/kooki. So I need that windows-XP and HP-director to scan multiple pages into pdf files. There are also occasional games that I tend to play using XP. I obviously need to look for more info on trackpad and scanners in the linux forums.  However, I am happy that I was able to replace my hdd without getting into windows sort of difficulties.

(before I succeeded I failed in an attempt trying to the install XP from the recovery CD's that I made four years ago.  I am glad that didnt succeed, because success would have meant having to re-update the windows and the various software packages-where are those cd's?)

---

### Post by Mark Phelps on 2009-02-18
Unless you're really deadset against using PCLinuxOS, you should check out the new 2009 version.  They just released a Beta 3, and like te 2007 version, it defaults to KDE desktop.

Check the distrowatch website for the latest info and a download link.

---

### Post by hopikrishnan on 2009-02-19
Thanks for your recommendation.  I am not against PC-OS.  As I had already outlined, Ubuntu 8.10 makes my wireless work without any extra effort. I will download the 2009 PC-OS and check it out.  I really liked that OS because it had the right driver for the trackpad mouse, whereas I am stuck with using an external usb mouse for Ubuntu.  Making HP all-in-one 1210 xi PSC do scanning for me seems to be a lost cause no matter which distro of linux I use.
hopi..

---

