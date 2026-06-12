---
title: "Installed Ubuntu using Wubi, but nothing happens"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by Balzard on 2009-10-07
Hello,

I have good computer skills, but I am completely new with the Linux universe, and I would like to discover it. I recently downloaded Ubuntu 9.04 and tried it without installing it, but I would now like to install it using Wubi.

I placed the Ubuntu ISO in the same folder as Wubi.exe and started the application, after which the window automatically closed itself (no confirmation message or invitation to reboot).

When I boot my computer, WindowsXP starts automatically and I don't have the choice of booting Ubuntu.

I tried reinstalling Ubuntu a few times, with no success. I also used the "checkdisk /r" and "fixmdr" commands.

I would prefer using Wubi instead of creating a partition. Can anyone tell me why I can't boot into Ubuntu?

---

### Post by sailthesea on 2009-10-07
If you have good internet connection its probably easier to do it online Install Wubi inside Windows and then run and install from the website It just seems to work better like that Once done you will be given the dual boot option at bootup
Start here 

[http://wubi-installer.org/](http://wubi-installer.org/)

Welcome and Good Luck!

---

### Post by ram2500 on 2009-10-07
I have heard that Windows Disk Cleanup can accidentally mistaken the boot record images (Wubi) as junk files if you happen to run Cleanup right after installation, instead of rebooting. 

Another possibility: which drive did you select to install to? You may have accidentally mistakened, say, a flash-card or an external drive (if you have those connected) instead of the C: drive. What I would do is to uninstall Ubuntu (Ubuntu is actually listed in  Add/Remove Programs) and re-do the whole process, making sure to install to the C: drive.

---

### Post by Balzard on 2009-10-08
I've downloaded the Ubuntu twice already (once from a French Ubuntu-related website, once from the official website), so I doubt the Wubi-downloaded ISO will do much of a difference... plus, it sometimes tries to download the AMD 64bit version, even if I use an Intel 32bit interface.

Also, I tried rebooting right after installing, and nothing changes.

Could there be a link with my previous installation? Here's what I did prior to trying Wubi.

1. Downloaded Ubuntu ISO file and burned it.
2. Tried the OS without installing it.
3. Decided to install it from the Ubuntu interface, chose "dual boot" method, without creating a partition prior to that
4. For some reason, there wasn't any space left on the hard drive for installing updates, so I returned to Windows and decided to unintall Ubuntu using Partition Magic (I simply deleted the 2 partitions that didn't appear in Windows Explorer but were related to Ubuntu)
5. When I restarted my computer, an error appeared, so I inserted the Windows CD and used the "fixmbr" command in the Restore options.
6. I ran the "checkdisk /r" command
7. Tried installing Ubuntu with Wubi, without success (either from the Ubuntu CD or the ISO)

Help!

---

### Post by Balzard on 2009-10-08
I've just tried letting Wubi download and install Ubuntu, but it still doesn't work!

---

### Post by sailthesea on 2009-10-08
> **Balzard said:**
> I've downloaded the Ubuntu twice already (once from a French Ubuntu-related website, once from the official website), so I doubt the Wubi-downloaded ISO will do much of a difference... plus, it sometimes tries to download the AMD 64bit version, even if I use an Intel 32bit interface.

Also, I tried rebooting right after installing, and nothing changes.

Could there be a link with my previous installation? Here's what I did prior to trying Wubi.

1. Downloaded Ubuntu ISO file and burned it.
2. Tried the OS without installing it.
3. Decided to install it from the Ubuntu interface, chose "dual boot" method, without creating a partition prior to that
4. For some reason, there wasn't any space left on the hard drive for installing updates, so I returned to Windows and decided to unintall Ubuntu using Partition Magic (I simply deleted the 2 partitions that didn't appear in Windows Explorer but were related to Ubuntu)
5. When I restarted my computer, an error appeared, so I inserted the Windows CD and used the "fixmbr" command in the Restore options.
6. I ran the "checkdisk /r" command
7. Tried installing Ubuntu with Wubi, without success (either from the Ubuntu CD or the ISO)

Help!

 3 4 5 I think you gravel trapped the drive with attempts at installing and partitioning 
6 If you are windows savvy use the disk management tool to fully delete all ubuntu partitions and fully resize the HDD for windows then defrag and try again 
7 Maybe with Wubi download If your LiveCD worked the system OK there shouldn't be any problem
Install and Run Wubi INSIDE Windows and it will download and install ubuntu in a virtual drive You can boot into either at startup
 Hope you get there:P

---

