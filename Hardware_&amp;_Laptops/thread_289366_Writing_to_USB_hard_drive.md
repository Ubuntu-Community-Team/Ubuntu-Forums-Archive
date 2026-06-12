---
title: "Writing to USB hard drive"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by jalefkowit on 2006-10-30
Hey everybody...

I picked up my first external hard drive over the weekend -- a Western Digital "My Book" 250GB unit, formatted as FAT32, that connects up via USB2.  Ever since I got it home, I've been trying to set it up so that I can write to it ](*,) 

When I plug it in, Kubuntu Edgy automagically recognizes it and mounts it as /media/My Book.  So far so good.  I can go into the drive and browse around all I want.  But when I try to write anything, I get a "read only" error.

A little poking around the forums and I discover that this is my cue to learn about fstab.  So I start trying the various suggestions I find.  I set it up in fstab with the "user" and "rw" options.  Still no luck.  I set the UID and GID options to my user and group numbers. *Still* no luck.  I stop using "defaults" and try turning on suid, exec, dev.  *Still* no luck.

The best I have been able to do is to get write permissions for a short period of time -- and then suddenly the permissions go away and I get the read-only errors again.  My guess is that this is happening because I did something else that got sudo permissions activated in the keyring, so I was inheriting root.  Then the keyring expires and I'm back to my standard privileges, so, failure.  (Note that this is an end-of-my-tether guess, so I'm open to correction.)

Somebody help! I know there has to be a way to get this to work. I refuse to consider any other possibilities. [-( 

Here's what I get when I run fdisk -l as root:

```
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         765     6144831    b  W95 FAT32
/dev/hda2             766        7859    56982555    f  W95 Ext'd (LBA)
/dev/hda3            7860        9772    15366172+  83  Linux
/dev/hda4            9773        9964     1542240   82  Linux swap / Solaris
/dev/hda5             766        7859    56982523+   7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)
```

(/dev/sda1 is the My Book.)

And here's what I currently have when I run mount:

```
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/hda1 on /media/hda1 type vfat (rw,utf8,umask=007,uid=0,gid=46)
/dev/hda5 on /media/hda5 type ntfs (rw,nls=utf8,umask=007,uid=0,gid=46)
/dev/sda1 on /media/My Book type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

```

Any thoughts?

---

### Post by jalefkowit on 2006-10-31
I hate to do this, but since nobody's responded yet... *bump*

---

### Post by sebastfr on 2006-11-01
> **jalefkowit said:**
> Hey everybody...

And here's what I currently have when I run mount:

```
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/hda1 on /media/hda1 type vfat (rw,utf8,umask=007,uid=0,gid=46)
/dev/hda5 on /media/hda5 type ntfs (rw,nls=utf8,umask=007,uid=0,gid=46)
/dev/sda1 on /media/My Book type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

```

Any thoughts?


Hiya...

Can you write to your disk when you're root?

I think your 'umask' is wrong basically... should be something like '000'  if you want to give everybody Read/Write/eXecute. This is an option you can pass to mount (when you mount your drive)

hope this helps

seb.

---

### Post by red_Marvin on 2006-11-01
IIRC:
777 is the code for rwx for all users

Each digit represents a user type:
Left digit: owner
Middle digit: group
Right digit: other

The value of the digit is the sum of:
1: read
2: write
4: execute

So:
000: No rights except for root.
770: Owner and group have full rights (and root of course, that's the point of being root...)
777: All users have full permissions...

EDIT: Also the uid and gid are user/group identification numbers, which you can find out with the "users and groups" program

---

### Post by sebastfr on 2006-11-01
> **red_Marvin said:**
> IIRC:
777 is the code for rwx for all users

Each digit represents a user type:
Left digit: owner
Middle digit: group
Right digit: other

The value of the digit is the sum of:
1: read
2: write
3: execute

So:
000: No rights except for root.
770: Owner and group have full rights (and root of course, that's the point of being root...)
777: All users have full permissions...

EDIT: Also the uid and gid are user/group identification numbers, which you can find out with the "users and groups" program


Nope not true... for mount it's a 'umask' which represents the rights users DO NOT HAVE (cf. 'man mount' for vfat), so it's exactly the opposite!!

000: rwx for everybody
...
777: nobody's got any rights....

seb


EDIT: and by the way, the permissions are represented in octal (0->7) so the value is the sum of :

1-read (2^0)
2-write (2^1)
4-execute (2^2) not '3'

hence 0 for no permissions, 7 for everything

And for the umask (which is the opposite of the permissions above):

1-no read
2-no write
4-no execute

hence 0 for all permissions, 7 for no permissions

:)

---

### Post by red_Marvin on 2006-11-01
I didn't know about the umask stuff (thanks for enlightening me :)) I thought it was the same as for chmodding...
Is there any special reason as to why it uses "inverted" permissions (exept that it should fit with the name (mask))?

Anyway, the '3' that should be a '4' was a simple typo, I'll fix that.

[SIZE="1"]EDIT: What do you mean by octal?
Each user has three flags with two values, that would make them binary, no? That the maximum value equals seven is only a consequence of the number of flags and the number of possible states: 2^4-1 (AFAIK)[/SIZE]

---

### Post by sebastfr on 2006-11-01
he he I just found about it when I got the same problem as the creator of the thread!... no idea why it is inverted, the 'man' page just mention that it deals with permissions one does not have... weird... but why not?!

btw after re-reading my previous reply, sorry if I sounded cocky about it, I didn't meant to :)

seb

EDIT:

> 
EDIT: What do you mean by octal?
Each user has three flags with two values, that would make them binary, no? That the maximum value equals seven is only a consequence of the number of flags and the number of possible states: 2^4-1 (AFAIK)


well each permission (owner, group, user) can have a value between 0 and 7 hence octal. if there were another flag beside r,w,x then the representation of the permission would be hexadecimal etc. And it's (2^3-1) but probably a typo again :)

From 'man chmod':

> 
chmod changes the permissions of each given file according to mode, which can be either a
symbolic  representation  of changes to make, or an octal number representing the bit pattern for the new permissions.


voila :)

---

### Post by jalefkowit on 2006-11-01
This is incredibly frustrating.

Yesterday, after much tinkering, I modified the relevant line in fstab to this:

```
/dev/sda1 /media/mybook vfat noauto,rw,users,umask=000 0 0
```

... and suddenly I had reliable, steady write access for hours.

Then I come home today, boot up, and find that I'm back to read-only again.  NOTHING has changed.

WTF??? ](*,) 

It's things like this that make me want to go back to Windows.  Almost ;)

---

### Post by red_Marvin on 2006-11-02
Have your fstab changed?
are you logged in as another user?  Mounting as another user...

-----
EDIT I think I see what you mean by octal, now.
anyway the '4' comes from me converting from 'counting starts at zero' to 'counting starts at one' wrongly...
-----

---

### Post by jalefkowit on 2006-11-02
No, no, and no.  Still logged in as me, still mounting as me, fstab is unchanged.

---

### Post by sebastfr on 2006-11-02
> **jalefkowit said:**
> This is incredibly frustrating.

Yesterday, after much tinkering, I modified the relevant line in fstab to this:

```
/dev/sda1 /media/mybook vfat noauto,rw,users,umask=000 0 0
```

... and suddenly I had reliable, steady write access for hours.

Then I come home today, boot up, and find that I'm back to read-only again.  NOTHING has changed.

WTF??? ](*,) 

