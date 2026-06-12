---
title: "Battery Not Recognised"
date: 2013-05-25
forum: Hardware
---

### Post by comradetimkin on 2013-05-25
I have recently fixed a Samsung netbook and have tried installing Ubuntu, Xubuntu and Lubuntu onto it. In all instances the battery is not correctly recognised, in spite of the fact that it's clearly working (maintains power without ac). It's mighty frustrating, as on netbook it's kind of vital for me to know the correct battery status, being as I intend to use it mainly on the move and have a nice extended battery for it. 

I have Ubuntu on my main powerful laptop and have no issues with the battery, and am at a loss to understand what the issue is. On the netbook, the problem has variously manifested itself in lubuntu by showing random indications (one second it shows 7% charged, the next it claims 100%, then 0%), and in Xubuntu and Ubuntu by indicating that there is no battery present at all.

I have spent two days now reading around on this, and am no closer to fixing it. I did wonder whether a BIOS update would sort it, but that requires Windows as Samsung do not provide BIOS update for the NC10 in any other format. 

Please help! Thanks you.

---

### Post by linrunner on 2013-05-25
Hi,

i would definitely try a BIOS update first.

---

### Post by comradetimkin on 2013-05-25
> **linrunner said:**
> Hi,

i would definitely try a BIOS update first.

Right now that's proving tricky, as I am not having any success installing Windows via usb. Have tried with both XP and then 7, both being a total pain - XP can't get past the second stage of installation because of some missing .dll error, and 7 won't install after the initial screens because of missing drivers (various work-arounds tried and failed) - but I guess that's off-topic for here really. The point is, it looks like I'm stuck with this Bios for the forseeable, and wonder whether there is anything else I can try. 

Thanks for the initial reply, any other ideas?

---

### Post by comradetimkin on 2013-05-25
Further  update - after hours of searching about and no experience in doing such  operations, I was successful in flashing the last BIOS version released  for the machine, and it has unfortunately made no difference at all  (other than probably taking a few minutes off my life expectancy when  watching the machine turn itself off at the end of the process - it took  me a couple of seconds to find out this was in fact to be expected). 

I have to say that the issue seems pretty widespread, with loads of  people reporting such problems, and yet there is virtually nothing out  there suggesting any solution. For something as basic and necessary as  this, it seems surprising that a fix doesn't appear to be being  aggressively pursued. It's a fundamental piece of hardware!

Interrogating ACPI shows the battery is detected (battery present)  but percentages are all 0%, so absolutely no idea how much juice is  there. The icon on the panel says 0% too, and conky shows empty status.  Grrr.

---

### Post by linrunner on 2013-05-26
When ACPI reports zero for all values, something goes wrong between ACPI BIOS and the kernel. Hence my suggestion to update the BIOS (always a bit thrilling ...).

Which version of Ubuntu do you use? You tried different flavours, but (i suspect) all from the same version with the same kernel?

---

### Post by comradetimkin on 2013-05-27
Am currently using Xubuntu, as mentioned earlier I have tried Ubuntu, Lubuntu and Xubuntu, so yes - all the same kernel. Any suggestions for a nice, light, netbook-suitable distro with a different kernel?

---

### Post by comradetimkin on 2013-05-28
Come on folks, surely someone has a clue for something as fundamental as the latop battery not being recognised?? This is driving me to distraction. I tried rolling back the kernel to an earlier version, which initially *appeared* to work - but lo and behold, once rebooted it's right back to its old tricks, 0% all the way. 

This is just mad, there must be a solution! Seriously grateful for any help that anyone can offer.

---

### Post by linrunner on 2013-05-28
You still didn't answer my question about the Ubuntu **version**: 12.04, 12.10, 13.04, ...?

---

### Post by comradetimkin on 2013-05-28
Ah sorry, I thought you meant which distro - apologies for not reading more closely. Have tried Ubuntu 12.04, Lubuntu 13.04, currently using Xubuntu 13.04. Thanks for bearing with me - although I've dabbled in the past, I'm really quite a noob at this.

---

### Post by linrunner on 2013-05-28
I would give Xubuntu (or Ubuntu) 12.04**.1** a last try &#8211; **.1** because it still uses the "old" 3.2 kernel.

---

### Post by comradetimkin on 2013-05-28
As per my last reply, have tried Ubuntu 12.04, and also since your last post have also tried Lubuntu 12.04 on a live boot with no luck.

---

### Post by linrunner on 2013-05-29
Then I'm out of advice ...

---

