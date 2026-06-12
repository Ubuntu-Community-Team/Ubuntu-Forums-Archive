---
title: "Transferring Files from Ubuntu Desktop to A Windows Laptop?"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by wk1989 on 2007-08-21
I recently purchased a Dell Vostro 1500 Laptop which runs Windows Xp Home edition. I'm taking this laptop for school so I wanna transfer some files from my desktop running Ubuntu to the laptop. The desktop also has windows xp pro installed (I dual boot). What's the quickest waay to transfer these files? They're about 20 gigs in total. I have a 2gb USB drive, which could be used. I also have a wireless network so I can use ethernet (if I set up file sharing correctly). Btw, the files are stored on an ext3 partition. Thanks in advance!

---

### Post by Ek0nomik on 2007-08-21
If all your files are on the EXT3 partition you have a few options:

You could go back and forth putting all the data on your USB thumbstick device.

Or you could also log into your Ubuntu box via SSH and download all the files in a simple click and drag format.

If you don't have SSH installed on your Ubuntu box, you can do so by:

```
sudo apt-get install openssh-server
```

Then, on your Windows box, you will want to download WinSCP.

[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

This will allow you to login to your desktop.

It may go slow if you transfer it all via Wireless though.  You could plug an Ethernet cord from the desktop directly into the laptop and it will go faster.  The transfer rate may also not go as fast as you wish because all of the transferring of files is encrypted by using SSH.  You can disable it if you wish.

Let me know if you have any more questions.

---

### Post by wk1989 on 2007-08-21
Well, I don't have a ethernet cable that can be used to establish a direct connection. Would samba allow me to share files from my desktop so they're accessible from a windows computer? Also how slow is SSH anyway? Compared to USB 2.0 (after accounting for the trouble of having to do multiple transfers). Which one should be faster?

---

### Post by Ek0nomik on 2007-08-21
I don't know about the speed, I have never used Samba.  Samba should allow you to connect to your Windows box though.

If you don't have an Ethernet cable then your speed issue will probably be the wireless anyways.

---

### Post by nwbearcat84 on 2007-08-21
I have used Samba for many years to transfer files between Linux and Windows machines.  It totally depends on the speed of your network, network cards, etc. Overall, it's a lot faster than using your USB drive.  Here is my favorite site for quick answers:  [http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page) under Feisty, Samba configuration is under section 1.19.4.  For future transfers, I would highly recommend getting a crossover (network cable that allows you to hook computers directly together).  You would be amazed how fast 20 gigs can be transfered.

---

### Post by Ek0nomik on 2007-08-21
> **nwbearcat84 said:**
> I have used Samba for many years to transfer files between Linux and Windows machines.  It totally depends on the speed of your network, network cards, etc. Overall, it's a lot faster than using your USB drive.  Here is my favorite site for quick answers:  [http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page) under Feisty, Samba configuration is under section 1.19.4.  For future transfers, I would highly recommend getting a crossover (network cable that allows you to hook computers directly together).  You would be amazed how fast 20 gigs can be transfered.

A 10/100 network card will transfer at maximum 10MB a second, while USB 2.0 can transfer up to 60MB a second.

---

### Post by nwbearcat84 on 2007-08-21
What about the time spent transferring information to the USB device, disconnecting it, connecting it to the other computer, deleting the files on the jump drive at some point, disconnecting it, and connecting it back to the first computer?  Been there done that, lots more babysitting involved... but I suppose it would work for people who have time to sit there and do it in a more manual fashion.

---

### Post by Ek0nomik on 2007-08-21
> **nwbearcat84 said:**
> What about the time spent transferring information to the USB device, disconnecting it, connecting it to the other computer, deleting the files on the jump drive at some point, disconnecting it, and connecting it back to the first computer?  Been there done that, lots more babysitting involved... but I suppose it would work for people who have time to sit there and do it in a more manual fashion.

Yeah I know, I thought about that too.  :)

Just thought I would point it out.

Getting an external hard drive would be a good investment.  Makes backups a breeze.

---

### Post by tyggna1 on 2007-08-21
If you dual-boot on both:  Then the easiest/fastest way, that would take only a few minutes would be to install the NTFS configuration utility on the Ubuntu with the partition you want to transfer the files from.  Move those files to your windows partition (probably about 2 mins).

From there, boot to windows (the longest part of this process), and share that folder.  You can either directly connect the two computers and set up a limited LAN that way, or connect them through a router.  After that, get on the computer you want to put the files on, and just drag them from the network share to your computer (should take about 3 or 4 minutes)