It's things like this that make me want to go back to Windows.  Almost ;)


Hey...

When you're back to read-only, how is your filesystem mounted? Is the 'umask' back to '077'? is it '000'?

Maybe when you re-plugged your usb drive it mapped to /dev/sd[b,c,d] ? That happened to me a few times on a similar configuration.

Seb

PS: i understand your frustration :)

---

### Post by jalefkowit on 2006-11-02
> When you're back to read-only, how is your filesystem mounted? Is the 'umask' back to '077'? is it '000'?

It is '000' (I'll double check via /etc/mtab when I get home, but this is what I remember).

I read in a few places that the value of umask should be a FOUR digit number, rather than three, so I've also tried '0000'.  This does not appear to make any difference.

> Maybe when you re-plugged your usb drive it mapped to /dev/sd[b,c,d] ? That happened to me a few times on a similar configuration.

Nope, it's consistently mapping to /dev/sda1.

One interesting thing is that sometimes, I can't get write permissions if I do ```
mount /dev/sda1
``` -- I have to do ```
sudo mount /dev/sda1
```.  Other times, it's the other way around.

---

### Post by jalefkowit on 2006-11-02
OK, I'm home and I just checked.  Here's what's currently in my fstab:

```
/dev/sda1 /media/mybook vfat umask=0000,uid=1000,gid=1000,noauto,rw,users,suid 0 0
```

And here's what shows up in /etc/mtab:

```
/dev/sda1 /media/mybook vfat rw,noexec,nodev,umask=0000,uid=1000,gid=1000 0 0
```

It's currently only letting me have write permissions if I mount with sudo.  There shouldn't be any reason for that as far as I can tell.  Any thoughts?

---

### Post by sebastfr on 2006-11-03
> **jalefkowit said:**
> OK, I'm home and I just checked.  Here's what's currently in my fstab:

```
/dev/sda1 /media/mybook vfat umask=0000,uid=1000,gid=1000,noauto,rw,users,suid 0 0
```

And here's what shows up in /etc/mtab:

```
/dev/sda1 /media/mybook vfat rw,noexec,nodev,umask=0000,uid=1000,gid=1000 0 0
```

It's currently only letting me have write permissions if I mount with sudo.  There shouldn't be any reason for that as far as I can tell.  Any thoughts?

Have you tried to set the 'fmask' (file mask) and 'dmask' (dir mask) options?

I just checked on my conf, and i don't touch at 'umask', I only set fmask and dmask to '000'... Can you try this (with sudo)?

Seb

---

### Post by jalefkowit on 2006-11-04
> I only set fmask and dmask to '000'... Can you try this (with sudo)?

Just tried it -- doesn't seem to make any difference.  I get write permissions for some variable-but-not-very-long period of time, then it falls back to non-write.

Grr!

---

### Post by sebastfr on 2006-11-06
Hmmm... running out of ideas really...

What about removing the uid,gid options?

seb

PS: btw don't you have some kind of automount? when I plug an external HD, a memory stick or a digital cam to my laptop, the system automatically mounts the device and gives me write access... is that not working on your machine?

---

### Post by larsemil on 2006-11-06
with my usb that mounts automaticly i had to do a chown user:group /media/ipod for write access...

---

### Post by jalefkowit on 2006-11-06
> PS: btw don't you have some kind of automount? when I plug an external HD, a memory stick or a digital cam to my laptop, the system automatically mounts the device and gives me write access... is that not working on your machine?

Oh, it automounts, all right.  But not with write access.  I get a nice automounted drive with that I can only read from. ](*,)

---

### Post by jalefkowit on 2006-11-07
OK, now things are really weird.  I have discovered a failsafe way to make the disk go from read-write mode to read-only mode after mounting: just open it in Konqueror.

Specifically, the steps are like this:

1) Mount external drive.  I've stripped the entry completely out of fstab, and have been using mount with options instead.  Using this gives me read-write access:

```
sudo mount /dev/sda1 /media/mybook -t vfat -o rw,users,umask=0000
```

2) To confirm writeable, open a text file on the disk, make changes, and try to write changes.  Changes are written.

```
vi /media/mybook/test.txt
```

3) Open Konqueror file browser and browse to /media/mybook.  Hit F5 key to ensure fresh view.

4) Try editing the text file again (by launching vi from the console with the same command as in #2).  Now the file is read-only.

WTF is Konqueror doing that throws the disk into read-only mode?

---

### Post by dannyboy79 on 2006-11-07
you need to completely remove the entry from your fstab because pmount automatically mounts removable devices with write status, per man pmount, read this: 
      pmount  ("policy mount") is a wrapper around the standard mount program
       which permits normal users to mount removable devices without a  matchâ
       ing /etc/fstab entry.

       pmount also supports encrypted devices which use dm-crypt and have LUKS
       metadata. If a LUKS-capable cryptsetup is installed, pmount will use it
       to  decrypt  the  device  first and mount the mapped unencrypted device
       instead.

       pmount is invoked like this:

       pmount device [ label ]

       This will mount device to a directory below /media  if  policy  is  met
       (see  below).  If label is given, the mount point will be /media/label,
       otherwise it will be /media/device.

       The   device   will   be   mounted   with    the    following    flags:
       async,atime,nodev,noexec,noauto,nosuid,user,rw

also, check out these threads and you can hopefully get your issue resolved. If you perform a search before posting a new thread there won't end up being tons of the same exact questions over and over.

[http://www.ubuntuforums.org/showthread.php?t=289016&highlight=usb](http://www.ubuntuforums.org/showthread.php?t=289016&highlight=usb)

[http://www.ubuntuforums.org/showthread.php?t=291849&highlight=usb](http://www.ubuntuforums.org/showthread.php?t=291849&highlight=usb)

---

### Post by jalefkowit on 2006-11-07
OK, I unmounted the drive, removed the entry from fstab, and remounted using

```
pmount /dev/sda1
```

instead of mount.

Thing is, I get the exact same behavior: drive mounts as writeable (in /media/sda1), but when I open it in Konqueror, it flips to read-only.  This is true even if pmount is invoked with the -w flag.

I'll go plow through those threads you cited but it doesn't look like pmount solves the problem (unless there's something I'm missing...?).

---

### Post by dannyboy79 on 2006-11-07
That sounds like a problem! i use gnome so I don't have that issue sorry I can't help you anymore. also, I was saying that if it's a removable device you shouldn't have to mount it all, if you plug it in, it should automagically appear on your desktop without having to so pmount blah blah.

---

### Post by jalefkowit on 2006-11-07
Yes, as I mentioned above it mounts automatically, but in read only mode.

---

### Post by dannyboy79 on 2006-11-07
> **jalefkowit said:**
> Yes, as I mentioned above it mounts automatically, but in read only mode.
alright well that's a problem then because that's not what it suppose to happen per man pmount. let's do some debugging, what does pmount -d /dev/sda1 return? keeping in mind that sda1 should be changed to match whatever is being automounted labeled. also, after you plug it in, please post the results of fdisk -l and your fstab.

---

### Post by jalefkowit on 2006-11-07
fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda3 -- converted during upgrade to edgy
UUID=a9b9c385-c396-487c-bf94-e2c02d337862 / ext3 nouser,defaults,errors=remount-
ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=1056-6E22 /media/hda1 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nou
ser 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=D8FCB253FCB22C1E /media/hda5 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,
auto,rw,nouser 0 1
# /dev/hda4 -- converted during upgrade to edgy
UUID=81ef299f-f8c8-47c7-aa4f-dba13c27ca26 none swap sw 0 0
/dev/hdc /media/cdrom0 iso9660 ro,noauto,user,exec 0 0
/dev/hdd /media/cdrom1 iso9660 rw,noauto,user,sync 0 0
```

fdisk -l:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)
```

pmount -d:

```

