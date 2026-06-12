---
title: "Alternate installer slow to create raid devices"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by Midahed on 2009-01-19
I'm using the Ubuntu 8.10 alternate CD to create four raid1 devices for /boot, /, swap and /home respectively.  I select manual partitioning and create the four partitions on each of the two drives:-

```
/boot    250 meg
/         25 gig
swap       5 gig
/home    170 gig
```

I then select the option to configure the raid devices.  It all works OK, but there's a long delay in the creation of the devices for swap and /home.  I select 'create MD device' and specify the use of two drives, zero spares, and identify the partitions to use.  Clicking 'continue' results in an almost instantaneous return to the screen ready to create the next device.  But that's only the case for the first two devices md0 and md1 for /boot and /.  The other two devices give every appearance of hanging when the device components are specified and 'continue' is clicked - the screen remains blank for about ten minutes, the disk access light is on constantly, but no disk activity can be heard.

It does eventually complete, but when I first saw this behaviour I was so convinced that it had locked-up that I rebooted the system.

What's it doing for all this time?  Why does the creation of md2 and md3 take so much longer than the creation of md0 and md1?

I would be better if the alternate installer had some mechanism to indicate that it was still running, or perhaps it could output a message to highlight those stages of the installation where things can take a while.

By the way, 8.04 is just the same.

Mike

---

### Post by Midahed on 2009-02-10
It turns out that it was a hardware problem that happened to manifest itself as 'pauses' during the installation process.  It's as if the system just stopped for several minutes, and then it would carry on as if nothing had happened.

The problem was that loads of the electrolytic capacitors on the motherboard were either bulging or had actually leaked.  There were six or so that were particularly badly affected - presumably because they were right next to the CPU heatsink and had been getting too warm.

A new motherboard sorted it out completely.

---

