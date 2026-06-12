---
title: "problem with ubuntu mounting hard drive"
date: 2011-03-06
forum: Hardware
---

### Post by Arminius on 2011-03-06
I had a hard drive named INTERNAL VI, which wouldn't mount at all, it seemed to have no mount point assigned to it.
So I went into the Fstab, now I can't show the code as it originally was
but the code I changed it to is this ```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=30d6b841-3ad2-4fbe-b872-ab85b3537759 /               ext4    errors=remount-ro 0       1
/dev/sda       /media/INTERNAL VI            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

with the only code I changed being the ```
/dev/sda       /media/INTERNAL VI            swap    sw   
``` part

This seemed to kind of work, cause when I went to mount the hard drive in ubunutu it mounted fine.

Problem is that when I reboot, I come up with an error message "ubuntu, an arror occured while mounting /media/internal" press s to skip mounting or m for manual recovery""

I had know Idea what to do in manual recovery so I skipped.

but when back in ubuntu it will mount just fine if u click on it under places in the menu.

oh and when mounting it calls internal instead of internal vi
so that might be a clue, any help?

---

### Post by Hedgehog1 on 2011-03-06
Arminius,

fstab is using 'white space' (spaces) to seperate data.

So, when it sees the drive name with a space:

```
UUID=30d6b841-3ad2-4fbe-b872-ab85b3537759 /         ext4    errors=remount-ro 0       1
/dev/sda       /media/**INTERNAL** [COLOR="DarkRed"]**VI**[/COLOR]            swap    sw              0       0
```

It thinks the **[COLOR="DarkRed"]VI[/COLOR]** is a setting.

Instead, if you uses the UUID of the partition/drive in  his file (like the line above does), you can name it anything you want with an issue:

```
UUID=30d6b841-3ad2-4fbe-b872-ab85b3537759 /         ext4    errors=remount-ro 0       1
UUID=*[COLOR="Lime"]**xxxxxxx-xxxx-xxxxxx-xxxxxxxxxxx**[/COLOR]*      none      swap    sw                0       0
```

***The Hedge***

:KS

_**p.s. Is INTERAL VI really your swap disk/partition?  It seems to be 'almost' setup that way.**_

As a REFERENCE (Your UUIDs will be different) here is my fstab:
```
# <file system> <mount point> <type> <options> <dump> <pass>
proc                                       /proc             proc  nodev,noexec,nosuid  0  0  
UUID=f2fd03c5-2835-415c-8448-75473daf624a  /                 ext4  errors=remount-ro    0  1  
UUID=cb0c7226-150e-45ca-ba5c-2e161dc10f6a  none              swap  sw                   0  0  
UUID=4aebc2c6-5984-47e3-b2ea-7fdfaf23343e  /home             ext4  nodev,nosuid         0  2
# Automount Windows paritions
UUID=EA561004560FCFED                      /media/Area51     ntfs  defaults             0  0  
UUID=5C28DA0E28D9E754                      /media/Area52     ntfs  defaults             0  0 
```

---

### Post by Hedgehog1 on 2011-03-06
If you need more help with this:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by Arminius on 2011-03-06
> p.s. Is INTERAL VI really your swap disk/partition? It seems to be 'almost' setup that way.

no it's not ment to be swap, I don't know how that happened, I sure didn't tell it to
I have 2 SATA drives, 1 is INTERNAL VI
the other contains 2 partions, most of which is the ubuntu OP, 4 GB's is the swap partition.
But my conky doesn't seem to be recognising any swap at all.
not sure how this mess came about.
So how would I find out the UUID of the internal VI drive?

---

### Post by vanadium on 2011-03-06
It is not meant to be swap, though you indicate you added the line yourself ???
You refer to /dev/sda: this would mean there is no partition table on that drive? Normally, device names for partitions are like /dev/sda1, /dev/sda2.

You would better remove the line you added all together. Then obtain information about the UUID and file system from the command
```

sudo blkid

```

The line in /etc/fstab should mention the correct file system and a valid mount point. It will reveal if you indeed have a swap partition. if you have, it is currently not used: it is not in /etc/fstab.

---

