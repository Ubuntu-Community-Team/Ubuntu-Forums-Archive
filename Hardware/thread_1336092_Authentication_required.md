---
title: "Authentication required"
date: 2009-11-24
forum: Hardware
---

### Post by nomko on 2009-11-24
Hello,

I have installed Ubuntu 9.10 recently and now i'm facing this remarkable fact: I have 2 hard disk in my computer:
1x 500 gig
1x 1000 gig
I've installed Ubuntu fully on the 500 gig disk and i'm using the 1 terabyte disk for downloads etc. Everytime when I startup my computer and i'm wanna get access o the 1 terabyte disk, Ubuntu ask for authentication. Why is that and how can i get rid of this? Cause after a while Ubuntu sort of unmount the 1 terabyte disk and it need authenication again when i try to access the 1 terabyte disk. I have never seen this before since i'm using Ubuntu. Who can help me?
Many thanks!
Nomko (The Netherlands).

---

### Post by ajgreeny on 2009-11-24
> **nomko said:**
> Hello,

I have installed Ubuntu 9.10 recently and now i'm facing this remarkable fact: I have 2 hard disk in my computer:
1x 500 gig
1x 1000 gig
I've installed Ubuntu fully on the 500 gig disk and i'm using the 1 terabyte disk for downloads etc. Everytime when I startup my computer and i'm wanna get access o the 1 terabyte disk, Ubuntu ask for authentication. Why is that and how can i get rid of this? Cause after a while Ubuntu sort of unmount the 1 terabyte disk and it need authenication again when i try to access the 1 terabyte disk. I have never seen this before since i'm using Ubuntu. Who can help me?
Many thanks!
Nomko (The Netherlands).
You will need to add a line to your /etc/fstab file to mountthe disk at boot time.  The contents of the line will depend on the disk device or UUID name and the filesystem it is formatted to, and it will also need a folder, which you will need to make, as the mountpoint.

Here are a number of formats for the lines you will need to add.  Just change the mountpoints and device names to fit your situation.

Automount linux partition. Add line to /etc/fstab:-
/dev/sdb1 /media/linux ext3 defaults, relatime 0 1

Automount fat32 windows. Add line to /etc/fstab:-
/dev/sdb1 /media/data2 vfat defaults,user,dmask=027,fmask=137 0 0

Automount ntfs windows. Add line to /etc/fstab:-
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
or
/dev/hda2 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0

---

### Post by nomko on 2009-11-24
> **ajgreeny said:**
> You will need to add a line to your /etc/fstab file to mountthe disk at boot time.  The contents of the line will depend on the disk device or UUID name and the filesystem it is formatted to, and it will also need a folder, which you will need to make, as the mountpoint.

Here are a number of formats for the lines you will need to add.  Just change the mountpoints and device names to fit your situation.

Automount linux partition. Add line to /etc/fstab:-
/dev/sdb1 /media/linux ext3 defaults, relatime 0 1

I hope that last one has to be realtime?

---

### Post by doomsword2001 on 2009-11-24
/dev/sda2 /home/backup ext4 defaults
this is what i've done and works for me, found it somewhere can't remember :D

---

### Post by sisco311 on 2009-11-24
> **nomko said:**
> I hope that last one has to be realtime?

nope, it relatime.


```
man mount | less --pattern\="relatime"
```
Update inode access times **rela**tive to  modify  or  change  **time**.

EDIT:

[uhelp]community/Fstab[/uhelp]

