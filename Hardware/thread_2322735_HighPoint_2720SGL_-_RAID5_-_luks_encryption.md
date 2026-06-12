---
title: "HighPoint 2720SGL - RAID5 - luks encryption"
date: 2016-04-30
forum: Hardware
---

### Post by boba23 on 2016-04-30
Hey folks,

I am about to release my old Samsung 750gb drives md software raid5 array with new WD Blue 6TBs. Bought an 2720SGL to replace my aging Promise SATA300 (which served me well btw). Question I am facing is, do I actually want to use the Highpoint "hardware raid" features or would I be better off sticking with mdtools / mdadm.
Especially I want to keep all my data encrypted with luks, like I have it now, and still be able to have the mdadm features I need available. so the main question is, if I go HighPoint raid:

- can I still do online resizing of my raid5 array, e.g. add additional 6TB drives and most important does this work with an luks encrypted array?
- is it possible to configure e-mail alerts
- how about performance? I guess the raid5 performance of the controller should be a little better than software raid? (I am using an Athlon X2 245e, 8GB Ram, Ubuntu headless 14.04.4 Server)

I will use the controller in any case, if not hw raid, then just as hba, should I then flash the non-raid bios from highpoint?

Any other pros and cons that one could think of?

thanks

boba

---

### Post by frostschutz on 2016-04-30
For Linux only you're usually better off with mdadm. No need to buy an expensive HW-RAID controller (and what happens if it dies), a usually more cost-effective HBA will do (or simple SATA controllers, onboard SATA, for low number of disks).

> I guess the raid5 performance of the controller should be a little better than software raid?

Well, possibly. To the OS it looks like a single disk so everything RAID related is handled by the controller itself.

The software RAID has to do its own parity calculations, and split / merge IO to / from each disk by itself. More work for the kernel.

But it's not worth the price of a HW-RAID controller. On my current Haswell box, I have this message in my kernel logs:

```

[    0.083248] raid6: sse2x1   gen() 10406 MB/s
[    0.100260] raid6: sse2x1   xor()  8160 MB/s
[    0.117274] raid6: sse2x2   gen() 13019 MB/s
[    0.134285] raid6: sse2x2   xor()  8970 MB/s
[    0.151297] raid6: sse2x4   gen() 15246 MB/s
[    0.168308] raid6: sse2x4   xor() 10791 MB/s
[    0.185321] raid6: avx2x1   gen() 20429 MB/s
[    0.202334] raid6: avx2x2   gen() 23500 MB/s
[    0.219348] raid6: avx2x4   gen() 27546 MB/s
[    0.219417] raid6: using algorithm avx2x4 gen() 27546 MB/s
[    0.219490] raid6: using avx2x2 recovery algorithm

```

The kernel runs a little benchmark there to determine the best algorithm for parity calculations, in this case for raid6 (which is more complicated than raid5 due to double-parity).

The algorithm it ends up using is an order of magnitude faster than the LUKS encryption speed with AES-NI enabled (on my box according to `cryptsetup benchmark`, aes-xts 256bit ~2600MiB/s, 512bit ~2000MiB/s).

Basically you should not be able to notice any performance impact fromt his. If there are performance issues with software raid they'll have other causes... the Linux kernel RAID is not perfect (but neither is hardware and the kernel at least can be improved over time).

> should I then flash the non-raid bios from highpoint?

I'm not familiar with the BIOS of this card. For mdadm, ideally it should present drives as they are (full capacity, including smartctl capability, whatever physical sector size the drive has), and not emulated as virtual raid-0 drives.

Test it... a drive partitioned using GPT while hooked on your controller, should be detected properly when connecting it to an onboard port.

> - is it possible to configure e-mail alerts

That should be possible for any kind of RAID, with true hardware RAID you usually need a utility specific to your hardware to query the array state (and have a service in the background monitoring and sending mails if need be).

With mdadm you should run RAID self tests but also SMART self tests and montoring... detect errors early, replace disks immediately.

---

