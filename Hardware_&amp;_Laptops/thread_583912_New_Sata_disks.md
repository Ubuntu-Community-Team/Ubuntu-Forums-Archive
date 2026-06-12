---
title: "New Sata disks"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by cotn on 2007-10-20
A few weeks ago I have done an upgrade to Debian Etch. Succesfully!

Today I have added two new SATA(1) drives and configured them to raid0(stripe 64k) with a Raid Bios Setup utility from uLi Electronics. 

I just want to use these devices as extra storage but I can't acces them. 

I found information on the Internernet about mdadm and dmraid and tried several given options but nothing seems to work:

```

# dmraid -r
No RAID disks

```

```

cfdisk  /dev/md0
 FATAL ERROR: Cannot read disk drive (instead of cannot open drives)

```

Am I in the wrong direction or what ?

Can somebody help please ?

Thanks in advance!

---

### Post by Stuart_1745 on 2007-10-20
I hate to tell you this but I had/have the same [problem]("http://ubuntuforums.org/showthread.php?p=3540647") as you

long story short ULI "raid" is a fake raid. and the tool Linux uses to read fake raids doesn't support the ULI chipset(no idea why not, it just doesn't). so yeah.

---

### Post by cotn on 2007-10-21
Yeah, I think you're right! 

Too bad.. I think I just do without RAID..

In bios I configured them to SATA without raid.. And  you can access youre devices again in linux when you install the Sata uLi drivers.. (modprobe sata_uli)

For other drivers check: [http://linux-ata.org/driver-status.html#ahci](http://linux-ata.org/driver-status.html#ahci)

---

### Post by cotn on 2007-10-21
Yeah, I think you're right! 

Too bad.. I think I just do without RAID..

In bios I configured them to SATA without raid.. And  you can access youre devices again in linux when you install the Sata uLi drivers.. (modprobe sata_uli)

For other drivers check: [http://linux-ata.org/driver-status.html#ahci](http://linux-ata.org/driver-status.html#ahci)

---

### Post by cotn on 2007-10-21
I fdisked the two drives to  "type: Linux raid autodectect"

Then: 
```

# mdadm --create --verbose /dev/md0 --level=stripe --raid-devices=2/dev/sda1 /dev/sdb

# cat /proc/mdstat
Personalities : [raid0]
md0 : active raid0 sdb1[1] sda1[0]
      241247872 blocks 64k chunks

unused devices: <none>

# mkfs.ext3 /dev/md0
... blablabla ....

# mdadm --detail --scan --verbose > /etc/mdadm/mdadm.conf
# mkdir /media/raid
# vi /etc/fstab

[CODE]
/dev/md0        /media/raid/    ext3    defaults        1       2

```

# mount -a
[/CODE]

And now I have software RAID... Works fine for me... 

Solved!

---

### Post by cotn on 2007-10-24
Not completely solved.. sorry :(

When  i reboot I get the folloing message (everytime): 

```

fsck.ext3: Invalid argument while trying to open /dev/md0
/dev/md0:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

* A maintenance sell will now be started
CONTROL-D will terminate this shell and resume system boot.

```

When I type "e2fsck -b 8193 /dev/md0" it gives the same result as described above.

When I type fdisk -l, the devices /dev/sda and /dev/sdb are not shown in the list. This is weird.

Now here is the trick to get md0 to function again:

```

#fdisk /dev/sda
quit

#fdisk /dev/sdb
quit

fdisk -l #Now I can see /dev/sda and /dev/sdb... Weird !!

# mdadm --create --verbose /dev/md0 --level=stripe --raid-devices=2/dev/sda1 /dev/sdb
# mdadm --detail --scan --verbose > /etc/mdadm/mdadm.conf
# mount -a

```

So it seems that when I boot my pc it doesn't automaticly detect /dev/sda and /dev/sdb..

Can someone help me out to solve this.. I can't get it to work...

---

### Post by celestius on 2008-03-07
hmm i setup a raid0 with two sata disks just a minute ago. here's what i did

[http://ubuntuforums.org/showthread.php?t=717357](http://ubuntuforums.org/showthread.php?t=717357)

---

