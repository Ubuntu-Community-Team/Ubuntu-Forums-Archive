---
title: "VIA VT6421 PCMCIA eSATA Card: System Lockup"
date: 2011-08-11
forum: Hardware
---

### Post by dtwai on 2011-08-11
Hey guys,

I have an old Samsung Q10 notebook, running Ubuntu Server 11.04, and I am using it as a p2p box.

Yesterday I bought a "generic" (can't find the brand) PCMCIA eSATA card, as I am going to attach another hard drive into the system.

It worked properly: It can detect the drive, it can ls the drive and it can access the drive.

$ lspci -k|grep -i VT6421 -A 2
03:00.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
	Subsystem: VIA Technologies, Inc. VT6421 IDE RAID Controller
	Kernel driver in use: sata_via
	Kernel modules: sata_via

The problem is: when I try to make transmission to download files into that drive, the whole system freezes. It has refused to accept incoming connections, and doesn't respond to any input. The display just freezes. It won't work again - the only way to do is hard resetting the system.

Now I have command-line and hardware access to the machine.

My system has attached a Kingston USB thumb drive, which has the Ubuntu OS inside, a Seagate ST2000DL003 2TB drive connected to internal IDE socket via SATA to IDE adapter, and a Seagate ST3500418AS 500GB drive connected to the eSATA card by a eSATA-SATA cable.
The cable and the drives are working properly - exchanged those parts do not give good results.

All those drives are formatted as an EXT4 partition across the whole drive, and the 2TB one is using GPT, if that matters.

If you need more output, you can ask me here.

Sorry for my bad English.

---

### Post by dtwai on 2011-08-12
After I did a dd on the drive, I found the following in dmesg.
[IMG]http://www5.picturepush.com/photo/a/6305333/img/6305333.jpg[/IMG]
Could this error related with the problem?

---

### Post by arnuschky on 2011-09-07
Hey,

I have the same problem. I started a new bug report for this:
[https://bugs.launchpad.net/ubuntu/+source/linux-lts-backport-natty/+bug/843639](https://bugs.launchpad.net/ubuntu/+source/linux-lts-backport-natty/+bug/843639)

Cheers,
Arnuschky

---

