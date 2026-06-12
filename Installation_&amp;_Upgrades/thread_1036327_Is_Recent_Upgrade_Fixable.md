---
title: "Is Recent Upgrade Fixable?"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by Virgo53 on 2009-01-10
Hi All, 

I recently upgraded from Dapper to Hardy, but not without some
issues...like plagued with no automount of my USB NTFS hard drive, cannot mount it manually since I do not have permission to do so.

I edited the fstab line pertaining to it, but NTFS configuration
changed it. Now during bootup, the following displays:

.:195: Can't open /etc/default/rcS
error: '/etc/init.d/rc' exited outside the expected code flow.
init: rc2 main process (2934) terminated with status 2
:confused:

---

### Post by mikewhatever on 2009-01-11
Why don't you post the content of your fstab, <cat /etc/fstab>.

---

### Post by Virgo53 on 2009-01-12
The results of /etc/fstab:

#<filesystem>  <mount point>  <type>  <options>  <dump>  <pass>

proc  /proc proc defaults 0 0

# Entry for /dev/sda3 :
UUID= d49aaf25-2fc8-41f6-84a7-e1f2a0dd2f4c / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1

# Entry for /dev/sda1 :
UUID= 0FAB-7EE1 /media/hda1 vfat defaults,utf8,umask=007,uid=0,
gid=46,auto,rw,nouser 0 1

# Entry for /dev/sda2 :
UUID= 386C96CE6C9685F2 media/hda2 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1

# Entry for /dev/sda4 :
UUID= 7fd62120-c4e2-4cb3-bb3b-7e4d36652d24 none swap sw 0 0

# Entry for /dev/sdb1 :
UUID= 55D123D9E79ABF54 media/sde1 ntfs umask=222,utf8 0 0

---

### Post by mikewhatever on 2009-01-12
You seem to have two ntfs entries, which one's giving you problems?
Not sure it's relevavnt, but media/hda2 and media/sde1 are not valid mount points, /media/hda2 and /media/sde1 are.

---

### Post by Virgo53 on 2009-01-12
sda3 (ubuntu)
sda1 (windows recovery)
sda2 (windows xp pro)-ntfs
sda4 (linux swap)
sdb1 (usb hard drive)-ntfs

The last entry, sdb1 is the problem;

Originally, the last entry read:

/dev/sde1 /media/sde1 ntfs uid=1000,gid=1000auto,rw,owner,
quiet 0 0

I edited it to read:

/dev/sde1 /media/sde1 ntfs-3g auto,users,uid=1000,gid=100,
dmask=027,fmask=137,locale-en_US.utf8 0 0

But ntfs configuration changed it for whatever reason to read:

/dev/sdb1 /media/sde1 ntfs umask=222,utf8 0 0

---

### Post by mikewhatever on 2009-01-14
I must confess, I don't know what ntfs configuration is. Is it a program?

---

### Post by Archmage on 2009-01-14
Kindly note that ntfs-3g is an extra program that needs to be installed. But now you can mount ntfs without the program.

I would suggest to put a # before the entry for the external harddrive, go into Windows, safely remove the hardware, than shutdown Windows, remove the usb-drive, start in Ubuntu and than plug in the drive. This way it should be detected automatical.

(If it isn't detect automatical it seems that it hasn't disconnected "clean" in Windows and/or Ubuntu. If this happen Ubuntu wont mount it.)

---

### Post by Virgo53 on 2009-01-15
Archmage,

  Your suggestion currently is not possible since at the

present time, I am not able to boot into Ubuntu- unless

there is a way to it that I am not aware of. :confused:

---

### Post by mikewhatever on 2009-01-16
A live cd, and I was dead serious about 'ntfs configurations', what is it?

---

### Post by Virgo53 on 2009-01-16
Mikewhatever,

Yes, I'm thinking that a LiveCD may be what is needed to get

everything straightened out. For answers about NTFS, see:

[URL="http://www.ntfs-3g.org/[/URL]

---

### Post by Virgo53 on 2009-01-18
Update: The LiveCD I downloaded and burned as an iso file and installed

after formatting the previous Hardy installation got everything

rockin' & rollin'! :guitar:

I guess the only way to view or print any files from my Windows partition

is to just reboot into Windows, because I have no intentions of editing

any more system files in Ubuntu in order to change permissions to access

files that "belong to root". Running gksu nautilus did not resolve it,

and I certainly do not want to hose my new installation!

---

