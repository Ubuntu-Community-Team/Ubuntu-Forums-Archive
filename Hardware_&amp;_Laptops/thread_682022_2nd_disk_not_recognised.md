---
title: "2nd disk not recognised"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by matski on 2008-01-29
Hi there.

I have two ide drives in my box.  The 2nd drive is formatted with NTFS and Ubuntu (Gutsy) has never had a problem mounting it and reading to it.

For some reason I can no longer see the drive listed in Computer so cannot mount it.  

In case the disk was faulty I popped in into an external ide caddy but could read and write to it with no problems.

Hope someone can help - thanks in advance.

---

### Post by taurus on 2008-01-29
What are the outputs of these commands from a terminal?  Maybe you need to mount it by hand (probably with a force option) if it didn't get shut down cleanly.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by matski on 2008-01-29
Thanks for the reply.  The outputs of the commands are as follows:

sudo fdisk -l

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8dee8dee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28e3d320

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    7  HPFS/NTFS

```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ef47705b-7032-43f6-a8a1-9b4611197d14 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4ca0d2b1-7f1a-4bfe-9ee3-eb68f5024aa7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/sdb1    /media/TRANSMAT    ntfs-fuse    auto,gid=1001,umask=0002    0    0

```

df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             108G   14G   89G  14% /
varrun                506M  212K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   96K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile

```

I had edited fstab to force mount the drive at boot which was working fine.

---

### Post by taurus on 2008-01-29
So, everything is working fine now.

Otherwise, what happens when you run this command from a terminal?

```
sudo mount -t ntfs /dev/sdb1 /media/TRANSMAT
```

---

### Post by matski on 2008-01-30
Sorry to mislead, the drive is no longer mounting.  I just wanted to point out that I had originally edited fstab to force mount the drive at boot which did work for a time.

I will try the command suggested when I get home.

Thanks again,

Mat

---

### Post by matski on 2008-01-30
I ran the command from a terminal - nothing happened.  It did not mount the drive, no error was generated either.

---

### Post by taurus on 2008-01-30
Can you post these again?

```
sudo fdisk -l
df -h
```

---

### Post by matski on 2008-01-30
Sure thing.

sudo fdisk -l
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8dee8dee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28e3d320

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    7  HPFS/NTFS

```

df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             108G   14G   89G  14% /
varrun                506M  208K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   96K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             187G  184G  2.7G  99% /media/TRANSMAT

```

---

### Post by taurus on 2008-01-30
> **matski said:**
> Sure thing.

df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             108G   14G   89G  14% /
varrun                506M  208K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   96K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
**[COLOR="Blue"]/dev/sdb1             187G  184G  2.7G  99% /media/TRANSMAT[/COLOR]**

```

It's already mounted to /media/TRANSMAT.

```
ls -la /media/TRANSMAT
```

---

### Post by matski on 2008-01-30
Thanks for your help so far. I didn't think to browse it using terminal.

Is there any reason why it is no longer visible in Computer or showing as a mounted icon on the desktop?

---

### Post by matski on 2008-01-31
After a reboot I am back to, what appears to be, no mounted drive so shortcuts that point to the 2nd disk do not work.

Running the last two commands then allow me to view and use the 2nd drive again and all shortcuts work.

Seems a bit odd and I would prefer for the drive to mount automagically as it was before or at least be visible in Computer.

---

### Post by taurus on 2008-01-31
If you want to mount it through /etc/fstab, why don't you edit the current entry to make it look this now.

```
/dev/sdb1    /media/TRANSMAT   ntfs-3g   defaults   0   0
```
Save it.  Then install ntfs-3g driver so you can read/write to it.

```
sudo apt-get update
sudo apt-get install ntfs-3g
```
Reboot.

---

### Post by matski on 2008-01-31
great stuff. its now back to how it was. many thanks :)

---

### Post by LingLings on 2008-04-06
**What is my problem?**

I have the same setup as Matski and I'm now having the same problem with the 2nd disk no longer being recognized.

I've Ubuntu (Gutsy) using two ide drives in my box with 2nd drive formatted with NTFS and I've never had a problem mounting it and reading to it.

I originally edited fstab to force mount the drive at boot.  This worked for a short time (six weeks) and now for some unknown reason I can no longer see the drive listed in Computer so cannot mount it.

Unlike Matski I'm a total Noob and easily confused so I'm hoping somebody can explain how I can resolve this problem.  Here is my set up and what I've tried so far:

**What's my setup?**

sudo fdisk -l

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9f5f9f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19269   154778211   83  Linux
/dev/sda2           19270       19457     1510110    5  Extended
/dev/sda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa42db598

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36483   293049666    7  HPFS/NTFS
```

cat /etc/fstab

```
 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f5182923-8bb0-4a66-8c33-54e6b17686bc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ff6c83bf-d7bf-446c-88a2-025a9b2886a0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1       /media/STORAGE  ntfs-3g defaults        0       0
```

df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             146G   96G   43G  69% /
varrun                252M   84K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  100K  252M   1% /dev
devshm                252M   16K  252M   1% /dev/shm
lrm                   252M   34M  218M  14% /lib/modules/2.6.22-14-generic/volatile
```

**What have I tried?**

sudo mount -t ntfs /dev/sdb1 /media/STORAGE

```
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/STORAGE -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/STORAGE ntfs-3g defaults,force 0 0

```

Therefore I tried...

mount -t ntfs-3g /dev/sdb1 /media/STORAGE -o force

```
mount: only root can do that
```

I don't understand this message and I realize that it might be something obvious but could someone explain?

I have also tried the solution suggested by Taurus:

> If you want to mount it through /etc/fstab, why don't you edit the current entry to make it look this now.

```
/dev/sdb1    /media/TRANSMAT   ntfs-3g   defaults   0   0
```

Save it. Then install ntfs-3g driver so you can read/write to it.

```
sudo apt-get update
sudo apt-get install ntfs-3g
```

Reboot.


But, unfortunately, this didn't work for me.  Any help offered will be greatly appreciated

---

### Post by LingLings on 2008-04-06
I have now tried the following

sudo bash
mount -t ntfs-3g /dev/sdb1 /media/STORAGE -o force

```
fuse: failed to access mountpoint /media/STORAGE: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdb1 (STORAGE)
```

Then after a reboot

sudo apt-get update
sudo apt-get install ntfs-3g

Then after this

sudo mount -t ntfs /dev/sdb1 /media/STORAGE

```

fuse: failed to access mountpoint /media/STORAGE: No such file or directory
FUSE mount point creation failed
```

Does this shed any light on the matter for anyone out there?

---

