---
title: "Nvidia Quadro K620 Driver"
date: 2015-07-31
forum: Hardware
---

### Post by Yashwant_Singh on 2015-07-31
Hi,

I have Dell precision T1700 workstation E3 1226/ 1TB/4* 8GB/ DVDRW/ 2GB Nvidia K620 and installed ubuntu 14.10 but the display is showing 800X600.

Please share the Nvidia Quadro K620 2GB Card driver. Also share how to install the driver because i am new user of ubuntu.

Thanks,
Yashwant

---

### Post by grahammechanical on 2015-07-31
Ubuntu 14.10 reached end of life 23rd July. Its software repositories are now closed. You should upgrade to 15.04.

The way to change video drivers in Ubuntu from 14.04 and later is to go to System Settings>Software & Updates>Additional Drivers tab. You will need to be connected to the internet and you will need to allow the utility time to find suitable drivers. But there may be a problem because Ubuntu 14.10 has reached end of life.

The Nvidia web site recommends the 352.30 driver which may not be availble in 14.10 but might be available in 15.04. I cannot find any information that the 346 series drivers support the Quadro K620 card. You may find that even 15.04 does not have a driver for this card. You may need to install the development version of 15.10 which is halfway through its 26 week development period. I have been using 15.10 since the first week of development and it is remarkably stable. I would not normally recomend installing a development version but if that is the simple way of getting a driver for your video adapter then you may need to consider it.

A more complicated method is by means of a PPA. But first upgrade to 15.04 and see what drivers Additional Drivers is offering then.

Regards.

---