resolved /dev/sda1 to device /dev/sda1
mount point to be used: /media/sda1
no iocharset given, current locale encoding is UTF-8
locale encoding uses UTF-8, setting iocharset to 'utf8'
Cleaning lock directory /var/lock/pmount_dev_sda1
device_whitelist: checking /etc/pmount.allow...
device_whitlisted(): nothing matched, returning 0
find_sysfs_device: looking for sysfs directory for device 8:1
find_sysfs_device: checking whether /dev/sda1 is on /sys/block/sda (8:0)
find_sysfs_device: major device numbers match
find_sysfs_device: minor device numbers do not match, checking partitions...
find_sysfs_device: checking whether device /dev/sda1 matches partition 8:0
find_sysfs_device: checking whether device /dev/sda1 matches partition 8:1
find_sysfs_device: -> partition matches, belongs to block device /sys/block/sda
device_removable: corresponding block device for /dev/sda1 is /sys/block/sda
get_blockdev_attr: value of /sys/block/sda/removable == 0
find_bus_ancestry: device 0:0:0:0 (path /sys/devices/pci0000:00/0000:00:08.2/usb2/2-3/2-3.1/2-3.1:1.0/host0/target0:0:0/0:0:0:0, bus scsi) does not match, trying parent
find_bus_ancestry: device target0:0:0 (path /sys/devices/pci0000:00/0000:00:08.2/usb2/2-3/2-3.1/2-3.1:1.0/host0/target0:0:0, bus ) does not match, trying parent
find_bus_ancestry: device host0 (path /sys/devices/pci0000:00/0000:00:08.2/usb2/2-3/2-3.1/2-3.1:1.0/host0, bus ) does not match, trying parent
find_bus_ancestry: device 2-3.1:1.0 (path /sys/devices/pci0000:00/0000:00:08.2/usb2/2-3/2-3.1/2-3.1:1.0, bus usb) matches query, success
policy check passed
spawnv(): executing /sbin/cryptsetup '/sbin/cryptsetup' 'isLuks' '/dev/sda1'
spawn(): /sbin/cryptsetup terminated with status 255
device is not LUKS encrypted, or cryptsetup with LUKS support is not installed
locking mount point directory
mount point directory locked
spawnv(): executing /bin/mount '/bin/mount' '-t' 'udf' '-o' 'nosuid,nodev,user,async,atime,noexec,uid=1000,gid=1000,umask=000,iocharset=utf8' '/dev/sda1' '/media/sda1'
spawn(): /bin/mount terminated with status 32
spawnv(): executing /bin/mount '/bin/mount' '-t' 'udf' '-o' 'nosuid,nodev,user,async,atime,noexec,uid=1000,gid=1000,umask=000' '/dev/sda1' '/media/sda1'
spawn(): /bin/mount terminated with status 32
spawnv(): executing /bin/mount '/bin/mount' '-t' 'iso9660' '-o' 'nosuid,nodev,user,async,atime,noexec,uid=1000,gid=1000,iocharset=utf8' '/dev/sda1' '/media/sda1'
spawn(): /bin/mount terminated with status 32
spawnv(): executing /bin/mount '/bin/mount' '-t' 'iso9660' '-o' 'nosuid,nodev,user,async,atime,noexec,uid=1000,gid=1000' '/dev/sda1' '/media/sda1'
spawn(): /bin/mount terminated with status 32
spawnv(): executing /bin/mount '/bin/mount' '-t' 'vfat' '-o' 'nosuid,nodev,user,quiet,shortname=mixed,async,atime,noexec,uid=1000,gid=1000,umask=077,iocharset=utf8' '/dev/sda1' '/media/sda1'
spawn(): /bin/mount terminated with status 0
unlocking mount point directory
mount point directory unlocked
```

---

### Post by givré on 2006-11-09
Hi jalefkowit,

This seams to be rather something strange with konqueror.
To confirm that, i'd like to have more information.
1. Check that there is no refernce of /dev/sda1 in your fstab
2. Plug your usb device. Is it automouting ?
3. If yes, can you give me the output of :
```
mount #or /etc/mtab if you prefer
```
```
id
```
Check also that you have r/w on the drive :
On a terminal, go to the root of your usb device (probably /media/usbdisk)
Test if it's writable :
```
touch new
ls -l new
```
5. If no automount , can you give me the output of :
```
PMOUNT_DEBUG=1
pmount-hal /dev/sda1
```

Thanks

---

### Post by dannyboy79 on 2006-11-09
by simply reading a few posts back, I can answer almost all your questions and this isn't even my problem.

> **givré said:**
>  Hi jalefkowit,
1. Check that there is no refernce of /dev/sda1 in your fstab
he posted the output of fstab, here it is:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda3 -- converted during upgrade to edgy
UUID=a9b9c385-c396-487c-bf94-e2c02d337862 / ext3 nouser,defaults,errors=remount-
ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=1056-6E22 /media/hda1 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nou
ser 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=D8FCB253FCB22C1E /media/hda5 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,
auto,rw,nouser 0 1
# /dev/hda4 -- converted during upgrade to edgy
UUID=81ef299f-f8c8-47c7-aa4f-dba13c27ca26 none swap sw 0 0
/dev/hdc /media/cdrom0 iso9660 ro,noauto,user,exec 0 0
/dev/hdd /media/cdrom1 iso9660 rw,noauto,user,sync 0 0

> **givré said:**
>  2. Plug your usb device. Is it automouting ?
yes it is, he stated that here, Originally Posted by jalefkowit  
Yes, as I mentioned above it mounts automatically, but in read only mode.  
 
> **givré said:**
> 
3. If yes, can you give me the output of :
```
mount #or /etc/mtab if you prefer
```
```
id
``` 
this one unfortunately he didn't already answer so he'll have to give ya this answer. 

> **givré said:**
> 
Check also that you have r/w on the drive :
On a terminal, go to the root of your usb device (probably /media/usbdisk)
Test if it's writable :
```
touch new
ls -l new
```  

he has already stated a couple times, it is not writable, see this, Originally Posted by jalefkowit  
Yes, as I mentioned above it mounts automatically, but in read only mode. 
 
> **givré said:**
> 
5. If no automount , can you give me the output of :
```
PMOUNT_DEBUG=1
pmount-hal /dev/sda1
```

Thanks 

it is automounting per the statement I have already quoted a few times, and his debug ( i think that's what the below info is?)info has already been pasted, here ya go:
resolved /dev/sda1 to device /dev/sda1
mount point to be used: /media/sda1
no iocharset given, current locale encoding is UTF-8
locale encoding uses UTF-8, setting iocharset to 'utf8'
Cleaning lock directory /var/lock/pmount_dev_sda1
device_whitelist: checking /etc/pmount.allow...
device_whitlisted(): nothing matched, returning 0
find_sysfs_device: looking for sysfs directory for device 8:1
find_sysfs_device: checking whether /dev/sda1 is on /sys/block/sda (8:0)
find_sysfs_device: major device numbers match
find_sysfs_device: minor device numbers do not match, checking partitions...
find_sysfs_device: checking whether device /dev/sda1 matches partition 8:0
find_sysfs_device: checking whether device /dev/sda1 matches partition 8:1
find_sysfs_device: -> partition matches, belongs to block device /sys/block/sda
device_removable: corresponding block device for /dev/sda1 is /sys/block/sda
get_blockdev_attr: value of /sys/block/sda/removable == 0
find_bus_ancestry: device 0:0:0:0 (path /sys/devices/pci0000:00/0000:00:08.2/usb2/2-3/2-3.1/2-3.1:1.0/host0/target0:0:0/0:0:0:0, bus scsi) does not match, trying parent
find_bus_ancestry: device target0:0:0 (path /sys/devices/pci0000:00/0000:00:08.2/usb2/2-3/2-3.1/2-3.1:1.0/host0/target0:0:0, bus ) does not match, trying parent
find_bus_ancestry: device host0 (path /sys/devices/pci0000:00/0000:00:08.2/usb2/2-3/2-3.1/2-3.1:1.0/host0, bus ) does not match, trying parent
find_bus_ancestry: device 2-3.1:1.0 (path /sys/devices/pci0000:00/0000:00:08.2/usb2/2-3/2-3.1/2-3.1:1.0, bus usb) matches query, success
policy check passed
spawnv(): executing /sbin/cryptsetup '/sbin/cryptsetup' 'isLuks' '/dev/sda1'
spawn(): /sbin/cryptsetup terminated with status 255
device is not LUKS encrypted, or cryptsetup with LUKS support is not installed
locking mount point directory
mount point directory locked
spawnv(): executing /bin/mount '/bin/mount' '-t' 'udf' '-o' 'nosuid,nodev,user,async,atime,noexec,uid=1000,gid=1000,umask=000,iocharset=utf8' '/dev/sda1' '/media/sda1'
spawn(): /bin/mount terminated with status 32
spawnv(): executing /bin/mount '/bin/mount' '-t' 'udf' '-o' 'nosuid,nodev,user,async,atime,noexec,uid=1000,gid=1000,umask=000' '/dev/sda1' '/media/sda1'
spawn(): /bin/mount terminated with status 32
spawnv(): executing /bin/mount '/bin/mount' '-t' 'iso9660' '-o' 'nosuid,nodev,user,async,atime,noexec,uid=1000,gid=1000,iocharset=utf8' '/dev/sda1' '/media/sda1'
spawn(): /bin/mount terminated with status 32
spawnv(): executing /bin/mount '/bin/mount' '-t' 'iso9660' '-o' 'nosuid,nodev,user,async,atime,noexec,uid=1000,gid=1000' '/dev/sda1' '/media/sda1'
spawn(): /bin/mount terminated with status 32
spawnv(): executing /bin/mount '/bin/mount' '-t' 'vfat' '-o' 'nosuid,nodev,user,quiet,shortname=mixed,async,atime,noexec,uid=1000,gid=1000,umask=077,iocharset=utf8' '/dev/sda1' '/media/sda1'
spawn(): /bin/mount terminated with status 0
unlocking mount point directory
mount point directory unlocked


Hopefully you can help him with this because if so, you'll most likely be helping a lot of others, this is a hot issue lately and it's very weird since you state that thjis is suppose to "just work" and it doesn't. we're not just talking about 1 or  2 people either, they are more than that as I said, just search and you'll see

---

### Post by givré on 2006-11-09
dannyboy79, when you do a debugging session, you have to do it entirely, from the start to the end, not few part there, and other part there. Can you please let me doing that. Thanks.

My question are rather simple. jalefkowit, can you reply to all of them in this order, thanks.

---

### Post by dannyboy79 on 2006-11-09
> **givré said:**
>  dannyboy79, when you do a debugging session, you have to do it entirely, from the start to the end, not few part there, and other part there. Can you please let me doing that. Thanks.
i am not sure what you are saying here, all i was pointing out is that he already posted the output from pmount -d which according to what you posted in another thread (you stated that PMOUNT_DEBUG=1
pmount-hal /dev/sda1 was more or less the same as pmount -d, i thought that's what you stated anyway?) is what he posted once, then i posted it again since you asked for it. 

> **givré said:**
> My question are rather simple. jalefkowit, can you reply to all of them in this order, thanks. 

you're right, i just don't understand why you're asking him for something he already posted above?? I merely copied what he already posted which ARE the answers to your questions.

---

### Post by givré on 2006-11-09
I don't know why i always have to justify me in full details, because i already reply to this question :
```
when you do a debugging session, you have to do it entirely, from the start to the end, not few part there, and other part there.
```
When you fall into a problem, you usually try a lot of different things, and some of them can affect others, even if you don't know it. So when you start debugging, you have to be sure that all is ok, and that the config is set correctly. 
Do you know what mean Q & A ?

For the other question, pmount & pmount-hal are slightly different, in fact the one use by the system is pmount-hal, but 
- in any way, if pmount fail, pmount-hal will also fails. So it's also interesting to have the output of pmout
- pmount is more intuitive to use in debug mode, you don't have to set a user variable, just need an other option, so it's more easy to remember.

---

### Post by dannyboy79 on 2006-11-09
> **givré said:**
> I don't know why i always have to justify me in full details, because i already reply to this question :
```
when you do a debugging session, you have to do it entirely, from the start to the end, not few part there, and other part there.
```

i didn't ask that you justify yourself, i basically asked how does one go about what you are asking us to do? If what he did by issuing pmount -d isn't a debugging session, than please inform us how to one because I myself am a newbie and I have no idea how to do a debugging session. "start to the end" are you saying that I have to shut down and start a new session? is there a debugging session that'll show up in the list when a person goes to select session?

---

### Post by givré on 2006-11-09
> **dannyboy79 said:**
> If what he did by issuing pmount -d isn't a debugging session
Right, but the result wasn't useful, and you have to know why you do that before asking it.
> **dannyboy79 said:**
> than please inform us how to one because I myself am a newbie and I have no idea how to do a debugging session. 
I'll start a wiki page on how to debug external device.
> **dannyboy79 said:**
> "start to the end" are you saying that I have to shut down and start a new session? 
That's not the point. You just have to take all the paramaters in case.
> **dannyboy79 said:**
> is there a debugging session that'll show up in the list when a person goes to select session?
Of course not. That's also not the point.

EDIT : There is already a lot of useful info on the wiki :
[https://wiki.ubuntu.com/DebuggingProcedures](https://wiki.ubuntu.com/DebuggingProcedures)

---

### Post by dannyboy79 on 2006-11-09
> **givré said:**
> Right, but the result wasn't useful, and you have to know why you do that before asking it.
 
I'll start a wiki page on how to debug external device.
 
That's not the point. You just have to take all the paramaters in case.

Of course not. That's also not the point.

ok, well you're talking as if i know what debugging is? i only asked the questions because I don't know what debugging is and I am asking you these questions so that I can learn. you say that some of my questions "aren't the point", well what is the point? as I stated I am trying to learn here.

---

### Post by givré on 2006-11-09
> **dannyboy79 said:**
> ok, well you're talking as if i know what debugging is? i only asked the questions because I don't know what debugging is and I am asking you these questions so that I can learn.
debugging is not more trying to find why a program don't work as expected, and trying to find a way to resolve the problem.
But what we can only do in this forum is to find if the problem is due to the user. If you find a bug in a program, it's not the place to ask for help, you should file a bug in launchpad : [https://launchpad.net/distros/ubuntu/](https://launchpad.net/distros/ubuntu/) it's where the developers can help you.
> **dannyboy79 said:**
>  you say that some of my questions "aren't the point", well what is the point? as I stated I am trying to learn here.
That's not the point just because you can ask people to do something only when you know why you do it, what is the expected result, and when it don't work properly. You'll probably want to ask 'how do i learn that', and i'll reply you, simply like we learn everything, by experience.
Be curious, ask, and you'll learn a lot.

But all that is a bit off topic,
jalefkowit, if you're removable device still don't work properly, just follow the step i asked you to do before the start of this discussion, sorry ;)

---

### Post by jalefkowit on 2006-11-09
> jalefkowit, if you're removable device still don't work properly, just follow the step i asked you to do before the start of this discussion, sorry 

OK -- I'm at work now but when I get home I'll give it a shot and post the results.

---

### Post by jalefkowit on 2006-11-09
OK, here goes nothing.

> 1. Check that there is no refernce of /dev/sda1 in your fstab

Done. fstab: 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda3 -- converted during upgrade to edgy
UUID=a9b9c385-c396-487c-bf94-e2c02d337862 / ext3 nouser,defaults,errors=remount-
ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=1056-6E22 /media/hda1 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nou
ser 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=D8FCB253FCB22C1E /media/hda5 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,
auto,rw,nouser 0 1
# /dev/hda4 -- converted during upgrade to edgy
UUID=81ef299f-f8c8-47c7-aa4f-dba13c27ca26 none swap sw 0 0
/dev/hdc /media/cdrom0 iso9660 ro,noauto,user,exec 0 0
/dev/hdd /media/cdrom1 iso9660 rw,noauto,user,sync 0 0
```

