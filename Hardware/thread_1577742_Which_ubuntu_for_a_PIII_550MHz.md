---
title: "Which ubuntu for a PIII 550MHz?"
date: 2010-09-19
forum: Hardware
---

### Post by asktoby on 2010-09-19
I have a PIII 550MHz laptop here.
What do you think would be faster: Xubuntu, or Ubuntu netbook edition?

---

### Post by sikander3786 on 2010-09-19
How much RAM have you got? I think Xubuntu will be much better.

---

### Post by Cpierce on 2010-09-19
Don't forget Lubuntu as well.

---

### Post by cascade9 on 2010-09-19
Xubuntu doesnt run much better on low spec systems than ubuntu does. 

You might be better of with lubuntu, or a minimal install + Xfce.

---

### Post by sikander3786 on 2010-09-19
> **cascade9 said:**
> Xubuntu doesnt run much better on low spec systems than ubuntu does. 

You might be better of with lubuntu, or a minimal install + Xfce.
Xubuntu worked for me on a PIII 600MHz with 256 RAM. And it performed much better than Ubuntu. Still I agree, Lubuntu is a better choice.

---

### Post by snowpine on 2010-09-19
You can read about Ubuntu/Xubuntu system requirements here:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Your computer is not a "netbook" so I do not recommend the Netbook Edition.

Depending on how much RAM you have, you might be happier with a non-Ubuntu solution such as Puppy Linux.

---

### Post by efflandt on 2010-09-20
Two boot parameters you may want to check out which I used on PIII 550 I think with 512 MB:

**acpi=force** because the kernel does not trust acpi before y2k.

**lapic** because mine would not fully power down during shutdown without that.

Flash seemed to run smoother in Ubuntu than Kubuntu, but still sluggish frame rate.  Eventually I installed Ubuntu 8.10 based Qimo for kids and upgraded that to 9.04.  Worked fine for the kids games and no great loss if my twin nephews break it.

I recently installed IPCop on an older K6-2/400 w/128 MB RAM and it had no acpi, so trying to force that did nothing good or bad.  And I do not think it did apic or lapic either, but it fully powered down anyway with the older 2.4 kernel used by IPCop.  It only uses 30 watts and works fine as a back up squid proxy at work.

---

### Post by asktoby on 2010-09-27
Just to follow up, I went with Puppy Linux and have been very pleased with it. Very fast on this old machine, but fully featured, doing things like Youtube and Wifi out of the box.

---

### Post by garner_nc on 2010-09-27
I run Puppy off a flash drive on older machines. Sometimes just for the heck of it on my main machine. It's REALLY fast compared to a full boat distro. It seems to have most everything I need to do.

All the Best,
D. White

---

