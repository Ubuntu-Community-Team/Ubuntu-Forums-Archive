---
title: "USB MemStick does not automount"
date: 2005-07-25
forum: Hardware &amp; Laptops
---

### Post by vgeddes on 2005-07-25
My Memory Stick does not automount. Yet is is detected and listed as ```
/dev/sdb1
```. 

I have to manually type ```
pmount /dev/sdb1 usbdisk
``` whenever I want to access it, which is not a really happy state of affairs.

Editing the options in the gnome *Removable Drives & Media* configuration does not solve the problem either

I need help please!

Ubuntu Hoary
kernel: 2.6.11-1-amd64-k8

Vincent Geddes

---

### Post by mr_bean on 2005-07-25
Add it to fstab??

---

### Post by majikstreet on 2005-07-25
This is my 'howto' that I wrote on another forum about mounting a flash drive:
Edit your /etc/fstab and add this at the bottom:
```

/dev/sda1  /mnt/usb  vfat  defaults,rw,noauto,users,sync  0 0

```
Then what you want to do is type:
```

mkdir /mnt/usb

```

Now when you want to use it, plug it in then type:
```

mount /mnt/usb

```
Then before you unplug it type:
```

umount /mnt/usb

```

And yes, it is really "umount" _not_ unmount!
Edit your /etc/fstab and add this at the bottom:
```

/dev/sda1  /mnt/usb  vfat  defaults,rw,noauto,users,sync  0 0

```
Then what you want to do is type:
```

mkdir /mnt/usb

```

Now when you want to use it, plug it in then type:
```

mount /mnt/usb

```
Then before you unplug it type:
```

umount /mnt/usb

```

And yes, it is really "umount" _not_ unmount!


But if you don't can't get sda1 to work, try using sda or sdaX replacing X with a number.

I put two scripts on my desktop to mount and unmount the drive:
mount:
```

#!/bin/bash
mount /mnt/usb

```
unmount:
```

#!/bin/bash
umount /mnt/usb

```




Now,
I imagine when you edit your fstab, you can replace noauto with auto and it should automount.

majikstreet

---

### Post by dmallery on 2005-07-27
the problem here is that it worked as late as last week.

then there must have been something in apt-get that broke it.  i have one updated machine that does not work and one un-updated that still does.

for the life of me, i can't figure out how the working system actually automounts.  but it works and spawns gthumb for pix.  it also works with usb jump drives.

could someone please post some clues as to how the automount shipped with ubuntu actually works???

many thanks in advance

dave mallery

---

### Post by varunus on 2005-07-27
Ubuntu uses the Gnome Volume Manager to automatically mount and unmount drives.  One way to debug it on the non-working computer:

Open up a terminal
Type "killall gnome-volume-manager" and press enter
Type "gnome-volume-manager" and press enter (notice, no '&' at the end of that)
Plug in your usb drive

Any errors will be outputted to the terminal.  Post them here; I've found that the pmount command (which gnome-volume-manager uses) can sometimes get messed up.

You could also try a reboot, some apt-get updates can mess up HAL and DBUS and need you to restart them.

---

### Post by dmallery on 2005-07-27
BRAVO!!

gnome-volume-manager was NOT running. (reason unknown).

starting it fixed the problem.  i guess a reboot would have worked...

many thanks!

now i have something to research and understand.

dave

---

### Post by Ken.Lank on 2005-07-27
[QUOTE=varunus]
Any errors will be outputted to the terminal. Post them here; I've found that the pmount command (which gnome-volume-manager uses) can sometimes get messed up.
[/QUOTE]
I'm having the same issue, so I figured I'd post up my results ...
```
manager.c/925: New Device: /org/freedesktop/Hal/devices/usb_device_5ac_1300_1001_-1_000A2700100F32C7
manager.c/925: New Device: /org/freedesktop/Hal/devices/usb_usb_device_5ac_1300_1001_-1_000A2700100F32C7_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/scsi_host_3
manager.c/925: New Device: /org/freedesktop/Hal/devices/scsi_3_0_0_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/block_8_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/block_3C06-885A
manager.c/961: Changed: /dev/sda1
manager.c/904: Added: /dev/sda1
Error: could not execute pmount

```

---

### Post by majikstreet on 2005-07-27
[QUOTE=Ken.Lank]I'm having the same issue, so I figured I'd post up my results ...
```
manager.c/925: New Device: /org/freedesktop/Hal/devices/usb_device_5ac_1300_1001_-1_000A2700100F32C7
manager.c/925: New Device: /org/freedesktop/Hal/devices/usb_usb_device_5ac_1300_1001_-1_000A2700100F32C7_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/scsi_host_3
manager.c/925: New Device: /org/freedesktop/Hal/devices/scsi_3_0_0_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/block_8_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/block_3C06-885A
manager.c/961: Changed: /dev/sda1
manager.c/904: Added: /dev/sda1
Error: could not execute pmount

```[/QUOTE]
 Reboot?

