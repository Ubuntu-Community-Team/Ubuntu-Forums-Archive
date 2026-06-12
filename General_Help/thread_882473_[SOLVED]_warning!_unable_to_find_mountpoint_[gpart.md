---
title: "[SOLVED] warning! unable to find mountpoint [gparted error]"
date: 2008-08-07
forum: General Help
---

### Post by dreadmeat on 2008-08-07
i've tripped over this error posted in a few places: here, LQ and gparted forums.
none have been answered!

gparted error = > warning
unable to find mountpoint
unable to read the contents of this filesystem!
because of this some operations may be unavailable.
screenshot = edited

fstab = > # <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=aab70474-924a-43c7-9192-822e8bbb03af / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=dfa70845-551c-4c2c-a339-e7d3ca5d94b1 none swap sw 0 0
#os
/dev/sda1 / ext3 defaults 0 1
#odd
/dev/scd0 /media/cdrom0 udf,iso9660 users,noauto,exec,utf8,sync 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 users,noauto,exec,utf8,sync 0 0
#extended
/dev/sda4 / extended defaults 0 0
#files
/dev/sda2 /media/sda2 ext3 defaults 0 0
/dev/sda5 /media/sda5 swap defaults 0 0 

---

### Post by dreadmeat on 2008-08-07
apparently dev/sda1 *is* mounted, but bash $mount doesn't show it.
if i boot up the live gparted disc i see no error.
sda1 *must* be mounted or i wouldn't have access to my os :confused:


any help much appreciated, i'm not the only human getting this error.

---

### Post by Rocket2DMn on 2008-08-07
You should comment out the entry for sda4 in fstab, this is an "extended" partition which doesn't actually having any content itself, it is like a shell for logical partitions (not physical ones, though it is a physical partition itself).  Logical partitions allow users to escape the physical maximum of 4 partitions per drive.
So that partition should not attempt to be mounted, and certainly not at the root of the filesystem!

---

### Post by dreadmeat on 2008-08-07
like > #extended
**[COLOR="Red"]#[/COLOR]**/dev/sda4 / extended defaults 0 0

or

> #extended
/dev/sda4 [COLOR="Red"]***then nothing***[/COLOR]?


tia man =)

---

### Post by Rocket2DMn on 2008-08-07
The first one, the # at the front of the line.  That makes the line a comment, so the program that parses the file will ignore it.

---

### Post by dreadmeat on 2008-08-07
y'reckon that will fix the gparted sda1 'error' too?
i mean sda1 *somehow* **is** mounted [wtfbbq?]

---

### Post by Rocket2DMn on 2008-08-07
On further investigation it looks like you manually added all these to fstab, which duplicated the root and swap filesystems (they are declared up in the file with UUIDs).  Can you please post the output of these commands:
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
I think you need to comment out the sda1, sda2, and sda4 entries.  sda5 looks like a data partition, so you can leave that one.  The above commands will help me create the correct fstab file for you.

---

### Post by dreadmeat on 2008-08-07
yeah mate, gimme a sec aye =) **brb**

---

### Post by dreadmeat on 2008-08-07
sudo fdisk -l
> 
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7557e111

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1262    10136983+  83  Linux
/dev/sda2            1276       15838   116977297+  83  Linux
/dev/sda4            1263        1275      104422+   5  Extended
/dev/sda5            1263        1275      104391   82  Linux swap / Solaris

Partition table entries are not in disk ordercat /etc/fstab
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc          proc         defaults                       0  0  
# Entry for /dev/sda1 :
UUID=aab70474-924a-43c7-9192-822e8bbb03af  /              ext3         relatime,errors=remount-ro     0  1  
# Entry for /dev/sda5 :
UUID=dfa70845-551c-4c2c-a339-e7d3ca5d94b1  none           swap         sw                             0  0  
#os
/dev/sda1                                  /              ext3         defaults                       0  1  
#odd
/dev/scd0                                  /media/cdrom0  udf,iso9660  users,noauto,exec,utf8,sync    0  0  
/dev/scd1                                  /media/cdrom1  udf,iso9660  users,noauto,exec,utf8,sync    0  0  
#extended
/dev/sda4                                  /              extended     defaults                       0  0  
#files
/dev/sda2                                  /media/sda2    ext3         defaults                       0  0  
/dev/sda5                                  /media/sda5    swap         defaults                       0  0sudo blkid  
> /dev/sda1: UUID="aab70474-924a-43c7-9192-822e8bbb03af" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="fc4f6fad-632e-48f8-a1bf-2088c06a6cfa" 
/dev/sda2: UUID="6cd84707-bdd5-4aa5-9a5f-e51dbd31de2b" SEC_TYPE="ext2" TYPE="ext3"mount 
> /dev/sda4 on / type extended (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda2 on /media/sda2 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)


