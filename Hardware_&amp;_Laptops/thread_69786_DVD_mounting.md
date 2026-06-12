---
title: "DVD mounting"
date: 2005-09-27
forum: Hardware &amp; Laptops
---

### Post by xolot1 on 2005-09-27
greetings.
this is my first post, ive been using ubuntu for around 2-3 months now though.
i tried it out just b/c i wanted to learn about linux.
warning: i can act rashly, and get excited when doing stuff, so hopefully i havent screwed anything up - causing this problem.

i had:
scd0
scd1

i got a dvd drive (from my dad at work).
i planned on replacing the scd1 with this scsi dvd r/rw  (hp dvd writer dvd300i - rather old).

only one of the two scsi slots on the mother board worked, for some reason, so i have a scsi harddrive set as master, and the dvd as slave.

i can get bios/scsi bios to recognize the device, but not ubuntu.

ive not yet learned much about cd drives on linux, so im kinda unsure what to do.

after running dmesg (as suggested in another thread), the dvd's file system is hdb. dmesg spits out the correct info about the drive, but can't seem to open it (hdb: command error: error=0x54
ide: failed opcode was 100
i/o error, dev hdb, sector 64)

fstab looks something like:
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
#/dev/scd1       /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb       /media/cdrom1   udf,iso9660 rw,user,noauto  0       0

as you can see, i #'ed the old scd1 (so i could remember what it was if i needed)
then haveing no idea what to do i copied the scd1 info, changed scd1 ->hdb, and ro ->rw

the drive will not mount.
complains about incorrect fs type (is that the iso9660 thing?)


can anyone explain what to do?
should i just wait for breezy to officially come out, reinstall w/the drive and hope that works?
is there something that i can do now?


thanks so much for the help:)

---

### Post by mlomker on 2005-09-27
> i planned on replacing the scd1 with this scsi dvd r/rw  (hp dvd writer dvd300i - rather old).


Is it only DVD's that don't mount or also data CD's?  iso9660 is for cd's and udf for DVD's.

If Ubuntu is giving you a mount error then it is seeing the drive just fine, but there might be something wrong with it.  Was the drive working in a machine before you got it?

You should be able to verify the device name with **dmesg | grep CD**.  Your fstab looks fine if the device name is right and the /media/cdrom1 directory exists.

---

### Post by xolot1 on 2005-09-28
it doesnt seem to mount anything at all.

the dmesg | grep cd looked fine, no errors and correct names (to my knowledge).

thanks for the info, im gonna try the drive on windows see if thatll work.

is there anything else i can be trying?

---

### Post by mlomker on 2005-09-28
> is there anything else i can be trying?

Not really.  CD-Rom's are rarely a problem in linux...if it's plugged in right and works in Windows then it should be good in Ubuntu.

---

### Post by xolot1 on 2005-09-28
looks like youre right.
it wont work on windows - it installs, but wont show up under my compter, etc.
oh well.

thanks for the help!
i can still think of this as a success as ive learned a bunch about cd drives now.

---

