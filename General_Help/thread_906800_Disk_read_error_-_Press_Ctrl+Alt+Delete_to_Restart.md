---
title: "Disk read error - Press Ctrl+Alt+Delete to Restart (Black screen on repair)"
date: 2008-08-31
forum: General Help
---

### Post by poosenki on 2008-08-31
I have a dual boot of Windows XP and Ubuntu 8.04 set up but recently I've been getting a "Disk read error has occurred, press Ctrl+Alt+Delete to restart" error when trying to boot into Windows. I thought maybe a repair installation would fix this, but when I try to do that, the CD loads, it displays the first message about checking hardware, and then immediately goes completely black.

I'd really love to get Windows running again if possible. Any advice?

---

### Post by tjwoosta on 2008-08-31
i think your best bet is probably to just backup all your data and reinstall windows

1. try to mount the windows (ntfs) partition from ubuntu   
(it should show up in the Places menu as 56GB Volume, or however big the volume of the partiton is, mine is 56GB)

2. copy all of your important documents and stuff from windows into the ubutnu partition

3. delete the windows(ntfs) partition using gparted (gnome partiion manager)    
(you can install gparted from the add-remove programs list)

4. insert windows install cd and install windows to the unallocated space **BE SURE NOT TO OVERWRITE UBUNTU**
(installing windows to the unallocated space will not overwrite ubuntu, but it will overwrite GRUB with the default windows boot-loader, meaning you can no longer boot into ubunutu, but dont worry its an easy fix as long as you have an ubuntu live cd)

5. after installing windows and setting up everything you will want to install an ext3/ext2 compatibility driver (allows windows to acess the ubuntu(ext3) partition)

this is the one i use [http://www.fs-driver.org/]("http://www.fs-driver.org/")

6. restart the computer after installing the driver and it should automount the ubutnu partion  (it will show up with all the other devices)

7. copy all the files from the ubuntu partiton back over to windows

8. shutdown the computer

9. pop in the ubuntu live cd

7. this link tells you how to reinstall GRUB boot-loader after windows overwrites it
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

