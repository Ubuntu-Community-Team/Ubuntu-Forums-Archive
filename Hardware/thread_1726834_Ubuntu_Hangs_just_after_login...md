---
title: "Ubuntu Hangs just after login.."
date: 2011-04-11
forum: Hardware
---

### Post by Faris1985 on 2011-04-11
I have installed Ubuntu on my HP Pavillion DV6 1444ee recently using install side by side option..The Ubuntu hangs just after login at the splash screen and i cant do anything..Everything literally freezes..The mouse and everything..No icons load and nothing works..I have tried Ctrl+Alt+F1 but it does not work too.. I love Ubuntu dont know why but due to this problem I cant explore it any further..**PLS HELP!!**

---

### Post by KegHead on 2011-04-11
Hi!

How much ram do you have?

Results of free in terminal?

KwgHead

---

### Post by Faris1985 on 2011-04-12
Hello! I have got 2GB RAM.. Actually i am a noob to ubuntu so do not know what do you mean by "Results of free in terminal?" Thanks..

---

### Post by KegHead on 2011-04-12
Hi!

goto terminal and type in "free".

And post.

Thanks!

KegHead

---

### Post by Faris1985 on 2011-04-12
This appeared

             total       used       free     shared    buffers     cached
Mem:       1987784     716860    1270924          0      41844     303008
-/+ buffers/cache:     372008    1615776
Swap:      1694712          0    1694712

---

### Post by Hippytaff on 2011-04-12
What graphics card do you have? you can find out by opening a terminal and doing 
 
```
lspci
```

---

### Post by Faris1985 on 2011-04-12
> **Hippytaff said:**
> What graphics card do you have? you can find out by opening a terminal and doing 
 
```
lspci
```
THIS APPEARS

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Intel Corporation WiFi Link 1000 Series
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

