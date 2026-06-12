---
title: "&quot;EXT3-fs error&quot; is this a harddrive problem?"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by GrantShoe on 2007-03-11
lately my computer has been freezing.  I'd be doing nothing and i'd hear a click and everything would freeze.  I recently installed Kubuntu and before that, it sat for 3 months with nothing.  I started to think that this was because of my harddrive being kinda old.  and then i thought that it might be a bad install?

just a bit ago, the screen went black but my mouse still worked... i didn't know what that was so i closed out of xorg and i found this:

```
* Activating swap...                                                                      [ ok ]
* Checking root file system...
fsck 1.39 (29-May-2006)
/dev/hda1: clean, 123255/9584640 files, 1340764/19169280 blocks
                                                                                                            [ ok ]
* Checking file systems...
fsck 1.39 (29-May-2006)
                                                                                                            [ ok ]
[17187989.120000] EXT3-fs error (device hda1): ext3_get_inode_loc: unable to re
d inode block - inode=6129550, block 12255300
[17187989.120000] EXT3-fs error (device hda1): ext3_get_inode_loc: unable to re
d inode block - inode=8421458, block 16842762
```

what do I do? i'm sick of cold reboots, i want to get this resolved.  But i reallllly don't want to buy a new HDD...

---

### Post by apjone on 2007-03-13
run up a live cd. Open a terminal and become root then run 

root@home:~# fsck.ext3 -p -c -f /dev/hda

this should check the disk and auto repair anything it finds wrong.
 
A good low level format also works. If it keeps clicking though then you should get a new disk.

---

### Post by GrantShoe on 2007-03-31
after letting my linux box sit for a bit, i booted straight to the Live CD andi ran the fsck command and this returned:
```
fsck.ext3: Bad magic number in super-block while trying to open /dev/hda 
/dev/hda:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

what exactly is a 'low level format' and how do i do this?

---

