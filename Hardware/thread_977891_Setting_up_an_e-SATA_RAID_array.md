---
title: "Setting up an e-SATA RAID array"
date: 2008-11-10
forum: Hardware
---

### Post by costre on 2008-11-10
Hello!

I just bought a MicroNet SR4 external e-SATA hard drive. It's an array of four separate 1TB drives.

Just curious if there's any one way to go about setting this drive up? I'd like to be able to use all 4 TB, no mirroring or fancy things like that.

This is my output of fdisk -l, 
[I]
root@albin-desktop:/home/albin# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009b28f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14590   117194143+  83  Linux
/dev/sda2           14591       60558   369237960   83  Linux
/dev/sda3           60559       60801     1951897+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000698ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdg: 2000.4 GB, 2000409772032 bytes
255 heads, 63 sectors/track, 243202 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005c5cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      243202  1953520033+  83  Linux

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      121601   976760001    7  HPFS/NTFS

[B]Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30353434

Disk /dev/sdi doesn't contain a valid partition table

Disk /dev/sdj: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e0ae6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1         244     1959898+  fd  Linux raid autodetect
/dev/sdj2             245      121601   974800102+  fd  Linux raid autodetect

Disk /dev/sdk: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ee0dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1               1         244     1959898+  fd  Linux raid autodetect
/dev/sdk2             245      121601   974800102+  fd  Linux raid autodetect

Disk /dev/sdl: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00008c3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1               1         244     1959898+  fd  Linux raid autodetect
/dev/sdl2             245      121601   974800102+  fd  Linux raid autodetect[/B]
[/I]


The drive(s) in question would be sdi (SDI) through sdl (SDL). It says "Linux raid autodetect", which I assume is a good thing?

I can see the four "activity"-LED's on the front of the drive light up and flash one after the other during boot-up, as Linux starts it obviously recognizes all the four drives.

All drives show up in gparted.

