---
title: "Installation won't start; what are these errors?"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by orangepsycho86 on 2009-01-28
i previously had a vista partition on my self-built pc but this morning i decided to get rid of it (parents were sick of getting viruses so i convinced them to try linux) but i've been trying for hours to get the install to work and i've had no luck. i downloaded the 8.10 i386 iso and burned it to a dvd. the disk will boot and the live cd starts fine. i've tested the memory, checked the disk for errors, and the md5 checked out fine so i'm certain the disk is good for installation (also installed ubuntu on an older laptop with ease with this same disk so i know it works fine) but after i tried to start the install the ubuntu loading screen starts moving then when it starts to load it seems to freeze and after about 5 minutes some errors show up. keep in mind this is a completely wiped hard drive with no partitions on it after i deleted the old one with vista on it. i got these errors at first:

udevd-event[4270]: run_program: exec of program ' /lib/udev/edd_id' failed

udevd-event[4272]: run_program: exec of program ' /lib/udev/hdparm' failed

udevd-event[4341]: run_program: exec of program ' /sbin/modprobe' failed

udevd-event[4344]: run_program: exec of program ' /sbin/modprobe' failed

udevd-event[4346]: run_program: exec of program ' /lib/udev/path_id' failed

udevd-event[4348]: run_program: exec of program ' /lib/udev/path_id' failed

udevd-event[4966]: run_program: exec of program ' /sbin/modprobe' failed

udevd-event[4968]: run_program: exec of program ' /sbin/modprobe' failed

udevd-event[4974]: run_program: exec of program ' /sbin/modprobe' failed

Segmentation fault
/etc/rcS.d/S10udev: 105: readlink: Permission denied
/etc/rcS.d/S10udev: 1: usplash_write: Permission denied
init: rcS main process (3831) killed by SEGV signal
init: Unable to execute "/bin/sh" for rc-default: Permission denied
init: rc-default main process (4982) terminated with status 255


then after those errors i thought maybe i needed to have a raw partition created on the hdd so i popped an xp disk in and created a new raw partition. popped the ubuntu disk back in and i got these errors:

* Preparing restricted drivers...                                         [ OK ]
* Setting the stystem clock
* Starting basic networking...                                            [ OK ]
* Starting kernel event manager...                                        [ OK ]
* Loading hardware drivers...
/etc/rcS.d/S10udev: 105: usplash_write: not found
/etc/rcS.d/S10udev: 105: readlink: not found
/etc/rcS.d/S10udev: 1: usplash_write: not found
/etc/init.d/rc: 372: sh: not found
/etc/init.d/rc: 372: sh: not found
init: rcS main process (3804) killed by SEGV signal
init: Unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default main process (4968) terminated with status 255


one more last ditch attempt was to pop the xp disk back in and format the raw partition with ntfs and stop the install before any files were copied over. no dice either...i'm out of ideas now. any suggestions would be greatly appreciated!!

---

### Post by cariboo on 2009-01-28
It looks like your installation is corrupt, your listings says that there are files missing.

I would suggest checking the hard drives integrity by using the hard drive manufacturers dianostic software.

Jim

---

### Post by orangepsycho86 on 2009-01-28
wouldn't the integrity be ok though if i can install any windows os on the hdd or mac os either?? both work fine for me...

---

### Post by Therion on 2009-01-28
Short answer:  Try installing 8.04 instead of 8.10

Maintain your good burning practices (e.g. burn it slow, check the MD5 etc.)

---

### Post by orangepsycho86 on 2009-01-28
already tried that. i burned 2 different copies at 4x with the same results and also had a copy of 8.04 that i tried with similar results.

---

