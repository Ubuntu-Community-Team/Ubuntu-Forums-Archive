---
title: "Moved Partition and new UUID won't mount in fstab"
date: 2013-11-03
forum: Hardware
---

### Post by nalgarryn on 2013-11-03
Hi Guys,

I have an 80GB HDD in my laptop. Initially it was partitioned ~35GB for Ubuntu, 3GB for swap, and the rest as NTFS.

What I did was delete the #GB and NTFS partitions, made a new swap partition at the end of the drive, and grew the Ubuntu partition.

The UUID did not change for the ubuntu partition, but it obviously did for the swap partition because I deleted it and created it anew. I've changed fstab to use the new UUID but my swap partition is still not mounting.

I'm running Lubuntu 13.04 on an Acer Aspire 5315-2681 (not the most powerful hardware). The last OS install I did was 12.04, and it seems quite slow since the last OS update.

Any help is appreciated!

---

### Post by steeldriver on 2013-11-03
How are you determining that the swap isn't mounting? are you getting a boot error? Swap doesn't usually appear in the mount command output (or /etc/mtab) - what does 'swapon -s' say?

---

### Post by nalgarryn on 2013-11-04
> **steeldriver said:**
> How are you determining that the swap isn't mounting?

I am running Lubuntu and under the Accessories tab in the menu is an item called 'Disks'. When I boot, it describes that partition as unmounted. It's also how I mount it manually on boot.
 
> **steeldriver said:**
> what does 'swapon -s' say?
```

Filename                Type        Size    Used    Priority
/dev/zram0                              partition    508472    436144    5
/dev/sda2                               partition    3140700    0    -1
```

If I get an error codes on boot, they're not noticeable. The only reason I knew the swap wasn't mounting was because I did get an error code for the old partition (cannot mount UUID, ##...###). I commented it out in fstab and the error went away. Tried adding the new swap partition but it doesn't seem to work.

---

### Post by nalgarryn on 2013-11-08
If I do a fresh boot and try 'swapon -s' I get:

```
@Aspire-5315:~$ swapon -sFilename				Type		Size	Used	Priority
/dev/zram0                              partition	508472	379304	5
```

So it's definitely not mounting.

Any help here would be appreciated.

---

### Post by oldfred on 2013-11-08
Post these:
 sudo blkid -o list
      
 cat /etc/fstab

---

### Post by nalgarryn on 2013-11-16
Sorry, I was without Internet because I moved and I just got new service today.

```
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              c9755d3e-c9dd-405a-8d3a-1528d9653047
/dev/sda2  swap    swap     <swap>         d6b87aa9-c693-493b-bfbf-30c3c9e5ea7c
/dev/zram0 swap             <swap>         575f2ac9-210a-4eb6-8293-427d4a8f26d7



```

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c9755d3e-c9dd-405a-8d3a-1528d9653047 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=ca5f41be-4467-4852-9b97-29b2e582745b none            swap    sw              0       0
UUID=d6b87aa9-c693-493b-bfbf-40c3c9e5ea7c      none    swap      sw    0    0



```

You can see where I just commented out the old one and added in the new partition. What part did I do wrong?

---

