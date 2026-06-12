---
title: "[HOWTO] Highpoint RocketRAID 2640x4 Driver Install"
date: 2011-12-23
forum: Hardware
---

### Post by ionospheric on 2011-12-23
This is to explain the simplest way to get the Highpoint RocketRAID 2640x4 RAID controller card to work with Ubuntu. I will get to the problems I faced later, let me just say that it is a sad state of affairs when you have to recommend others NOT to use the driver installer that is posted on the manufacturers web site. Building the driver on your system means no worries about the kernel version not matching the driver.

I chose Ubuntu 10.04 because it is the most recent long term support version.
Hardware: 
- Highpoint RocketRAID 2640x4 RAID controller
- two Patriot TorqX 64GB SSD drives on the RAID controller
- one Patriot TorqX 64GB SSD drive on the mainboard SATA controller for the OS

Steps:
- Install the card in your system and connect the SATA drives.
- Boot the system, and a new BIOS setup screen will come up that is  controlled by the RAID controller
-Hit CTRL-H to get into the RAID controller setup.
- Create a RAID array
- Reboot

Note that you can setup a RAID array without installing any drivers.

Next:
- Start Ubuntu
- Verify that the hardware is present and recognized:
```
lspci
```
- Download the source code archive rr264x-linux-src-v1.3-legacy_single-101203-0910.tar.gz from
[http://www.highpoint-tech.com/USA_new/rr2600_download.htm]("http://www.highpoint-tech.com/USA_new/rr2600_download.htm")
(It is called "Linux Open Source" and the link is v1.3)

- Now install the build environment
```
sudo apt-get install build-essential checkinstall
```

- change into the source directory:
```
cd rr2640-linux-src-v1.3-legacy_single/product/rr2640/linuxls
```

- Build the driver
```
sudo make install
```

- Load the driver
```
sudo modprobe rr26xx
```

- Verify that the driver is loaded
```
lsmod
```

If everything went well, you can now use gparted to verify that a new volume is available (on my system, it is /dev/sdb).

- use gparted to create a partition table and a partition

- add an according line to /etc/fstab:
```
/dev/sdb1 /mnt/raid               ext4    errors=remount-ro 0       1
``` 

- create a mount location
```
sudo mkdir /mnt/raid
```

- change permissions to your username:
```
sudo chown -R username:username /mnt/raid
```

- mount the new volume
```
sudo mount /mnt/raid
```

You should now be able to use the RAID array like any other storage.

The manufacturer offers a GUI to control the RAID array, and that is where the problems start. There are only RPMs, no deb packages, and when you convert the RPMs to deb's with alien as suggested, you end up with broken packages.

More info on this:
[http://ubuntuforums.org/showthread.php?p=10712667]("http://ubuntuforums.org/showthread.php?p=10712667")

[http://ubuntuforums.org/showthread.php?t=1608698]("http://ubuntuforums.org/showthread.php?t=1608698")

Once it works, the performance is pretty good: 200 MB/s read, and between 100-200 MB/s write. An SSD-RAID server for Christmas! :D

---

### Post by pals0007 on 2012-10-10
The "make" command does not work for me, any ideas?

wisdom@Mint-Desktop /usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux $ sudo make install
make[1]: Entering directory `/usr/src/linux-headers-3.6.1-030601-generic'
  CC [M]  /usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/os_linux.o
  CC [M]  /usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.o
/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.c: In function ‘scsicmd_buf_get’:
/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.c:452:39: error: ‘KM_BIO_SRC_IRQ’ undeclared (first use in this function)
/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.c:452:39: note: each undeclared identifier is reported only once for each function it appears in
/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.c:452:2: error: too many arguments to function ‘kmap_atomic’
include/linux/highmem.h:66:21: note: declared here
/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.c: In function ‘scsicmd_buf_put’:
/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.c:482:55: error: macro "kunmap_atomic" passed 2 arguments, but takes just 1
/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.c:482:2: error: ‘kunmap_atomic’ undeclared (first use in this function)
make[2]: *** [/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.o] Error 1
make[1]: *** [_module_/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.6.1-030601-generic'
make: *** [rr62x.ko] Error 2

---

### Post by pals0007 on 2012-10-11
ANY help out there?????????????

---

### Post by ZoZo on 2012-10-13
> **pals0007 said:**
> The "make" command does not work for me, any ideas?

wisdom@Mint-Desktop /usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux $ sudo make install
make[1]: Entering directory `/usr/src/linux-headers-3.6.1-030601-generic'
  CC [M]  /usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/os_linux.o
  CC [M]  /usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.o
/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.c: In function &#8216;scsicmd_buf_get&#8217;:
/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.c:452:39: error: &#8216;KM_BIO_SRC_IRQ&#8217; undeclared (first use in this function)
/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.c:452:39: note: each undeclared identifier is reported only once for each function it appears in
/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.c:452:2: error: too many arguments to function &#8216;kmap_atomic&#8217;
include/linux/highmem.h:66:21: note: declared here
/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.c: In function &#8216;scsicmd_buf_put&#8217;:
/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.c:482:55: error: macro "kunmap_atomic" passed 2 arguments, but takes just 1
/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.c:482:2: error: &#8216;kunmap_atomic&#8217; undeclared (first use in this function)
make[2]: *** [/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build/osm_linux.o] Error 1
make[1]: *** [_module_/usr/local/src/rr62x-linux-src-v1.2/product/rr62x/linux/.build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.6.1-030601-generic'
make: *** [rr62x.ko] Error 2

This problem arises with kernel 3.6, since the following patches are included:
[https://lkml.org/lkml/2012/6/23/57](https://lkml.org/lkml/2012/6/23/57)
This makes the highpoint driver sources officially incompatible with kernel 3.6, so you can either downgrade to 3.5 and not ever upgrade until highpoint releases new drivers, or you can try to patch the highpoint drivers.

Edit: I succeeded in compiling the drivers, but they're the rr2340, not rr62x. What I did was look for calls to kmap_atomic and kunmap_atomic in the source code (under os_linux.c and osm_linux.c in my case), and removed their second argument (HPT_something). Then I deleted the #define lines referring to KM_BIO_SRC_IRQ (under osm_linux.h in my case), they weren't needed anymore. Then 'make install' and voilà. You can try the same technique on your side.

---

### Post by linuxkidd on 2012-10-20
The modifications described by ZoZo worked for rr62x.

Patch file attached.

NOTE: I've not rebooted onto this driver yet, so I can't confirm the driver functions, but it does compile cleanly.

---

### Post by pals0007 on 2012-10-20
> **linuxkidd said:**
> The modifications described by ZoZo worked for rr62x.

Patch file attached.

NOTE: I've not rebooted onto this driver yet, so I can't confirm the driver functions, but it does compile cleanly.

Linuxkidd,

Thanks for the patch, but I am new to all this, could you explain what I do with it now?
thanks

---

### Post by LeighOrf on 2012-10-26
Thank you very much for the patch. I applied the same logic to the rr232x codebase and everything seems to be working fine.

I am a hair's breadth from chucking rocketraid and just doing all software raid (would rather not pay for a new motherboard and migrate everything over). One of these days, their code is just going to no longer work, I'm afraid. I have 4 1.5 TB drives hanging off and probably a few in the closet formatted with their layer on top. Such is life.

Until that day comes... every kernel upgrade is is a nailbiter, especially the major ones.

Thanks again for the patch.

---

### Post by pals0007 on 2012-11-25
Hey LK,

Thanks for helping me out before, worked like a charm, BUT, LOL
I upgraded the os, and it comes with 3.5 kernel. will the patch still work? secondly I tried the patch, I got no errors while patching the drivers but i do get an error on "sudo make install" the error i get is: 

/bin/sh: 1: cannot create /usr/local/src/Highpoint: Is a directory
make: *** [/usr/local/src/Highpoint] Error 2

Would you know how to solve this? thanks in advance for any advice.

---

### Post by pals0007 on 2012-11-25
OK after many F-ups and confusion here are the steps I used to get it installed, I hope this helps others.

#PREPARE SYSTEM
1. Verify the Card is recognized
```
lspci
```

2. Install the Build Tools
```
sudo apt-get install build-essential checkinstall
```

3. Build Version Management
```
sudo apt-get install cvs subversion git-core mercurial
```

4. Make a common build directory
```
sudo chown $USER /usr/local/src
```

5. Make the build directory writeable
```
sudo chmod u+rwx /usr/local/src
```

#APPLY PATCH FOR KERNALS 3.6 AND ABOVE
#OTHERWISE SKIP TO INSTALL DRIVER SECTION
1. tar -xzvf rr62x-linux-src-v1.2-120601-1355.tar.gz
2. cd rr62x-linux-src-v1.2
3. zcat ../rr62x-linux-src-v1.2.kernel-3.6.patch.gz | patch -p1

The patch will apply with output like the following:
patching file osm/linux/os_linux.c
patching file osm/linux/osm_linux.c
patching file osm/linux/osm_linux.h

Once this is done, the driver should compile like normal.

#INSTALL THE DRIVER
1. Go to "rr62x-linux-src-v1.2/product/rr62x/linux
2. Build Driver
```
sudo make install
```

3. Load Driver
```
sudo modprobe rr62x
```

4. Verify Driver is loaded
```
lsmod
```

##FINISHED

---

### Post by wigbam on 2012-11-29
Thank you very much for this patch! Works on 272x too.

---

### Post by pals0007 on 2013-01-01
Just installed kernel 3.7, now this doesnt work again, does any one know how to get the patch to work with 3.7 or future proof it with 3.8 compatability. Thanks in advance.

---

### Post by erni on 2013-01-04
Thanks all! Manage to patch the 3.7.1 kernel according to this patch. Now my rr2680 is working on 3.7.1 :D.
Hopefully the same will work on 3.8 when its released.

---

### Post by Viper187 on 2013-03-18
Could someone do an updated guide? The current driver version is 1.9. There's also an archive with old files, but they're a bunch of install scripts with no real instructions. I'm trying to get a 2640X1 card working on 10.04 64-bit. Looks like the download with the install scripts is only for kernal 2.6.32-21 as well. Current is 2.6.32-45, I believe.

---

### Post by Sundown89 on 2013-05-11
Can someone post the patch to get this working on 3.7.0 kernel? I can't seem to fix it myself.

---

### Post by andrew29 on 2013-09-01
pals0007's method works pretty well until kernel 3.10..

I got 
" unknown field name 'proc_info' " errors during compile...

Anyone can share the experience on kernel 3.10 ??

---

### Post by camper2 on 2013-09-28
At the moment none of the open source drivers for any rocketraid card  (safe for those with in-kernel sources) seem to support 3.10+
I made a patch for 2340 which appears to work (tested with Gentoo hardened-sources-3.10.1-r1).

[ATTACH]246574[/ATTACH]

---

### Post by camper2 on 2013-09-29
I've created patches for all rocketraid drivers with a similar structure.
Also (re)added patchkernel target to all drivers where it was missing.
Untested save for the rr2340 driver.

620,622: rr62x-linux-src-v1.2-kernel-3.11.patch
640,644: RR64x-Linux-Src-v1.1-kernel-3.11.patch
640L,642L,644L,644LS: RR64xl-Linux-Src-v1.3-kernel-3.11.patch
1720: rr172x-linux-src-v1.2-kernel-3.11.patch
1740,1742: rr174x-linux-src-v2.4-kernel-3.11.patch
2210: rr2210-linux-src-v1.5-kernel-3.11.patch
2220,2224: rr222x-linux-src-v1.9-kernel-3.11.patch
2240: rr2240-linux-src-v1.11-kernel-3.11.patch
2300,2302,2310,2314: rr231x_0x-linux-src-v2.5-kernel-3.11.patch
2320,2322: rr232x-linux-src-v1.10-kernel-3.11.patch
2340: rr2340-linux-src-v1.7-kernel-3.11.patch
2522: rr2522-linux-src-v1.2-kernel-3.11.patch
2640X1,2640X4,2642: RR264x-Linux-Src-v1.5-kernel-3.11.patch
2644X4: RR2644-Linux-Src-v1.7-kernel-3.11.patch
2680,2684: RR268x-Linux-Src-v1.9-kernel-3.11.patch

[ATTACH]246613[/ATTACH]

---

### Post by bvanaerde on 2013-10-18
> **camper2 said:**
> 1740,1742: rr174x-linux-src-v2.4-kernel-3.11.patch
[ATTACH]246613[/ATTACH]
I have just tested this on Ubuntu 13.10 (kernel 3.11.0-12-generic) with RocketRaid 1740, this works flawlessly!
I cannot thank you enough for this...

---

### Post by ulysses768 on 2013-10-21
I successfully patched the rr272x driver by looking at camper2's patches.  It worked for me with kernel 3.11.0-12-generic.
Thanks
[ATTACH]247137[/ATTACH]

---

### Post by camper2 on 2013-10-26
New patchset with support for 27xx cards.
Updated version detection code - patchkernel should now work with an unconfigured kernel source tree without having to set KERNEL_VER

---

### Post by simen.storsveen on 2013-10-31
The patch works great with rr2640x4 and [COLOR=#000000]kernel 3.11.0-12-generic.
Thanks a lot!

[/COLOR]

---

### Post by misu3108 on 2013-11-10
how do you apply the patch? I have RocketRaid 2680 and can't get it to work. When I type hptsrv I get Driver is not loaded. I'm using ubuntu 12.04 x64. Any advice would be great.

Thanks.

---

### Post by misu3108 on 2013-11-10
> **camper2 said:**
> I've created patches for all rocketraid drivers with a similar structure.
Also (re)added patchkernel target to all drivers where it was missing.
Untested save for the rr2340 driver.

620,622: rr62x-linux-src-v1.2-kernel-3.11.patch
640,644: RR64x-Linux-Src-v1.1-kernel-3.11.patch
640L,642L,644L,644LS: RR64xl-Linux-Src-v1.3-kernel-3.11.patch
1720: rr172x-linux-src-v1.2-kernel-3.11.patch
1740,1742: rr174x-linux-src-v2.4-kernel-3.11.patch
2210: rr2210-linux-src-v1.5-kernel-3.11.patch
2220,2224: rr222x-linux-src-v1.9-kernel-3.11.patch
2240: rr2240-linux-src-v1.11-kernel-3.11.patch
2300,2302,2310,2314: rr231x_0x-linux-src-v2.5-kernel-3.11.patch
2320,2322: rr232x-linux-src-v1.10-kernel-3.11.patch
2340: rr2340-linux-src-v1.7-kernel-3.11.patch
2522: rr2522-linux-src-v1.2-kernel-3.11.patch
2640X1,2640X4,2642: RR264x-Linux-Src-v1.5-kernel-3.11.patch
2644X4: RR2644-Linux-Src-v1.7-kernel-3.11.patch
2680,2684: RR268x-Linux-Src-v1.9-kernel-3.11.patch

[ATTACH]246613[/ATTACH]

[SIZE=4]How do you apply the patch file?[/SIZE]

[SIZE=4]Can you please show the commands step by step?
I have RR2680 and cant install the drivers.[/SIZE]

Thanks.

---

### Post by irish-link on 2013-11-11
Open the tar file or extract it. Pick the .patch file that goes with your specific card. I have a rocket raid 622 so mine is rr62x-linux-src.......

Now that i have identified what file i want i can follow the patching process from [http://www.cyberciti.biz/faq/appy-patch-file-using-patch-command/](http://www.cyberciti.biz/faq/appy-patch-file-using-patch-command/)

So... you will need to do this in the command line
navigate to your source folder. 
So you will now see the folders (inc, lib, osm, product, README)

type "patch -p1 < /home/user/yourpatchfile.patch"
so my command line looked like this

cd /home/irish-link/rr62x-linux-src-v1.2

ls 
    inc
    lib
    osm
    product
    README

patch -p1 < /home/irish-link/rr62x-linux-src-v1.2-kernel-3.11.patch


This will then patch my files.

---

### Post by schorschi-v on 2013-11-17
Applied patch for rr6x with 1.1 sources from highpoint for 644 card.  Compiled and installed on 3.11-13 generic.  Drive recognized, show up as devices and in syslog apparently correctly.  Testing.  Will update post here after some basic testing done.  644 card has some issues under Windows, driver seems to have issues, a lot of bus resets, so should be interesting to see if under Linux same issue results.

Only issue during make...

root@psycho:~/rr64x-linux-src-v1.1/product/rr64x/linux# make ARCH=x86_64
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-13-generic'
  CC [M]  /root/rr64x-linux-src-v1.1/product/rr64x/linux/.build/os_linux.o
  CC [M]  /root/rr64x-linux-src-v1.1/product/rr64x/linux/.build/osm_linux.o
  CC [M]  /root/rr64x-linux-src-v1.1/product/rr64x/linux/.build/div64.o
  CC [M]  /root/rr64x-linux-src-v1.1/product/rr64x/linux/.build/hptinfo.o
  CC [M]  /root/rr64x-linux-src-v1.1/product/rr64x/linux/.build/config.o
  LD [M]  /root/rr64x-linux-src-v1.1/product/rr64x/linux/.build/rr64x.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /root/rr64x-linux-src-v1.1/product/rr64x/linux/.build/.him_magni.o.cmd for /root/rr64x-linux-src-v1.1/product/rr64x/linux/.build/him_magni.o
  LD [M]  /root/rr64x-linux-src-v1.1/product/rr64x/linux/.build/rr64x.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-13-generic'

Seems to be soft issue.  Make install worked regardless, modprobe of rr64x forced scans of disks and spin up of disks if needed.

---

### Post by bjforesthowell on 2013-11-22
How do you go about installing this patch? I'd love to get my array back up and running again.

Just read further up in the thread. I'll give this a shot first!

---

### Post by bjforesthowell on 2013-11-23
It worked like a champ! Thanks!

---

### Post by alexemena on 2013-12-03
Hey Everyone,

I new to building anything and looking for some help. I tried to follow others in this post however with little success. I have a rocket raid 2680 ubuntu 13.10 kernal 3.11.0-14-generic.

what ive done

$ cd /home/alex/rr268x-linux-src-v1.9/

$ patch -p1 < /home/alex/Desktop/rr268x-linux-src-v1.9-kernel-3.11.patch

patching file inc/linux_32mpa/Makefile.def
patching file osm/linux/hptinfo.c
patching file osm/linux/os_linux.c
patching file osm/linux/osm_linux.c
patching file osm/linux/osm_linux.h
patching file osm/linux/patch.sh

$ cd /home/alex/rr268x-linux-src-v1.9/product/rr2680/linux/

# make install

at this point it just hangs in process, it wont print anything any doesn't appear to be building anything. Would appreciate any help as I said im fairly new to this

---

### Post by Hudy on 2013-12-11
Adding my thanks here. Almost found this by accident, and now on fedora 19 I have 3.11 patched up thanks to your good work. Highpoint's web site is badly out of date, and I won't be buying anything by that company ever again.  But for now, I can keep using the one I have.

---

### Post by alexemena on 2013-12-11
Got a friend of mine to ssh into my computer to lend a hand.

Turns out I didn't have the kernel headers installed. Which is annoying because I checked for this, just not through apt.

BR

Alex

---

### Post by xhudik on 2013-12-13
cool, thanks for your work guys!!!! 

Patch  **rr64xl-linux-src-v1.3-kernel-3.11.patch** (from tar.gz package) is seamlessly working also **for RR64xl-Linux-Src-v1.3-130325-0207** taken from ([www.highpoint-tech.com/BIOS_Driver/RR64xL/Linux/RR64xl-Linux-Src-v1.3-130325-0207.tar.gz]("http://www.highpoint-tech.com/BIOS_Driver/RR64xL/Linux/RR64xl-Linux-Src-v1.3-130325-0207.tar.gz")) in new OpenSuse 13.1 (3.11.6)

well done!

---

### Post by martinblank64 on 2013-12-14
Hey guys, wondering if somebody can help. This is driving me absolutely insane. I've got a system with a RR 1740 RAID card and three drives configured in RAID 5. I am trying to install Lubuntu 13.10 (32-bit) on this system. From the live CD, I can successfully install the build tools, compile the kernel module and activate it using the patch from camper2. After that, everything goes downhill fast. I try to start gparted, and sometimes it takes a LONG time to scan for devices (like 15-20 minutes). It never actually finishes, and instead the speaker on the RAID card starts beeping.

Other times when I start gparted, it scans the drives relatively quickly, but instead of finding the array, it finds all three individual drives (!)??? And it has a strange warning about a partition table existing outside the drive. What on earth??? Has anybody else experienced/solved anything like this? This is with the 3.11 kernel. Keep in mind, it finds the individual drives WHILE they are part of an array and initialized in the RAID BIOS.

Here's the real kicker. I know neither the RAID card nor the drives are defective. I can install Windows Server 2003 on this system (same RAID 5 array) using the RAID drivers without any issue whatsoever.

---

### Post by xhudik on 2013-12-19
small addendum:

I have contacted Highpoint support - they are going to publish new source codes for their RR64 after some QA tests. They send me sources for 64x (version 1.3.5) it is working seamlessly. So if you have problems with applying patches, or willing to try new version, here it is... (**just be aware these source codes didn't go through official QA test. I was approved to upload it to a linux community**)

---

### Post by mesterkent on 2013-12-30
Thank you very much! Works perfectly with my rather ancient rr2320 card.

---

### Post by gapplewagen2 on 2014-01-30
I'm trying to compile the patched rr272x driver with the 3.11.0-15 kernel but I'm getting the following error:

```

sudo make install KERNELDIR=/lib/modules/3.11.0-15-generic/build
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
  CC [M]  /home/user/Documents/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build/os_linux.o
  CC [M]  /home/user/Documents/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build/osm_linux.o
  CC [M]  /home/user/Documents/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build/div64.o
  CC [M]  /home/user/Documents/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build/hptinfo.o
/home/user/Documents/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build/hptinfo.c: In function ‘hpt_proc_show_info’:
/home/user/Documents/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build/hptinfo.c:268:6: error: ‘start’ undeclared (first use in this function)
  if (start) *start = buffer;
      ^
/home/user/Documents/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build/hptinfo.c:268:6: note: each undeclared identifier is reported only once for each function it appears in
/home/user/Documents/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build/hptinfo.c:268:22: error: ‘buffer’ undeclared (first use in this function)
  if (start) *start = buffer;
                      ^
make[2]: *** [/home/user/Documents/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build/hptinfo.o] Error 1
make[1]: *** [_module_/home/user/Documents/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
make: *** [rr272x_1x.ko] Error 2

```

Any ideas?

---

### Post by gapplewagen2 on 2014-01-30
I was originally using rr272x_1x-linux-src-v1.5-kernel-3.11v2.patch from camper2's archive and it didn't work for me.  I went back and used the patch from ulysses768 and it worked fine for my rr2722.  Thanks!

---

### Post by mbksgx on 2014-02-09
hello, i have a 2680, and i was told the patch here works. however, some say it is not stable? i intend to use it for v12 server. thanks for any hints.

in view of the machine being a server v12, what would be a well supported 8 port card?

---

### Post by jdm12989 on 2014-02-20
My specs are:
rr2720sgl with BIOS v1.0
Gnombuntu 13.10 with kernal 3.11.0-17
hptsvr-2.1.5.13.0409
driver 1.5 with Ulysses's patch

My issue is that the raid card bios says my raid 5 is intact but the web management GUI say that no drives exist. Has anyone else seen this issue or know of anything I could check to investigate further?

Also does anyone know if updating the BIOS loses your raid configuration?
[!] I shutdown, disconnected the drives, rebooted, updated BIOS via the web gui.
Shutdown, reconnected the drives, and everything working with no data loss. Now running v1.5

---

### Post by irish-link on 2014-02-20
Hi all! First i want to say thank you to everyone on this thread. Every time i redo my server or have an inadvertent update i come back here. I recently contacted HPT support regarding my RR622 and they got back to me with Source 1.3.3. I wanted to make sure that i post it here if it can help anyone. Right now i am running Kern 3.11 and will be updating to 3.12 to see if it works. The readme states that it has only been tested with 3.10. I thought i would post it here because it is not up on their site. 


[ATTACH]250542[/ATTACH]

Edit: I just compiled with make / make install and am up and running. I can confirm that it works find with Kernel 3.12.11. 
I should note that i am running Fedora 19 but building from source for a Kernel is still the same. (I know this is an ubuntu forum but I haven't found a better source for this kind of help or a better community, also my laptop wasn't the one that needed the drivers my server was)

---

### Post by irish-link on 2014-02-20
> **jdm12989 said:**
> My specs are:
rr2720 with BIOS v1.0
Gnombuntu 13.10 with kernal 3.11.0-17
hptsvr-2.1.5.13.0409
driver 1.5 with Ulysses's patch

My issue is that the raid card bios says my raid 5 is intact but the web management GUI say that no drives exist. Has anyone else seen this issue or know of anything I could check to investigate further?

Also does anyone know if updating the BIOS loses your raid configuration?

jdm12989 At one point i had it not recognize that any drives existed but through the web manager i told it to re scan and they all showed up. Once that happened my raid 5 was back and running just fine. However i am using rr622. The web manager was still 1. something when this happened but its worth a shot.

---

### Post by jdm12989 on 2014-02-20
> **irish-link said:**
> jdm12989 At one point i had it not recognize that any drives existed but through the web manager i told it to re scan and they all showed up. Once that happened my raid 5 was back and running just fine. However i am using rr622. The web manager was still 1. something when this happened but its worth a shot.

I tried rescanning through the web manager as you suggested and I still have nothing...
Also found out that the newest version of web manager works with my card on Ubuntu 12.10. So there is something missing/wrong with the patch for 3.11.0-17.

---

### Post by Danny_Watts on 2014-03-01
Patched against 1.2 source on 12.04 (3.11) an everything worked great!

Installed via DKMS using instructions from: [https://help.ubuntu.com/community/RocketRaid#Updated_and_simplified_procedure_for_Ubuntu_13.04_or_later](https://help.ubuntu.com/community/RocketRaid#Updated_and_simplified_procedure_for_Ubuntu_13.04_or_later)

(starting @ step 5 after patch)

Thanks!!

---

### Post by egorks on 2014-03-06
> **camper2 said:**
> At the moment none of the open source drivers for any rocketraid card  (safe for those with in-kernel sources) seem to support 3.10+
I made a patch for 2340 which appears to work (tested with Gentoo hardened-sources-3.10.1-r1).

[ATTACH]246574[/ATTACH]

mate! 

patch worked perfectly for opensuse 13.1 kernel 3.11.10-7-default driver rr2680
opensource drivers from rocketraid v 1.9

thanks a bunch!

---

### Post by maarten5 on 2014-04-23
> **egorks said:**
> mate! 

patch worked perfectly for opensuse 13.1 kernel 3.11.10-7-default driver rr2680
opensource drivers from rocketraid v 1.9

thanks a bunch!

Didn't manage to get the array to show up on OpenSUSE 13.1 install. I downloaded the v1.5.12.0720 drivers from Highpoint and applied the patch

```
patch -p1 < /home/user/rr264x-linux-src-v1.5-kernel-3.11.patch
``` 

installed the build environment using


```
sudo zypper in -t pattern devel-kernel

```

then ran from /product/rr2640/linux


```
make install


sudo modprobe rr26xx

```

lsmod lists the module but the array doesn't appear. Any pointers at all would be very welcome (tia).

I also tried copying rr26xx.ko to a USB key and attempt to load that as a driver at installation time but no go, the installer doesn't seem to find any drivers, not sure if I missed a step there.

---

### Post by john198 on 2014-04-23
Hi all, just joined up about an hour ago to get this patch that the cool handyman: ***camper2*** cooked up :cool:

I use RR2340 and use 12 of the 16 connectors with the rest for spare as a big RAID 5 system, although partitioned in smaller ones.
All sorts of data on it mostly databases and web stuff, testing areas etc etc :razz:

I hope I won't get kicked out of here when I say I'm not a Ubuntu guy, I use Fedora 20 now and has always been a Red Hat dude
all the way back when it was called Red Hat 7, although didn't REALLY start working with Linux until Red Hat 9 :oops:

I just tried this 3.11 patch on my Fedora 20 machine, because I lost the M/B on the old one with Fedora 14 where the original drivers did work :biggrin:
The patch itself was OK and so was the compile of it, but I still haven't put the RAID card in and tested if I can read the data.

This F20 has kernel: > 3.13.9-200.fc20.x86_64
and I will get back to you when I get this finished with everything set up and let you know if this patch works for this too.

I bought this RAID card back in 2009 (I think) for almost $900 and it has not given me any problems what so ever unless you think of this :razz:
so why would I want to trough it away when it still works.
The only problems that I had was the WD Green that gave me lots of bad blocks after about a month or so running 24/7
so I switched to WD Black and no error so far :biggrin: and that's like a year since the last disk was replaced.

Anyhow... this setup will probably take a while as I've been trying to get this new setup running for about 4 weeks now,
I got lots of other stuff going on, but I will!!! be back to report the result of this test.

If it works... I will get down on my knees and pray to my new GOD... [http://ubuntuforums.org/member.php?u=1865547](http://ubuntuforums.org/member.php?u=1865547)


Merry XMas Evry1 :tongue: :tongue:

---

### Post by maarten5 on 2014-04-24
> **john198 said:**
> Hi all, just joined up about an hour ago to get this patch that the cool handyman: ***camper2*** cooked up :cool:  ...  I hope I won't get kicked out of here when I say I'm not a Ubuntu guy, I use Fedora 20 now and has always been a Red Hat dude all the way back when it was called Red Hat 7, although didn't REALLY start working with Linux until Red Hat 9 :oops:    I'm more into OpenSUSE but do have a look at Ubuntu with every new release. Seems like a friendly community though so I don't think there's going to be a stoning here. :)  Thanks to camper2 for creating the patches, I sorely neglected to explicitly do that in my earlier post. Some frustration seeped in there. So - again - thanks and also to anyone that can offer advice.

---

### Post by dmhymers on 2014-05-05
I just installed the drivers for a HPT 2640x4, looks to be working now under kernel 3.11.0-12 (linux mint 16) with the wonderful camper2's patch and the instructions in the OP. This lets me see an array that I had previously created under windows and NTFS. I appear to have read/write access to the now-visible partition without having done any of the below. Can anyone confirm for me that using the partition as-is won't cause things to explode on me, that the below events are only if you need to create a new partition?

> **ionospheric said:**
> - use gparted to create a partition table and a partition

- add an according line to /etc/fstab:
```
/dev/sdb1 /mnt/raid               ext4    errors=remount-ro 0       1
``` 

- create a mount location
```
sudo mkdir /mnt/raid
```

- change permissions to your username:
```
sudo chown -R username:username /mnt/raid
```

- mount the new volume
```
sudo mount /mnt/raid
```

You should now be able to use the RAID array like any other storage.

---

### Post by virtualguy on 2014-05-11
Im trying to get this running with a RocketRaid 2220 on 3.11.0-19-generic (ubuntu 13.10) but can't seem to get it to compile. 

Using camper2's r2 patch and the v1.9 source from HighPoint and it complains its can't find rr222x-linux-src-v1.9/product/rr2220/linux/.build/.rr2220.o.cmd to build rr222x-linux-src-v1.9/product/rr2220/linux/.build/rr2220.o

It does produce a hptmv6.ko, though I can't boot if I make install and the reboot with the raid card in.


On a side note, is the hptmv6 driver required if I only intend to do software raid? The disks are showing up as /dev/sdX but are definitely not working (I/O error) without the driver loaded.


Any ideas?

---

### Post by mausilveira on 2014-05-12
Hello Irish, thank you for your post here. Yeah, a little off since this is for ubuntu, but I appreciate your help. I was not able to compile the drive, when I run "make" either with fedora 19 or 20 it just sits there, no error message, but no results. How did you do it? Did you had any trouble compiling it? 

Thank you in advance!

---

### Post by parkingmeter on 2014-05-25
I've made the mistake of performing a fresh install of Ubuntu 14.04 with kernel 3.13.0-24-generic which isn't supported by the current driver for my 2720sgl card.  Camper2's patch for 3.11 didn't work; no surprise there :)

Is there anyone on the thread who could update the patch list? I hate begging, and I half expect a RTFM response. I'd appreciate a link to the 'manual' as well ;)

---

### Post by TMcKenzie on 2014-05-31
> **parkingmeter said:**
> I've made the mistake of performing a fresh install of Ubuntu 14.04 with kernel 3.13.0-24-generic which isn't supported by the current driver for my 2720sgl card.  Camper2's patch for 3.11 didn't work; no surprise there :)

Is there anyone on the thread who could update the patch list? I hate begging, and I half expect a RTFM response. I'd appreciate a link to the 'manual' as well ;)


I have been working on this for a couple days now, and fortunately found Camper2's patch.  I am running the latest Ubuntu 14.04 with the same kernel as you are.  I have the 2320 card, but I suppose what I did might work for you.

Using Camper2's patch file for my card I went through and replaced all the instances of "(3,10,0)" with "(3,13,0)".  Then I applied the patch to my installation directory.

Next, I used the following steps from [https://help.ubuntu.com/community/RocketRaid:]("https://help.ubuntu.com/community/RocketRaid):")

sudo dkms add -m rr62x -v 1.2
sudo dkms build -m rr62x -v 1.2
sudo dkms install -m rr62x -v 1.2
sudo modprobe rr62x

During the build process there were a couple of minor errors I had to correct, like balancing a couple #IF statements; nothing too difficult to figure out.  At this point the card is installed and running; I can see the drives attached to the card.

Good luck!

---

### Post by attfuzz on 2014-06-02
I've got the RocketRAID 644L running on Ubuntu 14.04 and this is what worked for me.

1) Download [RR64xl_Linux_Src_v1.3.5_13_09_27.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=248736&d=1387454788") found on page 4 of this thread.
2) cd Downloads
3) tar -xzvf RR64xl_Linux_Src_v1.3.5_13_09_27.tar.gz
4) cd rr64xl-linux-src-v1.3.5
5) cd product
6) cd rr64xl
7) cd linux
8) sudo make install
9) sudo modprobe rr640l

