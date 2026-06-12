---
title: "ntfs-3g external hdd write support"
date: 2006-09-05
forum: Hardware &amp; Laptops
---

### Post by adityasen on 2006-09-05
I've had no problems with ntfs write support in ubuntu after I installed the ntfs-3g package following the instructions here [http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+external+disk](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+external+disk)

Now my problem is with my external HDD. Ntfs-3g only enables write support for those devices listed in /etc/fstab. To enable write support on my external HDD, I manually added my ext HDD /etc/fstab and it works fine. But since I'm running a laptop, I dont always have my external drive connected. When it is not connected and i try to plug in a usb flash drives, i get a mount failed error. This is because the drive tries to mount on /dev/sda1, but that is listed in /etc/fstab as my external ntfs HDD. Now I dont want to go through the process of editing the fstab file each time i unplug my HDD so i get get support for flash drives. is there any workaround? such as getting all flash drives to mount on say /dev/sda2 or something like that?

Another thing. The HOWTO guide (link posted above) has mentioned about this problem and gives the solution by adding a script 'mount_with_ntfs_3g'. But this didnt work for me. When I plug in my HDD and run the script, i get an error 'device already mounted'. If i unmount manually and then run the script, i get 'failed to mount with ntfs-3g'

this is a really irritating problem. pls help

cheers
aditya

---

### Post by christhemonkey on 2006-09-05
I have that problem with the unmount script and the external hard drive not having a static mountpoint.

My current workaround is to just never unplug the hardrive, if i want to use another usb device, then tough :)

---

### Post by adityasen on 2006-09-05
thats not really much of a workaround. I'm sure there must be a way to solve the problem

---

