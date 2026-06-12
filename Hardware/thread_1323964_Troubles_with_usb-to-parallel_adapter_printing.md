---
title: "Troubles with usb-to-parallel adapter printing"
date: 2009-11-12
forum: Hardware
---

### Post by ZioNemo on 2009-11-12
Hi,
I have a brand new server that has NO parallel port, so, in order to attach my ancient and glorious HP Laserjet 4L :) , I bought an USB-to-parallel adapter.

```

mcon@server:~$ lsusb
...
Bus 003 Device 003: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
...
```

Apparently everything is ok and I can user System->Configuration->Printing to recognize my printer.

Problem is when I try to print a test page I get:
```
Nov 12 12:14:29 server kernel: [ 7089.737165] usblp0: nonzero read bulk status received: -62
Nov 12 12:14:30 server kernel: [ 7089.922140] usblp0: nonzero read bulk status received: -62
Nov 12 12:14:31 server kernel: [ 7091.426043] usblp0: nonzero write bulk status received: -62
```
The Printer is activated (deceived data indicator is on) but nothing is printed. If I force page eject directly on the printer I see a small part of the ubuntu test page (about one inch) and then some gibberish.

I found another post that seems promising ([hp-6l-am-usb-port-mit-usb-zu-parallel-adapter]("http://forum.ubuntuusers.de/topic/hp-6l-am-usb-port-mit-usb-zu-parallel-adapter/?highlight=usb+adapt")) but that is a bit German and my knowledge of that fine language is lacking :(
I seem to understand they solved the problem somehow, but I can't divine how.

Please help me
Thanks in Advance
ZioNemo

---

### Post by Yorkiede on 2010-01-06
In the German he basically says to buy the "Digitus DC USB-PM1 VPR 4.0" but he still cannot get it to print and he has had no new answers

---

### Post by k_a_a on 2010-07-10
I'm having trouble getting even as far as you have. I have a (very cheapo) usb-parrallel (DB25) converter cable which I know uses a pl2305 prolific chipset (from the windows drivers that come with it). When I plug it in an do 

lsusb

it is not listed.
Another post suggested: 

modprobe pl2305

is required to get it working but when I do this I get:

FATAL: Module pl2305 not found.

I have recently purchased and used a pl2303-based usb-serial converter that worked perfectly. I think i remember needing to do 'modprobe pl2303' to get it working but after that it worked fine everytime. Do you need to download/install modules?

Any help appreciated.

Cheers,

- Khalid.

---

### Post by mathiaho on 2010-10-02
Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=894223&highlight=laserjet+4L&page=2]("http://http://ubuntuforums.org/showthread.php?t=894223&highlight=laserjet+4L&page=2")

Post #15

It worked for me :)

Hope it helps

---

### Post by DkSoul on 2010-10-28
> **ZioNemo said:**
> ```

mcon@server:~$ lsusb
...
Bus 003 Device 003: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
...
```Apparently everything is ok and I can user System->Configuration->Printing to recognize my printer.

Problem is when I try to print a test page I get:
```
Nov 12 12:14:29 server kernel: [ 7089.737165] usblp0: nonzero read bulk status received: -62
Nov 12 12:14:30 server kernel: [ 7089.922140] usblp0: nonzero read bulk status received: -62
Nov 12 12:14:31 server kernel: [ 7091.426043] usblp0: nonzero write bulk status received: -62
```The Printer is activated (deceived data indicator is on) but nothing is printed. If I force page eject directly on the printer I see a small part of the ubuntu test page (about one inch) and then some gibberish.
I'm having the exactly same problem! Have you managed to fix it?

---