Hope this helps someone.

I've also got this to work on Ubuntu 14.10. But, before you run the sudo make install, you will need to edit the config.c file in the linux folder.

Right click on the config.c file and open with gedit, then:

comment the following line:
**//char driver_ver[] = "v1.3.5 (" __DATE__ " " __TIME__ ")";**
and add:
[B]char driver_ver[] = "v1.3.5";

[/B]Then run the sudo make install and then sudo modprobe rr640l commands on steps 8 and 9.

---

### Post by camper2 on 2014-06-10
> **parkingmeter said:**
> I've made the mistake of performing a fresh install of Ubuntu 14.04 with kernel 3.13.0-24-generic which isn't supported by the current driver for my 2720sgl card.  Camper2's patch for 3.11 didn't work; no surprise there 

That's a bit surprising. The patches should work with any kernel up to at least 3.14.* without modifications. Although not necessary at this point I should probably make a new patchset - at least some of the official drivers seem to have been updated, so it makes sense to sync with their modifications in order to lessen the work needed once a new kernel breaks the drivers again.

I'm not good at writing instructions (not running ubuntu in any case), but if someone would step up and provide them here I could include them in a readme file.

---

### Post by pletopia on 2014-06-24
> **TMcKenzie said:**
> I have been working on this for a couple days now, and fortunately found Camper2's patch.  I am running the latest Ubuntu 14.04 with the same kernel as you are.  I have the 2320 card, but I suppose what I did might work for you.

