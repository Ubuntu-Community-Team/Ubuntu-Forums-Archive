---
title: "Ubuntu 7.0.4 in Pavilion dv2000"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by citronio on 2007-07-15
I am having a problem with my cd-dvd drive after installing Ubuntu in a Pavilion dv2000 (a dv2525ea in fact).

I installed Ubuntu Studio from a dvd I burned using the laptop itself. After I installed it, I cannot access the cd-dvd drive at all. It does not even appear in the hardware manager. It is a cd-dvd SATA combo drive. And it does work, since it detects the any cd-dvd when I turn on the laptop, and reads it, no problem, but i cannot access it at all under ubuntu.

There is a folder in the Computer folder called "CD-ROM 1", but every time I try to open it I get the following error:

mount: special device /dev/hda does not exist

In the /dev folder there is no hda folder. There are several sda folders (sda, sda1, sda2, sda5), which are the hard drive and I think one of them is the cd rom (I do not have so many partitions in my hard drive!). 

From what I found around, it looks like the problem may be related to the fact that the cd drive is sata, and it looks like the system believes it is a partition from the hd.

Any ideas?

---

### Post by citronio on 2007-07-17
I have contacted HP, and they have told me it is a problem with the SATA controller.

They told me to disable the feature in the BIOS while a linux controller is released, but the menu they talk about to disable the SATA option in the BIOS is not available in my BIOS version.

While they get back to me, hopefuly, with a new suggestion, does anyone know a workaround to this?

Oh! btw, now I know what my drive is: HP EG919AV DVD RW SM DL LS FX n9400 Drive

---

