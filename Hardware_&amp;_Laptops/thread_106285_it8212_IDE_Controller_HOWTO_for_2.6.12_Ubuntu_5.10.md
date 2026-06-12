---
title: "it8212 IDE Controller HOWTO for 2.6.12 Ubuntu 5.10 Breezy Badger"
date: 2005-12-20
forum: Hardware &amp; Laptops
---

### Post by jimbosyn on 2005-12-20
**it8212 IDE Controller HOWTO for 2.6.12 Ubuntu 5.10 Breezy Badger**

**Description:**
This quick and dirty HOWTO was derived from my install notes.  I moved from CENTOS 4 to Ubuntu 5.10 (Breezy Badger) only to discover that my IT8212 pci ide controller was not supported by the Ubuntu 2.6.12 kernel.  This posed a problem for me since I needed to have support for my SOHO file server without purchasing a new controller card.  By following these instructions, you will be able to add support for the it821x cards to the standard ubuntu kernel with minimal fuss.
[B]
Background:[/B]
The problem I encountered with my it8212 was that it was simply not supported in the 2.6.12 series kernel.  The card is supported in later kernel releases, I believe starting with 2.6.15.  I tried the Dapper Drake Alpha CD and there was support for the card.  Dapper was however a little too experimental for my blood and I had many problems with networking and printing support. There is an -ac (Alan Cox) patch set on [http://www.kernel.org](http://www.kernel.org) that adds support for the it8212 , however this patch set is only compatible with 2.6.11 kernels. This was no good since I wanted to maintain full compatibility with the default Breezy kernel which was a 2.6.12 base.  I attempted to compile the kernel module from the manufacturer's website only to discover that it was not compatible with newer 2.6.x kernels. 

**Solution:**
I finally discovered that Alan Cox had back ported the 2.6.15 it8212 driver to 2.6.12 and posted it to the LKLM (Linux Kernel Mailing List) in the form of a patch(well, actually 2 patches).  I applied these patches and recompiled the kernel.  Now I have Breezy Badger stability with the added support for my it8212 ide controller card.  Here is the process to recompile your kernel with the Alan Cox it8212 patches.  The method used to recompile the kernel is distilled from the Ubuntu Kernel Howto on the Ubuntu WIKI.

**Technical Notes:** 
Here is the output from my lspci:
```
bash:~$ sudo lspci | grep IT
0000:00:0b.0 Unknown mass storage controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (PCI version seems to be IT8212, embedded seems (rev 13)
```

**References:**
* Ubuntu Kernel Howto:
[https://wiki.ubuntu.com/KernelHowto](https://wiki.ubuntu.com/KernelHowto)
* Alan Cox it8212 Patches:
[http://lkml.org/lkml/2005/6/20/210](http://lkml.org/lkml/2005/6/20/210)
[http://lkml.org/lkml/2005/6/20/265](http://lkml.org/lkml/2005/6/20/265)
* Ubuntu bugzilla id 21329.
[http://bugzilla.ubuntu.com/show_bug.cgi?id=21329](http://bugzilla.ubuntu.com/show_bug.cgi?id=21329)


**Procedure:**

1) Add yourself to the "src" group
```
bash:~$ sudo adduser my_username src
Adding user my_username to group src...
Done.
```

1a) Log out and back, then verify you are in the "src" group.
```
bash:~$ groups
my_username src audio adm dialout cdrom floppy video plugdev lpadmin
```

2) Obtain kernel source and build environment.
```
bash:~$ sudo apt-get install linux-source libncurses-dev fakeroot kernel-package
```

3) Unpack the source.
```
bash:~$ cd /usr/src
bash:~$ rm linux
bash:~$ tar -jxvf linux-source-2.6.12.tar.bz2
```

4) Add links necessary to apply the patches.
```
bash:~$ ln -s linux-source-2.6.12 linux
bash:~$ ln -s linux-source-2.6.12 linux-2.6.12
```

5) Download the patch files.
```
bash:~$ wget -O patch1-it8212 http://lkml.org/lkml/diff/2005/6/20/210/1
bash:~$ wget -O patch2-it8212 http://lkml.org/lkml/diff/2005/6/20/265/1
```


6) Apply the patches.
```
bash:~$ patch -p0 < patch1-it8212 
patching file linux-2.6.12/drivers/ide/ide-disk.c

bash:~$ patch -p0 < patch2-it8212 
patching file linux-2.6.12/drivers/ide/Kconfig
patching file linux-2.6.12/drivers/ide/pci/it821x.c
patching file linux-2.6.12/drivers/ide/pci/Makefile
patching file linux-2.6.12/include/linux/pci_ids.h
Hunk #1 succeeded at 1821 (offset 11 lines).
```

7) Copy the kernel config from /boot and configure kernel.
```
bash:~$ cp /boot/config-`uname --kernel-release` ./.config
bash:~$ cd /usr/src/linux
bash:~$ make oldconfig
```

8 ) Verify the module is configured.
```
bash:~$ grep IT821X .config
CONFIG_BLK_DEV_IT821X=m
```
*NOTE: If the line "CONFIG_BLK_DEV_IT821X=m" does not appear, something has gone wrong...

