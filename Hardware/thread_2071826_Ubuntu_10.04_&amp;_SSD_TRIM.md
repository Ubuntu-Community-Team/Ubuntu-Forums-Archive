---
title: "Ubuntu 10.04 &amp; SSD TRIM"
date: 2012-10-16
forum: Hardware
---

### Post by mrapoc on 2012-10-16
A customer of ours asked if his current 10.04 ubuntu setup (which uses an SSD) should be getting slower and slower. I asked how much slower it was and he replied - "A lot".

So being primarily a Windows user I started researching about TRIM support in Ubuntu. There doesn't seem to be a clean cut answer but some people saying the solution is to upgrade. 

He's a "if it ain't broke" kinda guy so what solutions do we have? 

Cheers

---

### Post by oldfred on 2012-10-16
HOWTO: Check If TRIM On Ext4 Is Enabled And Working On Ubuntu And Other Distributions
[http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking)

Good site on details:
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

These are some of the settings it should have:

 trim does need ahci in BIOS

You still need discard for trim and noatime to reduce writes. You can also use ext4 but turn journal off. I think that was about all I actually did. If using any newer version of gparted you should have alignment or first partition starts at sector 2048 and all partition starts are divisible by 8.

How to Tweak Your SSD in Ubuntu for Better Performance
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)
See comment: There’s no reason to use BOTH noatime and nodiratime, using noatime implies nodiratime.
[http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux](http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux)
Discussion of swap on SSD - best not to)
[http://ubuntuforums.org/showthread.php?t=1937251](http://ubuntuforums.org/showthread.php?t=1937251)

With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode.
change to noop i/o scheduler

I did not change my fstab when first installed so I ran this:
[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
sudo hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

---

### Post by pqwoerituytrueiwoq on 2012-10-16
upgrade the kernel to the maverick backport (search in synaptic) [the default kernel in 10.04 does not support trim]
* going higher than maverick will break virtualbox
add discard in fstab (and noatime if it is ext4)
enable ahci (instead of ide) in bios (if dual booting you will need to reinstall windows)
*XP is not ahci frendly

---

