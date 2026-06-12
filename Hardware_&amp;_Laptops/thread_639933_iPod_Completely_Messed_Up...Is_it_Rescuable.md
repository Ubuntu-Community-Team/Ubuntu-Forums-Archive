---
title: "iPod Completely Messed Up...Is it Rescuable?"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by parm289 on 2007-12-13
Hello,

In the process of trying to install ipodlinux on my 4gb ipod mini (2g i believe), i managed to completely wipe the drive clean and create one single ext3 partition on the disk - don't ask how.  Anyway, I reformatted the drive to fat32 using gparted in hopes of using the windows restore program to restore the original firmware.  However, windows no longer detects my ipod, and is unable to restore it.

I am now stuck with a useless ipod, and am having difficulties installing ipodlinux on it.  When I run the ipodlinux installer, i get an error message that I'm missing libcrypt.so.9.9.7.  So, is there any way to restore my ipod, considering that I am unable to install ipodlinux, windows doesn't recognize the device, and the linux IPL installer doesn't work?

Thanks for any help.

---

### Post by 1337455 10534 on 2007-12-13
Will your Linux detect your iPod? If so, try getting Rockbox on there.
The installer might require Wine.

A smarter option is to format, and reset it back to the original FS. Then see if it will be detected on Windows.

Best, but least likely to do anything, ask Apple for help.

---

### Post by 1337455 10534 on 2007-12-13
Try the iPodLinux installer again after running this in the terminal;

```

sudo apt-get install libcrypt.so.9.9.7

```

---

### Post by odbod on 2007-12-13
You really didn't need to wipe your whole ipod clean. You could of been able to dual boot linux and the original firmware easy.

---

### Post by fearnothing on 2007-12-13
In Windows, check in device manager for the iPod, it might appear just as a USB mass storage device. If it's not there then your iPod is beyond the abilities of Apple tech support (I work for them! :P) - but that's not to say it's completely irretrievable. Some unofficial methods may work but I can't guarantee that.

If it does appear in device manager, right click and uninstall it, disconnect the iPod, then reboot. Boot back in to Windows again, and hopefully the drive will appear in windows, format it as a FAT32 drive if so and then restore.

Oh, add to that you could try resetting it before doing either of those, it could be that the firmware is messed up and a reset could help there.

---

### Post by parm289 on 2007-12-13
Thanks for the replies, but nothing seems to work.

> Will your Linux detect your iPod? If so, try getting Rockbox on there.
The installer might require Wine.

A smarter option is to format, and reset it back to the original FS. Then see if it will be detected on Windows.

After trying several online methods to rcover my ipod (namely [http://youripodhub.blogspot.com/2007/10/repair-your-ipod-mini-using-linux.html](http://youripodhub.blogspot.com/2007/10/repair-your-ipod-mini-using-linux.html)), Gutsy detects that an Apple iPod is connected, but can't read from or mount the device, so Rockbox is not an option.  I had tried Rockbox before and liked it very much, but I actually wanted to tri-boot my ipod.

> Try the iPodLinux installer again after running this in the terminal;

Code:

sudo apt-get install libcrypt.so.9.9.7



This came back with the error:
```
E: Couldn't find package libcrypt.so.9.9.7
```
Plus, I installed all versions of libcrypt present in Synaptic, bu the installer still wouldn't work.

> 
If it does appear in device manager, right click and uninstall it, disconnect the iPod, then reboot. Boot back in to Windows again, and hopefully the drive will appear in windows, format it as a FAT32 drive if so and then restore.

This was actually the first thing I tried, but Windows simply wouldn't recognize the ipod.  I even tried reinstaling the ipod software that came with it, but still no luck. Now, Windows won't even detect my ipod.


Now, since Ubuntu won't read it, I think my ipod has become a paperweight...

---

### Post by 1337455 10534 on 2007-12-13
[http://downloads.sourceforge.net/mingwrep/libcrypt-2.17-20010126.zip?modtime=980463600&big_mirror=0](http://downloads.sourceforge.net/mingwrep/libcrypt-2.17-20010126.zip?modtime=980463600&big_mirror=0)
?

You might need to compile it (cd (the download directory), ./configure, make, sudo make install).
I didn'y find a configure file in there, but who knows... im on XP right now anyway.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libcrypt&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libcrypt&searchon=names&subword=1&version=gutsy&release=all)
: probably better... good luck...

---

