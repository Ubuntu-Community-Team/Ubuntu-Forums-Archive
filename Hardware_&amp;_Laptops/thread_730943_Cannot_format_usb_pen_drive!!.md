---
title: "Cannot format usb pen drive!!"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by saz on 2008-03-21
Hi there!

i tried to install ubuntu on my pen drive but it failed, said it was read only, no problem, it wasn't a matter of great importance, so i just let it go and tried to format my pen to use it normally, but when i try to format it it always fails! i've tried with gparted on the installed ubuntu, on the ubuntu live cd and on the gparted live cd, i also tried with fdisk...

can someone help me?

here goes a video with the error, only 500k..

---

### Post by pieisgood4589 on 2008-03-21
If the drive is read-only you can't make changes to it, you can only see what's in it and "read" the drive... You can't edit anything. Change the administrative preferences for the drive, I don't know how to in Ubuntu but I do know how to in Windows XP...:(

Some help for this poor fellow would help...:lolflag:

---

### Post by |{urse on 2008-03-21
type 

mount 

to see where the pendrive is mounted

cd /wherever/mount/says/it/is

if that doesnt help 

mount /dev/sdb1 /some/mount/point

cd /some/mount/point

that will put you into the directory where you mounted your pendrive

 *********BE VERY CERTAIN THIS THE SPECIFIC MOUNT POINT FOR YOUR PENDRIVE BEFORE ISSUINg A CHMOD COMMAND***********

sudo chmod -r 777 /some/mount/point

*if none of that is working try this then repeat the above*

sudo umount /dev/sdb1

sudo apt-get install dosfstools

mkdosfs -v -F 16 /dev/sdb1 

im assuming your usb key is seen as /dev/sdb1.. your mileage may vary

---

### Post by saz on 2008-03-21
none of that helped, i don't want to make it writable i just want to format it and go on with my life

---

### Post by L473ncy on 2008-03-21
Dude they're like what $15 for a 1Gb stick? Just get a new one and experiment with the screwed up one while you use the new one.

If you experiment enough you can probably fix the screwed up one and if not at least learn something. AND while you're doing that you have a1 GB stick to use for other things.

---

### Post by saz on 2008-03-21
> **L473ncy said:**
> Dude they're like what $15 for a 1Gb stick? Just get a new one and experiment with the screwed up one while you use the new one.

If you experiment enough you can probably fix the screwed up one and if not at least learn something. AND while you're doing that you have a1 GB stick to use for other things.

it was my dad's...

---

### Post by unutbu on 2008-03-21
How about try the following:

WARNING: before running the code, make sure your usb stick is /dev/sdb1. If something else, substitute it for /dev/sdb1 in the code below. If not sure, post the output of 

```
mount
``` (with the usb stick mounted, of course :))

BE VERY VERY SURE /dev/sdb1 is right for you or else you could lose a lot of data!

To format the stick and make it readable to Windows, Macs and Ubuntu:
```
sudo umount /dev/sdb1
sudo mkfs.vfat -F 16 /dev/sdb1
```

---

### Post by unutbu on 2008-03-21
Sorry, I should have viewed your error.ogg before posting.

Try using gparted to make just one partition on the stick. 
Try applying just that change.
Then go to the command line and try the commands I posted.

---

### Post by unutbu on 2008-03-21
Err, and you wanted ext3 it seems...

```
sudo mkfs.ext3  /dev/sdb1
```

---

### Post by saz on 2008-03-22
well putting all in one partition is what i want since the beggining! but it gives me an error as i showed in the first post

and i can't convert it to ext3, although on the shell everything goes fine, when i mount the stick again it is still at fat16...

i had tried all that before... :'(

---

### Post by saz on 2008-03-27
c'mon can't anybody help? there must be a solution my pen can't be damaged..

---

### Post by saz on 2008-03-27
i followed this guide:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/")

i think the problem has got to do with the syslinux thing.

everytime i mount the pen drive there is this file there "ldlinux.sys", and no matter how many times i delete it, it will always be there the next time i mount the pen drive!

i think that formatting is failing because always when i try to partition it during the process the pen drive automatically mounts again, and then gparted/fdisk cannot partition it because device is busy.. here goes the output of fdisk:

```
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.

Error closing file

```

---

### Post by saz on 2008-03-27
hey guys i tried many programs on XP to format my pen, all of them say that device is write-protected/unwritable!

so this must be it!

can't anyone help me with this?!!?!?

P.S. NO my pen drive do NOT have a switch on the side!

---

### Post by saz on 2008-03-28
any1?

---

### Post by saz on 2008-03-28
c'mon guy i cannot be the only one who had this problem! someone have to know how to fix this "write-protected" thingy!

;)

---

### Post by saz on 2008-03-30
no1?

---

### Post by saz on 2008-04-06
c'mon.. i can't be the only one with this problem...

---

### Post by drkjstr on 2008-04-14
I was having trouble formating my usb pendrive. The way I did is was using gparted.

If you don't have it installed:
```

sudo apt-get install gparted

```

Once installed:
```

sudo gparted

```

You then used the dropdown box on the right side to find your pendrive. Right click on the drive, you may have to unmount first, and then choose the format type from the "Format to ->". Then click on "Apply". Once done, you should be good to go

---

