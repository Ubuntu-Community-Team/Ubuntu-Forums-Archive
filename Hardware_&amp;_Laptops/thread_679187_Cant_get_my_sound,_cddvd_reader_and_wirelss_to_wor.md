---
title: "Cant get my sound, cd/dvd reader and wirelss to work!"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by utklasad on 2008-01-26
Ive just got my (FSC) Amilo Xa 2528
([www.fujitsu-siemens.com/Resources/175/1543626421.pdf](www.fujitsu-siemens.com/Resources/175/1543626421.pdf)).

I made a thread yesterday, didnt got my Unbuntu to works, alot of errors during the installation, I also read that this computer is hard to get working with all kind of Linux dists, But I made a private boot CD at installinux.com and got it to work, except those things:

- I cant open my DVD/CD - Reader, the computer dont find it.

- I cant get the speakers on my laptop to work, either my headset or 5.1 speakers / line in.

- I cant get the wireless to work, only with cable.

I wrote them in rang, the DVD/CD problem has priority one! :D
Anyone out there who can help me? Thanks.

---

### Post by utklasad on 2008-01-27
bump ~ comeon, someone? :d

---

### Post by Vitz on 2008-01-30
I am having the exact same problems and I'm frantically looking for some solutions. Anyone?

---

### Post by Yellow Pasque on 2008-01-30
The first step is to get your wireless working. Go to System -> Administration -> Restricted Driver Manager and see if Ubuntu offers to install drivers for your wireless.

It would also be helpful if you could post the output of the following commands so that we have an idea of what hardware we're working with:
```
lspci
cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by utklasad on 2008-01-30
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
07:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

Wireless and Sound fixed, just the DVD left, I have trying to get this to work, but it seems impossible :s

---

### Post by Vitz on 2008-01-30
How did you fix the sound? Wireless isn't much of a problem for me seeing as I just use a USB receiver.

The DVD drive is still bugging me too...

---

### Post by utklasad on 2008-01-30
> **Vitz said:**
> How did you fix the sound? Wireless isn't much of a problem for me seeing as I just use a USB receiver.

The DVD drive is still bugging me too...
Vitz, check those links, helped me: 

[http://forum.ubuntuusers.de/go.php?wikipage=Soundkarten_installieren/HDA](http://forum.ubuntuusers.de/go.php?wikipage=Soundkarten_installieren/HDA)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Now I'm only haveing trouble with the DVD, doh, got to get it work! :d

---

