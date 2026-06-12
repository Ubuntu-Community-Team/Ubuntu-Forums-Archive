---
title: "Samsung 840 EVO - SSD"
date: 2019-07-12
forum: Hardware
---

### Post by Shibblet on 2019-07-12
Alright... let's get down and dirty here...

I had a friend tell me that my Samsung 840 EVO Drive will only work "properly" in Windows, because the Samsung Magician Software is the only thing that will run Trim.

I would assume that Ubuntu supports Trim by default by now...  Alas, many a Google search has not found the proper answers I am looking for.

How does Linux handle SSD's, compared to Windows?  I always thought the EXT4 File System was far superior to NTFS.

---

### Post by #&amp;thj^% on 2019-07-12
There is no reason for not using Samsung EVO series SSDs with Ubuntu.
also see:
[https://askubuntu.com/questions/674320/what-ssd-optimization-are-needed-on-latest-ubuntu-version](https://askubuntu.com/questions/674320/what-ssd-optimization-are-needed-on-latest-ubuntu-version)

[https://askubuntu.com/questions/1400/how-do-i-optimize-the-os-for-ssds?noredirect=1&lq=1](https://askubuntu.com/questions/1400/how-do-i-optimize-the-os-for-ssds?noredirect=1&lq=1)

---

### Post by Shibblet on 2019-07-12
> **1fallen said:**
> There is no reason for not using Samsung EVO series SSDs with Ubuntu.
also see:
[https://askubuntu.com/questions/674320/what-ssd-optimization-are-needed-on-latest-ubuntu-version](https://askubuntu.com/questions/674320/what-ssd-optimization-are-needed-on-latest-ubuntu-version)

[https://askubuntu.com/questions/1400/how-do-i-optimize-the-os-for-ssds?noredirect=1&lq=1](https://askubuntu.com/questions/1400/how-do-i-optimize-the-os-for-ssds?noredirect=1&lq=1)

The first link was written in 2010, and the second in 2015.  Do these still apply for 19.04?

I am referring to this portion of the posting:

> 2) No Writes for Read Timestamps (suitable for SSD's and hard drives)

Mounting your partitions with the options noatime and nodiratime will stop timestamp writes when you read files and folders. These timestamp writes are not generally required unless you use a local mail server client such as mutt. The reason this is generally a bad idea, is because every read will produce a write when updating the timestamps. This decreases the life of the SSD.

Edit your /etc/fstab configuration file (carefully - take a backup to be sure as breaking your fstab configuration can prevent you system from working):

cp /etc/fstab ~/fstab-backup
gksudo gedit /etc/fstab

Edit the mounting options for your partitions by adding the text noatime and nodiratime to the lines defining your root (/) and other partitions if you have them (/home) - Note: if you have a /home partition, start with that just changing that partition if you are concerned about breaking something

# / was on /dev/sda2 during installation
UUID=587e0dc5-2db1-4cd9-9792-a5459a7bcfd2 /               ext4    noatime,nodiratime,errors=remount-ro 0       1

# /home was on /dev/sda3 during installation
UUID=2c919dc4-24de-474f-8da0-14c7e1240ab8 /home           ext4    noatime,nodiratime,defaults        0       2

You will need to reboot your machine before these changes take effect

3) Minimising writes from the OS and applications

Assuming that you are not running a mission critical product server, most people do not look at logs should something go wrong (especially as serious errors are rare for most Ubuntu users). Therefore you can configure Ubuntu so all logs get written to RAM memory rather than the SSD.

Note: only make the following changes when you have installed all software you are going to use (especially things like Apache web server), otherwise you may experience some issues with missing directories in /var/log

For background to this approach, see prolonging the life of your flash drive on ubuntu-eee.com

Open /etc/fstab with an editor (assuming you have backed up the /etc/fstab file)

gksudo gedit /etc/fstab

Add the following lines at the end of the fstab file and save:

# Uncomment these after all server based applications installed - eg. apache
#tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
#tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0
#tmpfs /var/log tmpfs defaults,noatime,mode=0755 0 0 
#tmpfs /var/log/apt tmpfs defaults,noatime 0 0
# none /var/cache unionfs dirs=/tmp:/var/cache=ro 0 0

You will need to reboot your machine before these changes take effect

---

### Post by oldfred on 2019-07-12
I have the 840 Pro as sda & HDD as sdb.
```
fred@bionic-z97:~$ sudo hdparm -i /dev/sda | grep FwRev
[sudo] password for fred: 
 Model=Samsung SSD 840 PRO Series, FwRev=DXM06B0Q, SerialNo=S1ANNSAF511092D

```

You just need noatime and then should not use nodiratime.

I usually turn off the standard Ubuntu version and add my own trim script to weekly cron.

       [http://arstechnica.com/gadgets/2015/04/27/ask-ars-my-ssd-does-garbage-collection-so-i-dont-need-trim-right/](http://arstechnica.com/gadgets/2015/04/27/ask-ars-my-ssd-does-garbage-collection-so-i-dont-need-trim-right/)
Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
Similar to what I do, except I do use ext4 , I use a daily cron task for TRIM, 
and I have Firefox on hard drive so no issues with cache. Swap is also on hard drive, but never used.
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)
[https://easylinuxtipsproject.blogspot.com/p/ssd.html](https://easylinuxtipsproject.blogspot.com/p/ssd.html)

```
fred@bionic-z97:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=8c92557f-cc60-438b-b1ea-ffea0adf0a1a /    ext4    noatime,errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=FD76-E33D  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda4 during installation
#UUID=3af6a910-59f8-4719-b58c-2e7484d435f0 none            swap    sw              0       0
# swap was on /dev/sdb7 during installation
UUID=a7750d57-5381-421b-82fa-b53194ab45c2 none            swap    sw              0       0
# Entry for /dev/sdb4 on Asus AR:
UUID=a0c1c99f-0f09-4787-a7cc-9e15bb3b4aa5 /mnt/data ext4 relatime,nofail,x-systemd.device-timeout=4 0 2
UUID=F626-A4D4  /boot/efi       vfat    defaults      0       1
# Reduce SSD wear
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
#UUID=49B1-4B33    /boot/efi    vfat    defaults    0    1
```

---

### Post by Dennis N on 2019-07-12
Yes, the /etc/fstab entries use noatime with SSD:
The SSD is Samsung 860
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/os_vg-ubuntu /               ext4    errors=remount-ro,noatime 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=968A-13F1  /boot/efi       vfat    defaults      0       1
/swapfile                                 none            swap    sw              0       0

```
And yes, it supports trim. 
Check trim status with:
```
dmn@Tyana:~$ systemctl status fstrim.timer
&#9679; fstrim.timer - Discard unused blocks once a week
   Loaded: loaded (/lib/systemd/system/fstrim.timer; enabled; vendor preset: enabled)
   Active: active (waiting) since Fri 2019-07-12 12:42:36 MST; 39min ago
  Trigger: Mon 2019-07-15 00:00:00 MST; 2 days left
     Docs: man:fstrim

```Timer triggers fsck at 00:00 every Monday, or it occurs first login after that time, then resets to next Monday. You can check if its working from examining journalctl:

```
dmn@Tyana:~$ journalctl | grep fstrim | grep Jul
Jul 01 12:33:47 Tyana fstrim[1217]: /: 5.9 GiB (6330462208 bytes) trimmed
Jul 08 00:20:42 Tyana fstrim[1237]: /: 6 GiB (6420729856 bytes) trimmed

```

---

### Post by him610 on 2019-07-12
Been using Samsung 840 SSD devices on two systems for 6+ years. No indication of any issues.
```

$ journalctl | grep fstrim | grep Jul
Jul 01 00:00:16 G4560 fstrim[9092]: /: 217.1 GiB (233092362240 bytes) trimmed
Jul 08 00:00:16 G4560 fstrim[29318]: /: 216.8 GiB (232816422912 bytes) trimmed

```

---

### Post by bunny9000 on 2019-07-14
> **Shibblet said:**
> Alright... let's get down and dirty here...

I had a friend tell me that my Samsung 840 EVO Drive will only work "properly" in Windows, because the Samsung Magician Software is the only thing that will run Trim.

I would assume that Ubuntu supports Trim by default by now...  Alas, many a Google search has not found the proper answers I am looking for.

How does Linux handle SSD's, compared to Windows?  I always thought the EXT4 File System was far superior to NTFS.

Your friend is right - at least he was.

[https://www.reddit.com/r/linux/comments/3a5zgq/dont_use_linux_on_samsung_ssds_xpost_rbuildapc/](https://www.reddit.com/r/linux/comments/3a5zgq/dont_use_linux_on_samsung_ssds_xpost_rbuildapc/)

There used to be a bug in the kernel that could potentially erase data when trim was run.

There is no obvious further comment, but a patch was released.

There have been similar threads:

[https://ubuntuforums.org/showthread.php?t=2328351](https://ubuntuforums.org/showthread.php?t=2328351)

I can't find a high enough ranked document that actually says it's fixed, but I would make a safe assumption that in the 4 years since it would have been fixed.

And yes this bug did only affect the samsung and crucial SSDs at the time.

Your SSDs may still slow down if you run it to 100% capacity since it needs some space to be able to run garbage collection / Trim (excuse if I intermixed those words I'm not an expert)

---

### Post by sevendogs1337 on 2019-07-14
I have been using Samsung 850 EVO's and Pros on FreeBSD and Linux for well over 3 years with zero data loss or issues. I let systemd run its trim routine or just do it manually myself since my machine doesn't stay on.

No hesitation running an SSD on Linux or any other OS for that matter.

---

