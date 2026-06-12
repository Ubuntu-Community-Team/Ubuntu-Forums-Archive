---
title: "unable to mount cd drive"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by vwaj on 2007-07-28
I recently installed Ubuntu 7.04 on my Dell Latitude D830 notebook, and I'm having trouble mounting my CD/DVD drive.  I'm a bit new to Linux, so bear with me.

I never could mount the drive.  Here are the contents of my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0bb4c20f-8d0e-491b-a1f4-b627e32fb3e0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=7e983d64-1128-4412-ad78-e930dcc7c14d /home           ext3    defaults        0       2
# /dev/sda1
UUID=07D7-0705  /media/sda1     vfat    noauto,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=76588D75588D34C1 /media/sda2     ntfs    noauto,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=820691830691793D /media/sda3     ntfs    noauto,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=dfa10132-569d-4bb2-ac25-5958c678c374 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I'm concerned that the "/dev/hda" entry in the last line is giving me problems, since /dev/hda does not exist.  When I try entering "sudo mount /dev/hda /media/cdrom0/" in a terminal, i get the error message ```
 mount: special device /dev/hda does not exist
```.  It seems some people have fixed this problem by editing the fstab file, changing "hda" to something else such as "cdrom."  However, there's nothing in my /dev/ folder that looks right -- no "cdrom," no "scd0," etc.

When I try "dmesg | grep CD" I see nothing.  That's what worries me...it's like the operating system doesn't even see the drive.

Any ideas?

---

### Post by wsmoser2004 on 2007-07-28
The way I usually check to see if Ubuntu recognizes a device is "sudo lshw" in a terminal.  That stands for "LiSt HardWare" I guess...I dunno :).  It spits out lots of stuff, so get ready to scroll...although once you get used to it you find it's organized pretty well.  

Here's the entry for my CD drive: 

```

              *-cdrom
                description: DVD reader
                product: RW/DVD GCC-4241N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0C29
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom

```

As you can see there, apparently my CD drive has four "logical names."  Hopefully yours will mention a name you haven't tried yet in your fstab :).  It's interesting that your fstab says /dev/hda for your CD drive, I thought that was usually for hard disks (well...back in Dapper that is :)).  Mine is listed as /dev/cdrom in my fstab, but you already said that didn't work for you... :)

I have never yet found a CD drive that Ubuntu does not recognize, although perhaps yours will be the first :).

---

### Post by vwaj on 2007-07-28
thanks for the response wsmoser...unfortunately cdrom actually does not show up when i do lshw.  so is there anything i can do if ubuntu actually does not see the drive?

for reference: someone else made a thread a few minutes after i made mine, reporting exactly the same problem.  it can be found here: [http://ubuntuforums.org/showthread.php?t=511998](http://ubuntuforums.org/showthread.php?t=511998).

---

### Post by wsmoser2004 on 2007-07-29
vwaj-

Looks like your problem was resolved in the other thread.  I've never heard of doing that, but I'll keep it in mind for the future...

-wsmoser2004

---

