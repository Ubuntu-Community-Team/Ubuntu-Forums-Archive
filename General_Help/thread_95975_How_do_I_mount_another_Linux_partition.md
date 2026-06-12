---
title: "How do I mount another Linux partition?"
date: 2005-11-27
forum: General Help
---

### Post by Noelinho on 2005-11-27
hmm, what about mounting something like another linux partition?

I havew fedora installed, and want to access that - it would probably be on (0,2).

---

### Post by Bachstelze on 2005-11-27
[QUOTE=Noelinho]hmm, what about mounting something like another linux partition?

I havew fedora installed, and want to access that - it would probably be on (0,2).[/QUOTE]

It works exactly the same like mounting a fat 32 partition.

---

### Post by Noelinho on 2005-11-27
I get this:

```
mount: /dev/hda3 already mounted or /media/fedora/ busy
root@dyn224143:/home/noel# sudo mount /dev/hda2 /media/fedora/ -t ext2 -o iocharset=utf8,umask=000
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

How would I find out what the file extension is? In fdisk it just says Linux.

In fact, here is my fdisk:

```
root@dyn224143:/home/noel# fdisk -l

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5115    41086206    7  HPFS/NTFS
/dev/hda2            6399        6411      104422+  83  Linux
/dev/hda3            6412        9733    26683965   8e  Linux LVM
/dev/hda4            5116        6398    10305697+   5  Extended
/dev/hda5   *        5116        6341     9847813+  83  Linux
/dev/hda6            6342        6398      457821   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 1027 MB, 1027604480 bytes
16 heads, 32 sectors/track, 3920 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3920     1003504    b  W95 FAT32
```

hda5 in my Ubuntu partition, hda1 is Windows XP.

---

### Post by Bachstelze on 2005-11-27
If it is Linux and not ext2 then is certainly is ext3.

---

### Post by Noelinho on 2005-11-27
I had the same problem though.

---

### Post by Bachstelze on 2005-11-27
Then you may want to run System > Administration > Disks to find out more

---

### Post by Noelinho on 2005-11-27
/dev/hda2 is ext3, 102Mb.

/dev/hda3 is apparently unformatted, 25.45Gb.

Both are labelled inaccessible.

---

### Post by Bachstelze on 2005-11-27
And which is the one you want to mount ?

---

### Post by Noelinho on 2005-11-27
The one with my Fedora installation and files, which would be /hda3.

---

### Post by anil_robo on 2005-11-27
[quote=Noelinho]hmm, what about mounting something like another linux partition?

I havew fedora installed, and want to access that - it would probably be on (0,2).[/quote] 
Check: [http://www.ubuntuguide.org/#mountunmountfat]("http://www.ubuntuguide.org/#mountunmountfat")

---

### Post by Noelinho on 2005-11-27
I have, it's not helped :)

---

### Post by Bachstelze on 2005-11-27
[QUOTE=Noelinho]The one with my Fedora installation and files, which would be /hda3.[/QUOTE]

Hang on now... If you have Fedora installed on it, it should definitely be formatted as ext2/3. Try running Fedora and finding the same thing as the Ubuntu Disk Manager and see what it tells. It's really weird :/

---

### Post by Noelinho on 2005-11-27
Yeah, well the reason I'm trying to mount fedora in ubuntu is because when I installed Ubuntu, it didn't recognise Fedora, and I haven't been able to edit GRUB because I don't know the kernel build etc for the GRUB loader to load it :mad:

---

### Post by Bachstelze on 2005-11-27
Then I really don't know. The only solution I see is reinstalling Fedora with your partition formatted as ext3, but there might be something better...

---

### Post by Noelinho on 2005-11-27
Hmm, ok. Thanks for your help anyway. It's a real pain, all I want is to copy my files over to Ubuntu, or at least be able to mount them! What a polava.

Never mind, thanks anyway.

---

### Post by Kevinator on 2005-11-27
[QUOTE=Noelinho]hmm, what about mounting something like another linux partition?

I havew fedora installed, and want to access that - it would probably be on (0,2).[/QUOTE]
(0,2) looks like GRUB's partition syntax. mount uses the linux syntax: /dev/hda3, for example.

---

### Post by Noelinho on 2005-11-27
Yeah, it is, but that's not what the problem is.

---

### Post by Kevinator on 2005-11-27
[QUOTE=Noelinho]Yeah, well the reason I'm trying to mount fedora in ubuntu is because when I installed Ubuntu, it didn't recognise Fedora, and I haven't been able to edit GRUB because I don't know the kernel build etc for the GRUB loader to load it :mad:[/QUOTE]
Don't you just need to tweak /boot/grub/menu.lst?

---

### Post by Noelinho on 2005-11-27
Yeah, and I've tried to add Fedora, with:

```
title		Fedora Core 4, kernel 2.6.14-1.1637
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.14-1.1637_FC4 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd		/boot/initrd.img-2.6.14-1.1637_FC4.img
boot
```

Trouble is, there's a problem with either the kernel or initrd lines. I've a feeling it's the kernel build, but I have no idea.

I originally installed it from the August DVD from Linux Magazine, with kernel build 2.6.11, which would still be there (although it's been updated twice since), so if I could find out the exact build / initrd line from that, I could probably recover it. Trouble is, I don't, as don't know how/where to find out :(

---

### Post by Kevinator on 2005-11-27
Right, so you need to mount it just to figure out what kernels and initrds are available. But the Gnome disk manager says it appears to be unformatted. I'm afraid the partition has been corrupted somehow. Maybe you can do a fsck on it and find out more.

---

### Post by Noelinho on 2005-11-27
This is what I got:

```
root@dyn224143:/home/noel# fsck /dev/hda3
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/hda3

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@dyn224143:/home/noel# fsck /dev/hda2
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/boot: clean, 52/26208 files, 33890/104420 blocks.
```

---

### Post by Kevinator on 2005-11-28
Yeah, it definitely sounds like it's not a valid ext2 partition (and therefore also not a valid ext3 partition). If you are really sure that it was formatted as ext3 then I think you can assume some form of corruption and turn your attention to figuring out if and how you can recover anything.

If you aren't completely sure, maybe there's a tool available that can probe the partition and attempt to guess the file system?

---

### Post by Noelinho on 2005-11-28
Proble, solved - I decided to try mounting the drives in Windows. Managed it in 5 minutes, retrieved the grub file, ammended the real one, et voila, it all works :)

---

