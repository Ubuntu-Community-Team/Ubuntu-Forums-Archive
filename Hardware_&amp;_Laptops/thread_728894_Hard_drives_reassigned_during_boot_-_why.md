---
title: "Hard drives reassigned during boot - why?"
date: 2008-03-19
forum: Hardware &amp; Laptops
---

### Post by qbee42 on 2008-03-19
My hard drives shift back and forth during boot. I have two drives, of which I boot Ubuntu Gutsy 7.10 from the second partition of the first drive. The second drive is used as a Samba data drive. Normally the drives are mapped like this:

/dev/sda2
/dev/sdb1

About every third time I boot, the drives map this way:

/dev/sde2
/dev/sdf1

I assume the BIOS is picking up my USB flash drive readers and mapping them in ahead of the real hard drives. I have the latest version of the BIOS, have turned off legacy USB support, and disabled booting from USB devices. 

It's not a big deal, except that I'm forced to dual-boot to run a development system that absolutely has to have Windows (it's what I do for a living, so I can't avoid it). The drive mappings shift and screw up any persistent links I have with the data drive, so I have to reboot until it comes up correctly.

I've searched and searched, but only found a couple of posts relating to this issue. It could be I don't know the proper search terms to use, or maybe it isn't a common problem.

Any ideas will be greatly appreciated.

Tom

---

### Post by mcduck on 2008-03-19
All you need to work around that is to mount your partitions using the UUID instead of the device name. You can use the 'blkid' command to get the UUID for your drive, and then just edit /etc/fstab to use it.

For example, instead of using a line like this:

/dev/sda2 /media/flash vfat user,rw 0 0

..you should use this:

UUID=fab05680-eb08-4420-959a-ff915cdfcb44 /media/flash vfat user,rw 0 0

---

### Post by qbee42 on 2008-03-19
Thanks, that should do it. I still wonder why my BIOS does that, but that's not something I'm going to fix, so I'll just have to work around it.

Tom

---

### Post by qbee42 on 2008-03-19
Another question comes to mind as I think about this: Is there any reason I need to worry about the mapping on the root drive? It seems to work the same whether it gets automatically mapped as /dev/sda2 or /dev/sde2. Obviously I need to use the UUID for the data drive, as my mount points get screwed up otherwise. Are there hidden issues?

Thanks,
Tom

---

### Post by mcduck on 2008-03-19
> **qbee42 said:**
> Another question comes to mind as I think about this: Is there any reason I need to worry about the mapping on the root drive? It seems to work the same whether it gets automatically mapped as /dev/sda2 or /dev/sde2. Obviously I need to use the UUID for the data drive, as my mount points get screwed up otherwise. Are there hidden issues?

Thanks,
Tom
If you have no probelms with root partition then you don't need to worry about it.

Anyway, you can safely use UUID for everything. The only thing you might need to remember is that if you edit the partitions (like resize them, for example), their UUID's will change and you'll need to edit the fstab again to use the new UUID's.

---

### Post by qbee42 on 2008-03-19
I did some testing and see that my root and swap partitions are already mapped via UUID. The second drive is the one I mapped as /dev/sdb1, so I ran blkid to get the UUID for it and changed /etc/fstab to use the UUID. The second drive shows up as empty, and no longer shows an icon on my desktop. Changing back to the /dev/sdb1 makes it work okay again. It is an NTFS formatted drive, so I don't know if that causes any trouble. Here is what I have so far:

tom@big-bob:~$ blkid
/dev/sda1: UUID="50547FE7547FCDEA" TYPE="ntfs" 
/dev/sdb1: UUID="DB2728E4B5331CC" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="5b08dabe-6acb-48c4-a043-032d6bbbffe0" 
/dev/sda2: UUID="d5027b0d-90d8-415b-9e42-9455a933b9fc" SEC_TYPE="ext2" TYPE="ext3" 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d5027b0d-90d8-415b-9e42-9455a933b9fc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5b08dabe-6acb-48c4-a043-032d6bbbffe0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1		 /media/commondrive	ntfs	0	0
# UUID=DB2728E4B5331CC/media/commondrive	ntfs	0	0

If I uncomment the last fstab line and comment the /dev/sdb1line the commondrive disappears. Any idea why that would be the case? I see that the UUIDs on the NTFS volumes are funny looking.

Thanks,
Tom

---

### Post by mcduck on 2008-03-19
> **qbee42 said:**
> I did some testing and see that my root and swap partitions are already mapped via UUID. The second drive is the one I mapped as /dev/sdb1, so I ran blkid to get the UUID for it and changed /etc/fstab to use the UUID. The second drive shows up as empty, and no longer shows an icon on my desktop. Changing back to the /dev/sdb1 makes it work okay again. It is an NTFS formatted drive, so I don't know if that causes any trouble. Here is what I have so far:

tom@big-bob:~$ blkid
/dev/sda1: UUID="50547FE7547FCDEA" TYPE="ntfs" 
/dev/sdb1: UUID="DB2728E4B5331CC" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="5b08dabe-6acb-48c4-a043-032d6bbbffe0" 
/dev/sda2: UUID="d5027b0d-90d8-415b-9e42-9455a933b9fc" SEC_TYPE="ext2" TYPE="ext3" 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d5027b0d-90d8-415b-9e42-9455a933b9fc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5b08dabe-6acb-48c4-a043-032d6bbbffe0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1		 /media/commondrive	ntfs	0	0
# UUID=DB2728E4B5331CC/media/commondrive	ntfs	0	0

If I uncomment the last fstab line and comment the /dev/sdb1line the commondrive disappears. Any idea why that would be the case? I see that the UUIDs on the NTFS volumes are funny looking.

Thanks,
Tom

If that's a direct copypaste from your actual fstab, then you have a typo there ;)
```
# UUID=DB2728E4B5331CC/media/commondrive	ntfs	0	0
# UUID=DB2728E4B5331CC /media/commondrive	ntfs	0	0
```
There should be a space between the UUID and the mount path..

No need to worry about the different looking UUID, that looks just fine.

---

### Post by p_quarles on 2008-03-19
Moved to the hardware section.

---

### Post by qbee42 on 2008-03-19
That typo is there because I tried it with and without whitespace. It didn't work either way. I'm pretty much at a loss about why it doesn't mount using the UUID.

Tom

---

### Post by qbee42 on 2008-03-21
My question has now been refined to one about mounting drives via their UUID. If you look at the posts above, you can see that I am trying to mount a SATA hard drive by UUID to avoid issues regarding the assignment of drive labels. It should work. The Ubuntu partition of the main drive is mounted this way, as well as the swap partition, but I can't get it to work with an NTFS partition on a second drive. 

Any help will be greatly appreciated.

Tom

---

