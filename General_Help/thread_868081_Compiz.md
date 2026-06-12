---
title: "Compiz"
date: 2008-07-23
forum: General Help
---

### Post by adamant715 on 2008-07-23
It doesnt let me enable Compiz, it gives me an error saying "Desktop effects could not be enabled". Anyway I can enable the effects?

---

### Post by Soopa on 2008-07-23
Have you tried [this thread]("http://ubuntuforums.org/showthread.php?t=809695")?  The tips there are what worked for me.

---

### Post by adamant715 on 2008-07-23
Yea, I tried the Compiz-Check and it says Skip on al of them then says I have a vesa driver.

---

### Post by Kevbert on 2008-07-23
Please post the output from terminal of
```
lspci
```
Compiz works on most nVidia, ATI and Intel graphics cards.

---

### Post by chris09 on 2008-07-23
> **adamant715 said:**
> It doesnt let me enable Compiz, it gives me an error saying "Desktop effects could not be enabled". Anyway I can enable the effects?

Have you tried going into System-> Apperance-> and in the tabs select "Visual Effects" and select :Extra but you need an advance graphics card

---

### Post by adamant715 on 2008-07-23
> **Kevbert said:**
> Please post the output from terminal of
```
lspci
```
Compiz works on most nVidia, ATI and Intel graphics cards.

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)

---

### Post by Kevbert on 2008-07-24
Please take a look at this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=675870").

---

### Post by adamant715 on 2008-07-24
That doesn't help anything, their using a complete different version than me. And when I try to choose drivers it doesn't have any.

---

