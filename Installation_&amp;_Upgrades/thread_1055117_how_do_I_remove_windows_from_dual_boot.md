---
title: "how do I remove windows from dual boot"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by alicemoon on 2009-01-30
I am running ubuntu as a dual boot on my laptop and my pc with windows xp and now use ubuntu 99% of the time - I want to take the plunge and remove xp from my laptop - if that is successful I will go for an ubuntu only PC.
 The reason I am going for the laptop first is that the grub is no longer letting me boot into windows - and rather than struggling with it as I don't use windows much at all now I would rather get rid of it and have use of the space.
How do I do this - is it best to just re-install over everything or can I preserve my files - I have searched the forum &  googled but all I can find seems to be about removing Ubuntu so some clear help on removing windows would be gratefully received.

---

### Post by caljohnsmith on 2009-01-30
How about first opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And please identify your partitions. Also, would you be happy with turning the XP partition into a data partition for your personal files, or do you want to add that space on to your Ubuntu partition?

---

### Post by alicemoon on 2009-01-30
thanks for answering - here is what I got
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13662e6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78573914    39286926    7  HPFS/NTFS
/dev/sda2        78573915   156216059    38821072+   5  Extended
/dev/sda3       156231936   156296447       32256   ef  EFI (FAT-12/16/32)
Partition 3 does not end on cylinder boundary.
/dev/sda5        78573978   152954864    37190443+  83  Linux
/dev/sda6       152954928   156216059     1630566   82  Linux swap / Solaris

is there an advantage to having a data section rather than it all being on my ubuntu partition?

---

### Post by caljohnsmith on 2009-01-30
OK, according to your partition table, your Ubuntu sda5 partition is physically next to your Windows partition, so if you wanted you could absorb the space from the Windows partition into your Ubuntu partition. But unless your sda5 Ubuntu partition is getting full, I would recommend just formatting your sda1 Windows partition to use as a data partition for your personal files. That's generally a good practice because if something were to happen to your Ubuntu install, your personal files will be on a separate partition. So if that sounds like something you would want to try, you could install and run gparted (the Ubuntu partition editor) with:
```
sudo apt-get install gparted
```
That will install gparted, and then it is usually most convenient to just run gparted by going to System > Admin > Partition Editor from your Ubuntu desktop menus. Or you can run gparted from your Ubuntu Live CD, because the Live CD comes with gparted all ready included. Once you fire up gparted, just format the sda1 partition to maybe ext3, and then you can use it for your personal files after that. I would assume you would probably want to have the sda1 data partition automatically mounted on start up, so you would just need to add it to your /etc/fstab file. If you need any help doing that, let me know. Otherwise let me know how it goes.

---

### Post by alicemoon on 2009-01-30
ok thanks I will try that just one more quick question - can I use gparted to readjust the size and add a bit more to my ubuntu partition and have slighly less space for my personal files as I don't tend to hold big files on my laptop so I will not need all the space the windows partition is taking up - or will this cause problems with the ubuntu partition.

---

### Post by caljohnsmith on 2009-01-30
If you want to resize your sda5 Ubuntu partition to use some of the space from sda1, the first thing I would recommend would be to make sure you have anything important in Ubuntu backed up to somewhere else. Then it's just a matter of booting the Live CD (you won't be able to do this from your Ubuntu install), run gparted, right-click your swap partition and select "swapoff", delete your sda1 Windows partition, expand your sda2 extended partition to the left so that it takes up some of the space from the deleted sda1 partition, and finally you can then expand your sda5 partition so that it begins at the new beginning of the sda2 extended partition (the sda2 extended partition is just a "container" for your logical partitions sda5 and sda6). After that, using whatever free space you left at the beginning of the drive, you can create another primary partition with that space, and use that as your data partition. When you pull up gparted and see the graphical layout of your partitions, I think it will be clearer what I mean, but if you have any problems let me know. Good luck and hope it all goes OK.

---

### Post by alicemoon on 2009-01-30
many thanks for your clear explanations -I will have a go over the weekend and let you know what happens

---

### Post by alicemoon on 2009-01-31
well I have reformatted the windows to ext3 using gparted and  set the permissions so that I can write to it. I do need some help setting up the etc/fstab file - I had a quick go but it would not let me open the partition so I must have been doing something wrong. I reset the fstab file back to it's original state. The partition shows on my laptop but I have to enter my password to mount it. Thanks for your help so far as it gave me the confidence to go ahead.

---

### Post by Moop on 2009-01-31
Take a look at psychocats tutorial on mounting linux. That should get your permissions sorted out on the new partition. 

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by caljohnsmith on 2009-01-31
Alicemoon, glad to hear the repartitioning went smoothly. How about posting the output of:
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
```
And also, where do you want to mount the new sda1 data partition? The usual place is to mount it in /media, but you can mount it anywhere you want, for instance in some directory in your home folder if you wish. Please let me know which directory you want to mount it to, and we can work from there if you want.

---

### Post by alicemoon on 2009-01-31
Caljohn
thanks for the swift reply - output as follows
sudo fdisk -lu
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13662e6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78573914    39286926   83  Linux
/dev/sda2        78573915   156216059    38821072+   5  Extended
/dev/sda3       156231936   156296447       32256   ef  EFI (FAT-12/16/32)
Partition 3 does not end on cylinder boundary.
/dev/sda5        78573978   152954864    37190443+  83  Linux
/dev/sda6       152954928   156216059     1630566   82  Linux swap / Solaris

sudo blkid -c /dev/null
/dev/sda1: UUID="2423d807-a5e0-4656-bdd3-da089da1d9fc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="6495fc17-d802-4c78-b28d-b24278b89a12" TYPE="ext3" 
/dev/sda6: UUID="c76abb20-ca81-46d6-9daf-c366b1b2c906" TYPE="swap" 

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=6495fc17-d802-4c78-b28d-b24278b89a12 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=c76abb20-ca81-46d6-9daf-c366b1b2c906 none            swap    sw              0       0

I assumed you could only mount it as /media   is there an advantage to mounting it in a directory within the home folder?

---

### Post by alicemoon on 2009-01-31
> **Moop said:**
> Take a look at psychocats tutorial on mounting linux. That should get your permissions sorted out on the new partition. 

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

thanks for the link - I will have a look at it and hopefully it will improve my understanding - it's always a steep learning curve.

---

### Post by caljohnsmith on 2009-01-31
I think the only advantage of mounting the data partition in your home folder might be that it could be a little more convenient to access, but if you don't really have a preference, mounting it in /media is just fine. How about first opening your fstab:
```
gksudo gedit /etc/fstab
```
And then add at the bottom:
```
UUID=2423d807-a5e0-4656-bdd3-da089da1d9fc /media/[COLOR="Blue"]Data_sda1[/COLOR]	ext3 relatime,errors=remount-ro 0 0
```
And change the "Data_sda1" directory name if you want it called something different. Whichever name you decide on, you will also need to create that directory before you can mount sda1 on it:
```
sudo mkdir /media/[COLOR="Blue"]Data_sda1[/COLOR]
```
Then you can do:
```
sudo mount -a
```
And that should mount your new sda1 Data partition on /media/Data_sda1 (or whatever name you chose). Let me know how that goes or if you run into problems.

---

### Post by alicemoon on 2009-01-31
that's great it worked perfectly - many thanks for your time and help and the easy to follow instructions, when I take the final plunge anddecide to just run Ubuntu on my PC I will know the steps to take.

---

### Post by caljohnsmith on 2009-01-31
Glad to hear that worked OK without any problems; cheers and enjoy your Ubuntu install. :)

---

