---
title: "Various problems with Fujitsu Amilo-A A2000"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by Ess Age on 2008-01-16
Hello everyone,
I'm experiencing some problems on my FSC Amilo Laptop running Xubuntu 7.10 (not a single updated package as there is no way to connect to the net atm). The most annoying is that I don't get my ethernet card working and thus can't solve the other problems which might just need a simple driver/package download.
So I'll start with that problem:
Before installing Ubuntu to HD I ran (as usual I suspect) the installation-live-xubuntu. There the ethernet card (a RTL-8139/8139C/8139C+) ran with the module 8139too just fine. But after the installation it did not work. lspci and ifconfig both list the device correctly and the xubuntu network manager is able to work with it. But when it comes to any traffic, starting with the DHCP discovery, the interface doesn't seem to do anything. So I tried to assign the IP etc. by hand which didn't establish a connection either. So I followed a hint in a forum and tried to configure the interface via /etc/network/interfaces (auto/DHCP) and surprise: after rebooting the IP adress is fetched correctly just like with the live-CD... BUT no connection can be established. After ifdown/ifup-ing eth0 the DHCP discovery fails just as before with a timeout.
When using the xubuntu network manager dmesg shows the following (shortened):
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[3 secs later] NETDEV WATCHDOG: eth0: timed out
eth0: Transmit timeout, status 0c 00XX x07f media 1c. (where XX is either 04/05/24/25 in my test cases)
[4 queued packets]

I hope the error description suffices for a first hint. As it matched perfectly to the one provided [here]("http://ubuntuforums.org/showthread.php?t=664251&highlight=8139") I've tried to unplug and then plug in the cable but nothing happens (not even a message via dmesg).

My other problems in a short overview (mybe someone of you has a hint here, too):
1) USB (ALi USB 1.1 rev3) doesn't seem to work. When eg. a USB flash stick is plugged in at boot time, if just doesn't show up. On the other when applying it when already started nothing at all happens. Again USB worked with the installation-CD.
2) My sound (ALi M5451) doesn't work. Doesn't matter to me now, just wanted to mention it. :)
3) PCMCIA shows just the same behaviour like USB with the difference that devices apllied at boot time are usable. Applied later, nothing happens. The live-CD did a fine job here too.
4) The xfce battery monitor crashes after launching it. Though it shows the current percentage and the config dialog, both freeze.
5) A USB-mouse has hefty lags when used in live-xubuntu but I've read that this is normal.

When looking at all of those problems it seems just like there is a problem with a generic update notifier for system state changes. Is there something like this in linux which might be broken after installing xubuntu to HD?

That's it for now. Thanks in advance for any bit of help. I'm clueless atm ;)

---

### Post by Ess Age on 2008-01-17
Unfortunately I've no new information for you. I just can't get it to work. Any ideas?

---

### Post by Ess Age on 2008-01-18
bump

---

### Post by xubutex on 2008-02-26
Hi
I had problems in bootup with kernel 2.6.22-14-generic. I installed Amilo A specific kernel which worked better at least with my Amilo A cy26.

[http://rzr.online.fr/debian/linux-image-2.6.24-k7-amiloa_nrv.0.200802062000_i386.deb](http://rzr.online.fr/debian/linux-image-2.6.24-k7-amiloa_nrv.0.200802062000_i386.deb)

[http://rzr.online.fr/wiki.php?AmiloA](http://rzr.online.fr/wiki.php?AmiloA)
[http://philippe.coval.ifrance.com/www.rzr.online.fr/debian/00index.htm](http://philippe.coval.ifrance.com/www.rzr.online.fr/debian/00index.htm)

---

### Post by www.rzr.online.fr on 2008-05-01
> **xubutex said:**
> Hi
I had problems in bootup with kernel 2.6.22-14-generic. I installed Amilo A specific kernel which worked better at least with my Amilo A cy26.

[http://rzr.online.fr/debian/linux-image-2.6.24-k7-amiloa_nrv.0.200802062000_i386.deb](http://rzr.online.fr/debian/linux-image-2.6.24-k7-amiloa_nrv.0.200802062000_i386.deb)

[http://rzr.online.fr/wiki.php?AmiloA](http://rzr.online.fr/wiki.php?AmiloA)
[http://philippe.coval.ifrance.com/www.rzr.online.fr/debian/00index.htm](http://philippe.coval.ifrance.com/www.rzr.online.fr/debian/00index.htm)


Hey that's my kernel  :-)

On which version of ubuntu did you install it ?

I built it for debian, I'll update it soon, join the mailing list 
[http://rzr.online.fr/q/amiloa](http://rzr.online.fr/q/amiloa)

---

