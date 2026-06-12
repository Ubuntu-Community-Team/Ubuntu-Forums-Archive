---
title: "DVD Problems"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by Snyper64 on 2007-05-14
Ok, so I looked around and have seen that alot of people are having problems mounting DVD movies in Feisty(I never had any problems in Edgy). Now before everybody jumps in and starts yelling about the hardware and media players I will flat out say that my DVD drive works fine and my media players will play DVDs. It seems like my pc only plays certain DVDs without a hitch but other it will either take a couple of tries before it will mount or it just doesn't mount at all. Here's an example: I was playing Forever Knight(I just bought it on DVD last week) and finished disk 2 in the morning. I went and inserted disk 3 and it will not mount no matter what I do. So I go and toss in another DVD that always mounts, my Ghost in the Shell first movie and it automatically mounted and Gxine started up and plays it without a hitch. I tossed the Forever Knight disk in my Xbox 360 to see if maybe I got a bad disk but it played just fine. So my question is why will some DVDs mount and others won't?

So I decided to try a graphical mount utility to see if maybe there was something wrong with Ubuntus mounting utility and found a utility called KdiskFree and tried to mount the DVD that way but all it did is give me the following error:
```
Called: mount /dev/hdc
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
```

So I went into the terminal and typed in dmesg | tail and got the following output:
```
snyper64@ubuntuSnyper64:~$ dmesg | tail
[ 1695.508636] ide: failed opcode was: unknown
[ 1695.508702] hdc: error code: 0x70  sense_key: 0x05  asc: 0x24  ascq: 0x00
[ 1698.751350] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[ 1698.751356] hdc: packet command error: error=0x50 { LastFailedSense=0x05 }
[ 1698.751360] ide: failed opcode was: unknown
[ 1698.751435] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x00
[ 1698.753213] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[ 1698.753218] hdc: packet command error: error=0x50 { LastFailedSense=0x05 }
[ 1698.753221] ide: failed opcode was: unknown
[ 1698.753290] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x00
snyper64@ubuntuSnyper64:~$ 
```

So can anybody help me figure out what on earth is up with Feisty and get all of my DVDs working?
If you have any questions feel free to ask and I will be happy to answer them to the best of my ability to.

Thanks

Snyper64

---

### Post by rggavubt on 2007-05-14
I also can't play DVD's since I upgraded to Feisty.  I entered the "mount /dev/hdc" command and got this error:  [mntent]: warning: no final newline at the end of /etc/fstab
mount: can't find /dev/hdc in /etc/fstab or /etc/mtab

---

### Post by oky on 2007-05-20
I am also having problems. If I put a normal cd, it will be automatically mounted. If I put a DVD movie nothing happen. Also try manual mount, nothing. Please help I was so happy with the new version. In fact I was very impressed. But things like this need to get better in Linux. I can only imagine the longs hours spent putting this new version together. But watching a DVD should be as normal as executing a command in the shell.(from a users point of view).  It used to work on edgy.

---

### Post by philba on 2007-06-08
> **oky said:**
> I am also having problems. If I put a normal cd, it will be automatically mounted. If I put a DVD movie nothing happen. Also try manual mount, nothing. Please help I was so happy with the new version. In fact I was very impressed. But things like this need to get better in Linux. I can only imagine the longs hours spent putting this new version together. But watching a DVD should be as normal as executing a command in the shell.(from a users point of view).  It used to work on edgy.

I, too, have this problem.    CDROMs mount and show the icon, DVDs don't.  Clicking on the icon that shows up in places/computer gives the error message "Unable to mount media - there is probably no mdeia in the drive"   However, I can run Xine and play the DVD just fine...

Though, a different box running fiesty doesn't have the problem..  It automounts dvds and runs the program specified in the multimedia tab of system/preserences/removable...

---

### Post by philba on 2007-06-08
More info and maybe some hints...

I discovered that /etc/fstab had the wrong mount line for the device.  the install presumed that /dev/scd0 was the optical device (SATA connector, I think, though I thought s stood for scsi) but the dvd drive is plugged into the IDE connector which makes it /dev/hda.  

old:
/dev/scd0    /media/cdrom0  udf,iso9660 user,noauto 0 0

which I changed to:
/dev/hda    /media/cdrom0  udf,iso9660 user,noauto 0 0

now at least mount /dev/hda or mount /dev/dvd works and i can cd to the mount point and look at the dvd files.

It is still not automounting, though.  (note, the noauto in the fstab line is not what you think - it simply controls mounting via the mount -a option)  
edit:  no, that WAS the problem.  I had turned off automounting in system->preferences->removable->storage

---

### Post by philba on 2007-06-08
OK, to clean things up a bit.  It's solved  :popcorn: 

here is the solution to the problem.

/etc/fstab had the wrong device name for the optical drive.

In my case the actual drive is /dev/hda  (first device on the IDE connector)
The default installation had it as /dev/scd0

I modified the following line in /etc/fstab
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
to
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

and that fixed the problem.  It is now automounting my DVDs and running the associated player.

note: the reason it didn't seem to work was because I had turned off "mount removable media when inserted" in  system->preferences->removable drives...->storage

Ubuntu needs to improve how it figures out the optical drive for the fstab.  it clearly knows where the drive exists since system->preferences->hardware information shows an optical drive on the IDE controller.

---

### Post by Snyper64 on 2007-06-08
My fstab seems fine, I guess it was just you that was having the fstab problem. As of recently my drive seems to be mounting fine but now its not unmounting the DVDs saying I need to be root to do it? Is it just me or does Feisty still have a ways to go when it comes to mounting and unmounting peripherals?

---

### Post by philba on 2007-06-09
I'd check the permissions on the various files.  I've seen what you describe - typically when the file mounted by root and then a user tried to unmount it.  Same will happen if you press the eject button (since it tries to unmount).

---

### Post by Snyper64 on 2007-06-09
The eject button is the only way I can get the discs out of my drive when that happens, surprisingly when I use the eject button it doesn't give me the usual this drive was not unmounted properly, please use the unmount command to prevent errors on the device. As for permissions it does only show root and won't let me change anything. Hopefully all of these problems will be fixed with the next version of Ubuntu or better yet patched for Feisty.

---

