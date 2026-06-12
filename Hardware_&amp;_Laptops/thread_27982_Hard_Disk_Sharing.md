---
title: "Hard Disk Sharing"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by Loft on 2005-04-18
Not sure this is in the right section, but I've been experimenting with Ubuntu for a while now and wish to permanently dual boot with Windows XP. Now I have two hard disks, one for Windows and Ubuntu, and another with music and general documents. I want to be able share this between both Windows and Ubuntu, and have the ability to both read and write to it. At the moment it's NTFS, which I realise you can write to in Ubuntu, but it's a bit unstable right? Would formatting the drive as a FAT or FAT32 partition allow me to read/write in both OS's without any problems?

Thanks in advance.

---

### Post by domesticatewhat on 2005-04-18
I have an external hard drive formatted in fat32 and share it with a windows computer. I am able to write/read on both linux and windows...so yes fat32 would work.

---

### Post by Loft on 2005-04-18
Okay, thanks for the quick reponse.

---

### Post by wxlidar on 2005-04-18
Yep, you can read and write to FAT32 using both Linux and Windows. This is how I share data between the OS's.

_Dave

---

### Post by eXidos on 2005-04-18
Ok I'm now haveing a problem with my fstab file that should be a simple fix, but I cant get it. What is the syntax to get rw access for all users to my fat32 drive? (not just for root)

This is what I have right now:

/dev/hda4 /mnt/server vfat user,rw,exec,umask=000

This mounts the drive, I can read the drive listen to music open files and so on but I can't write to the drive. It says "you dont have permissions to write to the drive" all I need is the proper syntax in my fstab, but I cant figure it out.

please help!

Thank-you
X

---

