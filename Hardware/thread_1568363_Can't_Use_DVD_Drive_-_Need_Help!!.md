---
title: "Can't Use DVD Drive - Need Help!!"
date: 2010-09-05
forum: Hardware
---

### Post by Chris.Whitley on 2010-09-05
***********************FIXED******************


I have an HP Pavilion dv2000 that was given to me.  Seeing as how I will only be using it for interent/school, I decided to install Ubuntu Netbook Remix 10.04.

Everything is working amazingly except that no matter what I put in the DVD drive, it will not mount.  I've tried CD's and DVD's both of varying types (movies, music, burnt, games, etc.)  When I insert a CD or DVD, it will spin for a few seconds, then nothing.

The DVD drive according to Disk Utility is MATSHITA DVD-RAM UJ-851S

If I check the system monitor, it say the only files system is /dev/sda1 which is the HDD.  

I've tried the following commands in terminal and here are the results that follow
> 
dart@dart-netbook-remix:~$ sudo mount /dev/scd0 /cdrom
mount: /dev/sr0: unknown device
> 
dart@dart-netbook-remix:~$ sudo mount /dev/scd0 /cdrom -t udf
mount: no medium found on /dev/sr0
> 
dart@dart-netbook-remix:~$ sudo mount /dev/sr0 /cdrom
mount: /dev/sr0: unknown device
> 
dart@dart-netbook-remix:~$ sudo mount /dev/sr0 /cdrom -t udf
mount: no medium found on /dev/sr0
> 
dart@dart-netbook-remix:~$ sudo ls /dev -l | grep cd
lrwxrwxrwx  1 root root           3 2010-09-04 10:38 cdrom -> sr0
lrwxrwxrwx  1 root root           3 2010-09-04 10:38 cdrw -> sr0
drwxr-xr-x  2 root root          60 2010-09-04 10:38 pktcdvd
lrwxrwxrwx  1 root root           3 2010-09-04 10:38 scd0 -> sr0
crw-rw----  1 root cdrom    21,   0 2010-09-04 10:38 sg0
brw-rw----+ 1 root cdrom    11,   0 2010-09-04 10:38 sr0
> 
dart@dart-netbook-remix:~$ sudo ls /dev -l | grep dvd
lrwxrwxrwx  1 root root           3 2010-09-04 10:38 dvd -> sr0
lrwxrwxrwx  1 root root           3 2010-09-04 10:38 dvdrw -> sr0
drwxr-xr-x  2 root root          60 2010-09-04 10:38 pktcdvd
looking at /etc/fstab I get the following
> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=284baad6-cbb2-4daa-83b7-0496893bcf06 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=459268e2-23c9-4902-a4da-76ebaaa7bf50 none            swap    sw              0       0
I'm really at a loss here and would greatly appreciate any help.
Thanks in advance

---

### Post by Chris.Whitley on 2010-09-05
Wow got pushed to third page overnight, bumping thread.

anyone?

---

### Post by Chris.Whitley on 2010-09-05
OK so update on this

Since it would not let me mount the drive for some reason, I decided to just play around and unmount it.  I did "sudo umount /dev/sr0" and it seemed to unmount.  I then did the following and got the following result

> 
dart@dart-netbook-remix:~$ sudo mount /dev/sr0 /cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only


When i check the "/cdrom" folder, it is successful. The files are there and it's mounted.  So now the problem I'm having is this.  As stated above, when it mounts it mounts as read-only.  I presume that this was normal since the DVD i inserted is a game disc.  I'm trying to install the game using WINE.  The install file is a .exe and Ubuntu will not let me run it.  Normally I could just right-click > Properties > Permissions and select the "Allow executing file as program" and that would bypass the check and let it run. It's not letting me do that, the option is grayed out, and I'm assuming it's because it's mounted as read-only and apparently I don't have the permissions to do it.

Is there anyway to fix this problem?

Thanks in advance

---

### Post by garvinrick4 on 2010-09-05
I understand remix and desktop are exactly the same Operating System with 2 different
GUI's. So if you installed the ubuntu-desktop and had the choice of which one to use at log-in? The netbook package is specifically made for small screens same /. 
So is it the Optical drives hardware problem or the software, same software?
I have netbook installed and it is cool to run around the internet with and do minor operations, I like it. Nice to have Desktop option and uses same packages already installed.
 Doe's it eject:
```
sudo eject /dev/sr0
```

---

### Post by Chris.Whitley on 2010-09-05
I've used the desktop (gnome) enviorment for a while on my desktop.  Even though the laptop isn't a "netbook" I really like the GUI offered in Netbook Remix for a laptop setup.  The interface seems to feel increably "right" (if you know what i mean :D)

 I tried the eject command form the Disk Utility screen and it wouldn't work, thoughI'm not sure why it happened now but I did the "sudo eject /dev/sr0" and it ejected.  I closed the tray back and it's actually auto mounting it now.  I've restarted the laptop a few times to test it and it seems to be working.  Not sure why that fixed it but it did

Thanks for that suggestion.  I'll keep testing it out with various disc types to make sure it stays fixed.

---

### Post by garvinrick4 on 2010-09-05
Mark as solved please.

Remix is enjoyable to cruise around internet, like huge phone.

---

