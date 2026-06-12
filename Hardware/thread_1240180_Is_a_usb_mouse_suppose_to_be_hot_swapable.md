---
title: "Is a usb mouse suppose to be hot swapable??"
date: 2009-08-14
forum: Hardware
---

### Post by SpaCeTraNce on 2009-08-14
I have searched the board and have come up with several mouse problems but no posts related exactly to mine. 

I am running jaunty on a Dell D610. After initial installation I _think_ my mouse was 'hot swapable', meaning if I booted my box without my mouse, then plugged a USB mouse into it, it would work. But now... I have lost 'swapable' function...  it will not work at all untill I reboot.

To recap: If I start ubuntu w/o my mouse (it doesn't matter which mouse I use, wired or wireless, logitech or microsoft) plugged in it will not work untill I restart with it plugged in. OR if I suspend my computer, unplug mouse, go to local coffee shop, plug in mouse, resume puter... no mouse functioality untill I reboot.

Sure... I have a work around but it is annoying..... is this a problem with anyone else?? is this a problem with 8.xxx


Sorry if I was a little redundant
Sorry if I was a little redundant :)


 I found several posts about the mouse clicking function not working which is not the same problem.

---

### Post by snakeman21 on 2009-08-14
I believe the term you are looking for is "hot-pluggable"

Unfortunately, I don't know how to help you... All of my usb devices are hot-pluggable and haven't given me issues.

---

### Post by SpaCeTraNce on 2009-08-14
Humm.... I kinda wish this upon other users so maybe I could find a fix...

Question: I come from a windows background so Is there a 'repair install' type of option if I try installing ubuntu on top of itself???? Will it delete any documents???? Will it keep my audio/video codecs??? Will it keep any programs that I have installed since the OS load???


hot swappable is used to describe things which can be swapped out while the machine is running. Usually used to refer to hard drives (in servers) or other internal items. I too have never heard it used for a usb device but I couldn't think of another way to phrase it :confused:.... hot plugable .. thanks :)

---

### Post by cariboo on 2009-08-14
When you install Ubuntu, you are asked to partition your hard drive and format it, so you will loose everything. Plug your mouse in, then open a terminal and tpye:

```
dmesg | tail -n15
```

and paste the result in your next post.

---

### Post by edwardtilbury on 2009-08-14
I have a laptop and I can unplug it from one usb while it's on then plug it in another and it keeps working.. try plugging in 2 usb mice then booting and swapping the new one or vice versa.. maybe it's just that mouse.. It's unlikely, but worth a shot if you have an extra one hanging out.

---

### Post by SpaCeTraNce on 2009-08-17
These are the results to "cariboo907's posted command" if I plug in a mouse after booting:
*correction* sorry... these results came after awakening my computer from standby then plugging in a mouse

```
[ 4288.583006] Buffer I/O error on device sr0, logical block 0
[ 4288.583013] Buffer I/O error on device sr0, logical block 1
[ 4288.583022] Buffer I/O error on device sr0, logical block 2
[ 4288.583028] Buffer I/O error on device sr0, logical block 3
[ 4288.583034] Buffer I/O error on device sr0, logical block 4
[ 4288.583040] Buffer I/O error on device sr0, logical block 5
[ 4288.583045] Buffer I/O error on device sr0, logical block 6
[ 4288.583051] Buffer I/O error on device sr0, logical block 7
[ 4288.586248] end_request: I/O error, dev sr0, sector 0
[ 4288.586255] Buffer I/O error on device sr0, logical block 0
[ 4288.586262] Buffer I/O error on device sr0, logical block 1
[ 4296.732558] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4307.624052] wlan0: no IPv6 routers present
[ 4900.948129] usb 4-1: new low speed USB device using uhci_hcd and address 2
[ 4901.134188] usb 4-1: configuration #1 chosen from 1 choice

```> maybe it's just that mouse.. I have tried several mice/mouses

---

### Post by SpaCeTraNce on 2009-08-17
These are the results to "cariboo907's posted command" if I plug in a mouse _**before**_ booting:
```

[   24.822554] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.822557] Bluetooth: BNEP filters: protocol multicast
[   24.846444] Bridge firewalling registered
[   28.499224] [drm] Initialized drm 1.1.0 20060810
[   28.623969] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.623976] pci 0000:00:02.0: setting latency timer to 64
[   28.624505] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   29.574272] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.585554] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1078.061641] CPU0 attaching NULL sched-domain.
[ 1078.061767] CPU0 attaching NULL sched-domain.
[ 1089.508779] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1100.168037] wlan0: no IPv6 routers present
[ 1114.024235] CPU0 attaching NULL sched-domain.
[ 1114.024351] CPU0 attaching NULL sched-domain.

```


Here is what I just found out:

If i boot my computer with the mouse plugged in:
it works... 
and 
if I unplug it and plug it back in:
it still works. 

Matter of fact i can unplug it and plug in another usb mouse and that mouse even works.
Conclusion: If i boot my computer with any usb mouse plugged in... I have no problems. If I boot my computer without a USB mouse... I am forever left to using my touchpad *Yuck!* If I come out of standby... I can only use my touchpad....

---

### Post by harry2006 on 2009-08-17
you might try this[this might(not) work, btw] 
it seems your sys is not able to load pr oper module right after you plug your mouse and the case is just the opposite when the sys boots with mouse plugged in...try manually loading the module for your mouse using modprobe...
note: the second post related to dmesg with mouse plugged-in doesn't seem to include the messages related to loading drivers for your mouse, you might have to _grep_ those messages...

---

### Post by SpaCeTraNce on 2009-08-17
> **harry2006 said:**
> you might try this[this might(not) work, btw] 
it seems your sys is not able to load pr oper module right after you plug your mouse and the case is just the opposite when the sys boots with mouse plugged in...try manually loading the module for your mouse using modprobe...

How do I do that????


> **harry2006 said:**
> note: the second post related to dmesg with mouse plugged-in doesn't seem to include the messages related to loading drivers for your mouse, you might have to _grep_ those messages...

I'm dont know how to grep things yet, I ran the grep --help. So would I do something like this:
```
dmesg | grep "something about mouse drivers goes here"
```... I ran dmesg without piping it and came up with a whole bunch of stuff. At the end of the list I saw the entries for when I was unplugging and replugging in the mouse but I got lost when looking for the mouse drivers getting originally loaded.

---