Using Camper2's patch file for my card I went through and replaced all the instances of "(3,10,0)" with "(3,13,0)".  Then I applied the patch to my installation directory.

Next, I used the following steps from [https://help.ubuntu.com/community/RocketRaid:]("https://help.ubuntu.com/community/RocketRaid):")

sudo dkms add -m rr62x -v 1.2
sudo dkms build -m rr62x -v 1.2
sudo dkms install -m rr62x -v 1.2
sudo modprobe rr62x

During the build process there were a couple of minor errors I had to correct, like balancing a couple #IF statements; nothing too difficult to figure out.  At this point the card is installed and running; I can see the drives attached to the card.

Good luck!

Like you, I have the 2320. I followed the directions as you seem to have but when I got to modprobe line, it didn't work. Not sure why? Any ideas ? Can provide more info if requested .. here is a snippet from last few lines

```
DKMS: build completed.
ubuntu@ubuntu:~/rr62x-linux-src-v1.2$ sudo dkms install -m rr62x -v 1.2

rr62x:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/3.11.0-12-generic/updates/dkms/

depmod....

Backing up initrd.img-3.11.0-12-generic to /boot/initrd.img-3.11.0-12-generic.old-dkms
Making new initrd.img-3.11.0-12-generic
(If next boot fails, revert to initrd.img-3.11.0-12-generic.old-dkms image)
update-initramfs....

DKMS: install completed.
ubuntu@ubuntu:~/rr62x-linux-src-v1.2$ sudo modprobe rr62x
ERROR: could not insert 'rr62x': No such device
```

when I run lspci .. i definately see my card listed .. 03:04.0 SCSI storage controller: HighPoint Technologies, Inc. RocketRAID 2320 SATA-II Controller (rev 09)

---

### Post by camper2 on 2014-06-30
> **pletopia said:**
> when I run lspci .. i definately see my card listed .. 03:04.0 SCSI storage controller: HighPoint Technologies, Inc. RocketRAID 2320 SATA-II Controller (rev 09)I think you're using the wrong driver. Support for the 2320 is done by the rr232x-linux-src-v1.10-090716-0928 driver.

---

### Post by pletopia on 2014-06-30
> **camper2 said:**
> I think you're using the wrong driver. Support for the 2320 is done by the rr232x-linux-src-v1.10-090716-0928 driver.

Hmm .. that does seem reasonable. Didn't even think about that just blindly followed that guys post since he said he had the 2320 AND got it working

Will try that driver now and see what happens

EDIT: Bingo, thx camper2. And also thank you for the patch files too :)

