---
title: "sound problem for compaq f750us"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by richardd2137 on 2008-04-12
Hello, I got everything working in Ubuntu 7.10 on my Compaq Presario f750us laptop except I'm having a sound problem, I get sound but when I plug in my headphones the deck speakers don't turn off. I hear sound out of the headphones and deck speakers. Is there a way to fix this? Any suggestions on how to solve my problem?
Richardd

---

### Post by Crafty Kisses on 2008-04-12
> **richardd2137 said:**
> Hello, I got everything working in Ubuntu 7.10 on my Compaq Presario f750us laptop except I'm having a sound problem, I get sound but when I plug in my headphones the deck speakers don't turn off. I hear sound out of the headphones and deck speakers. Is there a way to fix this? Any suggestions on how to solve my problem?
Richardd

Post the following output:
```
lspci
```

---

### Post by fhantazm on 2008-04-20
I had the same problem, but Hardy solved it. Not sure if youre in a position to try  the beta, but it is surprisingly stable and I have run into very few bugs. Compiz-Fusion runs great with the 7000m.

---

### Post by schibros on 2008-05-10
> **richardd2137 said:**
> Hello, I got everything working in Ubuntu 7.10 on my Compaq Presario f750us laptop except I'm having a sound problem, I get sound but when I plug in my headphones the deck speakers don't turn off. I hear sound out of the headphones and deck speakers. Is there a way to fix this? Any suggestions on how to solve my problem?
Richardd


I also got everything working on Gutsy, but have the same problem as Richardd. When i plug in my headphones, it does not disable the Laptop speakers.

Major problem is I cant use the inbuilt Mic of the laptop. I have not tried external Mics thoug. Well i hope Hardy will solve this problem.

Pls Help

Compaq Presario F750us.

Thanks in advance.

---

### Post by schibros on 2008-05-10
> **Codename said:**
> Post the following output:
```
lspci
```


Here is my output from the lspci command.




00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0533 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

---

### Post by InlawBiker on 2008-05-15
Any update on the F750US laptop running Heron?  This looks like a screaming deal for a dual-core laptop, under $450(US) these days.  

My concerns are:

1. wireless apapter, probably not Intel?
2. Sound - what hardware is in it?

Video is a slam dunk, the Geforce 7000M should run Compiz without any issues.

Greg.

---

