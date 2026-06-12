---
title: "ubuntu installation partition wizard help"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by dansar99 on 2009-06-23
I have downloaded a Ubuntu dist to cd after trying Wubi. I uninstalled Wubi Ubuntu and trying to install Ubuntu in a partition of 27.1 g's. I get to the partition wizard and I am confronted with a decision. The bar shows my recovery partition and C drive in green. The 27.1 free space is colored orange with 24.6 g alloted to /dev/sda3 and 2.5 g to Ubuntu 9.04 with a slider that I can adjust. What would be the proper adjustment if any?. Is there any danger of losing Windows XP if I do this? Also I had removed Wubi Ubuntu using add/remove but my boot screen still gives me that choice. Will this effect my installation? I am just trying to be careful because I have lost my XP installation discs.Thank you for any help.  Dan

---

### Post by running_rabbit07 on 2009-06-23
Inside Microsoft XP go to your start menu and click run. Inside run enter Backup. The default Windows backup program should ask if you want to install, do it. This handy program will allow you to back up to another hard drive or make a backup disc set. You really should back up your system before doing partition work. I installed my partitions without any problems but not being able to reinstall windows isn't an option you want to loose. Or at least make backup copies of important files such as pics, music and documents.

When you install Ubuntu it should fix the boot loader you were talking about. You should adjust the install to use the whole partition you allready created for Ubuntu or just let it do it's thing if you are not worried abiout that little extra space.

---

### Post by dansar99 on 2009-06-23
thank you for replying.  My problem is my cd writer doesn't work but my cd-rom does. So making back up disks is a problem. I created the ubuntu disk on another computer.  Is there a way I can create the back up and burn it with another computer?. Thanks again.  Dan  P.S.  I typed Backup in run and I got a message that said Windows cannot find Backup.

---

### Post by presence1960 on 2009-06-23
> **dansar99 said:**
> I have downloaded a Ubuntu dist to cd after trying Wubi. I uninstalled Wubi Ubuntu and trying to install Ubuntu in a partition of 27.1 g's. I get to the partition wizard and I am confronted with a decision. The bar shows my recovery partition and C drive in green. The 27.1 free space is colored orange with 24.6 g alloted to /dev/sda3 and 2.5 g to Ubuntu 9.04 with a slider that I can adjust. What would be the proper adjustment if any?. Is there any danger of losing Windows XP if I do this? Also I had removed Wubi Ubuntu using add/remove but my boot screen still gives me that choice. Will this effect my installation? I am just trying to be careful because I have lost my XP installation discs.Thank you for any help.  Dan

choose the "manual" option at that screen. Then highlight the 27.1 GB disk. Click Edit partition and set the parameters such as partition type (primary or extended), Use as (Filesystem - usually ext 3 or ext 4) Mountpoint (set as /) Then continue with the install

---

### Post by presence1960 on 2009-06-23
here is where you choose "manual" option

---