---

### Post by 6-mail-f on 2014-09-03
> **camper2 said:**
> I've created patches for all rocketraid drivers with a similar structure.
Also (re)added patchkernel target to all drivers where it was missing.
Untested save for the rr2340 driver.

620,622: rr62x-linux-src-v1.2-kernel-3.11.patch
640,644: RR64x-Linux-Src-v1.1-kernel-3.11.patch
640L,642L,644L,644LS: RR64xl-Linux-Src-v1.3-kernel-3.11.patch
1720: rr172x-linux-src-v1.2-kernel-3.11.patch
1740,1742: rr174x-linux-src-v2.4-kernel-3.11.patch
2210: rr2210-linux-src-v1.5-kernel-3.11.patch
2220,2224: rr222x-linux-src-v1.9-kernel-3.11.patch
2240: rr2240-linux-src-v1.11-kernel-3.11.patch
2300,2302,2310,2314: rr231x_0x-linux-src-v2.5-kernel-3.11.patch
2320,2322: rr232x-linux-src-v1.10-kernel-3.11.patch
2340: rr2340-linux-src-v1.7-kernel-3.11.patch
2522: rr2522-linux-src-v1.2-kernel-3.11.patch
2640X1,2640X4,2642: RR264x-Linux-Src-v1.5-kernel-3.11.patch
2644X4: RR2644-Linux-Src-v1.7-kernel-3.11.patch
2680,2684: RR268x-Linux-Src-v1.9-kernel-3.11.patch

