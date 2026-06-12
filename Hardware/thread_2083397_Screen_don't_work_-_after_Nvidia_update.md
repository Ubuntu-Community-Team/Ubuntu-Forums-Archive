---
title: "Screen don't work - after Nvidia update"
date: 2012-11-12
forum: Hardware
---

### Post by erezson on 2012-11-12
Hi,

I have Lenovo idepad with invidia N10. I run an update to the driver and after reboot the screen doesn't turn on at all.

Help

---

### Post by Dlambert on 2012-11-12
What guide/steps did you follow?

---

### Post by erezson on 2012-11-12
> **Dlambert said:**
> What guide/steps did you follow?

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings

---

### Post by erezson on 2012-11-13
Problem solved.

Because the screen didn't turn on at all I assumed that the driver update affected the BIOS, so I found a way to recover the BIOS with a USB flash drive.

For those who will find this message one day with the same problem, follow this: [http://forums.lenovo.com/t5/IdeaPad-S-series-Netbooks/LENOVO-BIOS-RECOVERY/td-p/332989](http://forums.lenovo.com/t5/IdeaPad-S-series-Netbooks/LENOVO-BIOS-RECOVERY/td-p/332989)

Cheers

---

