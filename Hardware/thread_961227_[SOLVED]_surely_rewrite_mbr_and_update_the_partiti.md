---
title: "[SOLVED] surely rewrite mbr and update the partition table on installed running syste"
date: 2008-10-28
forum: Hardware
---

### Post by probume on 2008-10-28
Hi,
I've got an Acer laptop and I can't boot from optical drive nor USB anymore. I've grub as boot loader, winXP on the second part of first hdd and ubuntu on the second hdd with a /boot partition.
I've dumped (with dd, partimage failed with ntfs )the first hdd original config witch had vista on the second partition and ntbootloader as bootloader.
I would like to reinstall vista, but the partition size has been modified for winxp (from 120GB to 15GB ich).
I'd like to modifie the partition table of sda without rewriting the mbr, but I don't remember the exact size of he original vista partition
( Can I retrieve it from the vista bz2 image? if yes, how ? )

I'd like to know if
1- I can restore the mbr wich had ntloader and the good partition table for vista, then use "grub-install --rootdirectorie=/boot /dev/sda" and have grub config unchanged ?

2 - then use bzcat /path/to/my/dumpedvista.bz2 | dd of=/dev/sda2. I'm not sure this /dev/sda2 will be the one of the restored partition table with correct size (120GB) or the one of the actual partition table with a smaller size for xp (15GB). I don't want to reboot to make fedora read the restored partition table, unless all is done and I'm not sure partprobe will not mess all up.

3- Is it possible to test the changes on a virtual machines ? Virtual box 2.0.4 failed to load the vmdk pointing to /dev/sda in user mode (access denied) and don't want to launch the virtual machine in root mode (kvm desactivation required).

---

### Post by probume on 2008-10-29
up](*,)

---

### Post by caljohnsmith on 2008-10-29
If you do:
```
bzcat /path/to/my/dumpedvista.bz2 | wc -c
```
Then I believe that should give you size of your original Vista partition, in bytes. Once you know that, you could maybe use fdisk/parted to manually setup a partition for Vista of that exact size, and then copy the image into the partition with dd. That's the general idea I would try, but how about posting:
```
sudo fdisk -lu
```
So I can see what your partition table currently looks like.

---

### Post by probume on 2008-11-10
Thanks a lot caljohnsmith, sorry I didn't reply earlier, I couldn't connect anymore...
result from fdisk -lu :

Disque /dev/sda: 320.0 Go, 320072933376 octets
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 secteurs
Units = secteurs of 1 * 512 = 512 bytes

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1            2048    20973567    10485760   27  Inconnu
La partition 1 ne se termine pas sur une frontière de cylindre.
****translation*******
The partition doesn't end on a cylinder frontier (don't know why, I didn't change sda1 size, Acer did that
**********************
/dev/sda2   *    20980890    51697169    15358140    c  W95 FAT32 (LBA)
/dev/sda3        51697170   625137344   286720087+   7  HPFS/NTFS

---

### Post by caljohnsmith on 2008-11-10
The first thing I notice is that the sda3 partition starts right after sda2 ends, so are you planning on deleting/resizing sda3 to make room for sda2 to be 120 GB? It looks like you have no other choice, unless you want to put Vista in sda3. You can use Ubuntu's partition editor to do that under System > Admin > Partition Editor. 

I would go ahead and make space for Vista, and once you know the exact size of Vista's partition using that command I gave earlier, you could do:
```
sudo parted /dev/sda
```
Then in the parted dialog screen do:
```
mkpartfs primary ntfs <start sector> <stop sector>
```
And you can use the "sudo fdisk -lu" to find exactly where the new partition should start, i.e. in the sector right after the previous partition. After that you would use dd to copy your Vista partition back in place.

If you would like more specific help, how about letting me know the exact byte-count number you get for the Vista partition, and then posting "sudo fdisk -lu" again after you have room for Vista on the sda drive. We can work from there if you like.

---

### Post by probume on 2008-11-10
Very happy to work with you caljohnsmith :)

Périphérique   Boot    Start     End        Blocs       Id  Système
/dev/sda1              2048      20973567   10485760    27  Inconnu
/dev/sda2        *     20980890  51697169   15358140    c   W95 FAT32 (LBA)
/dev/sda3              51697170  625137344  286720087+  7   HPFS/NTFS

Partition1 doesn't end on a cylinder frontier (don't know why, I didn't change sda1 size, Acer did that, it's an hidden partition.

Yes, I will delete sda3

vista dump size : 154666008576  ( after 3 hours of decompression ;) Next time I'll use 7za...

Sould I do :
mkpartfs primary ntfs 20980890 20980890+"result from bzcat /vistadump.bz2 | wc -c"=154686989466

---

### Post by caljohnsmith on 2008-11-10
> **probume said:**
> 
Sould I do :
```
mkpartfs primary ntfs 20980890 20980890+"result from bzcat /vistadump.bz2 | wc -c"=154686989466
```
I think that will work, but theoretically I think the stop point should be:
```
stop point = start sector + partition size - 1
```
In other words, say if the Vista partition were just 2 sectors in size, and if the start point were sector 3, then using your method the stop point would be 3+2=5; but if the partition goes from sector 3 to sector 5, it is actually 3 sectors in size since we have to count the first starting sector: sectors 3, 4, and 5 = 3 sectors total. Thus the minus one in the formula above.