[ATTACH]246613[/ATTACH]

I can confirm that this patch works with the RocketRaid 2640x4 and the rr264x-linux-src-v1.5 drivers on Gentoo vanilla sources 3.14.17

---

### Post by michael206 on 2014-10-01
> **attfuzz said:**
> I've got the RocketRAID 644L running on Ubuntu 14.04 and this is what worked for me.

1) Download [RR64xl_Linux_Src_v1.3.5_13_09_27.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=248736&d=1387454788") found on page 4 of this thread.
2) cd Downloads
3) tar -xzvf RR64xl_Linux_Src_v1.3.5_13_09_27.tar.gz
4) cd rr64xl-linux-src-v1.3.5
5) cd product
6) cd rr64xl
7) cd linux
8) sudo make install
9) sudo modprobe rr640l

Hope this helps someone.

This all works fine until I run:

sudo modprobe rr640l

 to which I get:

modprobe: ERROR: could not insert 'rr640l': No such device

I know it's a highpoint rocket 640l in there, the box is in front of me! The closest I can see in lspci is:

SATA controller: Marvell Technology Group Ltd. 88SE9230 PCIe SATA 6Gb/s Controller (rev 10)

Anyone have any ideas? This is on ubuntu Ubuntu 14.04.1 LTS.

---

### Post by camper2 on 2014-10-01
what does lspci -nn show for that device?

---

### Post by michael206 on 2014-10-01
# lspci -nnv | grep SATA
00:1f.2 SATA controller [0106]: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller [8086:3a22] (prog-if 01 [AHCI 1.0])
        Capabilities: [a8] SATA HBA v1.0
09:00.0 SATA controller [0106]: Marvell Technology Group Ltd. 88SE9230 PCIe SATA 6Gb/s Controller [1b4b:9230] (rev 10) (prog-if 01 [AHCI 1.0])
        Subsystem: Marvell Technology Group Ltd. 88SE9230 PCIe SATA 6Gb/s Controller [1b4b:9230]
        Capabilities: [e0] SATA HBA v0.0

