---
title: "error 17"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by freeeki on 2009-02-10
Hi,

i am a first time ubuntu (or linux) user.
i have installed linux together with vista, which worked fine until i tried to use neogrub as an extension to the vista boot loader.
i followed the instructions as displayed [here]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")

when i start up i get to choose between vista or linux but when i choose linux i get the error 17 message, saying that a specific file cannot be found...

i've looked on the forum for similar problems and based on what was stated there i've done the following

i've mounted the linux partition from the ubuntu live cd to find the content of my menu.lst file:

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		9b3007f0-0cb9-4c24-a198-0f092f3447da
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9b3007f0-0cb9-4c24-a198-0f092f3447da ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		9b3007f0-0cb9-4c24-a198-0f092f3447da
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9b3007f0-0cb9-4c24-a198-0f092f3447da ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9b3007f0-0cb9-4c24-a198-0f092f3447da
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9b3007f0-0cb9-4c24-a198-0f092f3447da ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9b3007f0-0cb9-4c24-a198-0f092f3447da
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9b3007f0-0cb9-4c24-a198-0f092f3447da ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9b3007f0-0cb9-4c24-a198-0f092f3447da
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1
```


and i've tried the fdisk -l thing (don't really know why), which gave me this:

```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1964    15728640    7  HPFS/NTFS
/dev/sda3   *        1964       52957   409603068    7  HPFS/NTFS
/dev/sda4           52958       91201   307194930    5  Extended
/dev/sda5           52958       89647   294712393+  83  Linux
/dev/sda6           89648       91201    12482473+  82  Linux swap / Solaris

```

so my vista is on the sda3 partition
and ubuntu is on the sda5

hope this helps you help me :)

thanks

---

### Post by Pumalite on 2009-02-10
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by freeeki on 2009-02-10
i tried the filesystem check:

```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda5
                                                                               
  125543 inodes used (0.68%)
     654 non-contiguous inodes (0.5%)
         # of inodes with ind/dind/tind blocks: 5883/49/0
 1853822 blocks used (2.52%)
       0 bad blocks
       1 large file

   92404 regular files
   15035 directories
      69 character device files
      26 block device files
       3 fifos
     101 links
   17993 symbolic links (16917 fast symbolic links)
       4 sockets
--------
  125635 files

```

gonna try to reboot and see if it makes a difference

---

### Post by freeeki on 2009-02-10
so the filesystem check didn't make a difference

i've also tried to replace this

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
**uuid		9b3007f0-0cb9-4c24-a198-0f092f3447da**
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9b3007f0-0cb9-4c24-a198-0f092f3447da ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

```

by this

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
**root		(hd0,4)**
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=9b3007f0-0cb9-4c24-a198-0f092f3447da ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

```

this gave the following message:

```
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=9b3007f0-0cb9-4c24-a198-0f092f3447da ro quiet splash

Error 2: Bad file or directory type
```

any ideas

---

### Post by caljohnsmith on 2009-02-10
If I remember correctly, the NeoGrub that comes with EasyBCD cannot handle the newer ext3 file system that Intrepid uses, because Intrepid formats its ext3 partitions to sue an inode size 256 bytes instead of 128 bytes that previous Ubuntu versions used. Thus you get a Grub error 2. If you really want to use EasyBCD to boot Ubuntu, I think your best bet is to install Grub to the boot sector of your Intrepid partition, and then "chain load" that boot sector with EasyBCD. They have a tutorial about it here:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Good luck and let me know how it goes.

---

### Post by freeeki on 2009-02-10
> **caljohnsmith said:**
> If I remember correctly, the NeoGrub that comes with EasyBCD cannot handle the newer ext3 file system that Intrepid uses, because Intrepid formats its ext3 partitions to sue an inode size 256 bytes instead of 128 bytes that previous Ubuntu versions used. Thus you get a Grub error 2. If you really want to use EasyBCD to boot Ubuntu, I think your best bet is to install Grub to the boot sector of your Intrepid partition, and then "chain load" that boot sector with EasyBCD. They have a tutorial about it here:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Good luck and let me know how it goes.

i am sorry, but could you explain what you've posted a bit further...

do i understand correctly from the link that you have sent me that i should re-install ubuntu all together?

do you suggest an alternative for booting with EasyBCD?
its not that i really want to use it,
being new to this i just did what i was told...
:)

as an alternative i have tried to re-install GRUB using the live cd as instructed here [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

i have done 
> grub> find /boot/grub/stage1

which gave me
> (hd0,4)

then i have done
> grub> root (hd0,4)

but instead of getting something like this
> Filesystem type is ext2fs, partition type 0x83

i just got
> root (hd0,4)

and then i don't really know how to proceed
(if that is at all possible, considering the strange response i got on the last command)
should i install GRUB to MBR or to a partition?


sorry for the trouble
thanks

---

### Post by caljohnsmith on 2009-02-10
> **freeeki said:**
> 
should i install GRUB to MBR or to a partition?

Since you mentioned that it doesn't matter to you whether you use EasyBCD or not, I would definitely recommend just installing Grub to the MBR and using it as your boot manager. From your Live CD, how about doing:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
Then reboot, and you should be able to boot into Ubuntu if all goes well. If your Grub menu does not all ready have a working entry to boot Vista, how about posting:
```
sudo fdisk -lu
```
And we can work from there.

---

### Post by freeeki on 2009-02-10
okay,

i ve continued with the installation of GRUB on (hd0,4)
and then i ve added the entry to EasyBCD as instructed by the link that you provided

and it works now!!

thanks guys

just one final question
apparently ubuntu has created a swap partition
i first tried to add that to EasyBCD but that didn't work
then i used the other partition, the one on which ubuntu is installed, and that worked
what does the swap partition do?
what is it for?
should i have installed GRUB to that partition?

thanks again...
:)

---

### Post by caljohnsmith on 2009-02-10
You don't need to boot the swap partition or install Grub to its boot sector, the swap partition is used basically as virtual memory when you are using all your RAM. Here's some more info:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Anyway, glad to hear you can boot Ubuntu OK now.

---

