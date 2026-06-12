---
title: "noob requires help mounting iriver h10."
date: 2006-05-08
forum: Hardware &amp; Laptops
---

### Post by randomusername on 2006-05-08
Hi folks,

I've just got my hands on an iriver h10, and I'm having issues.

It should mount as a standard USB mass storage device.  Ubuntu appears
quite happy to automagically mount any other USB mass storage device
that I connect to it, but no luck with this one.

dmesg shows :
```
[4294857.532000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[4294857.645000] usb 1-2: device descriptor read/64, error -71
[4294857.859000] usb 1-2: device descriptor read/64, error -71
[4294858.062000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[4294858.175000] usb 1-2: device descriptor read/64, error -71
[4294858.389000] usb 1-2: device descriptor read/64, error -71
[4294858.592000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[4294859.000000] usb 1-2: device not accepting address 4, error -71
[4294859.102000] usb 1-2: new full speed USB device using uhci_hcd and address 5
[4294859.510000] usb 1-2: device not accepting address 5, error -71
```

And thats all I get from it. Nothing mounted, no new sda devices in /dev.

Any ideas as to what my issue could be here?

---

### Post by DeadEyes on 2006-05-09
I have an MTP version according to iRiver Linux is not supported.

Nevertheless

This is off the top of my head as I'm not at home, but I'll add corrections later.

Make sure you have the latest firmware, there is a windows updater which makes this painless (read iRiver manual for instructions)

```

#mkdir /media/H10

```

add an entry **like** (again note it's off the top of my head) the following to your /etc/fstab

```

/dev/sda1   /media/H10  vfat    noauto,user,rw  0   0

```

Remove the battery from your iRiver and put it back in.
Connect iRiver to usb. 
Keep holding down O button and on button until "emgenercy boot" meesage disappears.
```

$mount /media/H10

```
now install a program called easyh10 I think there is a package in the repos.

look for a .model file installed with easyh10 that matches your player.
copy it to /media/H10 and rename it easyh10.model

copy your mp3s to /media/H10/Music folder, it might be different depending on the version of your player

now use easyh10 to update your players database (see man for proper usage)
```

easyh10 -U -on /media/H10

```

umount your drive this may take some time.
```

$umount /media/H10

```

if you get an error message close down current konsole and open up a new one to try again

Thats more or less how I use mine, I hope this gets you up and running too.

---

### Post by randomusername on 2006-05-10
Thanks for the reply.

I've already updated to the latest firmware and kicked the
device into UMS mode.  It's a H10 20GB, so it does not have
a removable battery.

Mount points and fstab entries have been created, the problem
is it just wont mount.  As shown from the dmesg output below, 
the PC appears to detect a USB device when I connect the H10,
but is unable to talk to it. :-k

---

### Post by pcormack on 2006-05-10
try 

sudo mount -a

then try access the USB device

---

### Post by randomusername on 2006-05-11
[QUOTE=pcormack]try 

sudo mount -a

then try access the USB device[/QUOTE]

Thanks, but that does not work.

The issue still appears to be that the device is not recognised - 
for some reson ubuntu can't tell what my H10 actually is, and as
such there is nothing to mount.

I need to be able to get the H10 recognised as a UMS device before I
can do anything with it - such as mounting it.

This is frustrating, as it is really the only thing holding me to windows
at the moment. :(

---

### Post by pcormack on 2006-05-11
i have a standard mount to my iRiver H320 and it works just fine, the some mount point looks after my USB memory stick also

> 
/dev/sda1 /media/usb1 auto user,atime,auto,rw,dev,exec,suid 0 0


---

### Post by DeadEyes on 2006-05-15
try searching [http://www.misticriver.net/forums.php](http://www.misticriver.net/forums.php)

---

### Post by randomusername on 2006-05-16
Problem solved.

It was a hardware issue - a problem with the contacts on the usb 
cable.  

If you press it in on just the right angle, it is detected as a ums device
and automounted with no problems.  Stop pressing it in, and you get the
problem stated in my original post.

Just seems odd that it works fine under XP without having to do this.

In any case, thanks go to **DeadEyes** & **pcormack** for their
suggestions.

- random

---

### Post by Eman64 on 2006-11-29
Done all of this and when I update, I get this
```
human@Ubuntu:~$ easyh10 -U /media/H10
EasyH10 [CUI] 1.5  Copyright (c) 2005-2006 by Nyaochi

H10 model template: /media/H10/easyh10.model
Path to database: /media/H10/System\DATA/
Path to music: /media/H10/Music/

Enumerating music files:
  834 files found.                                                            

Reading H10 model template:
  H10 (MTP2) 20GB firmware 2.51 - 2.51

Reading H10 media database
Failed to read the H10 database (code = 3).
ERROR: Database update.

```
This always happens](*,)

UPDATE:
Fixed it, no need to worry

---

