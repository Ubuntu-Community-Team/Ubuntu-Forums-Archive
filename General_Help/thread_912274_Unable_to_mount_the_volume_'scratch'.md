---
title: "Unable to mount the volume 'scratch'"
date: 2008-09-06
forum: General Help
---

### Post by MacDuff on 2008-09-06
I am using:
Ubuntu 8.04
A USB adapter to connect a hard drive to a USB port  
A hard drive that was taken from a Windows XP system formatted NTFS

When I connect the drive nothing appears on the desktop but I can use "Places" or "Computer" and see that the system has named it "Scratch" and displays the USB icon,  but when I try to mount it I get the error message: "Cannot Mount Volume. Unable to mount the Volume 'Scratch'. Mount point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

Where and what settings must I change to mount this USB drive.

---

### Post by cariboo on 2008-09-06
Try and mount the disk manually:

```
sudo mount /dev/sdxx /mnt
```

Where /dev/sdxx is your external hard drive. To find what device it is in a terminal:

```
sudo fdisk -l
```

Jim

---

### Post by MacDuff on 2008-09-06
Jim:  I tried that but it does not seem to show the device (sudo fdisk -l)

Here is the output:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa538e5a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Still not being very knowledgeable about Linux and just for the heck of it I tried to mount the /dev/sda5 and got this message which, to me tells me it is just my on-board hard drive swap space.

/dev/sda5 looks like swapspace - not mounted
mount: you must specify the filesystem type

Any more suggestions?
Thanks
Mac

PS I just had a look at the "Places" after plugging in the USB drive and "Scratch" has disappeared.  When I look at "Computer" I see a "USB drive" there but no mention of "Scratch'

Don't know if this is relevant

---

### Post by MacDuff on 2008-09-06
Tried the drive on a desktop Ubuntu system and it mounted immediately. 
Turns out is is formatted with Linux.  It had one directory on it: "Lost+Found"
I could not do anything with the disk because I did not have permission but as Sudo I could add a directory to it.

This is the result of an fdisk -l command
mac@comm:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e5b92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23612   189663358+  83  Linux
/dev/sda2           23613       24321     5695042+   5  Extended
/dev/sda5           23613       24321     5695011   82  Linux swap / Solaris

<USB Drive is correctly identified below>

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc2dcc2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9964    80035798+  83  Linux

After adding a directory to it, I un-mounted it and tried it again on my laptop but it still would not mount.

It appears that wherever my laptop is trying to mount the drive is not correct.  How can I find where that is?

---

### Post by mc4man on 2008-09-06
This probably won't help but...
**Sometimes** the > Mount point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /) error can be solved this way

From terminal   ```
gconf-editor
```
When there navigate to system -> storage -> drives and or volumes  and see if the drive is listed there
If so the mount point key can **only** contain the volume label, not a typical mount point.
See screen for an **incorrect** key, trying to mount this volume will produce above error, editing back to just the drive label will allow mounting (ie. TEST_3

Edit: also are you sure the setup your using can properly power the drive?

---

### Post by MacDuff on 2008-09-06
Had a look a the Configuration Editor and under "Storage" > volumes there is only one item "_org_freedesktop_Hal_device...." it goes on and on but no mention of the USB Device.

Yes on the power.  The drive has a power supply plugged into it.  As mentioned, it auto-mounts on a desktop machine but not on the laptop.

I just tried another "fdisk -l" on the laptop and now it shows the drive, but I still cannot mount it

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc2dcc2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9964    80035798+  83  Linux
mac@T-61:~$ 

Anymore suggestions... please and thank you.

---

### Post by MacDuff on 2008-09-06
Solved the problem of the drive not mounting by setting a new volume label and formatting the drive to ext3 file system.

It now auto-mounts and is identified as 82.0 GBMedia but I cannot do anything with it because I do not have permission.

Questions:
How do I assign a volume label to it so it is the same name on every computer to which it is attached?

How do I set permissions so it can auto-mount on all my computers without having to create an fstab entry?

---

### Post by mc4man on 2008-09-06
Unmount the drive but leave connected
run in order (change red to match drive and user name, desired volume name (no spaces, use _ for 2 or words

```
sudo mkdir /media/fix

sudo mount /dev/[COLOR="Red"]sdb1[/COLOR] /media/fix

sudo chown [COLOR="Red"]doug:doug[/COLOR] /media/fix

sudo umount /dev/[COLOR="Red"]sdb1[/COLOR] /media/fix

sudo rmdir /media/fix

sudo e2label /dev/[COLOR="Red"]sdb1[/COLOR] [COLOR="Red"]STORAGE[/COLOR]
```

will give write permissions to the set user name on any linux system (only to set user name though, ie. if you use the same user name on multiple systems your good


edit; maybe there's a way to give rw to all users on any system, would love to know (if there isn't that may be one advantage of fat32 or ntfs over ext2/3 on usb drives

---

### Post by MacDuff on 2008-09-06
Thanks mc4man

I was just wondering if I should format the drive as an NTFS drive when I discovered your message. I will give your method a try before I do anything else.

I did discover how to create volume labels so I should now be good to fix everything that was bugging me.

Thanks again

---

### Post by MacDuff on 2008-09-07
I tried the suggestions offered by mc4man.  They could not be stated more clearly yet they did not work.  When I got to step 4 (umount) I got the message that the drive was not mounted.  I re-tried several times and in checking the directory confirmed that the drive was not mounting.

Finally I gave up and formatted the drive to fat32, quickly changed the volume label using Windows commands and everything works just fine. 

While I am enjoying most of Ubuntu and would not change back to Windows, things like this problem make me wonder, when Linux is so very good at most things, why can it not be at least as easy to use as Windows accomplish this sort of task? 

If you are still tuned in mc4man, thanks for the suggestions.  I had hoped to learn something new but had to fall back on MS, cough, choke.

---

### Post by mc4man on 2008-09-07
I maybe should of mentioned
Ex.

> 
doug@doug-desktop:~$ sudo mount /dev/sdb8 /media/fix
doug@doug-desktop:~$ sudo umount /dev/sdb8 /media/fix
umount: /dev/sdb8: not mounted
umount: /dev/sdb8: not mounted

It never tells you it has been unmounted -  it's a little ambiguous, it's basically saying the drive is no longer mounted, ie. 'not mounted' 

after chowning you mount by either unplugging and replugging in the drive (automount) or by going to places - removable media and just clicking on it. A command like will not work
> doug@doug-desktop:~$ sudo mount /dev/sdb8 
mount: can't find /dev/sdb8 in /etc/fstab or /etc/mtab


The fat32 is perfectly fine for usb and you don't have to worry about 'ownership'


edit : and why it repeats the not mounted is also 'weird'

---

### Post by MacDuff on 2008-09-07
I hear and understand but it did not work anyway.  Thanks for the explanation of the message telling me that the drive was not mounted.  That did perplex me but I went through the entire list and still did not have a drive with which I could work.

I wish this was the first time that something like this has happened.  Unfortunately it is only the most recent of several (many?).  I think Ubuntu and I have not yet established a genuine rapport.  Either that or my hands move before they receive instructions from my conscious brain.  

Seriously, I think that is a problem for we who have spent decades working with MS products, dating back to MS-DOS.  Our hands have been conditioned to work without thinking and it bites us when we move to a slightly different way of doing things.  It is not JUST our hands but the thought pattern is also different  :-?

---