---

### Post by Rocket2DMn on 2008-08-07
Looks like the UUID on your swap partition changed, so we'll fix that.

OK, if I were you, I would make my fstab file look exactly like this:
```
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=aab70474-924a-43c7-9192-822e8bbb03af / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=fc4f6fad-632e-48f8-a1bf-2088c06a6cfa none swap sw 0 0
#odd
/dev/scd0 /media/cdrom0 udf,iso9660 users,noauto,exec,utf8,sync 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 users,noauto,exec,utf8,sync 0 0

#/dev/sda2
UUID=6cd84707-bdd5-4aa5-9a5f-e51dbd31de2b /media/sda2 ext3 defaults 0 2
```
In order to edit fstab, let's make a backup, then open it
```
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```
Then copy and paste in the new stuff, save and close, and run
```
sudo mount -a
```

---

### Post by dreadmeat on 2008-08-07
> **Rocket2DMn said:**
> Looks like the UUID on your swap partition changed, so we'll fix that.

OK, if I were you, I would make my fstab file look exactly like this:
```
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=aab70474-924a-43c7-9192-822e8bbb03af / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=fc4f6fad-632e-48f8-a1bf-2088c06a6cfa none swap sw 0 0
#odd
/dev/scd0 /media/cdrom0 udf,iso9660 users,noauto,exec,utf8,sync 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 users,noauto,exec,utf8,sync 0 0

#/dev/sda2
UUID=6cd84707-bdd5-4aa5-9a5f-e51dbd31de2b /media/sda2 ext3 defaults 0 2
```
[/code]will do mate, thanks.
you are right i manually edited my fstab
so you are saying that i 'doubled up' on some of the entries.
i've been meaning to ask what the uuid deal is too.

i might just add that i am the only human using this machine so full on all ages backstage pass is cool with me.

---

### Post by Rocket2DMn on 2008-08-07
I updated the post since you saw that, refresh the page :)
For some info on UUID, see [uhelp]community/UsingUUID[/uhelp]

---

### Post by dreadmeat on 2008-08-07
whoah i posted too soon, sorry ha ha


edit: ok f5 :p

---

### Post by mcduck on 2008-08-07
```
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0 
# Entry for /dev/sda1 :
UUID=aab70474-924a-43c7-9192-822e8bbb03af / ext3 relatime,errors=remount-ro 0 1 
# Entry for /dev/sda5 :
UUID=dfa70845-551c-4c2c-a339-e7d3ca5d94b1 none swap sw 0 0 
#os
/dev/sda1 / ext3 defaults 0 1 
#odd
/dev/scd0 /media/cdrom0 udf,iso9660 users,noauto,exec,utf8,sync 0 0 
/dev/scd1 /media/cdrom1 udf,iso9660 users,noauto,exec,utf8,sync 0 0 
#extended
/dev/sda4 / extended defaults 0 0 
#files
/dev/sda2 /media/sda2 ext3 defaults 0 0 
/dev/sda5 /media/sda5 swap defaults 0 0 
```

The root partition is defined twice in that fstab. Remove the second entry:

# Entry for /dev/sda1 :
UUID=aab70474-924a-43c7-9192-822e8bbb03af / ext3 relatime,errors=remount-ro 0 1

#os
/dev/sda1 / ext3 defaults 0 1

..and, like already mentioned, the extended partition is nothing you can mount (or actually use fore anything, it's just a container for other partitions. So it should be removed from fstab as well.

---

### Post by dreadmeat on 2008-08-07
i need a restart...

---

### Post by Rocket2DMn on 2008-08-07
Yes, do your restart, I thought it might be necessary b/c of the duplicate root entry.

---

### Post by dreadmeat on 2008-08-07
right awesome, just what i wanted.
time to read up on uuids now, i was reading older documentation regarding fstab editing i'm sure.

thanks mcduck too.

silly question: do i thank each individual post or just one?

---

### Post by Rocket2DMn on 2008-08-07
RE: Thanks - that's up to you.  Generally you thank posts that you find to be extremely useful.  Some people are very liberal about dishing out Thanks; I tend to use it sparingly, it makes it more "special" if you will.

Since we got your problem fixed, I'm off to bed now.  Happy Ubuntu-ing!

---

### Post by dreadmeat on 2008-08-07
right, you'll get one meaningful one from me.
thanks a lot for your help and enjoy your sleep.

i'm about to tuck into a home made chicken curry, wicked.

---

