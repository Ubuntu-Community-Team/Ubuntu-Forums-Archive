---
title: "Memory Configuration - Desktop w/4 gb DDR2 SLI"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by PokerFacePenguin on 2007-11-18
I just completed a new build of a Desktop and cannot see all of my ram in ubuntu.  I never had this much ram in an ubuntu machine.  Anyone have any ideas?

The Problem:  

System monitor in GNOME reports that I only have 2.7 gigabytes of RAM.  I have 4 megabytes of DDR2 SLI Ready RAM installed in this machine.  The BIOS reports to me that I have 4 gigs, but ubuntu does not.  I have an XFX motherboard and have the SLI setting enabled for MAX CPUOC.  

Relevant Specs:
Gutsy Ubuntu 7.10

Quad Core Q6600 2.4 Ghz 4x2mb 1066 FSB

XFX nForce 680i LT SLI Motherboard, NVIDIA, Socket 775, ATX, Audio, PCI Express, SLI Ready, Gigabit LAN, S/PDIF, USB 2.0 & Firewire, Serial ATA, RAID

Corsair TwinX pc6400 DDR2 800 mhz E.P.P. (4 x 1 gig sticks)

This thing rocks :guitar::guitar::guitar: , but I want it to use all the available resources I spent my hard earned cash on. :-({|= :)

---

### Post by tinycamp on 2007-11-18
you need to compile your kernel with the following parameter on the .config

```
CONFIG_HIGHMEM4G=y
```

or, when configuring, enable that option while doing

```

make menuconfig

```

---

### Post by PokerFacePenguin on 2007-11-18
> **tinycamp said:**
> you need to compile your kernel with the following parameter on the .config

```
CONFIG_HIGHMEM4G=y
```

or, when configuring, enable that option while doing

```

make menuconfig

```

Thanks for the quick response.
Oh, so the default kernel of gutsy must be changed.  That makes sense.  

I will scruff around and check that out.

---

### Post by PokerFacePenguin on 2007-11-18
> **tinycamp said:**
> you need to compile your kernel with the following parameter on the .config

```
CONFIG_HIGHMEM4G=y
```

or, when configuring, enable that option while doing

```

make menuconfig

```

Ok, so i poked around and found [https://help.ubuntu.com/community/Kernel/Compile#head-18233ed0977bbdf77cd45200af6cd9335b07c030](https://help.ubuntu.com/community/Kernel/Compile#head-18233ed0977bbdf77cd45200af6cd9335b07c030)

to tell me how to build that kernel.  It appears that I have the generic 2.6.22.14 generic version currently.  

Do I need to append the .14 onto the end of the sudo apt-get build-dep linux-source-2.6.22 command to keep me on par?  I don't want to deviate too much from the standard kernel that I have (I don't wanna end up with the frankenstein kernel).   I just want to change that one option in the config.  

Are these instructions:

[https://help.ubuntu.com/community/Kernel/Compile#head-18233ed0977bbdf77cd45200af6cd9335b07c030](https://help.ubuntu.com/community/Kernel/Compile#head-18233ed0977bbdf77cd45200af6cd9335b07c030)

 the best way to go about merely getting the ability to use all my memory?

---

### Post by tinycamp on 2007-11-18
as far as i know you dont need to do that with sources, the closest match is the right one

good luck!

---

### Post by PokerFacePenguin on 2007-11-18
> **tinycamp said:**
> you need to compile your kernel with the following parameter on the .config

```
CONFIG_HIGHMEM4G=y
```

or, when configuring, enable that option while doing

```

make menuconfig

```

Hmm, I followed those instructions for downloading the source and the highmem option for the generic kernel already has the option set to yes.  Any further thoughts?

I found a similiar issue in this thread:
[http://ubuntuforums.org/showthread.php?t=154555](http://ubuntuforums.org/showthread.php?t=154555)

---

### Post by tinycamp on 2007-11-19
have you tried booting that new kernel???

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-19
Hi, I also own 4GB DDR2, to get full 4GB support follow this:

After typing ```
make menuconfig
```
A "Linux Kernel Configuration" will shown, navigate to
```
Processor type and features -> High Memory Support -> Choose 64GB
```

Save and compile the kernel.
I saw your post on the "Memory Recognition in Server", well... I recommend you to use "make menuconfig" instead of editing the .config file.

---

### Post by PokerFacePenguin on 2007-11-21
> **Milk & Toast & Honey said:**
> Hi, I also own 4GB DDR2, to get full 4GB support follow this:

After typing ```
make menuconfig
```
A "Linux Kernel Configuration" will shown, navigate to
```
Processor type and features -> High Memory Support -> Choose 64GB
```

Save and compile the kernel.
I saw your post on the "Memory Recognition in Server", well... I recommend you to use "make menuconfig" instead of editing the .config file.

Thanks for the tip.  I had to leave town last weekend but now i am back here on thanksgiving holidays trying it again.  I left my machine running and compiling with an autobuild command found in one of the kernel compiling howtos, but when i tried to dpkg install it i still dont get the extra ram available.  I realize there are many howtos and different ways to achieve the same goal, but I am getting bogged down in all of these different threads.  It has been a while since i have played around with kernel hacking and I am not really familiar with the latest/best ways of doing it.  I am currently running gutsy stock (generic version)  and would like to just modify that one option to reclaim my 4 gigs RAM.  I have an nvidia chipset and graphics card, but I will be able to enable those restricted drivers from gnome.  I assume that is probably the only caveat in doing the rebuild,  

Should I download fresh source from somewhere and then make menuconfig, or should I try it from the /boot directory, or maybe the stuff i downloaded into ~/ where i now have autobuilt (after manually editing config) all flavours of the kernel.  I have a pile of new debs in there and thought that dpkg the deb would get me what I wanted, but my config in /boot is the old config file after installing the deb.

I probably screwed up by having to leave in mid stream.
Is there a concise guide to give me a stock ubuntu kernel (for gutsy) and a generic flavour with the 4gig option enabled?
.  

Please point me into the right direction.  It is just the one option that I want to change.  Maybe I can get braver after that.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-22
I learn a lot from [this thread]("http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel") to kernel compilation. Also [this thread]("http://ubuntuforums.org/showthread.php?t=538068&highlight=kernel") to patch my kernel with CFS support.
* Credits to master_kernel and volsungs.

To summarize, this are the steps I used to compile my kernel:
[LIST=1]
[*]Install gutsy's server kernel.
```

sudo apt-get install linux-image-2.6.22.14-server

```
[*]Boot into guty's server kernel.
[*]Install kernel source.
```

sudo apt-get install kernel-source

```
[*]Change directory to /usr/src
```

cd /usr/src

```
[*]Unpack the kernel's source, and change directory to there.
```

tar xf kernel-source-2.6.22.tar.bz2 && cd kernel-source-2.6.22

```
[*](Optional) Apply the CFS scheduler (follow the steps in the second link I provide).
Using CFS, running multiple CPU hungry programs won't make your computer sluggish. I used CK patches before, but I think CFS "feels" more responsive.
[*]Copy the gutys's server kernel config
```

sudo cp /boot/config-`uname -r` /usr/src/linux-source-2.6.22/.config

```
[*]Make the menuconfig, and set the memory support to 64GB.
```

sudo make menuconfig

```
```

Processor type and features -> High Memory Support -> Choose 64GB

```
[*]Change back the preemption model to desktop.
```

Processor type and features -> Preemption Model -> Choose Voluntary Kernel Preemption (Desktop)

```
[*](Recommended) Since you're using Core 2 Quad - Q6600, choose the processor type to "Core 2/newer Xeon", to make your processor usage optimal (I think it's faster). 
```

Processor type and features -> Processor family -> Choose Core 2/newer Xeon

```
[*]Compile the kernel using make-kpkg, and don't forget to use CONCURRENCY_LEVEL=5, you'll surprise when you did this :) .
When I use this parameter, compiling kernel only took ~15 minutes on my Quad Core, if not, it took 45 minutes to finished.
```

sudo CONCURRENCY_LEVEL=5 make-kpkg --initrd --revision=***<enter_your_revision>*** kernel_image kernel_headers modules_image

```
[*]The *.deb will resides in /usr/src, you can install that now.
```

cd /usr/src

```
```

sudo dpkg -i linux-headers-2.6.22.<your_revision>.deb linux-image-2.6.22.<your_revision>.deb

```
[*]Reboot and enjoy your 4GB :) .
[/LIST]

EDIT: 
If you get errors about your firmware just make the link to your gutsy's server firmware. (I got this somewhere but I forget where)
```

sudo ln -sf /lib/firmware/2.6.22.14-server /lib/firmware/2.6.22.<your_revision>

```

And for NVidia driver, I install them by downloading the driver from NVidia's sites, I never use Ubuntu's stock driver, so I don't know how to activate "Restricted Driver".

---

