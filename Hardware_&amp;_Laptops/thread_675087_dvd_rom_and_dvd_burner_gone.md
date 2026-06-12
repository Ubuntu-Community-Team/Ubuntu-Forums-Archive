---
title: "dvd rom and dvd burner gone"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by RoeZ on 2008-01-22
Hi there,

I have been strugeling with this for some time now.
What happend is i got an update message from ubuntu, didn't really looked what got updated.
After that my dvd-rom and my dvd burner are gone. I have looked at alot of threads regarding this problem but no fixes, actually the posts that are very similar are unanswered.

I have tried to put in a cd, i have tried to put my devices cable on an other slot. they are both ide devices on the same cable. When i boot my computer with the gutsy gibbon live cd it loads, but it reaches a point where it can't go further and shows BusyBox, don't know if this has to do with the same problem, when starting the livecd before it reaches BusyBox it complains it can't find fd0, wich i guese is my floppy drive, so i disabled this in bios and in my fstab, wich doesn't fix the live-cd problem, but i don't really care about that, at least if it doesn't regard this.

This is my fstab :
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e5d648db-2ff2-4123-b8a1-e7156f2df1a3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=d8999827-e0d9-43fc-be45-0aa7d14f4e30 /home           ext3    defaults        0       2
# /dev/sda5
UUID=16F47030F4701469 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=8A941C16941C077B /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=12F3DE83D8F8CDA1 /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
UUID=9CFC2153FC2128CA /media/sdc1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=b8b55cda-3614-4208-ad20-d098c4611bab none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

here is my output when i do the command 'mount'
```

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw)
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sdb5 on /media/sdb5 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sdc1 on /media/sdc1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

when i do mount /dev/scd0 i get :
```

mount: special device /dev/scd0 does not exist

```

same goes for scd1.

I looked at my system -> preferences -> hardware information, but no sign of any dvd player or burner.

I kinda know my dvd drives work cause they boot when the live cd. I have tried some more commands and looked into more files, but can't remember them anymore (new to linux)

Also i tried a usb dvd burner from my friend wich worked flawlessly. Before the update of ubuntu my drives both worked flawlessly also. My friend told me i should boot into another kernel, but when i start up my 'grub' i believe it's called, doesn't show any other kernel versions

If anyone could help me out or point me in the right direction, that would be great!

---

### Post by wrightee on 2008-01-22
Same problem.. see this thread:

[http://ubuntuforums.org/showthread.php?t=353550](http://ubuntuforums.org/showthread.php?t=353550)

Add **noaipc acpi=off** to grub menu list to get it back (after the line that looks like this: kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=eb9630c0-add2-43c6-af04-5dd1d2217f6d ro quiet splash) ... but beware, you might lose ethernet if you do.

Or.. switch bootloader to Lilo from Grub, but that comes with its own set of issues..

Let me know if you find a way...

---

### Post by mc4man on 2008-01-22
Seems kinda odd to see in fstab your scd0 with a mount point of cdrom1 and your scd1 with mount point of cdrom0. In every setup I've done with 2 cd/dvd drives the drive in a master position will be /dev/scd0 - cdrom0 and the one in a slave position /dev/scd1 - cdrom1

---

### Post by TeaSwigger on 2008-01-22
Similarly, I've just installed a new dvd-rw and it's nowhere to be found in Kubuntu, depite being present and hunky-dorey in BIOS and Win2kPro, to wit my help wanted thread:
[http://ubuntuforums.org/showthread.php?t=674787](http://ubuntuforums.org/showthread.php?t=674787)

Hope we can find an answer.

---

### Post by RoeZ on 2008-01-23
wrightee i have tried to add that rule to my menu.lst but that didn't do anything, my ethernet still works but no dvd / cd-rom drives, i tried to enter a dvd and a cd of course. I am now gonna try to start ubuntu without the ide cable attached to the slot, and then after that (i hope ubuntu removes all known cd / dvd devices from fstab) i am gonna reattach it, i let you guys know.

If any1 has an other option i might try, pleeaasee let me know!

---

### Post by RoeZ on 2008-01-23
Wel as i tought that didn't do anything, i tried disabling 1 of the drives, no luck, i tried disabling the other drive, no luck either. I don't know anything i can try next, if any1 has sugestions please let me know

---

### Post by RoeZ on 2008-01-23
I did a recovery mode of ubuntu and it said something about not being able to load scd1, i had an option to force load the drive, wich i did, after that still no dvd / cd and also my 2 harddisks are gone, only the harddisk where ubuntu is on is now present, this kinda sucks

---

### Post by RoeZ on 2008-01-23
I am now in Windows Vista and everything works here, all drives, all dvd drives, and I can burn dvd's. I kinda liked ubuntu but i think i will give up, unless anybody knows something i can try

---

### Post by RoeZ on 2008-01-25
Anyone please? i would like to give ubuntu another try, but not without my drives :)

---

### Post by RoeZ on 2008-02-12
I went back to Vista, grub started Ubuntu automatically because i forgot to choose Vista, i tought, well i'm in ubuntu now anyway, let's insert a cd, it works, i tought that's nice but i still need to be able to load ubuntu from cd, i tought let's try that, that also worked, all problems fixed without me doing anything, kinda strange i think

---