---

### Post by nwbearcat84 on 2007-08-21
I do have to agree with Ek0nomik.  An external HD would be the easiest way to keep backups.  This would also make it easier to keep a master copy of all your files.  I tend to find myself having to sync copies of all my files as I have multiple computers and no external HD, though one of these days I plan on buying one.  If you decide to go with Samba, I've not tried using a similar software in Windows, but if you carefully control your shared files (turning sharing on and off), you can use a software such as SyncBack from [www.2brightsparks.com](www.2brightsparks.com) to keep your files synced on both computers, thus reducing the amount of times you have to transfer back and forth (this also works going from a computer with all your files on it to one with none of them).  It's been awhile since I've used it, but if I remember correctly, it works great, and relatively fast.  If anybody knows of a similar software for linux, I'd like to know about it.

---

### Post by Ek0nomik on 2007-08-21
> **nwbearcat84 said:**
> I do have to agree with Ek0nomik.  An external HD would be the easiest way to keep backups.  This would also make it easier to keep a master copy of all your files.  I tend to find myself having to sync copies of all my files as I have multiple computers and no external HD, though one of these days I plan on buying one.  If you decide to go with Samba, I've not tried using a similar software in Windows, but if you carefully control your shared files (turning sharing on and off), you can use a software such as SyncBack from [www.2brightsparks.com](www.2brightsparks.com) to keep your files synced on both computers, thus reducing the amount of times you have to transfer back and forth (this also works going from a computer with all your files on it to one with none of them).  It's been awhile since I've used it, but if I remember correctly, it works great, and relatively fast.  If anybody knows of a similar software for linux, I'd like to know about it.

Have you looked at any of the software available in the repository?

```
fleur@love:~$ sudo aptitude search backup
p   afbackup                                                                               - Client-Server Backup System (Server side)                                                       
p   afbackup-client                                                                        - Client-Server Backup System (Client side)                                                       
p   afbackup-common                                                                        - Client-Server Backup System (common files)                                                      
p   backup-manager                                                                         - command-line backup tool                                                                        
p   backup-manager-doc                                                                     - documentation package for Backup Manager                                                        
p   backup2l                                                                               - low-maintenance backup/restore tool for mountable media                                         
p   backupninja                                                                            - lightweight, extensible meta-backup system                                                      
p   backuppc                                                                               - high-performance, enterprise-grade system for backing up PCs                                    
p   cdbackup                                                                               - CD-R(W) backup utility                                                                          
p   cedar-backup2                                                                          - local and remote backups to CD-R/CD-RW media                                                    
p   cedar-backup2-doc                                                                      - local and remote backups to CD-R/CD-RW media (documentation)                                    
p   chiark-backup                                                                          - backup system for small systems and networks                                                    
p   dvbackup                                                                               - backup tool using MiniDV camcorders                                                             
p   dvdbackup                                                                              - tool to rip DVD's from the command line                                                         
p   dvdbackup-dbg                                                                          - debug files for dvdbackup                                                                       
p   faubackup                                                                              - Backup System using a Filesystem for Storage                                                    
p   flexbackup                                                                             - Flexible backup tool for small to medium sized installations                                    
p   floppybackup                                                                           - Floppy backup using a diversity of floppy formats                                               
p   hubackup                                                                               - Concise and easy to use backup application for the desktop user                                 
p   ibackup                                                                                - Automated backups (even remote) of machine configurations                                       
p   jpilot-backup                                                                          - Backup plugin for J-Pilot                                                                       
p   libmultisync-plugin-backup                                                             - Backup plug for MultiSync                                                                       
i   rdiff-backup                                                                           - remote incremental backup                                                                       
p   sbackup                                                                                - Simple Backup Suite for desktop use                                                             
p   simplebackup                                                                           - Simple backup tool                                                                              
p   slbackup                                                                               - Skolelinux Backup system                                                                        
p   storebackup                                                                            - fancy compressing managing checksumming hard-linking cp -rua                                    
v   vbackup                                                                                -   
```

---

### Post by nwbearcat84 on 2007-08-22
Unfortunately, I have not had too much time to even be around my computers this summer.  I have been working really weird hours (as you can see by the time stamp on this post).  Now that I go back to college next week, I've been trying to spend a little more time getting them ready and stuff.  But thanks for the list... I knew it was probably a stupid, lazy question, but if you don't ask, you'll never learn.

---

