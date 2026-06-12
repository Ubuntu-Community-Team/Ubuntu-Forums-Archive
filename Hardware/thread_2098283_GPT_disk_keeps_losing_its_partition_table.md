---
title: "GPT disk keeps losing its partition table"
date: 2012-12-26
forum: Hardware
---

### Post by JPTaylor on 2012-12-26
I recently upgraded my machine's motherboard to a spare ASRock M3A770DE I had, from an older Asus board - and am having some peculiar issues..

I'm on 12.10 with the 3.5.0-21 kernel, running the 'server' x64 flavour. 

Previously I had two highpoint rocketraid 2640x1 SATA controllers, for which I had to manually build the drivers from source (and getting them working on 3.x kernels is no trivial matter) - the new motherboard only has one PCIe X8 slot free so have gone down to one controller in the meantime to try and get things moving until I can get an appropriate adaptec one. 

I have 6 3TB disks, and 2 1TB disks, running in JBOD mode. On each controller (on board and the RR2640) there are 1x 1TB drive and 3x 3TB drives. This setup worked fine on my previous board..

however weird things are happening now - and it seems that all of my GPT drives I had attached to the rocketraid controller keep losing their partition table whenever I reboot. Each are western digital WD30EZRX drives, with a single ext4 file system. 

If I run gdisk against them, repair the main GPT from backup and do a partprobe, the partitions reappear, I can mount them ok and can access my data once again. However as soon as I reboot it looses this info and I get the usual message on boot. Again if I run through those tasks again, boot continues as normal. Subsequent fsck's on the disks showed no errors, and I am at a bit of a loss as to why.

I am inclined to think that it is a combination of some kind of kernel/hardware bug (I recall some issue with ext4 recently) but more likely crappy drivers from highpoint. I suspect upgrading to a decent adaptec card will solve some, if not all,  of the issues but before I part with the best part of $400 on a suitable 8 port card, is there anything else I have yet to try?

---

### Post by JPTaylor on 2012-12-26
Oh, and the GPT drives attached to the on board controller work just fine and have not lost their GPT tables.

---

### Post by oldfred on 2012-12-26
Does this board have the Asrock asmedia SATA ports. Someone posted this:

> So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!
    

And someone else:

> Asrock Extreme4 Z77 motherboard, which has 4 SATA3 ports: 2 Intel ports (0 & 1) and 2 Asmedia ports (A0 & A1).Had my DVD drive connected to one of the Asmedia ports (A1), and so I tried switching the connection to one of the Intel SATA2 ports and the errors went away.

    

---

### Post by JPTaylor on 2012-12-28
Well, after some further updates.. And flashing the firmware of the raid controller, it finally sprang to life! 

I'm definitely getting an adaptec or megaraid card soon though :)

---