9) Build the kernel.
```
bash:~$ fakeroot make-kpkg clean
bash:~$ fakeroot make-kpkg --append-to-version=-it821x kernel_image --initrd binary
```
*NOTE: This will take a while! My system took 45 minutes(AMD Athlon XP 2400+ with 768mb ram)

10) Install the newly built kernel package.
```
bash:~$ cd /usr/src
bash:~$ sudo dpkg -i kernel-image-2.6.12-it821x_10.00.Custom_i386.deb
Selecting previously deselected package kernel-image-2.6.12-it821x.
(Reading database ... 70698 files and directories currently installed.)
Unpacking kernel-image-2.6.12-it821x (from kernel-image-2.6.12-it821x_10.00.Custom_i386.deb) ...
Setting up kernel-image-2.6.12-it821x (10.00.Custom) ...
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.12-it821x
Found kernel: /boot/vmlinuz-2.6.12-10-386
Found kernel: /boot/vmlinuz-2.6.12-9-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```


11) Reboot your computer to enable the new kernel

---

### Post by ronmonki on 2005-12-22
Firstly many thanks for taking the time to write this, as I was totaly lost without it , I have found that I have had to preface a lot of the commands with sudo to get them to run. but i am getting this error when running the second fakeroot make pakg command:

any help would be much appreciated.

fs/inode.c:1093: error: static declaration of ‘generic_drop_inode’ follows non-static declaration
include/linux/fs.h:1418: error: previous declaration of ‘generic_drop_inode’ was here
make[2]: *** [fs/inode.o] Error 1
make[1]: *** [fs] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2
ossie@laskoreh:/usr/src/linux-2.6.12$

---

### Post by ronmonki on 2005-12-22
I had made a link to the correct version of GCC instead of installing the correct verision, so what i did was to install GCC 3.4 this fixed it, also setting MAKEFLAGS="CC=gcc-3.4" would have also solved it.

hope this helps someone else..

---

### Post by brakmaren on 2005-12-28
MILLIONS thank's mate.
You just removed the last obstacle for me to migrate compleatly to Ubuntu.
It's hard to install it on a machine where you can't reach the hd's ;) 
Altough
> bash:~$ sudo apt-get install linux-source libncurses-dev fakeroot kernel-package
did not work for me. a had to write
---
bash:~$ sudo apt-get install linux-source[COLOR="Red"]-2.6.12[/COLOR] libncurses-dev fakeroot kernel-package
---
to get it to work.

I can also add if another Noob is tryin this that after you've run [COLOR="Red"]make oldconfig[/COLOR] and it halts at  
[COLOR="Red"]IT821X IDE support (BLK_DEV_IT821X) [N/m/?] (NEW)[/COLOR]. Don't do like me, and hit the enter key :-o.
Hit the [COLOR="Red"]m[/COLOR] key instead :-)

//Anders

---

### Post by brakmaren on 2005-12-28
I'm running 2.6.12-k7. And i don't see a k7 linux source. 
1. Is there some way to do this AND keep the tweaks in k7 ?
2. Also, what will happen if a updated kernel hits the repositorys? 
    Will my kernel get updated, or have i 'broken' the auto update for the kernel ?

---

### Post by bwrutter on 2006-02-05
Great, Works like a charm if the IT8212 is set as a module. The IDE's are identified as hde....hdh.

However if hde is put into /etc/fstab then the reboot fails. Can use a mount command fine once the system is up...

Also on compiling into the kernel using "make menuconfig" the ide channels get swapped hda becomes hde and I get a kernel panic.

Still working the issue...

---

### Post by simplyadrian on 2006-02-21
When preforming the make oldconfig command it does not halt and prompt me to  set IT821X ide support to M and grep IT821X .conifg comes back with it not being set... How can I set the IT821X ide support to make?

---

### Post by simon0t7 on 2006-02-25
nice, thanks for teh guide!

---

### Post by grap3fruitman on 2006-04-26
I get an error during step nine; the compiling of the kernel:

> CC [M] drivers/ide/pci/amd74xx.o
CC [M] drivers/ide/pci/atiixp.o
CC [M] drivers/ide/pci/cmd64x.o
CC [M] drivers/ide/pci/cs5520.o
CC [M] drivers/ide/pci/cs5530.o
CC [M] drivers/ide/pci/sc1200.o
CC [M] drivers/ide/pci/cy82c693.o
CC [M] drivers/ide/pci/hpt34x.o
CC [M] drivers/ide/pci/hpt366.o
make[4]: *** No rule to make target `drivers/ide/pci/it821x.c', needed by `drivers/ide/pci/it821x.o'. Stop.
make[3]: *** [drivers/ide/pci] Error 2
make[2]: *** [drivers/ide] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2
user@ubuntu:/usr/src/linux$ 

Help. :cry:

---

### Post by RoboSK on 2006-05-07
Hello, i im compile it821x support as module, but i need BOOTING from HDD in it821x - in module does`n work, i need compile into kernel - is any way ?

thanks

---

### Post by bond711 on 2007-08-27
will this still work for the newer kernels?

---

