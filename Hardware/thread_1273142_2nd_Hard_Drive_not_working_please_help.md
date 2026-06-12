---
title: "2nd Hard Drive not working please help"
date: 2009-09-23
forum: Hardware
---

### Post by AnimeFreak on 2009-09-23
Reason:
Do to my stupidity i had to reinstall ubuntu. It worked before but not now.

Details: 
I have Ubuntu 9.04 (and have since it came out)

i have 2 80 gig hard drives 
one has ubuntu the other was just storage 

2nd hd is seen but cannot access 

Question:
i think i just need to format it but not 100% sure.  If that is what i need to do how do i go about doing it?  if its something else what is it?

Thank You in advanced for any and all help!

---

### Post by jammen33 on 2009-09-23
Did you set a mount point when reinstalling ubuntu?
you can do that under the manual configuration option in the installer

If you didn't try mounting it

Amusing the drive is sdb1(change the command accordingly)  
```
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
```

If that works then the drive should work

Here is a link to an Ubuntu wiki article on how to get the drive to auto mount

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

This might be a better tutorial 
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by AnimeFreak on 2009-09-23
> **jammen33 said:**
> Did you set a mount point when reinstalling ubuntu?
you can do that under the manual configuration option in the installer

it never gave me an opition

> This might be a better tutorial 
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)ok here is what the terminal says after i type in sudo blkid

```
sudo blkid
/dev/sda1: UUID="f8c7c61d-a369-4bfc-a2fa-938faadebed5" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="c97d4c96-f385-4391-b836-95c624d875bb"
```/dev/sda5 is the drive that i can't mount

---

### Post by AnimeFreak on 2009-09-23
bump

---

### Post by jammen33 on 2009-09-23
Can you post the output of:
```
sudo fdisk -l
```

---

### Post by jammen33 on 2009-09-23
> **AnimeFreak said:**
> 
/dev/sda5: TYPE="swap" UUID="c97d4c96-f385-4391-b836-95c624d875bb"
/dev/sda5 is the drive that i can't mount

it shows sda5 as the swap partition, you cannot mount this partition it is used as virtual memory when your ram space runs low.

also both of those partitions are on the same physical hard drive

---