Searches for 88SE9230 seem to come up with results for the 640l but still modprobe doesn't find it. At a bit of a loss as to where I'm going wrong and the controller is dropping out under load (Running the disks in JBOD) so I'd like to try the amended drivers.

---

### Post by camper2 on 2014-10-01
That doesn't appear to be a Highpoint device. All the drivers I have patched are for devices with the vendor code 1103 or 11ab as opposed to your 1b4b.
It's possible that your device is compatible, given that the Highpoint cards usually use Marvell controllers.

---

### Post by michael206 on 2014-10-01
Ah, it's a highpoint r640l not a highpoint rr640l for which the drivers page simply says [http://www.highpoint-tech.com/USA_new/series_r600-download.htm](http://www.highpoint-tech.com/USA_new/series_r600-download.htm) "Native Support in Linux". So I'm going to have to look elsewhere for why it's falling over and taking out all of the disks on it at once.

---

### Post by Spike42 on 2014-10-16
> **camper2 said:**
> I've created patches for all rocketraid drivers with a similar structure.
Also (re)added patchkernel target to all drivers where it was missing.
Untested save for the rr2340 driver.

620,622: rr62x-linux-src-v1.2-kernel-3.11.patch
640,644: RR64x-Linux-Src-v1.1-kernel-3.11.patch
640L,642L,644L,644LS: RR64xl-Linux-Src-v1.3-kernel-3.11.patch
1720: rr172x-linux-src-v1.2-kernel-3.11.patch
1740,1742: rr174x-linux-src-v2.4-kernel-3.11.patch
2210: rr2210-linux-src-v1.5-kernel-3.11.patch
2220,2224: rr222x-linux-src-v1.9-kernel-3.11.patch
2240: rr2240-linux-src-v1.11-kernel-3.11.patch
2300,2302,2310,2314: rr231x_0x-linux-src-v2.5-kernel-3.11.patch
2320,2322: rr232x-linux-src-v1.10-kernel-3.11.patch
2340: rr2340-linux-src-v1.7-kernel-3.11.patch
2522: rr2522-linux-src-v1.2-kernel-3.11.patch
2640X1,2640X4,2642: RR264x-Linux-Src-v1.5-kernel-3.11.patch
2644X4: RR2644-Linux-Src-v1.7-kernel-3.11.patch
2680,2684: RR268x-Linux-Src-v1.9-kernel-3.11.patch

[ATTACH]246613[/ATTACH]

Thank you very much for this patch camper2!!

Working for rr2340 on Ubuntu 14.04.1 LTS (kernel 3.13.0-37-generic) with official open source driver [rr2340-linux-src-v1.7-090925-0900.tar.gz]("http://www.highpoint-tech.com/USA_new/cs-series_rr2300_download.htm")

---

### Post by guilherme8 on 2014-11-13
Hi, 

Successfully installed !!!!

Ubuntu 14.04.1 LTS  (kernel 3.13.0-32-generic) or (kernel 3.13.0-39-generic)
RocketRAID 2640X4


from **camper2** ---> 2640X1,2640X4,2642: RR264x-Linux-Src-v1.5-kernel-3.11.patch

Patch: rocketraid-linux-3.11.patch.tar
Source: RR264x-Linux-Src-v1.5-120817-1641.tar.gz

copy from USB RR264x-Linux-Src-v1.5-120817-1641.tar.gz
copy from rocketraid-linux-3.11.patch.tar

```
lspci
tar -xvf RR264x-Linux-Src-v1.5-120817-1641.tar.gz
tar -xcf rocketraid-linux-3.11.patch.tar
cd rr264x-linux-src-v1.5
patch -p1 < /root/rr264x-linux-src-v1.5-kernel-3.11.patch
cd rr264x-linux-src-v1.5/product/rr2640/linux
make install
modprobe rr26xx
lsmod
```

and install !!!

---

### Post by riahc3 on 2014-11-20
Im trying to do a RocketRAID 640 on Ubuntu 14.04.1

Lets hope I don't have any problems.

---

### Post by bvanaerde on 2014-11-29
> **camper2 said:**
> I've created patches for all rocketraid drivers with a similar structure.
Also (re)added patchkernel target to all drivers where it was missing.
Untested save for the rr2340 driver.

620,622: rr62x-linux-src-v1.2-kernel-3.11.patch
640,644: RR64x-Linux-Src-v1.1-kernel-3.11.patch
640L,642L,644L,644LS: RR64xl-Linux-Src-v1.3-kernel-3.11.patch
1720: rr172x-linux-src-v1.2-kernel-3.11.patch
1740,1742: rr174x-linux-src-v2.4-kernel-3.11.patch
2210: rr2210-linux-src-v1.5-kernel-3.11.patch
2220,2224: rr222x-linux-src-v1.9-kernel-3.11.patch
2240: rr2240-linux-src-v1.11-kernel-3.11.patch
2300,2302,2310,2314: rr231x_0x-linux-src-v2.5-kernel-3.11.patch
2320,2322: rr232x-linux-src-v1.10-kernel-3.11.patch
2340: rr2340-linux-src-v1.7-kernel-3.11.patch
2522: rr2522-linux-src-v1.2-kernel-3.11.patch
2640X1,2640X4,2642: RR264x-Linux-Src-v1.5-kernel-3.11.patch
2644X4: RR2644-Linux-Src-v1.7-kernel-3.11.patch
2680,2684: RR268x-Linux-Src-v1.9-kernel-3.11.patch

[ATTACH]246613[/ATTACH]

This is still working for my RocketRaid 174x on Ubuntu 14.10 64bit!
Apart from the patch, I needed to change the following to file product/rr1740pm/linux:

comment the following line:
**//char driver_ver[] = "v2.4 (" __DATE__ " " __TIME__ ")";**
and add:
**char driver_ver[] = "v2.4";**

---

### Post by camper2 on 2014-11-30
> **bvanaerde said:**
> Apart from the patch, I needed to change the following to file product/rr1740pm/linux:

comment the following line:
**//char driver_ver[] = "v2.4 (" __DATE__ " " __TIME__ ")";**
and add:
**char driver_ver[] = "v2.4";**can you elaborate why that change is needed?

---

### Post by bvanaerde on 2014-11-30
Simply put, I could not install. It have an error with the usage of __DATE__.
I've had this problem for a while, not sure why.

I will post the exact error message when I need to install again (kernel update).

---

### Post by bvanaerde on 2014-12-01
Here's the error message:
> ~/Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux$ sudo make install
make[1]: Entering directory '/usr/src/linux-headers-3.16.0-25-generic'
  CC [M]  /home/ben/Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/os_linux.o
  CC [M]  /home/ben/Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/osm_linux.o
  CC [M]  /home/ben/Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/div64.o
  CC [M]  /home/ben/Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/hptinfo.o
  CC [M]  /home/ben/Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/config.o
[B]/home/ben/Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/config.c:26:30: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
 char driver_ver[] = "v2.4 (" __DATE__ " " __TIME__ ")";
                              ^
/home/ben/Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/config.c:26:43: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
 char driver_ver[] = "v2.4 (" __DATE__ " " __TIME__ ")";
                                           ^[/B]
