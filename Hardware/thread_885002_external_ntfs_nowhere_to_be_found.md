---
title: "external ntfs nowhere to be found"
date: 2008-08-09
forum: Hardware
---

### Post by crisarn on 2008-08-09
I've been stumped on this for a while, I have a ntfs external hard drive that I cannot find any trace of in ubuntu 8.04.  When i boot xp the drive appears in my computer just fine, but in ubuntu i cannot find it anywhere as if it is not detected.  I do have ntfs-3g installed as well as ntfs-config.  I need some help, I am new to linux so please be kind.

thanks in advance

---

### Post by crisarn on 2008-08-09
I ran fdisk -l and this is what i got

arnett@arnett-laptop:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10314    82847173+   7  HPFS/NTFS
/dev/sda2           10315       10436      979965   82  Linux swap / Solaris
/dev/sda3           10437       12161    13856062+  83  Linux
arnett@arnett-laptop:~$ 

the drive is not listed, what gives?

---

### Post by ThaRabbit on 2008-08-09
Hm, that seems weird. 

Please boot your system into Ubuntu with the external drive connected and powered up.

Then go to a terminal and do:
```
dmesg
```

Then please post the complete output of that command here:
[http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/)

and post the link from your address bar when it's done. 

Alternatively you could do:
```
dmesg > ~/dmesgoutput
```

This will create a file called "dmesgoutput" in your home folder, you can attach that file to your post.

---

### Post by crisarn on 2008-08-10
I thought it was strange too, thanks for the help.  here is the output form dmesg

[http://pastebin.ubuntu.com/36227/](http://pastebin.ubuntu.com/36227/)

---

### Post by ThaRabbit on 2008-08-10
> **crisarn said:**
> I thought it was strange too, thanks for the help.  here is the output form dmesg

[http://pastebin.ubuntu.com/36227/](http://pastebin.ubuntu.com/36227/)

You seem to be suffering a known problem:
[http://ubuntuforums.org/showthread.php?t=797789](http://ubuntuforums.org/showthread.php?t=797789)

And mainly this post in that topic for the suggested solution:
[http://ubuntuforums.org/showpost.php?p=5319512&postcount=3](http://ubuntuforums.org/showpost.php?p=5319512&postcount=3)

I am basing myself on these lines from your DMESG:
```
[   11.877229] usb 5-1: device descriptor read/64, error -71
[   11.931072] usb 5-1: device descriptor read/64, error -71

```

Now as we can see from the usb-dev mailing list archives ([http://kerneltrap.org/mailarchive/linux-kernel/2007/6/19/106270](http://kerneltrap.org/mailarchive/linux-kernel/2007/6/19/106270)), they suggest it's related to "CONFIG_USB_SUSPEND" and suggest to disable this. The consequence would be higher power use ([http://kerneltrap.org/mailarchive/linux-kernel/2007/6/19/106295](http://kerneltrap.org/mailarchive/linux-kernel/2007/6/19/106295)) as your USB devices will no longer be suspended

Please refer to the topic linked to by the first 2 links I provided and let us know if it helped you :)

---