---

### Post by varunus on 2005-07-27
Can you type the following:

ls -l /usr/bin/pmount*

And post the output here?

Also, go to System->Administration->Users and Groups, click on your user(s), click properties, go to user priviledges, and make sure "use removable media automatically" is checked.

---

### Post by twowheeler on 2005-07-31
Sorry to jump in on majikstreet's thread, but I have this issue too.  Here is my answer:

```
dan@ubuntu:~$ ls -l /usr/bin/pmount*
-rwsr-xr--  1 root plugdev 23704 2005-04-04 12:38 /usr/bin/pmount
-rwxr-xr-x  1 root root    16120 2005-04-04 12:38 /usr/bin/pmount-hal
dan@ubuntu:~$

```

I notice that pmount is group plugdev, and there is no group plugdev.  The pmount man page says this:

```
       Important  note  for  Debian:  The  permission  to  execute  pmount  is
       restricted to members of the system group plugdev. Please add all desk&#8208;
       top users who shall be able to use pmount to this group by executing

              adduser user plugdev

       (as root).

```

I will try this and let you know.

Edit: forgot the other part.  There is  no such option in the 'User Privileges' menu.  See my screenshot [here](http://mywebpages.comcast.net/dhassell/GnomeScreenshot.png) .  What am I missing?

---

### Post by pjman on 2005-08-18
Hello All,

I'm having the same type of problem but my output is different.

```

manager.c/925: New Device: /org/freedesktop/Hal/devices/usb_device_5dc_a410_3000_-1_1069A704070136021104
manager.c/925: New Device: /org/freedesktop/Hal/devices/usb_usb_device_5dc_a410_3000_-1_1069A704070136021104_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/scsi_host_3
manager.c/925: New Device: /org/freedesktop/Hal/devices/scsi_3_0_0_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/block_8_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/block_8_1
manager.c/961: Changed: /dev/sda1
manager.c/904: Added: /dev/sda1
Error: invalid file system name ''

```

Any ideas?

Thanks,
pjman

---

### Post by pjman on 2005-08-23
[QUOTE=pjman]Hello All,

I'm having the same type of problem but my output is different.

Any ideas?

Thanks,
pjman[/QUOTE]
 I figured it out. I needed to add this line to my /etc/fstab

```

/dev/sda1       /mnt/sda1       vfat    rw,user,noauto,noatime

```
:-)

pjman

---

### Post by lundse on 2005-11-02
I had a similar problem, in Breezy 5.10, and seem to have fixed it.
Try running pmount from terminal, if you get "this program needs to be installed suid root." maybe you just have to reinstall pmount as i did.
I used synaptic, searched for pmount, marked it for reinstall, applied the changes and now its working just fine (no reason to think automount won't work now, either).

Lundse

---

### Post by Avionix on 2005-11-05
:confused: I had the same problem with my USB Memory stick, I re-installed HAL and now it automounts OK. Now my camera won't mount, I get a Mount Error, unable to mount the selected volume,
Details mount: special device /dev/sda does not exist.
It worked fine up until today, ie for the last week.
Any Clues ? I'm brand new to this so please keep it simple.

---

### Post by Ubangi on 2006-02-14
I get the same problems. I had seen about half a dozen different solutions suggested on the forum and I tried them all, including adding hal and all the users to plugdev group, rebooting, etc, etc.. None of them work, apart from the manual pmount (thank god for that!):

pmount /dev/sdb1 usbdisk

I keep getting complaints about failed mount: "volume probably?! in format that cannot be mounted", despite the fact that there is nothing wrong with it after the manual mount.

Hal worked just once after its inital installation. I tried a usb camera and that crashed the whole system. Now hal no longer works. I have no idea why or if it is connected with the camera problem.

I respectfully suggest that this is the kind of thing that gives linux the bad name with the Windoze community.

For example, why cannot the installation of hal include the necessary group permissions already? Why are we supposed to guess that and do it afterwards? (Even if it did work).

---

### Post by PhilOSparta on 2006-02-15
I have the same problem on my 64 bit desktop.
The SanDisk is formatted  FAT.

On my 32 bit laptop and desktop everything is okay.
The device automounts and displays on the desktop.  It can be accessed by the logged in user.  
Disks Manager shows Device: /dev/sda1
                             Access Path: /media/usbdisk
                             Status: Accessible

On my 64 Bit desktop Disks Manager shows Device: /dev/sde1
                                                        Accesspath: None
                                                       Status: Inaccessible

dmesg | tail provides:  VFS: Can't find an ext2 filesystem on dev sde.
pmount /dev/sde1 usbdisk  mounts the drive and displays it on the desktop but it only has root privledges.

Any additional ideas?  I have tried everything I can think of.

EDIT:  Found a solution for my situation.
Reinstalled the following packages using synaptic:
gnome-volume-manager
hal
hal-device-manager 
pmount
Rebooted the machine and the USB thumb drive showed up in Synaptic.
Case Complete!

---