### Post by AnimeFreak on 2009-09-23
> **jammen33 said:**
> Can you post the output of:
```
sudo fdisk -l
```
  
  here it is

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf732f732

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris
```

---

### Post by AnimeFreak on 2009-09-23
> **jammen33 said:**
> it shows sda5 as the swap partition, you cannot mount this partition it is used as virtual memory when your ram space runs low.

also both of those partitions are on the same physical hard drive

oh ok my bad

---

### Post by FuturePusher on 2009-09-23
> **AnimeFreak said:**
> 

... (snip-snip) ...

2nd hd is seen but cannot access 

... (snip-snip) ...

if its something else what is it?




Well, according to fdisk (and most likely any other tool), Your 2nd HDD **_isn't_** seen/detected, neither by "HAL" or the core linux kernel.

If You see the drive appear in the BIOS output during startup (or storage section @ the BIOS/CMOS setup), we can probably unfortunately draw the conclusion that it's failing ("dieing")...
If You **don't** see it appear there at all, it could just be that You've forgotten to reconnect the power, or data, cable to it after any computer disassembly.

Verify it all on that hardware level first, then retry what You have done up until now to check it, and then please report back in this thread!

**EDIT:** Your system should show one HDD with the "sda" designation (main drive), and most likely "sdb" for Your secondary HDD, when You do a "ls -l /dev/sd*" in a terminal/console (no quotes when typing!)... if the second doesn't appear, the system isn't detecting it.

---

### Post by AnimeFreak on 2009-09-23
> **FuturePusher said:**
> Well, according to fdisk (and most likely any other tool), Your 2nd HDD **_isn't_** seen/detected, neither by "HAL" or the core linux kernel.

If You see the drive appear in the BIOS output during startup (or storage section @ the BIOS/CMOS setup), we can probably unfortunately draw the conclusion that it's failing ("dieing")...
If You **don't** see it appear there at all, it could just be that You've forgotten to reconnect the power, or data, cable to it after any computer disassembly.

Verify it all on that hardware level first, then retry what You have done up until now to check it, and then please report back in this thread!

**EDIT:** Your system should show one HDD with the "sda" designation (main drive), and most likely "sdb" for Your secondary HDD, when You do a "ls -l /dev/sd*" in a terminal/console (no quotes when typing!)... if the second doesn't appear, the system isn't detecting it.

everything is hooked up right and like i said i see it but when i formated it this started 
(i just bought it a week ago it worked then)

---

### Post by chris1950 on 2009-09-24
Go to Gparted - in the uper right corner it should show your current drive with a down arrow, click on the arrow and see if it shows the other drive (it may show it as unformated). If thats the case you can format and set the mount point or if formatted you can set the mount point.

---

### Post by Barijazz on 2009-09-24
Is there an sdb* entry in fstab?  If you did not install the 2nd drive during installation, Ubuntu may not know what to do with it.

BTW, when you say you can "see" the drive, where can you see it?

---

### Post by AnimeFreak on 2009-09-24
> **Barijazz said:**
> Is there an sdb* entry in fstab?  If you did not install the 2nd drive during installation, Ubuntu may not know what to do with it.

BTW, when you say you can "see" the drive, where can you see it?


in the computer folder its called mass storage device and when i try to mount it it says cit can't

---

### Post by AnimeFreak on 2009-09-24
ok i cheaked my patitions and i see it in the bios 


so how do i get it to to be seen in ubuntu

---

### Post by AnimeFreak on 2009-09-24
bump

---

### Post by FuturePusher on 2009-09-24
Hi again,

OK.. by now, with what You've described so far, it "sounds" like it's working properly on the hardware side.

On the OS & software side: You see the drive appear as a "Mass Storage Device" in Nautilus/"whichever-filemanager-You're-using" because that's how *HAL* handles all and any "media" added to the system, that's not explicitly specified in *fstab*.
Also, HAL should by default be set up to let the system's non-restricted users mount such media the way You're trying to.

OK, now with that stuff described a bit... here's what's most likely Your issue:
**The drive simply has no partition prepared on it!** You first need to have that on a brand new drive, then any kind of filesystem (ext2/3/4, jfs, fat32/ntfs, etcetera..) goes into the partition.

When You try and mount the device, HAL fails doing so because there's no filesystem on it, which there most often **can't** be without one/more partition(s) on it first.

So, do what **chris1950** suggested just recently;

* Select Your new drive in the dropdown list in gparted (press the two keys "Alt+F2", type "gksudo gparted" and hit the Return/Enter-key).
 (You'll be able to determine which that drive is as You should see no partitions/filesystems on it, just "grey emptiness" ("Not allocated") and the space free on it.)

* Right click on the grey "free space"-area, or the "not allocated" in the list below the graphic representation of the disk, and select "New..." in that popup menu... proceed with all & any suggestions from *gparted*.
(I suggest You choose to create one "primary" partition, taking up all available spece on the disk.)

* As long as You're satisfied with that drive being one large storage disk, format an ext3 filesystem on it if You want to be able to use Linux features (permissions etc.), or choose NTFS filesystem if You need to be able to access the files in "that other" OS... ;)


NOTE: If You **don't** see the drive we're talking about **at all**, in any way, shape or form, in *gparted* (more familiarily name "Partition Editor" in Menu: System » Administration" BTW..)... there's something erroneously configured in Your OS, which I doubt since You can see the actual **device** as You said (HAL detects it).

**EDIT:**
If You like You wrote, truly see any **partition(s)** on the disk in BIOS, the issue is instead more likely related to permissions already set on it's filesystem, or somewhere in *fstab*, which prevents users from mounting it... but I doubt this since, as You wrote, the drive appears as "Mass Storage Device"... and since *HAL* is what makes it appear. (HAL runs with root privileges and thus "has the powers needed" to inspect the drive for filesystems... If HAL finds any existing, the drive most often appears with the filesystem **label** rather than "Mass Storage Device". The latter usually appears when the disk is completely empty, as I'm suspecting!)

---

### Post by AnimeFreak on 2009-09-24
> **FuturePusher said:**
> Hi again,

OK.. by now, with what You've described so far, it "sounds" like it's working properly on the hardware side.

On the OS & software side: You see the drive appear as a "Mass Storage Device" in Nautilus/"whichever-filemanager-You're-using" because that's how *HAL* handles all and any "media" added to the system, that's not explicitly specified in *fstab*.
Also, HAL should by default be set up to let the system's non-restricted users mount such media the way You're trying to.

OK, now with that stuff described a bit... here's what's most likely Your issue:
**The drive simply has no partition prepared on it!** You first need to have that on a brand new drive, then any kind of filesystem (ext2/3/4, jfs, fat32/ntfs, etcetera..) goes into the partition.

When You try and mount the device, HAL fails doing so because there's no filesystem on it, which there most often **can't** be without one/more partition(s) on it first.

So, do what **chris1950** suggested just recently;

* Select Your new drive in the dropdown list in gparted (press the two keys "Alt+F2", type "gksudo gparted" and hit the Return/Enter-key).
 (You'll be able to determine which that drive is as You should see no partitions/filesystems on it, just "grey emptiness" ("Not allocated") and the space free on it.)

* Right click on the grey "free space"-area, or the "not allocated" in the list below the graphic representation of the disk, and select "New..." in that popup menu... proceed with all & any suggestions from *gparted*.
(I suggest You choose to create one "primary" partition, taking up all available spece on the disk.)

* As long as You're satisfied with that drive being one large storage disk, format an ext3 filesystem on it if You want to be able to use Linux features (permissions etc.), or choose NTFS filesystem if You need to be able to access the files in "that other" OS... ;)


NOTE: If You **don't** see the drive we're talking about **at all**, in any way, shape or form, in *gparted* (more familiarily name "Partition Editor" in Menu: System » Administration" BTW..)... there's something erroneously configured in Your OS, which I doubt since You can see the actual **device** as You said (HAL detects it).

**EDIT:**
If You like You wrote, truly see any **partition(s)** on the disk in BIOS, the issue is instead more likely related to permissions already set on it's filesystem, or somewhere in *fstab*, which prevents users from mounting it... but I doubt this since, as You wrote, the drive appears as "Mass Storage Device"... and since *HAL* is what makes it appear. (HAL runs with root privileges and thus "has the powers needed" to inspect the drive for filesystems... If HAL finds any existing, the drive most often appears with the filesystem **label** rather than "Mass Storage Device". The latter usually appears when the disk is completely empty, as I'm suspecting!)

i don't see it in gparted all i see is my filesystem hd

---

### Post by louieb on 2009-09-25
I haven't seen anything to suggest you have a 2nd hard drive. Even if it is a new drive with no partition table - no data - just a blank drive - the fdisk output would have a entry showing the size of drive and Gparted would show a blank drive. 

Is it a  SATA drive (narrrow data and power connector - no jumpers)?

Or IDE (also called PATA)  (wide data connector - usually white power connector - jumpers for setting  for master, slave, cable select, and sometime single) connection? 
Are you absolutely sure the data connector is pugged in the right direction, the  jumpers are set correctly on both drives? (colored wire goes should be closest to the power connector)      

> ok i cheaked my patitions and i see it in the bios I have never seen BIOS setup show partitons - only connected devices (hard drive(s), CD/DVD drive).

---

### Post by AnimeFreak on 2009-09-26
> **louieb said:**
> I haven't seen anything to suggest you have a 2nd hard drive. Even if it is a new drive with no partition table - no data - just a blank drive - the fdisk output would have a entry showing the size of drive and Gparted would show a blank drive. 

Is it a  SATA drive (narrrow data and power connector - no jumpers)?

Or IDE (also called PATA)  (wide data connector - usually white power connector - jumpers for setting  for master, slave, cable select, and sometime single) connection? 
Are you absolutely sure the data connector is pugged in the right direction, the  jumpers are set correctly on both drives? (colored wire goes should be closest to the power connector)      
its ide and like i said it worked before. nothing has been moved, unpluged, or opened since i last installed it. i had stuff on it before i reinstalled ubuntu but i formated it to put windows on it and windows wouldn't put a partioiont on it so i put it on this one.  then windows wanted to mess up so i reinstalled ubuntu and the problem then starts. 

> **louieb said:**
> I have never seen BIOS setup show partitons - only connected devices (hard drive(s), CD/DVD drive).
  exactly i only see hardware but it is there

---

### Post by FuturePusher on 2009-09-26
> **AnimeFreak said:**
> its ide and like i said it worked before. nothing has been moved, unpluged, or opened since i last installed it. i had stuff on it before i reinstalled ubuntu but i formated it to put windows on it and windows wouldn't put a partioiont on it so i put it on this one.  then windows wanted to mess up so i reinstalled ubuntu and the problem then starts. 


  exactly i only see hardware but it is there


Well, unfortunately it may still be faulty (and yes, that can happen even to a new drive.. not all drives are shipped from factory in perfect condition - even more likely if it's gotten a hard knock during handling)...

Like **louib** wrote, BIOS only lists the **devices** it detects, not what's on them... so a harddrive for instance may show up, but still have media defects...

If You have "smartctl" installed (check by running this in a terminal, without the quotes: "sudo smartctl --help", and run "sudo apt-get install smartctl" if You don't have it)... there's a simple way for You to first find out what drives are functional, and then check the status of those drives:

Run this in a terminal, again without quotes, to see what functional drives You have:
"sudo smartctl -H /dev/sd[abcdefg]"
You'll see "/dev/sda" appear in the error message You'll get, and hopefully "/dev/sdb" (any second drive... if You have a few more, they'll appear as well)

... and run this, again without quotes, to check the status of a drive (re-run for each drive ("sda"/"sdb"/"sdc" etc.), change the "/dev/sda" below to then next drive designation *smartctl* showed earlier...):
"sudo smartctl -H /dev/sda"

And, like I wrote earlier... You can also run "ls -l /dev/sd*" (no quotes) in a terminal to see which drives are detected by the system... but with *smartctl* You'll be able to see if the drive is itself reporting any bad condition, via "SMART" technology (hence the name of smartctl).

There's several things of what You've been suggested to do to find out what's going on, that You haven't done... or at least reported on here.
You can't get much more assistance here without doing so, just a friendly advice.

Let's hope the drive is in good condition to begin with... check it out with what's been suggested!

---

### Post by Barijazz on 2009-09-26
> in the computer folder its called mass storage device and when i try to mount it it says cit can't     Correct me if I'm wrong, but I don't think HAL should be identifying an IDE hard disk as a Mass Storage Device.  Isn't that default label typically assigned to removable media like SD cards and thumb drives?

I'm running UNR and my Computer directory shows Filesystem and USB Drive.  USB Drive is a place holder (or represents the SD Card mounted to /home) and isn't mountable. I suspect your Mass Storage Device is something similar and represents a potential mount point rather than any physically connected hardware.

Again, I could be wrong.  I've learned a lot due to my own mounting issues, but I've only been using Ubuntu for 6 months.

Oh, and to echo FuturePusher, it sounds like your HD or its formatting may have errors.  If Windows wouldn't format it, a problem may have occurred in the formatting during Windows installation.

---

