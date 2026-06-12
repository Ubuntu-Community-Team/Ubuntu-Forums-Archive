---
title: "HP Pavilion a1040n - Sound not working"
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by fbeauregard on 2005-05-01
Just installed Ubuntu 5.04 on this new HP desktop with no problem whatsoever except that the sound card did not get detected.

I disabled PnP Bios and made sure the on-board sound card is active. Also booting with the pnpbios=off option.

Still does not work.

Here is the info about the on-board card.

Integrated Intel High Definition(TM) audio (Azalia)
* Realtek ALC 880 chipset
* THX certification support
* 8-channels for Full Dolby 5.1/6.1/7.1 surround sound support with Dolby Pro Logic IIx

Output from lscpi :
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

Help would be greatly appreciated.

Francois

---

### Post by gasolio on 2005-05-02
Install alsa driver 1.0.9 and sound work fine.

---

### Post by roachkazy on 2007-10-13
i am having the same problem but am using ubuntu 7, and am very new. can someone tell me how to instal this driver i just downloaded it from [http://rpm.pbone.net/index.php3/stat/4/idpl/3301313/com/alsa-driver-1.0.9-0.1.rc1.rhfc2.ccrma.i586.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/3301313/com/alsa-driver-1.0.9-0.1.rc1.rhfc2.ccrma.i586.rpm.html)

---