So if that's true, I think you should instead use:
```
stop point = 20980890 + 154666008576/512 - 1 = 323062937 sectors
```
Note the divided by 512 is to convert your Vista byte size to sectors. So bottom line, I would do:
```
sudo parted /dev/sda
rm 2
mkpartfs primary ntfs 20980890s 323062937s
```
Make sure to include the "s" at the end of the numbers so parted knows the numbers are in sectors. Note the "rm 2" will first delete the sda2 partition, because you want to recreate sda2 with the next "mkpartfs" command. Once you've confirmed the partition is now the correct size and is still called sda2, you could copy over your Vista partition with:
```
bzcat /path/to/my/dumpedvista.bz2 | sudo dd of=/dev/sda2 bs=10M conv=notrunc
```
Note setting the dd block size to 10 MB will be alot faster than using dd's default 512 byte block size. Once that is all finished, I would try mounting the new Vista partition and making sure you can access your files:
```
sudo mount /dev/sda2 /mnt
ls -l /mnt
```
Anyway, give that a shot and let me know how it goes. :)

---

### Post by probume on 2008-11-10
Very good support caljohnsmith :)
Good explanation and it's a pleasure to understand what I'm doing.
I'll give it a try tommorow, I must sleep if I don't want to make a mistake ;) By the way, if it doesn't work, should I always be able to boot on linux ? I'm really afraid of grub not being able to boot linux anymore... And if it works, do I have something to change in grub conf to make it able to boot vista or will the current conf for XP work ?

---

### Post by caljohnsmith on 2008-11-10
> **probume said:**
> Very good support caljohnsmith :)
Good explanation and it's a pleasure to understand what I'm doing.
I'll give it a try tommorow, I must sleep if I don't want to make a mistake ;) By the way, if it doesn't work, should I always be able to boot on linux ? I'm really afraid of grub not being able to boot linux anymore... And if it works, do I have something to change in grub conf to make it able to boot vista or will the current conf for XP work ?
I assume you didn't post the full output of the fdisk command, because it only shows your sda drive; you mentioned Ubuntu was on your other drive. Anyway, you should be fine booting Ubuntu on the other drive, because you are only changing partitions on the sda Windows drive. Also, if the new partition that you create is sda2 again (which it should be), then most likely your Grub entry for Windows will work fine since it worked before. If the sda2 partition that you create is not exactly the same offset from the beginning of the HDD as the original Vista partition, I've heard from the experience of others that that could be a problem. But if the XP partition starts exactly where your old Vista partition did, I don't think you'll have a problem with that particular issue. 

The fact that you can't boot your CD/DVD drive any more is unfortunately a severe limitation, because if Vista needs even some minor repairs to get it working, you might be stuck. So it's up to you whether its worth deleting XP to replace it with Vista, knowing that there is definitely a risk involved. Let me know how it goes. :)

---

### Post by probume on 2008-11-12
:KS Here a star for you caljohnsmith !
All is working perfectly well, I now have Vista and Ubuntu :) Thank you so much !

All the step for people with the same problem (can't boot on media and want to reinstall another OS from partition dump/disk image when the partition table has changed, don't know if we are a lot ;)
See uper post for example if I'm not clear.

1 - Bzcat /path/to/image.bz2 | wc -c    (To find your image size in bytes (replace bzcat by the appropriate decompressor if not Bzip2) Let's assume the given number is x)
2 - Convert it to sector by deviding x by 512 = y sector and type  
sudo fdisk -lu (to see you partitions number, size, starting and ending sector)
3 - sudo parted /dev/sda
    rm 'partition number'  ( to remove some partition if you don't have enough space )
    mkpart primary "last partition end sector + 1"s "y"s (don't type the ")
Let's assume this new partition is sda2 change to the appropriate number for your case.
****WARNINGS*****
Linux has automatically mount my new partition, if so for you, umount your this partition before step 4
I don't know how GRUB work to find partitions but the surest way, if grub alreaydy boot another system, is to keep the same starting sector as this system for your new partition so that grub find it. But anyway, the partition number must be the same (in my case xp was on hd0,1 partition created for vista was hd0,1 too). I think it's the only important think for GRUB, and that the staring sector doesn't matter but I'm not sure !!! If someone knows...
*****************
4 - Bzcat /path/to/image.bz2 | sudo dd of=/dev/sda2 bs=10M conv=notrunc

Notes : 
- mkparts with ntfs didn't work, parted told me that it wasn't implemented yet... but no matter, all is included in such an image, you don't need to format your partition
- I now know dd is a bad way to make OS images, prefer partimage if possible (sometime won't work with NTFS, but if the image is created succefully, then it will rewrite succefully to) because your partition size doesn't have to be the same as when you did your image.


Hope all is clear ;)

---

### Post by caljohnsmith on 2008-11-12
That's great news, I'm glad it worked. Cheers and have fun with all your OSes. :)

---

