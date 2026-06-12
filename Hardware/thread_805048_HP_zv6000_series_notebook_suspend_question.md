---
title: "HP zv6000 series notebook suspend question"
date: 2008-05-23
forum: Hardware
---

### Post by Mauler5858 on 2008-05-23
I have Kubuntu 8.04 installed on my notebook, and i am having problems when awaking it from suspend mode.  I was able to activate suspend via the power settings, but when i awake it...it will hang up and the laptop will not operate correctly.  The only way i can seem to fix it is to restart x.

---

### Post by Melk79 on 2008-05-23
Do you have an Nvidia card?  I ran into some similar troubles... my screen would be simply white when resuming and I eventually resolved it, but it was Nvidia based.

---

### Post by aeleneski on 2008-05-23
I have the same laptop with ATI graphics, I am unable to even go into suspend mode. I seem to have this bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/212897](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/212897)

I am also running ATI 8.5 drivers.

---

### Post by Mauler5858 on 2008-05-24
> **aeleneski said:**
> I have the same laptop with ATI graphics, I am unable to even go into suspend mode. I seem to have this bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/212897](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/212897)

I am also running ATI 8.5 drivers.

Ah....this seems to be my problem as well, and i have the ati drivers.  i will bookmark that bug and keep track of it.

Thanks

---