sdi shows 932 GB of "unallocated" space
sdj shows 1.87 GB of swap (swapon) , and 930 GB of "unknown" FS
sdk shows 1.87 GB of swap (swapon) , and 930 GB of "unknown" FS
sdl shows 1.87 GB of swap (swapoff), and 930 GB of ext3 FS (seemingly "damaged", it's got that red sign with the exclamation mark)

I don't feel like diving in head first, any tips or suggestions are greatly appreciated, this is my first attempt ever at messing around with raid! :)

Thanks in advance!

---

### Post by costre on 2008-11-11
OK, I resolved the issue on my own.

First I slated the disks using gparted, creating only one big partition on each one.
Then I used MDADM to create the raid array, in my case the command was 

```
mdadm --create --verbose /dev/md0 --level=0 --raid-devices=4 /dev/sdi1 /dev/sdj1 /dev/sdk1 /dev/sdl1 

```

**/dev/md0** is the destination of the raid array
**level** is the raid level to be used, in this case RAID0
**raid-devices** is the number of disks, in this case four (4)
**/dev/sdi1** through **/dev/sdl1** are the four disks to be used in the array



I chose ext3 for the file system (perhaps I'll reformat it to something a little more fancy, but for now it'll do)

```
mkfs.ext3 /dev/md0
```

Then simply mount it at the desired mount point (I chose /media since it's after all an external, sort-of portable, drive)

```
mount /dev/md0 /media/raid
```

I could now check the array using 

```
df -vhT
```

which gave me 

**Filesystem    Type    Size  Used  Avail  Use%  Mounted on**
**/dev/md0         ext3    3.6T  197M  3.4T   1%         /media/raid**

That's it!

It's as simple as that. Hopefully it'll work after reboot etc :)

---

### Post by psusi on 2008-11-11
I hope you have a good backup plan you use frequently.  With 4 disks the odds of a failure are 4 times more likely.  If you loose one you loose all your data.  You might want to go with a raid 5 instead so you can handle a single disk failure.

---

### Post by costre on 2008-11-11
I have considered that, but the disk stack is very well ventilated, and I don't have any irreplacables on it at all. Thanks for the tip, though :)

---

### Post by costre on 2008-11-13
Alright, I seem to have been more n00bish than I thought when it comes to raid. 

The device I'm trying to configure is this:

[http://store.micronet.com/SR44000E.aspx](http://store.micronet.com/SR44000E.aspx)

The full name is a "4TB eSATA RAID with 2-port PCI-Express Card"

I hope this means it's hardware raid? The method I used in my previous post to arrange and mount the drives was (I learned) software raid.

So is it possible to configure hardware raid natively in Linux, or do you need special drivers? It says it supports XP, Vista, and OSX, but the customer support told me previous to the purchase that it worked in Linux.

I will mail the customer support, but any suggestions or comments on this issue from the Ubuntu community would be awesome :)

---

### Post by Coreigh on 2008-11-13
I did not find the explicit answer but I am guessing that this is software RAID all around. The PCIx card referenced is not specified as a RAID controller, although the description ([website here]("http://www.micronet.com/products/sr4.htm")) does say the product is "Bundled with an eSATA RAID controller,..." Is there software included with the device? When you boot the machine with the PCIx card installed is there a BIOS for the card that comes up after the machine BIOS before the OS? Hardware RAID settings would be there. If not then it is probably software RAID.

There is nothing *wrong* with software RAID, except that it is not hardware and is not as resilient. Keep back ups up to date and you will be fine.

Some of the reviews state that the RAID 5 included with the system is too slow. This may not be the case with Linux mdadm and you may have lesser performance needs than the reviewers.

---

### Post by costre on 2008-11-13
Well, there is a menu after startup. I am asked to "hit F4" to setup my disks (note: not the usual "hit F2 to enter setup", this comes after that)

In this little menu, I am only able to see one of the 1TB drives, but there is something like "create RAID 0-", and "create RAID 1-array". But since only one drive is showing in the little list instead of four, I'm not able to do anything useful in that menu.

Again, nothing irreplaceable is going on these drives. I guess I could reboot and have a closer look at that little boot-up application.

---

### Post by costre on 2008-11-13
Here we go again.

There are four LED's on the drive-array's chassis that shows the activity of each individual drive. When I start the computer no LED is lit. Just as the raid-menu shows up, the first LED lights up, and that's all. And as I said, only one drive is showing in the raid-menu.

There is an option, "CREATE RAID SET", which has options of raid0 or raid1. There is also "DELETE RAID SET", but there has to be two or more drives showing in the menu though.

Moving on. As Ubuntu starts, all LED lights up about halfway through the boot process, in a nice little twinkling pattern. The drives show up as four separate drives, and as I explained, I used MDADM to create a RAID0-array using these four drives.

There are a few jumper pins on the controller card, but no jumpers on them. Could simply be for attaching LED's for monitoring the activity of the two e-SATA ports.

I have mailed technical support, but any ideas are welcome!

---

### Post by psusi on 2008-11-13
Sounds like it's a fakeraid controller and it's broken since it only sees the one disk.

Best just to stick with the software raid.

---

### Post by costre on 2008-11-13
Yes, I thought so too .. but now I can't even mount the array. 

```
# mount /dev/md0 /media/raid
mount: you must specify the filesystem type
```

I don't know why. Could be that I rebooted with the e-sata cable in the second port on the controller, or that I executed the raid menu at boot-up. In any case, it looks like the array is ******. 

As I said, there's no important stuff on the drive, but it's not good that it seems to be more than a little unstable. I hope I can get hardware raid activated.

---

### Post by costre on 2008-11-13
Yes, I thought so too .. but now I can't even mount the array. 

```
# mount /dev/md0 /media/raid
mount: you must specify the filesystem type
```

```
#mdadm --create --verbose /dev/md0 --level=0 --raid-devices=4 /dev/sdi1 /dev/sdj1 /dev/sdk1 /dev/sdl1 

mdadm: chunk size defaults to 64K
mdadm: Cannot open /dev/sdi1: Device or resource busy
mdadm: Cannot open /dev/sdj1: Device or resource busy
mdadm: Cannot open /dev/sdk1: Device or resource busy
mdadm: Cannot open /dev/sdl1: Device or resource busy
mdadm: create aborted
```


I don't know why. Could be that I rebooted with the e-sata cable in the second port on the controller, or that I executed the raid menu at boot-up. In any case, it looks like the array is focked. 

As I said, there's no important stuff on the drive, but it's not good that it seems to be more than a little unstable. I hope I can get hardware raid activated.

---

### Post by psusi on 2008-11-13
Did you add an entry to /etc/fstab for /dev/md0?  If not, then mount has no way of knowing what filesystem you are trying to mount on /dev/md0, so it's telling you to specify the filesystem type ( with -t ).

Your attempt to recreate the array is failing because it is already active so the disks are in use.

---

### Post by costre on 2008-11-13
[b][i]EDIT: 
Thanks, I edited /etc/fstab the best I knew how, and the drive popped up mounted and ready after reboot! [/i][/b]


So how do I specify the file system? Mind you, I have rebooted before, and simply re-mounted without trouble :)

```
# mount -t ext3 /dev/md0 /media/raid

mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by psusi on 2008-11-14
Looks like md0 doesn't contain an ext3 filesystem.  Do as it says and check dmesg | tail.

---

### Post by costre on 2008-11-27
[i]Quick update ... Now it seems impossible to mount it (again). I have the same specs in /etc/fstab as before, but it doesn't mount on reboot. 

I'm getting frustrated over this, big time. I have mailed micronet again, hopefully they'll have something useful to say, unlike this post :)[/i]


***EDIT:***

I ran gparted and saw that the devices had changed letters. 
Instead of showing as **sdi, sdj, sdk, sdl** they showed as **sdh1, sdi1, sdj1, sdk1**

I edited /etc/mdadm/mdadm.conf and all is well.

Still thinking of why this happened though ...

***/EDIT***

---

