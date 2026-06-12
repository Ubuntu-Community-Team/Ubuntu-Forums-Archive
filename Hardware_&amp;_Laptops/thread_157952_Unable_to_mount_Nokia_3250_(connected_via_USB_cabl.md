---
title: "Unable to mount Nokia 3250 (connected via USB cable CA-53)"
date: 2006-04-10
forum: Hardware &amp; Laptops
---

### Post by Gimbo on 2006-04-10
Information about the phone can be found here: [http://www.forum.nokia.com/main/0,,018-2935,00.html?model=3250](http://www.forum.nokia.com/main/0,,018-2935,00.html?model=3250)

I've added the following line to my /etc/fstab file:
```

/dev/sda    	/media/3250   	vfat    iocharset=utf8,umask=000   0       0

```
**This error seems to be the reason why I can't mount the phone, but I need some help understanding it:**
```
andrew@FAMILYUB:~$ sudo mount -a
mount: /dev/sda: can't read superblock
andrew@FAMILYUB:~$ dmesg | tail
[4301124.806000] Buffer I/O error on device sda, logical block 245959
[4301124.825000] end_request: I/O error, dev sda, sector 245952
[4301124.843000] end_request: I/O error, dev sda, sector 245760
[4301124.862000] end_request: I/O error, dev sda, sector 245760
[4301124.880000] end_request: I/O error, dev sda, sector 245760
[4301124.898000] end_request: I/O error, dev sda, sector 245616
[4301124.916000] end_request: I/O error, dev sda, sector 245616
[4301138.280000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4301138.292000] end_request: I/O error, dev sda, sector 0
[4301138.293000] FAT: unable to read boot sector

```

----------[background information]----------
When I connect the phone up with the provided USB cable (model number CA-53), the phone recognises it's been plugged in and asks what mode it should be put in (Media player, PC Suite or Data transfer). On choosing Data transfer, it goes into offline mode and a scrolling bar appears saying the phone is connecting.

In Places>Computer, the phone appears as Drive. If I double-click that, it gives the following error:
```

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount

```

The phone *does* appear in System>Administration>Device Manager
----------------------------------

Thanks very much in advance for any advice.

---

### Post by xristos on 2006-06-17
same problem here 
any ideas ?

---

### Post by pingflood on 2006-07-02
I have the same problem here.
I've read anywhere you have to patch "unusual_devs.h".
But I don't know exactly what to do.

Hello kernel hackers? Any (other) idea?

---

### Post by Arless on 2006-07-30
I have the same problem, but i dont know what to do with the unusual_devs.h edited file. is it necessary compile kernel with the edited file??

---

### Post by pingflood on 2006-08-31
Hi there!

Good news!

Finally, I've found a patch here:
[https://lists.one-eyed-alien.net/pipermail/usb-storage/2006-July/002605.html](https://lists.one-eyed-alien.net/pipermail/usb-storage/2006-July/002605.html)

Just download the latest kernel source (form kernel.org), patch unusual_devs.h and recompile the kernel.

Infos about how to patch, recompile and install your kernel you can find here in UbuntuForums (use the search!)

I made it here, now I can mount and tranfer data from/to my phone in high speed (no more "60KBps" in crappy bluetooth transfer!!)

HTRH,
Ping Flood

---

### Post by alekz on 2006-10-29
Do you have a nice howto to patch the kernel? i've never done that.

Thanks

---

### Post by pingflood on 2006-11-15
Hi there!

The latest kernel already have the Nokia 3250 in unusual_devs.h. So, you don't have to patch anything. All you have to do is compile the latest version.

To alekz:
Here in ubuntuforums you have nice how-tos and troubleshoting regarding kernel recompile.

If you want to try by yourself, here is the way I do:

```

# apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget
cd /usr/src
# wget -c http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.18.2.tar.bz2

# tar xvjf linux-2.6.18.2.tar.bz2
# ln -sf linux-2.6.18.2 linux

cd linux
# cp /boot/config-`uname -r` .config
# make xconfig
# time make-kpkg --initrd kernel_image kernel_headers --append-to-version=-pingflood

# dpkg -i *.deb

```
The "#" at start of the line mean that you have to run as root (or with sudo).

Use at your own risk!

Don't forget, if you use nVidia drivers from repositories, you'll have to install the original version, directly from nvidia.com.

More about all of this, here in ubuntuforums. :)

Regards!

---

### Post by alekz on 2006-11-16
pingflood lot of thanks, now i can transfer files to my nokia cellphone, but i have a problem, when i boot with that kernel my cpu is always at 90 - 100% in use, how can i fix that? Thanks =)

---

### Post by olieviya on 2006-11-21
> **alekz said:**
> pingflood lot of thanks, now i can transfer files to my nokia cellphone, but i have a problem, when i boot with that kernel my cpu is always at 90 - 100% in use, how can i fix that? Thanks =)

Hey, I'm trying to mount my nokia 6233, I have no clue where to start, can you help please?:confused:

---

### Post by ayed on 2007-02-16
Didn't work for me, my mobile just froze and I had to restart it! Any feedback?

---

