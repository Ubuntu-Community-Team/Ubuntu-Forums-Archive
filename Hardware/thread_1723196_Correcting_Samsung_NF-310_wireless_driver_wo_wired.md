---
title: "Correcting Samsung NF-310 wireless driver w/o wired internet"
date: 2011-04-06
forum: Hardware
---

### Post by makender on 2011-04-06
I've got Netbook Remix 10.10 Maverick running on my Samsung NF-310. Unfortunately, this netbook is one of the few that has the Broadcom wireless driver issue. Here's my lspci output [ 05:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01) ]. I do not have access to a wired connection to the internet to set Ubuntu to download the appropriate driver for me. I do have a laptop that I can use to procure files and transfer them to the netbook via flash drive.

I installed from a USB flash drive and after reading this, [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx), I was able to find [ bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb ] in [ /media/PENDRIVE/pool/restricted/b/bcmwl ]. That particular linked reference specifies 10.04 and that netbook edition might require other dependencies. When I looked at the file in Software Center I get "Dependency is not satisfiable: dkms".

If anyone could give guidance on how to proceed I'd really appreciate it.

---

### Post by makender on 2011-04-07
Hopefully it's alright to give my thread a bump. I'm still hoping for some help...

---

### Post by makender on 2011-04-07
Further investigation lead me to [ [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) ]. That link noted 4313 unsupported by this particular b43 driver. The listed alternative links to [ [http://linuxwireless.org/en/users/Drivers/brcm80211](http://linuxwireless.org/en/users/Drivers/brcm80211) ]. Given that I can't simply git to my netbook, how do I go about procuring this driver under Win7 so that I may transfer with a flash drive. Also, if someone could help me out with what necessary commands I'd need to know, I'd appreciate it.

---

### Post by makender on 2011-04-07
[FONT=Verdana][SIZE=2]I tried to use the [/SIZE][/FONT][FONT=Verdana][SIZE=2][ [/SIZE][/FONT][FONT=Verdana][SIZE=2]git://git.kernel.org/pub/scm/linux/kernel/git/gregkh/staging-2.6.git ] link as an FTP, so [ [ftp://ftp.kernel.org/pub/scm/linux/kernel/git/gregkh](ftp://ftp.kernel.org/pub/scm/linux/kernel/git/gregkh) ], and transfer the folder. I get an error that it can't be transferred and the win7 ftp window stops responding followed by explorer.exe cycling.
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
I keep updating where I'm at on this more to bump the thread than to show my progress. My issue remains the same, how to acquire this git and how to install it on my netbook.
[/SIZE][/FONT]

---

### Post by makender on 2011-04-08
This'll be the last bump I make on this thread...

---

