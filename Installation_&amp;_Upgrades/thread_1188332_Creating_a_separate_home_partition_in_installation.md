---
title: "Creating a separate /home partition in installation"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by Togezo on 2009-06-15
I have a disc of Juanty ready, and shall be buying a Dell Insprion 1545 tomorrow (Celeron 585 processor)

When I first posted about considering switching to ubuntu, I repeatedly received advice to create a separate /home partition which, now I understand precisely what this means, I would very much want to do.

I was just wondering if someone could offer advice on how to do this during the installation process, rather than afterwards?

(Note: The laptop comes pre-loaded with Vista, but I plan to remove the windows partition entirely.)

---

### Post by Amilo1718 on 2009-06-15
if you have the disc ready
there should be no problem booting & installing to your hard drive with a personal /home partition
;)

---

### Post by ajgreeny on 2009-06-15
Just boot the live CD, double click "Install" and choose manual partitioning when you get to that stage of the installation.  The system will find your disk and show a pictorial representation of it and the partitions on it.  Select and delete all those you want to get rid of which will make some unallocated space (perhaps the whole disk, but that is your choice).

Now select the unallocated space and click in the New partition (can't remember exactly how it's worded, but it is close to that I think) and make a new partition of about 10GB with mount point / (root), another partition of most of the rest of the space mount point /home, and finally a small partition of about 1 -2 GB as swap (no mount point for this one) and let the system do it's thing.  Now you should end up with the separate /home as you want at the end of the install.

I hope that makes sense to you.  Give it a try, if it all goes wrong you have only lost about 20 mins, so no real disaster at this stage, but I think it will all become clearer when you actually do it.

---

### Post by Togezo on 2009-06-15
Ah, thanks so much! Yes, I was also concerned (forgot to mention) as to how big each of the partitions should be. Thankfully, that all makes perfect sense. 

Thanks!
(THIS is why I want to use community developed software- ask for advice and it's there in minutes)

---

### Post by brncao on 2009-06-15
the "/" is called the root. It's where you install the OS (Ubuntu), software, drivers, etc. Think of it as C: for Windows.
"/home" is like a personal home directory where you can store desktop settings and personal data. Think of it as Desktop and Settings for Windows. If you uninstall Ubuntu, the /home partition still remains. Lastly the Swap partition serves as virtual memory should you run out of memory. I think it's better to understand what these do so you can make an informed decision when you partition your drives.

---

