---
title: "IMPORTANT Kworld Plus TV - Will pay for howto"
date: 2007-12-25
forum: Hardware &amp; Laptops
---

### Post by gnomey on 2007-12-25
Hi,

I'm new to the forums.

Heres exactly what I want

I need to get my TV tuner installed and working perfectly.

its the Kworld Plus TV Analog PCI Card.

I really need a step by step guide on how t d this.
I'm running Ubuntu 7.10 64-bit.
I've tried loads of guides and none have worked so well.

I will offer 5euro via paypal if needed to get a howto.
I REALLY need this working fast,Very important.

anyways thanks for reading!

---

### Post by gnomey on 2007-12-25
Sorry if I am annoying, But can anyone help me?

I really really want this to work I am offering money to get it working I really need help!

---

### Post by gnomey on 2007-12-26
bump.

can anyone help at all?

---

### Post by gnomey on 2008-01-17
bump

---

### Post by patrickfromspain on 2008-01-17
Could you attach the outputs of lspci and dmesg?

---

### Post by gnomey on 2008-01-17
im a newb.

can you explain better?

---

### Post by gnomey on 2008-01-17
wait think i got it
lspci:
marcus@marcus-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)


dmesg is sooo long tell me if you need it

---

### Post by patrickfromspain on 2008-01-17
dmesg > dmesg.log

that will save everything from dmesg into the file dmesg.log. Just attach dmesg.log.

---

### Post by gnomey on 2008-01-17
its over the boards max size.

I just uploaded it to one of my sites

[http://ieboards.com/dmesg.txt](http://ieboards.com/dmesg.txt)

---

### Post by patrickfromspain on 2008-01-17
I seems like the card has been picked up correctly. Try to install tvtime and/or kdetv and there search for channels

---

### Post by gnomey on 2008-01-17
tvtime doesnt work ill try kdetv.

Yeah ive fiddled with this card and havent got it working yet,its detected in tvtime but i just get all black channels

---

### Post by gnomey on 2008-01-17
nope kdetv isnt working :(

---

### Post by patrickfromspain on 2008-01-17
then I'm afraid that the card still lacks support, sorry.

---

### Post by gnomey on 2008-01-17
> **patrickfromspain said:**
> then I'm afraid that the card still lacks support, sorry.

so nothing I can do?

EDIT:

this is the same card as mine except its the light version
[http://ubuntuforums.org/showthread.php?t=540862](http://ubuntuforums.org/showthread.php?t=540862)

I had followed that guide but my system is loading  saa7130  saa7133  saa7134 not just saa7134

---

### Post by gnomey on 2008-01-18
bump

---

### Post by FabioLimaCE on 2008-05-01
I found the solution an posted [HERE]("http://fabiolimace.blogspot.com/2008/03/placa-de-tv-kworld-no-linux.html"). Use Google Translate. It's in portuguese.

Use XawTV. It worked do me.

Good Luck! :guitar:

---

### Post by FabioLimaCE on 2008-05-01
By the way. We are in a forum for free. Linux is freedom. We are meant do help each other. Our payment is: knoledge and friendship. :guitar:

---

