---
title: "Unknown display - can't change resolution"
date: 2020-01-20
forum: Hardware
---

### Post by Torbjorn S.D. on 2020-01-20
Dear fellow Ubuntu users, 

I have a problem. Today I installed a new display (Samsung SyncMaster E2220). Its manual says the display should have 1920x1080 resolution but the highest resolution I'm able to set it to is 1024x768. Also, Ubuntu (Ubuntu 18.04.3) says my display is an "unknown display".

I have searched on google and looked at various forums but found no solution to my problem. Please help me.

Best regards,

---

### Post by CelticWarrior on 2020-01-20
What graphics card and connection are you using?

---

### Post by Torbjorn S.D. on 2020-01-20
> **CelticWarrior said:**
> What graphics card and connection are you using?

I don't think I have a graphics card. The connection I use is VGA, I think.

Best regards,

---

### Post by CelticWarrior on 2020-01-20
Integrated or discrete you certainly have a graphics card, otherwise you wouldn't have video :D. Please check by running ```
lspci
``` in terminal.

Very likely you'll find some Intel iGPU but it can be other and we need to know which one in order to try to solve the problem. Furthermore, do you have a DVI output? If you do and considering the monitor has a DVI input I strongly recommend you use that instead for better results.

---

### Post by Torbjorn S.D. on 2020-01-20
> **CelticWarrior said:**
> Integrated or discrete you certainly have a graphics card, otherwise you wouldn't have video :D. Please check by running ```
lspci
``` in terminal.

Very likely you'll find some Intel iGPU but it can be other and we need to know which one in order to try to solve the problem. Furthermore, do you have a DVI output? If you do and considering the monitor has a DVI input I strongly recommend you use that instead for better results.

I typed the lspci command. This is the output.

user@user-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H81 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042A USB 3.0 Host Controller

I don't know hot to interpret the command output.

When it comes to the VGA vs DVI, I thin my monitor has VGA and DVI-I connections, but my computer has VGA and dual-link DVI. I don't know how to proceed.

Best regards,

---

### Post by CelticWarrior on 2020-01-20
Here it is:

```
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th  Gen Core Processor Integrated Graphics Controller (rev 06)
```

(please always use code tags to post this kind of results. You can click Go Advanced and use "#" and paste inside).

Expected results, nothing to do with drivers, it's just that with the old VGA Ubuntu sometimes has issues recognizing the correct monitor and consequently present the proper resolution.

If you have DVI I strongly adivice to use it instead of VGA. The digital connection usually has no such problems.

---

### Post by Torbjorn S.D. on 2020-01-20
> **CelticWarrior said:**
> Here it is:

```
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th  Gen Core Processor Integrated Graphics Controller (rev 06)
```

(please always use code tags to post this kind of results. You can click Go Advanced and use "#" and paste inside).

Expected results, nothing to do with drivers, it's just that with the old VGA Ubuntu sometimes has issues recognizing the correct monitor and consequently present the proper resolution.

If you have DVI I strongly adivice to use it instead of VGA. The digital connection usually has no such problems.

I changed from VGA to DVI, as you advised me. Everything works perfectly now. Thank you very much for all your help!

Best regards,

---

### Post by CelticWarrior on 2020-01-20
You're welcome :)

Please use the thread tool to mark it as solved. It may be helpful for other users in the future.

---

