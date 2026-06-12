---
title: "2 devices sharing same IDE type cord?"
date: 2010-07-16
forum: Hardware
---

### Post by Nick_Jinn on 2010-07-16
Is this bad? Can I have a hard drive and an optical drive or two optical drives connected to the same motherboard through the same cord? Some of them have 2 connectors on them.

---

### Post by SebX86 on 2010-07-16
Hi,

It's not an issue as long as the two devices work at the same speed. 
In the other case, you will slow down the faster device.

If you have for example an UDMA33 optical drive on the same
cable than you HDD (which is theorically faster), then buy a new
cable and set the Optical drive on the other port. Otherwise keep it like it is now...

Sébastien

---

### Post by cascade9 on 2010-07-16
Yes, you can have 2 IDE devices on 1 IDE channel. Just make sure that only one of the devices is set to 'master' and the other device is set to 'slave' (or both set to 'cable select'). The jumper position for 'master', 'slave' and 'cable select' are normally found on the top of the drive, sometimes the rear of the drive, above where the IDE cable and molex plug is. 

> **SebX86 said:**
> Hi,

It's not an issue as long as the two devices work at the same speed. 
In the other case, you will slow down the faster device.

If you have for example an UDMA33 optical drive on the same
cable than you HDD (which is theorically faster), then buy a new
cable and set the Optical drive on the other port. Otherwise keep it like it is now...

Sébastien

That was true a long time ago, its not anymore. 

You can mix and match UDMA/ATA 33, 66, 100 and 133 and get full speed from both devices on a single IDE channel.

---

### Post by Nick_Jinn on 2010-07-16
You have been a great help Cascade.

I am thinking about putting 2 optical drives in my machine. Only problem is that there is only 1 IDE channel in my motherboard but 8 SATA plut-ins.....I guess they are expecting me to get SATA optical disks or something.

---

### Post by cascade9 on 2010-07-17
No problem. 

I havent run 2 optical drives since I changed from a CD-RW + DVD ROM (read only) a few years ago. Still, it should be fine if you want to have 2 optical drives on IDE. Apart from the master/slave/cable select settings, your going to need a IDE cable with 2 connectors (well, 3 really, but one gets plugged into the motherboard) 

BTW, the 'long' end goes into the motherboard, and the 'short' end (the end where the connectors are closer together) plugs into the drives ;)

---

### Post by Nick_Jinn on 2010-07-18
Thanks. It would be a shame if I tried to superglue it. ;"

---

