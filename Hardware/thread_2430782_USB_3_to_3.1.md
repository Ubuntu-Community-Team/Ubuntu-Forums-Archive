---
title: "USB 3 to 3.1?"
date: 2019-11-07
forum: Hardware
---

### Post by Robbyx on 2019-11-07
I can get a pci card to run 3.1. My external HD is usb 3. 

Will the usb 3 output from the HD plug into the usb3.1 card in the computer and not have compatibility problems?

As 3.1 is much faster than 3, will I see an improvement in speed of data tfr from the HD drive to the computer because of the 3.1card or will it default to usb 3 speeds?

---

### Post by CatKiller on 2019-11-07
> **Robbyx said:**
> I can get a pci card to run 3.1. My external HD is usb 3.  

USB specifications are stupidly named; things can state that they're USB 3 when they're using USB 2.

> Will the usb 3 output from the HD plug into the usb3.1 card in the computer and not have compatibility problems? 

In principle, that is what's supposed to happen. 

> As 3.1 is much faster than 3, will I see an improvement in speed of data tfr from the HD drive to the computer because of the 3.1card or will it default to usb 3 speeds?

Both ends will need to be able to operate at a given level for it to be available. Both ends negotiate what they're able to do, and then pick something they can both do. Transfer speeds will happen at the level of the slowest end, or even slower if they're unable to negotiate.

---

### Post by Robbyx on 2019-11-07
Thank you. I am still unclear.  Does your answer mean that if I have an external HD that can run 3.0 then it will not be able to operate at 3.1 speeds when attached to a 3.1 hub?  Instead will it be restricted to 3.0 transfer speeds even when connected to the 3.1 hub.

---

### Post by TheFu on 2019-11-07
> **Robbyx said:**
> Thank you. I am still unclear.  Does your answer mean that if I have an external HD that can run 3.0 then it will not be able to operate at 3.1 speeds when attached to a 3.1 hub?  Instead will it be restricted to 3.0 transfer speeds even when connected to the 3.1 hub.

The answer isn't clear because there's what should happen, in theory. Most storage devices can't come close to USB3.0 speeds. I've never seen any spinning disk storage device come  close to 50% of the USB3.0 theoretical throughput.

Then there is the real world where nobody can answer without having the exact same setup you have and actually trying it.

USB3 is 5Gbps, in theory.
USB3.1 is 10Gpbs, in theory.

The slowest device in your setup is 5Gbps, so nothing can exceed that in the chain.  If you get a USB3.1 storage device and connect it to the hub, we'd all love if the hub was limited to 10Gbps even if their is a USB3 (5Gbps) device also connected to a different port.  In theory, it should work that way. In practice, real-world, who knows?  

Heck, you'd be doing well to get 3000 Mbps from a spinning disk storage device.

I have a USB3.1 port on a system here. I do not have any USB3.1 storage devices.  The USB3 storage devices I've connected to it are slow, spinning disks, laptop disks put into cheap external enclosures and only powered over the USB connection.  Those  get closer to 40MBps (320 Mbps) throughput.  I do have external USB3 storage devices with external power which are much faster, but those are connected to other systems.

Here's some trivial tests on a USB3 port with a USB3 external, powered, device:
```
thefu@istar:/misc/b-D3$ mkdir tmp
thefu@istar:/misc/b-D3$ cd tmp/
thefu@istar:/misc/b-D3/tmp$ dd if=/dev/zero of=./zeros bs=4M count=10
10+0 records in
10+0 records out
41943040 bytes (42 MB, 40 MiB) copied, 0.167864 s, **250 MB/s**
thefu@istar:/misc/b-D3/tmp$ dd if=/dev/zero of=./zeros bs=4M count=100
100+0 records in
100+0 records out
419430400 bytes (419 MB, 400 MiB) copied, 2.60932 s, **161 MB/s**
thefu@istar:/misc/b-D3/tmp$ dd if=/dev/zero of=./zeros bs=4M count=500
500+0 records in
500+0 records out
2097152000 bytes (2.1 GB, 2.0 GiB) copied, 13.7992 s, **152 MB/s**

```
Multiply by 8 to get Mbps .... 
I should mention, I ran a number of initial runs to force the disk built-in cache to be full with other stuff.

For fun, I took an old, cheap, m.2 16GB SSD that has been moved to an external enclosure and ran the last test a few times. The file system on it is ext4. The fastest run was:
```
2097152000 bytes (2.1 GB, 2.0 GiB) copied, 54.1846 s, **38.7 MB/s**
```

I also tested a reputable SATA3 internal connected SSD and got  571 MB/s ... which turns into 4500 Mbps.  SATA3 is limited to 6Gbps.

Basically, if you aren't hooking up NVMe storage devices, USB3.1 seems to be a nice-to-have, for now, at least in my testing.  YMMV.

---

### Post by CatKiller on 2019-11-07
> **Robbyx said:**
> Thank you. I am still unclear.   

Welcome to the world of USB. 

> Does your answer mean that if I have an external HD that can run 3.0 then it will not be able to operate at 3.1 speeds when attached to a 3.1 hub?  Instead will it be restricted to 3.0 transfer speeds even when connected to the 3.1 hub.

USB 3.0, USB 3.1 gen 1, and USB 3.2 gen 1×1 are all exactly the same thing. The higher speeds that are theoretically possible with the newer specifications get different, exceedingly similar, names. So the speeds that you'll be able to get depend on the specific capabilities of each side of the connection, which may or may not be truthfully advertised. 

If your drive's connection can only operate at the slowest USB 3.0 speed, then it can only ever go that fast even if you plug it into something that could potentially go faster.

If the two sides are unable to negotiate that speed, the transfer will go slower still.

---

### Post by Robbyx on 2019-11-07
Thank you for your help. It is now a lot clearer.

---

### Post by TheFu on 2019-11-07
[https://www.howtogeek.com/446892/usb4-whats-different-and-why-it-matters/](https://www.howtogeek.com/446892/usb4-whats-different-and-why-it-matters/)  was published today about USB4.> 
Behind the scenes, the 40 Gbps USB4 speed is called Gen 3×2, and the 20 Gbps speed is Gen 2×2.

The USB guys need to stop the confusion and be consistent with their names.

---

### Post by tux-peng on 2019-11-07
Sometimes a higher revision USB port can run devices faster, but never exceeding the USB spec of the slower unit

---

