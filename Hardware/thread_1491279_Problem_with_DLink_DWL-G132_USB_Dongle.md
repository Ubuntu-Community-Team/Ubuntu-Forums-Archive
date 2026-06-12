---
title: "Problem with DLink DWL-G132 USB Dongle"
date: 2010-05-23
forum: Hardware
---

### Post by opethfan89 on 2010-05-23
Hi all

Sorry to beat a dead horse, as I know there are alot of these threads floating around, but I'm trying to get my wireless USB dongle working on my desktop, but I've had no luck. The only reason I am posting a thread is because I spent about 2 hours searching all over various forums for an answer, and I'll get halfway through the steps before I reach an error that prevents me from going any further. Also, the fact that I have not found a single thread newer than 06, for the most part, and the ones that are newer don't help me solve my problem.

All of the tutorials I've read mention ndiswrapper, and I've followed the steps to install it but I get to the part where I have to "make" it, and it gives me the following error:

```
kadar@linux-desktop:~/Desktop/test/ndiswrapper-1.56$ make
make -C driver
make[1]: Entering directory `/home/kadar/Desktop/test/ndiswrapper-1.56/driver'
Makefile:34: *** Cannot find kernel version in /lib/modules/2.6.31-20-generic/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/kadar/Desktop/test/ndiswrapper-1.56/driver'
make: *** [all] Error 2

```So I cannot make the ndiswrapper file to go forward with the rest of the commands.

I installed ndisgtk, downloaded the latest driver from DLink's website, navigated to the only .inf file I could find (in the Win2KXP folder), and I guess I have some minor success because it shows the net5agu file installed, and it says that the hardware is present (I have the USB dongle plugged in right now but using a hardwired connection to get online)

Every tutorial mentions the athfmwdl.inf file, and I downloaded this file but when trying to install it with ndisgtk it says it is an invalid driver file.

So basically, my problem lies in that the headers are not being detected (apt-get install linux-headers-generic says I have the latest version
```
kadar@linux-desktop:~$ ls /lib/modules
2.6.31-20-generic  2.6.32-21-generic  2.6.32-22-generic
``` shows the ones I have)

and the other problem is ndiswrapper not letting me MAKE it. Once I do that, I should be able to follow any instructions easily.

So please, if anyone has any advice or some more -recent- links, it'd be much appreciated. I'm sure there are still some users who use this rather popular dongle, and having an updated tutorial for 9.10-10.04 would be rather nice.


Thanks, and sorry for the long post.

Sincerely,
Opethfan89


*EDIT* Just wanted to include 2 last tidbits:

1) When I type sudo ndiswrapper -l, I get the following error (is it significant? do I need to worry about it?):
```
kadar@linux-desktop:~$ sudo ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
```

2) ```
neta5agu : driver installed
    device (2001:3A03) present
``` shows that at least one driver is present and detected. So how should I proceed from here? Where do I get the -working- version of the other file?

Thanks.

---

### Post by dino99 on 2010-05-23
need this package installed:

linux-firmware-nonfree_1.8_all.deb

[http://packages.ubuntu.com/lucid/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/lucid/all/linux-firmware-nonfree/download)

---

### Post by opethfan89 on 2010-05-24
> **dino99 said:**
> need this package installed:

linux-firmware-nonfree_1.8_all.deb

[http://packages.ubuntu.com/lucid/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/lucid/all/linux-firmware-nonfree/download)


Thanks, could you provide more detail with what I do with it? I've never installed a package from source, and using apt-get says the package is not found. When I try to add the software source, it says there is a serious error in line 55 the sources.lst file and I can't continue. Trying to update my software sources list keeps giving me an error saying "check your internet connection", even though I am hard-wired right now.

*EDIT* A quick search in ubuntu software center for "nonfree" turned up the file I'm looking for, installed it, but I still get the same error when trying to 'make' ndiswrapper. Any other suggestions..?

---

### Post by opethfan89 on 2010-05-24
I found a fantastic guide [here]("http://bigpixel.com/?p=167") and I can follow most of the steps up until about #4, where it says sudo modprobe ndiswrapper. It gives me the following error: 

```
FATAL: Module ndiswrapper not found.
```

Unfortunately I cannot follow forth with the rest of the steps after that. I found my driver CD and found the athfmwdl.inf file I needed, and installed it using ndisgtk, and it says the driver is installed and hardware is present, but when I type lsusb I get:

```
Bus 001 Device 004: ID 2001:3a03 D-Link Corp. [hex] DWL-G132 (no firmware)
```

So the hardware is detected, but there is a problem in the firmware still. Any suggestions?

---

### Post by opethfan89 on 2010-05-25
*BUMP*

Can anyone help me with this? I've been waiting for a response for a few days now.

---

### Post by harrykar on 2010-06-11
> **opethfan89 said:**
> *BUMP*

Can anyone help me with this? I've been waiting for a response for a few days now.

Same problem here. Im on a Lucid Lynx (amd64= 64 bit). I have a PC with Ubuntu 9.04 32 bit and the dongle work fine. But in Lucid Lynx (amd64= 64 bit) no. I find [http://napalmpiri.wordpress.com/dissected-hardware/dlink-dwl-g-132/](http://napalmpiri.wordpress.com/dissected-hardware/dlink-dwl-g-132/) interesting.

I open a Thread (lang:IT) about **DLink DWL-G132 USB Dongle **following [http://wiki.debian.org/ar5523#install](http://wiki.debian.org/ar5523#install) (if u don't want  buid it yourself u can find a *deb package in a launchpad repo here [http://ppa.launchpad.net/logari81/ppa/ubuntu/pool/main/a/ar5523/](http://ppa.launchpad.net/logari81/ppa/ubuntu/pool/main/a/ar5523/)). Ok buid-install-loadind driver but no lack in iwconfig(no wlan0 interface)

---