> 2. Plug your usb device. Is it automouting ?

Yes, on /media/My Book.

```
3. If yes, can you give me the output of /etc/mtab:
```

Yup:

```
/dev/hda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/hda1 /media/hda1 vfat rw,utf8,umask=007,uid=0,gid=46 0 0
/dev/hda5 /media/hda5 ntfs rw,nls=utf8,umask=007,uid=0,gid=46 0 0
/dev/sda1 /media/My\040Book vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,
gid=1000,umask=077,iocharset=utf8 0 0
```

> Check also that you have r/w on the drive :
On a terminal, go to the root of your usb device (probably /media/usbdisk)
Test if it's writable :

Here's what I get when I do a "touch new" (or try to touch any file on the USB disk):

```
touch: cannot touch `new': Read-only file system
```

I skipped step 5 since it automounted.

Hope this helps!

---

### Post by dannyboy79 on 2006-11-09
this may sound stupid, but can you rename the drive in winbloz from My Book to My-Book?  it might not matter but it also doesn't hurt to try anything at this point.

---

### Post by givré on 2006-11-10
dannyboy79, normally space should not be an issue, but that's may be an idea

did you test that ?

But before, could you do some more check, your problem is rather strange :
Device plug, can you give me :
```
ls -l /media
id         #you forgot this one last time
```

---

### Post by jalefkowit on 2006-11-10
> did you test that ?

I did try setting fstab so it would mount to /media/mybook instead of /media/My Book.  Didn't seem to make a difference.

ls -l /media gives:

```
lrwxrwxrwx  1 root       root           6 2006-06-07 18:11 cdrom -> cdrom0
drwxr-xr-x  2 root       root        4096 2006-06-07 18:11 cdrom0
drwxr-xr-x  2 root       root        4096 2006-11-01 21:19 cdrom1
drwxrwx--- 43 root       plugdev     8192 1969-12-31 19:00 hda1
dr-xr-x---  1 root       plugdev     8192 2006-11-05 22:17 hda5
drwxrwxr-x  2 root       plugdev     4096 2006-11-07 14:24 mybook
drwx------ 12 jlefkowitz jlefkowitz 32768 1969-12-31 19:00 My Book
drwxr-xr-x  2 root       root        4096 2006-06-11 21:31 windows
```

id gives:

```
uid=1000(jlefkowitz) gid=1000(jlefkowitz) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),111(admin),1000(jlefkowitz)
```

---

### Post by givré on 2006-11-10
I'd rather think that your drive is simply read only.
Did it works correctly in windows or whatever ?

---

### Post by dannyboy79 on 2006-11-10
> **jalefkowit said:**
> I did try setting fstab so it would mount to /media/mybook instead of /media/My Book.  Didn't seem to make a difference.

ls -l /media gives:

```
lrwxrwxrwx  1 root       root           6 2006-06-07 18:11 cdrom -> cdrom0
drwxr-xr-x  2 root       root        4096 2006-06-07 18:11 cdrom0
drwxr-xr-x  2 root       root        4096 2006-11-01 21:19 cdrom1
drwxrwx--- 43 root       plugdev     8192 1969-12-31 19:00 hda1
dr-xr-x---  1 root       plugdev     8192 2006-11-05 22:17 hda5
drwxrwxr-x  2 root       plugdev     4096 2006-11-07 14:24 mybook
drwx------ 12 jlefkowitz jlefkowitz 32768 1969-12-31 19:00 My Book
drwxr-xr-x  2 root       root        4096 2006-06-11 21:31 windows
```

id gives:

```
uid=1000(jlefkowitz) gid=1000(jlefkowitz) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),111(admin),1000(jlefkowitz)
```

that's not what I suggested. the mount point in media is being created by the system when you plug it in because there is no fstab entry you told us. so if you could rename the drive in windows, since it appears you named it My Book, to begin with, lets just try it to see if that changes anything. it couldn't hurt as it appears as though givre and myself are running out of ideas.

---

### Post by jalefkowit on 2006-11-10
> I'd rather think that your drive is simply read only.
Did it works correctly in windows or whatever ?

It does work fine in Windows 2000. 

Also, as I mentioned above, I did eventually find out how to get it to be read/write on initial mount -- automount doesn't do it, but it's possible to do it via fstab.  But as soon as I try to browse it in Konqueror it switches to read only.

Given this I'd be very skeptical that it's a problem with the hardware.

---

### Post by dannyboy79 on 2006-11-10
ok, you still haven't mentioned if you tried my suggestion? Maybe Konquorer has a problem with spaces, i don't know. i really want to know what the solution is for automounting upon plugging it in and being able to write to it W/O using fstab. givre swears it works, which he is correct, that does work for me, but it doesn't work for you and many others so what does that mean and how do we solve it?

---

### Post by givré on 2006-11-10
> **dannyboy79 said:**
> givre swears it works, which he is correct, that does work for me, but it doesn't work for you and many others so what does that mean and how do we solve it?
That's not that many people. You forget that it is a help & support forum, so of course people have problems, but the general point is that it woeks ;) .

jalefkowit, 
* try the tips of dannyboy (remove space from the label of your drive)
* Alternatively, try the following :
1st step :
```
mkdir test
sudo umount /dev/sda1
sudo mount /dev/sda1 test -o uid=1000,gid=1000,umask=077
ll
touch test/new
```
If it's working,
2nd step :
```
sudo umount /dev/sda1
pmount /dev/sda1 test
ll
touch test/new
```

---

### Post by jalefkowit on 2006-11-10
OK, both steps 1 and 2 work.  I'm not sure what they're supposed to accomplish, though -- are they supposed to be setting a mount point for /dev/sda1 in this new directory "test"? Because if I navigate into "test" after mounting, I don't get the contents of the drive -- just an empty directory (except for the file "new" created by touch).

Maybe a syntax error in your instructions?

---

### Post by dannyboy79 on 2006-11-10
> **jalefkowit said:**
> OK, both steps 1 and 2 work.  I'm not sure what they're supposed to accomplish, though -- are they supposed to be setting a mount point for /dev/sda1 in this new directory "test"? Because if I navigate into "test" after mounting, I don't get the contents of the drive -- just an empty directory (except for the file "new" created by touch).

Maybe a syntax error in your instructions?

if only the new file touch is on the folder than it doesn't appear to be working, if it did, you would see your entire sda1 partition correct? what he is trying to do I believe is rule out what command work and what don't. do a poperties within nautilus of the test folder and tell me how many gb it is, does that amount match the size of your sda1 partition?

---

### Post by givré on 2006-11-10
> **jalefkowit said:**
> OK, both steps 1 and 2 work.  I'm not sure what they're supposed to accomplish, though -- are they supposed to be setting a mount point for /dev/sda1 in this new directory "test"? Because if I navigate into "test" after mounting, I don't get the contents of the drive -- just an empty directory (except for the file "new" created by touch).

Maybe a syntax error in your instructions?
Well, I'm stupid :rolleyes: .
So The second instruction should be :
```
sudo umount /dev/sda1
pmount /dev/sda1 test
ll
touch /media/test/new
```

Why i ask you to do that. Apparently you get it working manually, so the first step is to mount it manually but with the options use by pmount,to know if the problem is due to the options used, the second step is to simply use pmount but with a different label (test) which don't have space on it, to know if the problem is due to the space.

---

### Post by jalefkowit on 2006-11-10
OK.  It mounts fine in /media/test, and I can touch the file fine.

(My shell doesn't recognize "ll" as a command -- I assumed that was a shortcut for ls -l.  Let me know if that's not the case.)

BUT -- browse /media/test in Konqueror, and then try touch-ing the file again, and I get
 
```
touch: cannot touch `/media/test/new': Read-only file system
```

