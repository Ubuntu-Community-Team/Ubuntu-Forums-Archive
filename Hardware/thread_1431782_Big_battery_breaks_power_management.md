---
title: "Big battery breaks power management"
date: 2010-03-17
forum: Hardware
---

### Post by irober02 on 2010-03-17
I have an Acer Aspire One running Ubuntu 9.10. All is good except for poor battery life so I bought a big battery (UM08B73 ZG5) with about 3 times the capacity of the standard one.

With the unit shutdown, I swapped in the new battery left it to charge fully (as indicated by the power LED extinguishing) and then powered up. Yippee, the power manager indicates 7-9 hours charge and it certainly has extended runtime on the battery.

My problem comes when I reconnect the power supply. The unit detects the power connection, briefly goes into powered mode but then swaps back to battery operation and indicates the battery is critically flat warns that it will soon shut down. (I don't know whether it really will shut down or not.)

It seems that some part of either ubuntu (gnome-power-manager 2.28.1 perhaps) or the BIOS hasn't realised I've connected a bigger battery, think it's overcharged and swap into discharge mode.

The power supply seems to charge the battery OK when it's shutdown and when it's sleeping. It also seems to be OK when I boot with the power supply connected. But, when I reconnect the power it goes haywire.

Any suggestions? Perhaps it's a bug in BIOS. Perhaps there's someway I can tell power-manager the new capacity of the battery.

bye

ian

---

### Post by irober02 on 2010-03-25
Here I go responding to my own post again...

I finally got frustrated enough and brave enough to upgrade the BIOS for my AAOD250. It went perfectly smoothly (after I remembered how to change to a different drive in DOS) and now my AAOD250 understands what to do with a big battery. I'm hoping that it won't freeze when I leave the lid closed for a long time (without suspending) but I haven't checked that yet.

For the record, I downloaded BIOS_Acer_1.27_A_A.zip from the Acer website and used unetbootin to create a bootable DOS USB drive (FreeDOS). 

It did take a while to convince myself that my Acer Aspire One KAV60 (sticker on base) is actually and Acer Aspire One D250. I ran the risk of bricking my nice netbook but it paid off and now it's working better.

Sucks to Acer for withdrawing Linux support. Fortunately, their product still works well with this OS. :-)

---

