---
title: "Burning CDs"
date: 2005-09-03
forum: Hardware &amp; Laptops
---

### Post by fakie_flip on 2005-09-03
I have a CW068D ATAPI CD-R/RW cd writer and a cdrom that is a seperate drive. It reads cds fine and can install software from it. Ubuntu even knows when a blank disk is in the drive. The system hangs when I try to burn a cd. Both Nautilus 2.10.0 and K3B have the same problem. The problem with burning did not happen under Windows just before this. I installed a cao module for K3B to work. K3B did not come with Ubuntu. I installed that seperatly, and I found the cao module for it to work. What can I do to get the cd burner working? I have took Ubuntu off and reinstalled it. Whenever i try to burn a cd, I get an hourglass that never goes away, the mouse can not move, and I have to logout and log back in to get Ubuntu working again. I am using the latest version, Ubuntu 5.04. Please help.

---

### Post by skatedawe on 2005-09-03
Try Graveman or Nerolinux
 
 Graveman:
 sudo apt-get install graveman

 Nero linux:
 [http://www.nero.com/en/nerolinux-prog.php?pak=13](http://www.nero.com/en/nerolinux-prog.php?pak=13)

---

### Post by byen on 2005-09-03
graveman (code mentioned above)
gnomebaker(works best with gnome...duh) (sudo apt-get install gnomebaker)

goodluck

---

### Post by fakie_flip on 2005-09-03
root@linux-box:~ #  sudo apt-get install graveman
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package graveman
root@linux-box:~ # sudo apt-get install gnomebaker
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@linux-box:~ #

I do not think the problem is with the burning software. K3B did not work. cd record from a terminal did not work, and nautilus did not work.

---

### Post by GoA on 2005-09-04
I'll lend your topic. :D My problem is "slow" cd-burning. My drive can burn for 48x speed in windows but in linux "only" for 15-18x speed. I'm using gnomebaker, I have enabled burnproof and DMA should be on.

---

