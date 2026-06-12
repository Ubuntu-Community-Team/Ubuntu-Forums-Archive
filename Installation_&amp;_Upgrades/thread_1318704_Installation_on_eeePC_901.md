---
title: "Installation on eeePC 901"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by Arostotal on 2009-11-07
I am new to Linux and was recommended to switch from Xandros to Ubuntu on my eeePC 901 so I downloaded 9.10 Netbook Remix and followed the various instructions to create a bootable USB stick.  

1.  The Left USB port does not seem to support a bootable USB stick (i.e. that does not work).
2.  The Right USB ports seem to work and the 901 boots but when I try to run the OS from the USB stick nothing seems to happen - just a blank screen.   I  can check memory ok so something is working.
3.  If I try to Install Ubuntu Network Remix I get the Ubuntu logo and then a screen full of what is to me complete gobbledeegoo...starting (initranmfs) BusyBox v1.12.....listing various options and a sentence that states 'There are EVEN MORE flags that are specific to each filesystem  You'll have to see the written documentation for those filesystems  Cannot mount /dev/loop1 on /cow

The person who recommended me said that his download (of another version of Ubuntu) installed on his 901 in a few minutes and he has a nice GUI etc., mine has taken hours and is for me totally unintellgible.  Am I expecting too much?

---

### Post by IRANianCha0s on 2009-11-08
When using usb-creator, check "Discarded on shutdown, unless you save them elsewhere" for documents and settings.

---

### Post by julianb on 2009-11-08
One thing you can try is using a 9.04 version of Ubuntu.

You can consider using (instead of Ubuntu Netbook Remix)

Masonux -- ubuntu based lightweight distribution, based on Ubuntu 9.04
Xubuntu

Some folks are experiencing problems with 9.10 because of the specific hardware they use... I bet most of the problems will be fixed in a couple months, but until then Ubuntu 9.04 ain't so bad.

---

### Post by hackvan on 2009-11-10
> **IRANianCha0s said:**
> When using usb-creator, check "Discarded on shutdown, unless you save them elsewhere" for documents and settings.
rather than re-running the whole usb-creator process, your tip provided the necessary hint for me to go fix the boot config files directly...  

REMOVE "persistent" from the kernel boot options in X:/syslinux/text.cfg and that does the trick...

my now-working kernel options are:

append  noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/netbook-remix.seed boot=casper initrd=/casper/initrd.lz --

---

### Post by paxmark1 on 2009-11-10
and there is always the minimalist openbox derivative of ubuntu called crunchbang linux which is still using 9.04.  Try it on a usb stick first if you do.  Either you will love it on a netbook or run screaming away.

peace   mark

---

