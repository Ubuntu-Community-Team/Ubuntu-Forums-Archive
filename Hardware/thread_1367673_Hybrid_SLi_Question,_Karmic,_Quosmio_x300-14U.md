---
title: "Hybrid SLi Question, Karmic, Quosmio x300-14U"
date: 2009-12-29
forum: Hardware
---

### Post by Pap88 on 2009-12-29
Hi everyone,
I have a Toshiba Qosmio X300-14U and I have had a bit of a headache so far getting any linux distro installed. Finally i have 9.10 installed, and the Nvidia 185.0 Driver active and configured. I just have two queries.

The onboard bluetooth only works if i've booted windows and used the toshiba bluetooth software before rebooting into linux. Any suggestions would be much appreciated.

Second, and more importantly, i realise that there is no support for Hybrid SLi, but i was wondering if it was possible to force my system to use the more powerful card instead of the weak one?

Thanks.

---

### Post by Martins2040 on 2010-02-06
> **Pap88 said:**
> Hi everyone,
I have a Toshiba Qosmio X300-14U and I have had a bit of a headache so far getting any linux distro installed. Finally i have 9.10 installed, and the Nvidia 185.0 Driver active and configured. I just have two queries.

The onboard bluetooth only works if i've booted windows and used the toshiba bluetooth software before rebooting into linux. Any suggestions would be much appreciated.

Second, and more importantly, i realise that there is no support for Hybrid SLi, but i was wondering if it was possible to force my system to use the more powerful card instead of the weak one?

Thanks.

Hey!

I have the exactly same laptop as you. Ive been messing around with the the gfx cards trying to log in using another card.
The problem is that default is using the 9400M card to boot the system up on.

The system contains:
1x9400M
2x9800M GTS for hydrid SLI.

Running terminal with command: lspci

02:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9800M GTS] (rev a1)
03:00.0 3D controller: nVidia Corporation G94 [GeForce 9800M GTS] (rev a1)
04:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M G] (rev b1)

Trying to write a different IDBus into xorg.conf than 04:00.0 makes an error. Here im lost to:(

Linux is detecting all cards, just not using em.

---