cc1: some warnings being treated as errors
scripts/Makefile.build:257: recipe for target '/home/ben/Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/config.o' failed
make[2]: *** [/home/ben/Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/config.o] Error 1
Makefile:1345: recipe for target '_module_/home/ben/Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build' failed
make[1]: *** [_module_/home/ben/Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-25-generic'
../../../inc/linux/Makefile.def:105: recipe for target 'rr174x.ko' failed
make: *** [rr174x.ko] Error 2


That's why I removed both __DATE__ and __TIME__ variables.

---

### Post by camper2 on 2014-12-03
Do you have CFLAGS set in you environment and if so what is its contents?

---

### Post by bvanaerde on 2014-12-05
Honestly, I don't know.
How can I check this?

---

### Post by camper2 on 2014-12-05
what does
```
set | grep FLAGS
```
show?
The error shown is cause by the -Werror option being active during compilation which is not the default.
The option causes a warning during compilation to be treated as an error - this is useful during development of a project but it shouldn't be a global default.
Since newer compilers tend to issue more warnings than older ones it can make software that compiled fine with the old compiler to no longer build even though nothing was changed (and the warning given likely isn't a problem in that case).
The option can be set on the command line during compiler invocation, it can be pulled from the environment or it might be set in the compiler's spec file (if you built the compiler yourself). In the latter case you'd know about it and the Makefile doesn't set that option.

---

### Post by nagehmai on 2014-12-11
> **mausilveira said:**
> Hello Irish, thank you for your post here. Yeah, a little off since this is for ubuntu, but I appreciate your help. I was not able to compile the drive, when I run "make" either with fedora 19 or 20 it just sits there, no error message, but no results. How did you do it? Did you had any trouble compiling it? 

Thank you in advance!

Hey dude, make sure you have the kernel source installed in /usr/src (yum install kernel-devel) for the kernel you're running.  I ran into the "make hanging with no output" problem too at first and went through the Makefile.def  and noticed it was trying to find the kernel source.

---

### Post by bvanaerde on 2014-12-11
> **camper2 said:**
> what does
```
set | grep FLAGS
```
show?


Nothing at all.

---

### Post by john198 on 2014-12-22
After some weeks...lmao :p (like half a year later... :p)

I decided to go with...... reinstalling old OS(Fedora 14) that can handle the "public" version of the driver.
I have waaaaay to much databases on the RAID to let those to go "poop" in case this driver might sc**ws the RAID5 up.

Anywho.... Just to let y'all know.
(I said I would get back to ya, even though it's way too late :lolflag: )


HEIL LINUX!!!!

---

### Post by travis24 on 2014-12-22
Just wanted to say thanks, got my 2 RR2320s up and running on CentOS 7.

---

### Post by whyacow on 2014-12-29
> **bvanaerde said:**
> This is still working for my RocketRaid 174x on Ubuntu 14.10 64bit!
Apart from the patch, I needed to change the following to file product/rr1740pm/linux:

comment the following line:
**//char driver_ver[] = "v2.4 (" __DATE__ " " __TIME__ ")";**
and add:
**char driver_ver[] = "v2.4";**

Hi,
I'm trying to do the install of the RR2340 in Ubuntu 14.10 and am getting the same error.  What file exactly did I have to edit to comment those lines out?  I checked /product/rrxx/linux and nothing in there had __DATE__ in them.

set | grep FLAGS produced no output for me as sudo or user.

---

### Post by whyacow on 2014-12-29
> **whyacow said:**
> Hi,
I'm trying to do the install of the RR2340 in Ubuntu 14.10 and am getting the same error.  What file exactly did I have to edit to comment those lines out?  I checked /product/rrxx/linux and nothing in there had __DATE__ in them.

set | grep FLAGS produced no output for me as sudo or user.

Oops I found it.  Had to clear the build cache out and this worked for me also.  Thanks camper2 and bvanaerde!!!

---

### Post by camper2 on 2014-12-31
Just switched to gcc 4.9 and ran into the same issue. It seems the kernel sets this -Werror option by default (even though this is a bad idea) and the driver seems to pick it up. The more proper solution imo would be to disable this. I'll  post an update shortly.
In the meantime it should be ok to simply add to the make command, like
make CFLAGS=-Wno-error=date-time

You're free to do whatever you want with the pathset, in particular you're allowed to publish it under any license of your choice. 

Please ask any questions here and don't send me private messages, since in general I don't login unless I want to post.

---

### Post by mbksgx on 2015-02-28
hi ... i am trying to install the driver but got lost at the compiling ... could any1 help?

ima linux noob.

i was able to get the opendriver from highpoint website. v2.1, is this the right version?

then i went to install gcc and there was another 1 compiler i think i forgot the name :P
i saw the in [allvariants] thread about the lengthy mod and edits, but i got lost in the midst of it. many of it pointed to old version of opendriver not 2.1

what should i do? use ubuntu v12? i am now using lubuntu v14. i have ols RR2680 card ... and of course many drives waiting to ... spin :D
or should i ... dump this and go 2720 since i saw a thread that it has workable driver?

---

### Post by mbksgx on 2015-02-28
> **travis24 said:**
> Just wanted to say thanks, got my 2 RR2320s up and running on CentOS 7.

oh gawd, how did you do it?

---

### Post by mbksgx on 2015-02-28
> **irish-link said:**
> Open the tar file or extract it. Pick the .patch file that goes with your specific card. I have a rocket raid 622 so mine is rr62x-linux-src.......

Now that i have identified what file i want i can follow the patching process from [http://www.cyberciti.biz/faq/appy-patch-file-using-patch-command/](http://www.cyberciti.biz/faq/appy-patch-file-using-patch-command/)

So... you will need to do this in the command line
navigate to your source folder. 
So you will now see the folders (inc, lib, osm, product, README)

type "patch -p1 < /home/user/yourpatchfile.patch"
so my command line looked like this

cd /home/irish-link/rr62x-linux-src-v1.2

ls 
    inc
    lib
    osm
    product
    README

patch -p1 < /home/irish-link/rr62x-linux-src-v1.2-kernel-3.11.patch


This will then patch my files.

hello everyone (again) ... i got lost (again) when he said "navigate to source folder" ... where is that?

---

### Post by ben154 on 2015-04-25
I just got the rr2210 driver to compile on ubuntu 14.04 with kernel 3.16.0-30. So stoked!! 4TB mirror working great. Thanks to all who contributed and guided me through this.

---

### Post by travis24 on 2015-09-06
> **mbksgx said:**
> oh gawd, how did you do it?


I gathered bits an pieces from this thread and was able to get all the requirements installed and then install. Here is the commands that I use. I just did it because I updated the kernel and zfs to a more recent version (now CentOS 7.1)

Download Driver and Patch
```

cd /root
wget http://www.highpoint-tech.com/BIOS_Driver/rr232x/Linux/new%20format/rr232x-linux-src-v1.10-090716-0928.tar.gz
wget http://ubuntuforums.org/attachment.php?attachmentid=246613&d=1380480857
```


Untar
```
tar -xvzf rocketraid-linux-3.11.patch.tar.gz
tar -xvzf rr232x-linux-src-v1.10-090716-0928.tar.gz
```

Patch
```
cd rr232x-linux-src-v1.10
patch -p1 < /root/rr232x-linux-src-v1.10-kernel-3.11.patch
```

Install
```
cd product/rr232x/linux
make install
```

---

### Post by bvanaerde on 2015-10-23
Anyone managed to install it on the new 4.2.0-16 kernel (Ubuntu 15.10)?

edit: had to make the following obvious changes:

**inc/linux/Makefile.def**
Add check for major version 4
> **ifneq ($(MAJOR), 4)**
ifneq ($(MAJOR), 3)
ifneq ($(KERNEL_VER), 2.6)
ifneq ($(KERNEL_VER), 2.4)
+$(error Only kernel 2.4/2.6/3.x/**4.x** is supported but you use $(KERNEL_VER))
endif
endif
endif
**endif**

**osm/linux/install.sh**
Add major version 4 to the kernel case:
> case ${KERNEL_VER} in
	2.4 )
	OBJ=o
	MODVER=`modinfo -f%{kernel_version} ${PWD}/${TARGETNAME}.${OBJ}`
	;;
	2.6 | 3.* | **4.*** )
	OBJ=ko
	MODVER=`modinfo -F vermagic ${PWD}/${TARGETNAME}.${OBJ} | cut -d' ' -f1`
	;;
esac

Let's hope it will still work for a long time like this...

---

### Post by Melotron07 on 2016-03-04
Hello.

Ive have been runing ubuntu for about 1 year and it took me a few days to get my rr2340 card installed.
Today i rebooted my computer after i had ran apt-get autoremove to clean up a few old pakages.

So when the computer starts up i cant access my raid span.
All the disks are there when I start up the raid card.

```
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:        14.04
Codename:       trusty

```

Ubuntu sees the raidcard too when i run "sudo lshw"
```
                resources: ioport:c000(size=4096) memory:fba00000-fbbfffff              *-scsi UNCLAIMED
                   description: SCSI storage controller
                   product: RocketRAID 2340 16 Port SATA-II Controller
                   vendor: HighPoint Technologies, Inc.
                   physical id: 4
                   bus info: pci@0000:02:04.0
                   version: 09
                   width: 64 bits
                   clock: 66MHz
                   capabilities: scsi pm msi pcix bus_master cap_list
                   configuration: latency=32
                   resources: memory:fba00000-fbafffff ioport:c000(size=256)



```

Ive downloaded the patch for the card from here too but I cant run it.
When I try to install the patch so am I getting the following error :

```
magnus@EXXON-SKYNET:~/Downloads$ sudo patch -p1 < rr2340-linux-src-v1.7.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -Naur rr2340-linux-src-v1.7/inc/linux/Makefile.def rr2340-kern32/inc/linux/Makefile.def
|--- rr2340-linux-src-v1.7/inc/linux/Makefile.def       2009-09-25 04:00:17.000000000 +0300
|+++ rr2340-kern32/inc/linux/Makefile.def       2012-04-21 21:27:08.689106896 +0300
--------------------------
File to patch:

```

Can anyone give me a ELI5 guide on how to install the drivers again or point me to a guide that tryes to explain it to someome with limited knowledge on Linux ;)

Regards Magnus Svensson

---

### Post by sunny8294 on 2016-03-21
> **irish-link said:**
> Hi all! First i want to say thank you to everyone on this thread. Every time i redo my server or have an inadvertent update i come back here. I recently contacted HPT support regarding my RR622 and they got back to me with Source 1.3.3. I wanted to make sure that i post it here if it can help anyone. Right now i am running Kern 3.11 and will be updating to 3.12 to see if it works. The readme states that it has only been tested with 3.10. I thought i would post it here because it is not up on their site. 


[ATTACH]250542[/ATTACH]

Edit: I just compiled with make / make install and am up and running. I can confirm that it works find with Kernel 3.12.11. 
I should note that i am running Fedora 19 but building from source for a Kernel is still the same. (I know this is an ubuntu forum but I haven't found a better source for this kind of help or a better community, also my laptop wasn't the one that needed the drivers my server was)

Thank you so much.  Really appreciate your help on this, because I gave up on my RR 622.

---

### Post by prophetx2 on 2016-04-04
Thanks to you and Camper2, my 2340 is back to life on 14.04 LTS 4.2.0-27-generic kernel!  Appreciate all the help!

---

### Post by eriksson252 on 2016-11-16
> **bvanaerde said:**
> Anyone managed to install it on the new 4.2.0-16 kernel (Ubuntu 15.10)?

edit: had to make the following obvious changes:

**inc/linux/Makefile.def**
Add check for major version 4


**osm/linux/install.sh**
Add major version 4 to the kernel case:


Let's hope it will still work for a long time like this...


Hi, sitting with a 2340 raidcard on 14.04 and thinking of upgrading to 16.04 to get LTS. Are you or anyone els running this driver on kernel 4.4? Anything els needed to be done then what you post here?

---

### Post by bvanaerde on 2016-11-19
Any luck with Ubuntu 16.10?
I'm getting these errors:

Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/os_linux.c:278:41: error: &#8216;struct gendisk&#8217; has no member named &#8216;driverfs_dev&#8217;
Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/os_linux.c:283:35: error: &#8216;struct inode&#8217; has no member named &#8216;i_mutex&#8217;; did you mean &#8216;i_mode&#8217;?
         mutex_lock(&bdev->bd_inode->i_mutex);
Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/os_linux.c:283:35: error: &#8216;struct inode&#8217; has no member named &#8216;i_mutex&#8217;; did you mean &#8216;i_mode&#8217;?
         mutex_lock(&bdev->bd_inode->i_mutex);

---

### Post by np-hardass on 2017-03-10
> **bvanaerde said:**
> Any luck with Ubuntu 16.10?
I'm getting these errors:

Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/os_linux.c:278:41: error: ‘struct gendisk’ has no member named ‘driverfs_dev’
Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/os_linux.c:283:35: error: ‘struct inode’ has no member named ‘i_mutex’; did you mean ‘i_mode’?
         mutex_lock(&bdev->bd_inode->i_mutex);
Downloads/RocketRaid/rr174x-linux-src-v2.4/product/rr1740pm/linux/.build/os_linux.c:283:35: error: ‘struct inode’ has no member named ‘i_mutex’; did you mean ‘i_mode’?
         mutex_lock(&bdev->bd_inode->i_mutex);

[https://github.com/NP-Hardass/np-hardass-overlay/tree/master/sys-block/rocketraid62x/files](https://github.com/NP-Hardass/np-hardass-overlay/tree/master/sys-block/rocketraid62x/files)

```

[COLOR=#000000]Add support for kernel 4.7[/COLOR]Inodes have their own locking function now rather than maintaining a mutex
to be manually operated on

--- a/osm/linux/os_linux.c    2017-03-06 07:14:19.897941188 -0500
+++ b/osm/linux/os_linux.c    2017-03-06 07:15:39.660942596 -0500
@@ -368,13 +368,17 @@
                             if (vbus_ext->sd_flags[id] & SD_FLAG_REVALIDATE) {
                                 if (bdev->bd_disk->fops->revalidate_disk)
                                     bdev->bd_disk->fops->revalidate_disk(bdev->bd_disk);
-#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,15)
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4,7,0)
+                                inode_lock(bdev->bd_inode);
+#elif LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,15)
                                 mutex_lock(&bdev->bd_inode->i_mutex);
 #else 
                                 down(&bdev->bd_inode->i_sem);
 #endif
                                 i_size_write(bdev->bd_inode, (loff_t)get_capacity(bdev->bd_disk)<<9);
-#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,15)
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4,7,0)
+                                inode_unlock(bdev->bd_inode);
+#elif LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,15)
                                 mutex_unlock(&bdev->bd_inode->i_mutex);
 #else  [COLOR=#000000]                                 up(&bdev->bd_inode->i_sem);
[/COLOR]
```

```

Support kernels >= 4.8 since driverfs_dev was removed

--- a/osm/linux/os_linux.c    2017-03-06 07:23:27.521950854 -0500
+++ b/osm/linux/os_linux.c    2017-03-10 22:37:45.280019653 -0500
@@ -364,7 +364,11 @@
                         blkdev_get(bdev, FMODE_READ, 0 __BDEV_RAW)
 #endif
                         ==0) {
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4,8,0)
+                        if (bdev->bd_disk && ((disk_to_dev(bdev->bd_disk)->parent)==&SDptr->sdev_gendev)) {
+#else
                         if (bdev->bd_disk && bdev->bd_disk->driverfs_dev==&SDptr->sdev_gendev) {
+#endif
                             if (vbus_ext->sd_flags[id] & SD_FLAG_REVALIDATE) {
                                 if (bdev->bd_disk->fops->revalidate_disk)
                                     bdev->bd_disk->fops->revalidate_disk(bdev->bd_disk);
```

---

### Post by jziemba95 on 2017-04-06
> **np-hardass said:**
> [https://github.com/NP-Hardass/np-hardass-overlay/tree/master/sys-block/rocketraid62x/files](https://github.com/NP-Hardass/np-hardass-overlay/tree/master/sys-block/rocketraid62x/files)

```

Support kernels >= 4.8 since driverfs_dev was removed

--- a/osm/linux/os_linux.c    2017-03-06 07:23:27.521950854 -0500
+++ b/osm/linux/os_linux.c    2017-03-10 22:37:45.280019653 -0500
@@ -364,7 +364,11 @@
                         blkdev_get(bdev, FMODE_READ, 0 __BDEV_RAW)
 #endif
                         ==0) {
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(4,8,0)
+                        if (bdev->bd_disk && ((disk_to_dev(bdev->bd_disk)->parent)==&SDptr->sdev_gendev)) {
+#else
                         if (bdev->bd_disk && bdev->bd_disk->driverfs_dev==&SDptr->sdev_gendev) {
+#endif
                             if (vbus_ext->sd_flags[id] & SD_FLAG_REVALIDATE) {
                                 if (bdev->bd_disk->fops->revalidate_disk)
                                     bdev->bd_disk->fops->revalidate_disk(bdev->bd_disk);
```



When I try to run the patch "patch -p1 < /root/rocketraid62x-1.3.3-support-kernel-4.8-fix-gendev-driverfs_dev-ref.patch", I get an error of 

> 
patching file osm/linux/os_linux.c
patch: **** malformed patch at line 16: bdev->bd_disk->fops->revalidate_disk(bdev->bd_disk);

what should I do? I've never patched a kernel that I know of so I'm a bit lost.

---

### Post by arvana2 on 2017-08-01
Thanks very much, [**[COLOR=#000000]np-hardass[/COLOR]**]("https://ubuntuforums.org/member.php?u=2061267") -- that update works for me!

---

### Post by afr33sl4ve on 2018-06-23
Yes, I know this is hella necro.

I just got a 2320 myself, and this thread has made it really easy to install the drivers.

I'm having trouble with the speaker, it's looping constantly.

---

