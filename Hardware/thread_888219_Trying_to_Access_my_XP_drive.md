---
title: "Trying to Access my XP drive"
date: 2008-08-12
forum: Hardware
---

### Post by Nicholas482109 on 2008-08-12
I just install Xubuntu on an external hard drive and I want to back up files on this laptop's internal Windows XP drive that won't boot windows anymore. I have gone as far as attempting to mount the drive but when I try it tells me it's running. When i tried to force it the terminal said 'only root can do that', aren't I root??

---

### Post by pastalavista on 2008-08-12
use sudo. change owner of drive to 'username'. I think this is the code..
```
sudo chown username /media/drivename
```

username = your logon name
drivename = whatever the name of your drive is in the media folder

---

### Post by Bruce M. on 2008-08-12
> **Nicholas482109 said:**
> I just install Xubuntu on an external hard drive and I want to back up files on this laptop's internal Windows XP drive that won't boot windows anymore. I have gone as far as attempting to mount the drive but when I try it tells me it's running. When i tried to force it the terminal said 'only root can do that', aren't I root??

Take a look at QuickStart in my sig, it backups Windows partitions.

In Ubuntu you are not root, but you can get temporary root access with "sudo".

Good Luck
Bruce

---

### Post by Nicholas482109 on 2008-08-12
Well i figured out how to set the root password and i mounted the drive. How can I find the name my cd/dvd drive to mount it? and can that appear on my desktop when i insert a cd?



nicholas@nicholas-laptop-XU:~$ dmesg | grep dvd
[   43.865126] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray

---

### Post by bpl07 on 2008-08-13
> **Nicholas482109 said:**
> I just install Xubuntu on an external hard drive 

That's your problem.  When you installed on the external, it wiped the MBR on the internal.  The MBR tells you bootloader what you have installed.

If you want to install xubuntu on the external drive, you should use the windows bootloader instead of grub, or put a partition for /boot on the internal drive.  This can be done during the install process by manually partitioning your drives.

If you simply want to fix xp, put in your windows xp cd, boot in to restore mode, select windows xp, type in the administrative password, then run "fixmbr" at the console.  You'll need to reinstall xubuntu after this.

If you just want to view the xp files, install ntfs-config in System>Administration>Synaptic, then run Applications>System Tools>NTFS Configuration Tool.  This will set up your drive to be automounted.

---

### Post by Nicholas482109 on 2008-08-13
Well the problem with XP started before I decided to install Xubuntu on this computer, I cannot run the recovery console because i do not have the admin password, this is a school issued Lenovo T60p. But what will happen if i plug this external into another computer? will i be able to boot Xubuntu?

---

### Post by evets25 on 2008-08-13
> **bpl07 said:**
> That's your problem.  When you installed on the external, it wiped the MBR on the internal.  The MBR tells your bootloader what you have installed.

If you want to install xubuntu on the external drive, you should use the windows bootloader instead of grub, or put a partition for /boot on the internal drive.  This can be done during the install process by manually partitioning your drives.


If we could put the problem with windows not booting aside for a moment, wouldn't it be far simpler just to install xubuntu on the external drive as a self-contained unit, with it's own MBR and /boot partition, then make the drive bootable? Then you'd just need to set the laptop to boot from the external drive first, add windows to the grub list, (which should happen automatically when you install xubuntu) and you're good to go. That way, if the drive is plugged it will boot xubuntu by default (but you could still select windows) and if it's not plugged in, the laptop will just boot windows from the internal drive like normal, and the internal drive isn't touched.

---

### Post by Nicholas482109 on 2008-08-13
> **evets25 said:**
> If we could put the problem with windows not booting aside for a moment, wouldn't it be far simpler just to install xubuntu on the external drive as a self-contained unit, with it's own MBR and /boot partition, then make the drive bootable? Then you'd just need to set the laptop to boot from the external drive first, add windows to the grub list, (which should happen automatically when you install xubuntu) and you're good to go. That way, if the drive is plugged it will boot xubuntu by default (but you could still select windows) and if it's not plugged in, the laptop will just boot windows from the internal drive like normal, and the internal drive isn't touched.

That's what I thought was going to happen when I installed Xubuntu. I'm not worried about the internal drive, my school will just give me a new hard drive and send this 'faulty' one to some company at no cost to me. 

So how can I install Xubuntu and have a /boot partition on it? Right now I have a 5gb partition with xubuntu on it and 490gb FAT32 for use as storage. I can reformat and partition the drive to do this, no files are on it yet.

---

