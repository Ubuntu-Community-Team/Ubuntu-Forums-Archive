---
title: "Ubuntu Server 13.04 and HighPoint RocketRaid 640L"
date: 2013-05-29
forum: Hardware
---

### Post by T Whatley on 2013-05-29
Simply, has anyone gotten this to work?

I just installed the card and the drives attached to the controller show up on the controller bios bootup but they do not show up in ubuntu via fdisk -l.

It sounded like I needed a driver but following the instructions at [https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid) yielded no results... further research said that this no longer applied to to kernels > 3.6 (raring is 3.8).

---

### Post by T Whatley on 2013-05-30
Also, if it helps/matters, I do not need the RAID functionality on the card itself... I was going to setup a software raid with mdadm.

Additionally, I'm not throwing in the towel already, but if anyone has any recommendations for a decent and cheap-ish sata3 controller card that will work with raring, I'm all ears.

---

### Post by T Whatley on 2013-05-30
I contacted Highpoint support and they provided me with the attached updated driver.

It worked flawlessly.

After hearing horror stories of Highpoint support, they got back to me within 12 hours with the correct drivers... pleasantly surprised.

Drivers attached for anyone that runs into this in the future.

---

