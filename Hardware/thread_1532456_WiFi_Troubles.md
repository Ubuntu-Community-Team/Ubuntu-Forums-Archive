---
title: "WiFi Troubles"
date: 2010-07-16
forum: Hardware
---

### Post by Marvin666 on 2010-07-16
My system is set up as described in my signature. My internal card is an Atheros AR9285. The external card is a WEC600N. I can't get my laptop to recognize the external card if I didn't boot with it in. Does anybody know how to force it to detect the external card without rebooting? Also, is there a way to disable the internal card, but still be able to use the external one? The internal card has such no signal quality it's not worth fooling with.

---

### Post by iponeverything on 2010-07-16
If you blacklist the module for internal card it will be disabled.

As for the internal card what do see in dmesg when it is plugged in?

---

### Post by iponeverything on 2010-07-17
> **milliirthomas said:**
> Google says it inadvertently sucked up fragments of e-mails, search requests and other online data over public Wi-Fi networks in more than 30 countries while photographing neighborhoods for its &#8220;Street View&#8221; mapping feature. Google said it was all a mistake, and the company is profoundly sorry for the error.

spam to raise the google rank of the link the sig.

---

### Post by Marvin666 on 2010-07-17
It's not worth it, seeing as how on my next shutdown I'm reinstalling Jaunty, and using karmic only when I need wifi. My dmesg is 1550 lines, and I'd have to sift for the relevant one twice.

---

### Post by ghulamyaseen on 2010-07-17
what is the output of lspci command?

> **Marvin666 said:**
> My system is set up as described in my signature. My internal card is an Atheros AR9285. The external card is a WEC600N. I can't get my laptop to recognize the external card if I didn't boot with it in. Does anybody know how to force it to detect the external card without rebooting? Also, is there a way to disable the internal card, but still be able to use the external one? The internal card has such no signal quality it's not worth fooling with.

---

### Post by Marvin666 on 2010-07-17
Same with or without external card. It;s express card 34 if that helps any.
```
marvin@Local-Machine:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9200M G] (rev b1)
06:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

---

