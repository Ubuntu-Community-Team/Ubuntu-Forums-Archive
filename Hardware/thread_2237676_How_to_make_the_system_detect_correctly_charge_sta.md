---
title: "How to make the system detect correctly charge status?"
date: 2014-08-03
forum: Hardware
---

### Post by zaghini-andrea on 2014-08-03
Yesterday, after correctly performed the installation of (UEFI) ubuntu 14:04 LTS 64-bit in dual-boot with Windows 8.1 64-bit on my laptop asus A551LN I had a serious problem: the operating system did not realize when the power supply was connected or not, it was as if I were always on battery, without being charging although connected to the power source, moreover after using ubuntu, then, neither windows was able to charge the battery (but recognizing the connection status of the power supply).

It's a pity, because the rest works, belonging to the fn + Fx to increase / decrease the brightness. I state that I had also encountered this problem using it on live-cd ...

Does anyone know how to fix it or I'll have to wait for the next release of Ubuntu hoping that will solve this problem?

Meanwhile, I'm using windows which fortunately runs well ... at least for now ... and luckily after a few reboots and using only windows the battery now has been fully charged ...

Thanks in advance

---

### Post by Axxon95 on 2014-08-03
Throwing it out there, it may or may not be a contributing factor, but what BIOS version are you running? Could be something with UEFI.
I was working on 2 Toshiba laptops(both same model and have uefi support) a little while back, I had upgraded their BIOS to version 2.1(had all prior bug fixes, but enabled Win8 support), and it lost all communication to the battery, though it would still consume charge as well as charge. I downgraded to 2.0 and it went back to normal.
They both run straight Ubuntu though.
From what I've seen in general though, UEFI+Windows8+Linux isn't the best combo.

Another thing to try would be to reseat the battery, my Ubuntu laptop would get stuck at roughly 95-99% charge until I reseat the battery.

---

