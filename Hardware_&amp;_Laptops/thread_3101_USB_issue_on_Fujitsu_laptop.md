---
title: "USB issue on Fujitsu laptop"
date: 2004-11-03
forum: Hardware &amp; Laptops
---

### Post by bmichel on 2004-11-03
Hello,

Just installed Ubuntu 3 days ago, first time I run a Debian distrib and Gnome. A really great and clean system that will make me switch to Linux.

Nearly everything is ok but USB support.  I've some usb hardware (printer, external hard drive, memory card reader) and I would like them to be recognized. but it's seems there is a failure when some usb modules are loaded (ehci)

here an extract of dmesg :

ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB (ICH4) USB2 EHCI Controller
ehci_hcd 0000:00:1d.7: BIOS handoff failed (104, 1010001)
ehci_hcd 0000:00:1d.7: can't reset
ehci_hcd 0000:00:1d.7: init 0000:00:1d.7 fail, -95
ehci_hcd: probe of 0000:00:1d.7 failed with error -95


Beside that I've tried another debian distrib Mepis liveCD (2004.4) and all usb are working well.

after many hours of search, i've found the following thread in a linux kernel forum about kernel 2.6.8.x :

[http://www.uwsg.iu.edu/hypermail/linux/kernel/0407.1/1817.html](http://www.uwsg.iu.edu/hypermail/linux/kernel/0407.1/1817.html)

it seems this is a workaround for some buggy bios.

I've no clue how i could apply this workaround and i don't want to build my own kernel (Ubuntu people are doing very well this job no !!!).

Thanks for your help

---

### Post by Magneto on 2004-11-03
do you know for sure you can use ehci on your laptop? 

try typing this at the commandline
```
insmod usb-uhci
```

then type
```
dmesg
```

see if your usb devices are found now
if so
sudo nano -w /etc/modules
and add the line

usb-uhci

---

### Post by bmichel on 2004-11-04
[QUOTE=Magneto]do you know for sure you can use ehci on your laptop? 

try typing this at the commandline
```
insmod usb-uhci
```
[/QUOTE]

response is module not found.  

lsmod or dmesg show that uhci-hcd is loaded. is it the same module ?

As I said in my post, I tried Mepis liveCD to check the hardware and everything is ok.

---

### Post by Magneto on 2004-11-04
[QUOTE=bmichel]response is module not found.  

lsmod or dmesg show that uhci-hcd is loaded. is it the same module ?

As I said in my post, I tried Mepis liveCD to check the hardware and everything is ok.[/QUOTE]

uhci_hcd is the uhci usb 1.0 driver for linux kernel version 2.6.x

usb-uhci is the usb 1.0 driver for linux kernels 2.4.x

ehci is the usb 2.0 driver and it might work with your motherboard's usb controller but I don't think so- I googled and saw people using that same hardware successfully with uhci

try 

rmmod ehci_hcd 

then 

rmmod uhci_hcd

then 

insmod uhci_hcd

then dmesg

ill bet that will work

---

### Post by bmichel on 2004-11-04
Same result.

I can't load modules with insmod but modprobe is ok.

after modprobe ehci-hcd, dmesg | grep ehci shows a failure of  this module:

ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB (ICH4) USB2 EHCI Controller
ehci_hcd 0000:00:1d.7: BIOS handoff failed (104, 1010001)
ehci_hcd 0000:00:1d.7: can't reset
ehci_hcd 0000:00:1d.7: init 0000:00:1d.7 fail, -95
ehci_hcd: probe of 0000:00:1d.7 failed with e

I forgot to mention that i have one usb port that is ok. this is the one with my mice. Mice seems handled by the uhci (usb1.1) module rather than ehci (usb2.0) like the other peripherals.
# lsusb

Bus 003 Device 002: ID 1241:1111 Belkin (?) Mouse
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

back to my original post, the linux kernel 2.6.8 thread below identified usb V2 issue with some bios (Fujitsu Amilo 7830 is one) and give a workaround. so how to apply it  or perhaps is it already applied by default in the coming ubuntu kernel release ?
[http://www.uwsg.iu.edu/hypermail/linux/kernel/0407.1/1336.html](http://www.uwsg.iu.edu/hypermail/linux/kernel/0407.1/1336.html)

---

### Post by Magneto on 2004-11-04
[QUOTE=bmichel]Same result.

I can't load modules with insmod but modprobe is ok.

after modprobe ehci-hcd, dmesg | grep ehci shows a failure of  this module:

ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB (ICH4) USB2 EHCI Controller
ehci_hcd 0000:00:1d.7: BIOS handoff failed (104, 1010001)
ehci_hcd 0000:00:1d.7: can't reset
ehci_hcd 0000:00:1d.7: init 0000:00:1d.7 fail, -95
ehci_hcd: probe of 0000:00:1d.7 failed with e

I forgot to mention that i have one usb port that is ok. this is the one with my mice. Mice seems handled by the uhci (usb1.1) module rather than ehci (usb2.0) like the other peripherals.
# lsusb

Bus 003 Device 002: ID 1241:1111 Belkin (?) Mouse
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

back to my original post, the linux kernel 2.6.8 thread below identified usb V2 issue with some bios (Fujitsu Amilo 7830 is one) and give a workaround. so how to apply it  or perhaps is it already applied by default in the coming ubuntu kernel release ?
[http://www.uwsg.iu.edu/hypermail/linux/kernel/0407.1/1336.html](http://www.uwsg.iu.edu/hypermail/linux/kernel/0407.1/1336.html)[/QUOTE]


yeah i just read some other places too about the same issue- seems some buggy bios's play around with the wrong bit
go to kernel.org and get some kernel sources and compile a new kernel yourself- you dont need all the crap ubuntu has as modules anyway 

2.6.8rc1 is from july and we're at 2.6.9 already - i think the patch is in there now

edit -  this was patched twice- once which screwed it up in 2.6.8 and again to fix it- thats what it looked like to me- no complaints about pre 2.6.8 handoff problems then rc1 comes out and its hosed
[http://kerneltrap.org/node/view/3443](http://kerneltrap.org/node/view/3443)         2.6.8-rc1 - broken
[http://kerneltrap.org/node/view/3694](http://kerneltrap.org/node/view/3694) -       2.6.9-rc1 - fixed
and no mention of the problem in 2.6.10-rc1 which is where we are as of 2 weeks ago

---

### Post by bmichel on 2004-11-04
Thanks for your help Magneto,

In fact, I will not go to build my own kernel and wait for Ubuntu release. I'm not a linux expert and don't want to become one. I use linux for web apps development as win xp. 
I think this is the spirit of Ubuntu to provide a nice ready to use Linux distrib. If my wishes were to build from scratch, Gentoo is the right choice.

Cheers

---

### Post by bmichel on 2004-11-09
I've updated my laptop bios (1.08c) and now usb is working fine. So problem was really bios rather than Linux.

Ubuntu is wondefull !!!

Cheers

---

