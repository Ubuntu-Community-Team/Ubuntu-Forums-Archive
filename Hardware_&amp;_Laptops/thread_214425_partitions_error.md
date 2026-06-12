---
title: "partitions error"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by fugit10 on 2006-07-12
hi, 
I'm new to ubuntu and linux in general so sorry if my questions seem newbish.
anyways I'm currently dual booting and made 4 partitions,
1 (ntfs) for my xp
2 (ext3) ubuntu
3 (ext3) swap
4 (ext3) to use as common data space for xp and ubuntu, I use a program to view the ext 3 under xp

Anyways for some reason the extra common space doesn't mount on to my desktop and I wasn't sure why. When I checked my fstab this is what came out
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

I also noticed something strange, I went to the disk manager under preferences and I noticed that I had 5 partitions and it treated my swap as a ntfs while the swap partition comes out as having no space. I was not sure why this happened. 
Can someone show me how to fix it so that
1) I can see the extra partition on my desktop
2) redirect my disk manager to recognize that the ntfs partition was actually my swap drive
3) also since the swap drive (that I had thought I created) is only 460mb but I got 1012 ram so wanted to increase it to that.

thanks

---

### Post by HAARP on 2006-07-12
Run
```
sudo fdisk /dev/sda
```

press 'p'
copy'n'paste everything here
press 'q' to quit

Be careful! ;)
Looks like there are more partitions than you have created or something..


You don't need to increase your swapfile. With 1GB RAM, it'll hardly ever swap.

---

### Post by fugit10 on 2006-07-12
hi,
thanks for the help btw
here's what came out

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2589    20796111    7  HPFS/NTFS
/dev/sda2            8576        8627      417690    f  W95 Ext'd (LBA)
/dev/sda3            8628        9729     8851815   83  Linux
/dev/sda4            2590        8575    48082545   83  Linux
/dev/sda5            8576        8627      417658+  82  Linux swap / Solaris

Partition table entries are not in disk order

also I used to hibernate my laptop under xp frequently when going to class and I heard to be able to do so in ubuntu your swap file had to be as big as your ram. is that true? i ask because currently I can't hibernate and was thinking the problem was due to that. also I noticed in xp the computer would get laggy after a while when using hibernate too frequently but I heard in linux u don't ever have to reboot so would this problem occur?
thanks

---

### Post by HAARP on 2006-07-12
I don't know much about Hibernation, but I think a seperate file is used to store the RAM.

My analysis: The devices are out of order. Don't ask me why :-k 

sda1: is still your Windows instalation (NTFS)
sda4: seems to be a Linux partition, but is not being mounted. It's taking almost all the space tho. Guess it's your common space?
sda5: Linux swap
sda3: the Ubuntu installation
sda2: small Windows partition?

I put them in the order as they appear on the disk.

Your fstab should look like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda3 / ext3 defaults,errors=remount-ro 0 1
/dev/sda1 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0
/dev/sda5 none swap sw 0 0
/dev/sda4 --folder-- ext3 defaults 0 2
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
```

whilst '--folder--' is the path you want your common space mounted to (eg. /media/sda4). Has to exist before mounting!

What sda2 is, I don't know. Try mounting it with:
```
sudo mkdir /media/test
sudo mount /dev/sda2 /media/test
```
and see what's there.

---

### Post by krazykirk on 2006-07-13
Just a tip, if you want a common space for Windows XP and Ubuntu, your best choice would be Fat32, as you can write to it on both Operating Systems. But it's your choice of course..

---

### Post by fugit10 on 2006-07-13
hey thx for the replies,
anyways i copied and pasted it but nothing has changed, but I also failed to mention one thing before as well
when I go to computers it detects that the partition is there but when I double click on it this is the error it gives me

mount: only root can mount /dev/sda4 on /downloads/

---

### Post by fugit10 on 2006-07-13
actually i got it working thx!
but now i got another problem still which is the sda2 partition
its the same size as my swap partition and I think what happened was when I reinstalled ubuntu it created another swap instead of using that space.
When I go to gparted now it shows sda2 as being extended with an lba flag and sda5 being right under it. I think they're linked together becuase when I right click on sda2 I can't do anything to it. is it possible erase both partitions then merge them together and reactivate the linux swap?
thanks

---

### Post by HAARP on 2006-07-13
Looking at the fdisk output, sda2 and sda5 occupy the same blocks.

sda1-4 are always primary or extended partitions. You only can have 4 of them. However, to get more partitions, you can create logical disks inside of extended partitons. Those act like normal partitions (expect you can't boot from them) They always get assigned sda5+
This is the case here. Logical disk sda5 inside of extended partition sda2
You need to first delete sda5, then you can remove sda2. But for gods sake, disable swapping first (sudo swapoff /dev/sda5). Then you can recreate them as a primary partition.
However, you can just keep it that way. No space is wasted.

---