I'm suspecting now that I wasn't really understanding the problem at first.  Maybe the drive _was_ mounting correctly, but it only _seemed_ like it wasn't because the write privileges were being removed because the first thing I always tried was moving some files onto the disk via drag & drop in Konq.

(To be clear -- the write permissions are not just disabled in Konq -- once I view the drive in Konq I can't write from anywhere, including the terminal.)

Which raises the question of why that would happen...

---

### Post by givré on 2006-11-10
```
(My shell doesn't recognize "ll" as a command -- I assumed that was a shortcut for ls -l. Let me know if that's not the case.)
```
I'm really stupid ](*,) :rolleyes: That's right. I use it so often that i forget that's it's not default.

Ok, all that is really interesting. So to summarize :
- This is not an options problem
- This is not a label problem (even if we don't bring strong evidence to be sure of that, i'm pretty that it's not.
- The problem start at soon as you browse it with konqueror.

At this point, i'm sure you have already test a lot's of things, but what's could be interesting to know is on what the permission is change (not sure my sentence is english ;) ).
So let's the things mounting automaticly, browse it with konqueror, and check the permission in a terminal :
```
ls -l /media
```

---

### Post by jalefkowit on 2006-11-10
OK.  I cleared out my old mount points in /media, so I'd be starting fresh.

Here's the output of ls -l in /media after doing so:

```
drwxr-xr-x  7 root root    4096 2006-11-10 16:51 .
drwxr-xr-x 22 root root    4096 2006-10-29 15:19 ..
lrwxrwxrwx  1 root root       6 2006-06-07 18:11 cdrom -> cdrom0
drwxr-xr-x  2 root root    4096 2006-06-07 18:11 cdrom0
drwxr-xr-x  2 root root    4096 2006-11-01 21:19 cdrom1
drwxrwx--- 43 root plugdev 8192 1969-12-31 19:00 hda1
dr-xr-x---  1 root plugdev 8192 2006-11-05 22:17 hda5
lrwxrwxrwx  1 root root      42 2006-10-05 23:54 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwxr-xr-x  2 root root    4096 2006-06-11 21:31 windows
```

And here's the output of ls -l in /media after plugging the HD back in and having it automount:

```
drwxr-xr-x  8 root       root        4096 2006-11-10 16:53 .
drwxr-xr-x 22 root       root        4096 2006-10-29 15:19 ..
lrwxrwxrwx  1 root       root           6 2006-06-07 18:11 cdrom -> cdrom0
drwxr-xr-x  2 root       root        4096 2006-06-07 18:11 cdrom0
drwxr-xr-x  2 root       root        4096 2006-11-01 21:19 cdrom1
drwxrwx--- 43 root       plugdev     8192 1969-12-31 19:00 hda1
dr-xr-x---  1 root       plugdev     8192 2006-11-05 22:17 hda5
lrwxrwxrwx  1 root       root          42 2006-10-05 23:54 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwx------ 13 jlefkowitz jlefkowitz 32768 1969-12-31 19:00 My Book
drwxr-xr-x  2 root       root        4096 2006-06-11 21:31 windows
```

It automounted as read-only. BUT -- this could be the same Konqueror issue, because when Kubuntu automounts the drive it automatically opens a Konq window showing the drive's contents.  So that might flip the drive into read-only mode, the same way it does when I manually browse there after manually mounting the drive...

---

### Post by givré on 2006-11-10
> **jalefkowit said:**
> ```

d**rw**x------ 13 jlefkowitz jlefkowitz 32768 1969-12-31 19:00 My Book
```

It automounted as read-only. BUT -- this could be the same Konqueror issue, because when Kubuntu automounts the drive it automatically opens a Konq window showing the drive's contents.  So that might flip the drive into read-only mode, the same way it does when I manually browse there after manually mounting the drive...
Hum, it's really strange, because this show clearly that the drive stay rw even after you browse it with konq, but you can't write on it.
To be fair, i have no clue what's happening there. I think you should file a bug on launchpad.

Did you try some alternatives, like thunar ?
You can mount the drive in the terminal with pmount, and try to browse it using thunar. That could show if it's a konqueror problem, or a more general problem.

---

### Post by dannyboy79 on 2006-11-10
yeah but the problem is that since he has kde, konquerer is installed by default so everytime he plugs in his usb drive, konquerer automagically opens up to the that mount point which in turn makes it not writable. so he would have to uninstall konquerer which i think then would uninstall kde. i have a way myabe to help him, givre, is there a way you can help him configure konquerer to not automagically open up when a usb hdd is plugged in? i can't help with them, I wouldn't know what to change? that would be the only way to see if this is a konquerer problem or something else. this is very weird, i mean aren;t there plenty of kde users that plug in usb hdd's???? something is very weird here!

---

### Post by givré on 2006-11-10
Of course it's possible to disable the open up (is it english ?) of konqueror. It's a long time that i didn't used kde, so i don't really remember where, and lot's of things change since that time. Somewhere in kcontrol, there should be something about that.

> this is very weird, i mean aren;t there plenty of kde users that plug in usb hdd's???? something is very weird here!
Don't do conclusion too quickly ;) . I know a lot of kde users that don't have this problem. So it might be more a specific problem.

Two last things, 
1. can you look at 
```
dmesg |tail 
```
when you have the "Read-only file system" error (the first time of course).

2. What locale do you use ?
```
locale
```

Thanks

---

### Post by jalefkowit on 2006-11-11
Sure thing.  First, I reported this in Launchpad to see if the devs have any insight. Bug report here:

[https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/71284](https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/71284)

Now to your questions.  dmesg | tail gives:

```
[17179631.272000] Bluetooth: L2CAP ver 2.8
[17179631.272000] Bluetooth: L2CAP socket layer initialized
[17179631.544000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179631.736000] Bluetooth: RFCOMM socket layer initialized
[17179631.736000] Bluetooth: RFCOMM TTY layer initialized
[17179631.736000] Bluetooth: RFCOMM ver 1.7
[17183293.756000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17183798.908000] FAT: Filesystem panic (dev sda1)
[17183798.908000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[17183798.908000]     File system has been set read-only
```

AHA!  Those last couple of lines are interesting.  Any idea what "invalid cluster chain" means?

locale gives:

```
LANG=en_US.UTF-8
LANGUAGE=en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

---

### Post by jalefkowit on 2006-11-11
I think I may finally have the problem licked! :KS 

I did some Googling around the error message I found in dmesg (" fat_get_cluster: invalid cluster chain"), and while I didn't find anything specific addressing my problem, I *did* find a page where someone was extolling the virtues of [dosfsck]("http://www.die.net/doc/linux/man/man8/dosfsck.8.html") (a tool I'd never heard of before) for fixing problems with FAT volumes.

So I crossed my fingers, dosfsck'd the USB hard drive, and started a new session.  Hey presto, the drive automounted, and it was writable -- even after I browsed around it in Konqueror!

The moral of the story: be sure you fsck your drives before you go looking for why they're not working :-D

Thanks so much to givré and dannyboy79 for helping me figure this out!  I owe you both a beer :-D

---

### Post by dannyboy79 on 2006-11-11
i am very happy you got it!!! more thanks goes to givre, he really knows is stuff and what to ask as far as output and troubleshooting it, make sure you back to launchpad and post the solution. great job for sticking this out.

---

