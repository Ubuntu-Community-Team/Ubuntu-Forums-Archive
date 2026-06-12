---
title: "Installing ubuntu 7.04 on two hard drives"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by xelu01 on 2007-05-13
I want to install ubuntu over two hard drives is there a way i can do that.

---

### Post by taurus on 2007-05-13
Put / and swap on the first and use the second harddrive for /home.

---

### Post by xelu01 on 2007-05-13
How do you do that when you do a full installation of ubuntu, i have a maxtor 100gb and western digital 320gb. I don't know how to do it so if you can guide me through i will really appreciate it.

---

### Post by jjordan on 2007-05-14
If you do the install to the 100GB while the 320GB is in the system it will automatically be detected and will be mounted under /media/whatever the label of the drive is.  There are some variations on what the drive is called under /media so take a look.

Is the drive formated and what file system is it using.  Possible answers here are FAT32 (Windows 95/98/ME), NTFS (Windows NT/2000/XP/Vista), HPFS (OS X) or any of the Linux Filesystems like EXT2 EXT3 etc.  If I had to guess i would say it is most likely to be NTFS.  

That will work but may take a couple of extra steps to get full access to read and write files to it.

My Home theater system has 4 HD's on the first one is a 10GB partition with Kubuntu installed and then the remainder formated with EXT3, the other three drives are formated EXT3 and all four of those "drives" appear as subdirectories under /media 

This does require a small change of mindset from the Windows world where each drive has a letter and you need to explicitly address them that way.  


- j

---

### Post by xelu01 on 2007-05-14
Thanks i will try it out, hope it works.

---

### Post by xelu01 on 2007-05-14
Ok i can see the drive but i can't write anything to it how can i write something to it.

---

