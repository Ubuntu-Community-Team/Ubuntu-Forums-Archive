---
title: "Ubuntu 12.04 LTS Suspend/Resume Freezing on ASUS UX32VD"
date: 2012-07-19
forum: Hardware
---

### Post by dmacm on 2012-07-19
I have the ASUS Zenbook Prime UX32VD, specs [here.]("http://www.asus.com/Notebooks/Superior_Mobility/ASUS_ZENBOOK_UX32VD/#specifications")

I have the model with the I7 and the 500Gb hdd with 24G SSD.

I am experiencing an issue where, whenever I close my lid, or click suspend from the menu, my computer freezes completely. I hit power and my keys light up and the fan spins louder, but I cannot bring up anything on the screen, all it shows is a blank black screen. I have read several similar issues. Any help would be greatly appreciated!

---

### Post by SveinT on 2012-07-20
> **dmacm said:**
> I have the ASUS Zenbook Prime UX32VD, specs [here.]("http://www.asus.com/Notebooks/Superior_Mobility/ASUS_ZENBOOK_UX32VD/#specifications")

I have the model with the I7 and the 500Gb hdd with 24G SSD.

I am experiencing an issue where, whenever I close my lid, or click suspend from the menu, my computer freezes completely. I hit power and my keys light up and the fan spins louder, but I cannot bring up anything on the screen, all it shows is a blank black screen. I have read several similar issues. Any help would be greatly appreciated!

Sadly, this is a common issue with this model. Suspend works on my machine, however, if I wait less than ~10min before resuming.

Hopefully it will be fixed soon. What version of ubuntu are you running? And what kernel (run "uname -a" in terminal)?

---

### Post by peter rus on 2012-07-24
Have a look at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027828](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027828)

When on Quantal: enable the quantal-proposed repo and do a dist-upgrade, please report results at above url

---