Since 8.04 (Hardy Heron) Ubuntu uses relatime as default for linux native file systems. You can find a discussion of relatime here : [http://lwn.net/Articles/244829/]("http://lwn.net/Articles/244829/")

EDIT2: [thread=283131]How to fstab[/thread]

---

### Post by ajgreeny on 2009-11-24
Thanks for that sisco311.  I've only just got back to the forum to see this.  I have actually seen this query (realtime not relatime) a few times on various linux sites, so it is obviously a spelling a lot of people think is a typo.

---

### Post by nomko on 2009-11-25
> **ajgreeny said:**
> Thanks for that sisco311.  I've only just got back to the forum to see this.  I have actually seen this query (realtime not relatime) a few times on various linux sites, so it is obviously a spelling a lot of people think is a typo.

Okay, i believe you guys when you're telling me it is relatime instead of realtime!

This is the contains of my fstab file:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=f3036f06-5275-44f7-ac9e-4dbe3ee28c5f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=c56c1f54-aebd-4eb5-bed8-5a2e10a96ec9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

So, I need to fill in  /dev/sdb1 /media/linux ext3 defaults, relatime 0 1 as last line?

But when i'm looking in the media folder, i can't see a mapping to my 1000 gig disk, why is that?

*edit*
I just found out that my 1000 gig disk is mounted as /media/NNTPGrab
So, i have to change /media/linux into /media/NNTPGrab?

---

### Post by sisco311 on 2009-11-25
You can mount it anywhere in the filesystem, just make sure that the directory exist.
```
sudo mkdir /media/NNTPGrab
```

I would use the UUID to mount it. Please post the output of:
```
sudo blkid
```
and I will post the fstab entry.

EDIT:
And the content of the fstab:
```
cat /etc/fstab
```

---

### Post by nomko on 2009-11-25
> **sisco311 said:**
> You can mount it anywhere in the filesystem, just make sure that the directory exist.
```
sudo mkdir /media/NNTPGrab
```I would use the UUID to mount it. Please post the output of:
```
sudo blkid
```and I will post the fstab entry.

EDIT:
And the content of the fstab:
```
cat /etc/fstab
```

Output of command "sudo blkid"

/dev/sda1: UUID="c56c1f54-aebd-4eb5-bed8-5a2e10a96ec9" TYPE="swap" 
/dev/sda5: UUID="f3036f06-5275-44f7-ac9e-4dbe3ee28c5f" TYPE="ext4" 
/dev/sdb1: LABEL="NNTPGrab" UUID="5900f0a5-a5c9-417e-92f3-cc502535824a" TYPE="ext3" 
/dev/sdg1: LABEL="Email" UUID="d320e028-8b1e-496e-8825-c6413c14e862" TYPE="ext3" 
/dev/sdg2: LABEL="Multimedia" UUID="debe1dee-138d-40bb-a920-fffb6498f49d" TYPE="ext3" 
/dev/sdg3: LABEL="Documenten" UUID="ca9cb23c-a0fb-4970-9bf3-2608ca95517c" TYPE="ext3" 

Output of command "cat /etc/fstab"

/dev/sda1: UUID="c56c1f54-aebd-4eb5-bed8-5a2e10a96ec9" TYPE="swap" 
/dev/sda5: UUID="f3036f06-5275-44f7-ac9e-4dbe3ee28c5f" TYPE="ext4" 
/dev/sdb1: LABEL="NNTPGrab" UUID="5900f0a5-a5c9-417e-92f3-cc502535824a" TYPE="ext3" 
/dev/sdg1: LABEL="Email" UUID="d320e028-8b1e-496e-8825-c6413c14e862" TYPE="ext3" 
/dev/sdg2: LABEL="Multimedia" UUID="debe1dee-138d-40bb-a920-fffb6498f49d" TYPE="ext3" 
/dev/sdg3: LABEL="Documenten" UUID="ca9cb23c-a0fb-4970-9bf3-2608ca95517c" TYPE="ext3" 
nomko@nomko-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=f3036f06-5275-44f7-ac9e-4dbe3ee28c5f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=c56c1f54-aebd-4eb5-bed8-5a2e10a96ec9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by sisco311 on 2009-11-25
Add this to the fstab:
```
UUID=5900f0a5-a5c9-417e-92f3-cc502535824a    [COLOR="Blue"]/media/NNTPGrab[/COLOR]    ext3    defaults,relatime    0    2
```

Create the mount point:
```
sudo mkdir [COLOR="Blue"]/media/NNTPGrab[/COLOR]
```

NOTE: you can change the[COLOR="#0000ff"] mount point [/COLOR]to whatever you want(i.e. /media/music or /media/data).

There is no need to reboot to test the settings, just run:
```
sudo mount -a
```
to mount the partitions listed in the fstab.

---

### Post by nomko on 2009-11-25
> **sisco311 said:**
> Add this to the fstab:
```
UUID=5900f0a5-a5c9-417e-92f3-cc502535824a    [COLOR=Blue]/media/NNTPGrab[/COLOR]    ext3    defaults,relatime    0    2
```Create the mount point:
```
sudo mkdir [COLOR=Blue]/media/NNTPGrab[/COLOR]
```NOTE: you can change the[COLOR=#0000ff] mount point [/COLOR]to whatever you want(i.e. /media/music or /media/data).

There is no need to reboot to test the settings, just run:
```
sudo mount -a
```to mount the partitions listed in the fstab.


Sisco311,

Many thanks! It is working!

---

### Post by sisco311 on 2009-11-25
Cool!!!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

