---
title: "Cannot unmount USB hard drive"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by Nickb-k on 2007-01-25
Hello,

I have a Freecom 120GB USB "Toughdrive" harddrive - usb powered, formatted to FAT32 using gparted.  I am running Xubuntu Edgy, with Fluxbox at home, but have the same problem on Ubuntu Breezy server at work.

I can mount the harddrive fine and read and write to it.  My fstab looks like:

```
/dev/sdb1    /media/nick_usb     auto rw,user,auto 0 2 
```

When I mount the device, using 

```
 mount /media/nick_usb 
```

It shows in mtab as ```
/dev/sdb1 /media/nick_usb vfat rw,noexec,nosuid,nodev,user=nick 0 0 
```

Which is all cool.  The problem is that when I unmount the drive, mtab thinks its unmounted but the drive is still spinning.  I have tried various commands including:

```
$ pumount /dev/sdb1/
```
```
$ umount /dev/sdb1
```
```
$ umount /media/nick_usb
```
```
$ pumount /media/nick_usb
```

As well as ```
eject /dev/sdb1
```  
```
eject /media/nick_usb
``` 
From looking in mtab, I can see that Xubuntu / Ubuntu thinks the drive is unmounted, but its still merrily spinning away.

Any ideas?  Thanks in advance.:KS 

Nick

---

### Post by antar on 2007-01-26
My Western Digital hard drive ALWAYS keeps spinning after I eject it, but when I unplug the USB, THEN it turns off.

Not sure if it's the best thing for the drive, but...

---

### Post by Nickb-k on 2007-01-26
No, I would think its a pretty bad thing to do for the drive.

I have also tried this:

```
$ hdparm -Y /dev/sdb1

/dev/sdb1:
 issuing sleep command
 HDIO_DRIVE_CMD(sleep) failed: Invalid argument
```

Which doesn't work either.

---

### Post by Nickb-k on 2007-01-30
I had almost accepted that there is no spin-down function for the harddrive in question.  But this is rediculous!  I have just noticed that when it is plugged into my MacBook and the Mac goes to sleep, the HD spins down.  I thought that this could just be becuase OSX turns off the  power to USB when it sleeps, but if I plug the Harddrive into the USB whilst OSX is asleep, the HD momenterily spins up.  So it seems that there *is* a way to spin it down - I just need to figure out what that method is.

Still hopeful

---

### Post by PARO on 2007-02-18
I had a similar question and found that > eject /dev/sde1 works for my usb device (rather than sdb, I navigated to dev to see where it'd pop up).  The unmount in XFCE seems to be doing the same thing as WinME used to, then when I'd use it in other OS's they would say "this device was not properly shut down" or something like that.  And likewise, the eject feature seems to work though. So maybe this might help someone.

---

### Post by nick_edwards on 2007-06-05
I have just bought a wwestern digital hard drive and seem to be haveing the same problem, under windows it spins down on stopping but if I eject under ubuntu it keeps spinning away, when I unplug it, it makes a desperate emergency spin down sound. I really don't want this drive to fail can anyone suggest something?

---

### Post by clem-vangelis on 2007-06-07
here is the solution : [http://ubuntuforums.org/showpost.php?p=2761781&postcount=15](http://ubuntuforums.org/showpost.php?p=2761781&postcount=15)

the complete thread is here : [http://ubuntuforums.org/showthread.php?t=451344&page=2](http://ubuntuforums.org/showthread.php?t=451344&page=2)

---

