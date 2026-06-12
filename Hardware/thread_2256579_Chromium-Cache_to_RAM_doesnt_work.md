---
title: "Chromium-Cache to RAM doesnt work"
date: 2014-12-13
forum: Hardware
---

### Post by albertwoodman on 2014-12-13
[FONT=arial]Hey guys! 

I ve searched at the web already and tried a few things, but I just cant get it worked. I want to move my chromium cache to a RAM disc on my up to date xubuntu 14.10 x64. I have already made a RAM disk via /etc/fstab file. At my last try I added the following to de ~/.chromiumcache file: 
/bin/rm ~/.cache/chromium 
/bin/mkdir /media/ramdisk/chromium 
/bin/ln -s /media/ramdisk/chromium ~/.cache/chromium 

Terminal: sudo chmod +x ~/.chromiumecache 

Then I have made a ~/.chromiumcache as a startapplication. Earlier I tried a few other ways, but they also failed. So I hope, you can help me. With firefox it was no problem. If you need further information about my system, please let me know. 

[/FONT][FONT=Arial][FONT=arial]Thx![/FONT]
[/FONT]

---

### Post by ibjsb4 on 2014-12-15
What about this?

[https://wiki.archlinux.org/index.php/Chromium_tweaks#Tmpfs](https://wiki.archlinux.org/index.php/Chromium_tweaks#Tmpfs)

---

### Post by albertwoodman on 2014-12-17
Hey. 

I dont know where to type the "$ chromium --disk-cache-dir=/tmp/cache". The second alternativ via /etc/fstab didnt work. My fstab looks this way: 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc1 during installation
UUID=e4918ce7-1b27-430a-b21f-5ebfcd67c8c0 /               ext4    discard,noatime,nodiratime,errors=remount-ro 0       1
# swap was on /dev/sdc2 during installation
UUID=09d22640-ae49-4b48-a677-cf84ae56b2d9 none            swap    sw              0       0


# temporary directories 
tmpfs /tmp tmpfs defaults,noatime,mode=1777  0 0 
tmpfs	/home/diangelo/.cache	tmpfs noatime,nodev,nosuid,size=500M	0	0


# log directories  
tmpfs /var/log tmpfs defaults,noatime,mode=0755 0 0 
tmpfs   /dev/shm        tmpfs   defaults      0 0


Thx for your help!

---

