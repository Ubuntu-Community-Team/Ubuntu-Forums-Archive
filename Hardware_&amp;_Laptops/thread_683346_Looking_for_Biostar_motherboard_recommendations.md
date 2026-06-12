---
title: "Looking for Biostar motherboard recommendations"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by sofasurfer on 2008-01-30
I once bought a name brand MB that I was unfamiliar with and could not get it working, and so now I am hesitant to buy a motherboard on ebay without having experience with that brand.

I am considering a Biostar NF61S Micro AM2 SE  for use with a AMD 64 4200+  dual core processor. I will be running 32 bit Ubuntu.

Does anyone forsee any problems? Thanks...

---

### Post by mrsticks on 2008-02-02
I am considering the same motherboard for a new PC.  I was hoping it would just work, but I am reading some things I dont like about the network card and sound card working properly.  

The network card is a PHY, which is apparently "driver-less".  Ive seen some chatter on this board about not getting the NIC to work at all.  From what I read here ( [http://www.linux-tested.com/results/asus_k8u-x.html]("http://www.linux-tested.com/results/asus_k8u-x.html") ) it depends on your motherboard's compatibility with linux not necessarily the NIC's.

I have also seen some concern over the on board sound.  The Realtek ALC861VD apparently works well with OSS not ALSA.  I dont know if it really matters in the end, as long as sound comes out of the speakers, I dont particularly care how it works.

This was the motherboard I was going to buy, but I might keep looking for something that "just works".  Though if I do end up buying this, I will report back any results in this thread.

-peter

---

### Post by sofasurfer on 2008-02-02
I just ordered Amd Athlon 64 X2 4200+ along with a BioStar NF61S Micro ATX. It was a package deal on Ebay. I got both for the cost of the processor alone. So if the board doesn't work I am really not out anything.

If you are looking for another board, I currently have a MSI K9N4 SLI which works great and I am very happy with.  It cost me $119 at a local shop. I know its quite a bit cheaper on line. 

Thanks for responding.

---

### Post by mrsticks on 2008-02-03
Let me know how the Biostar works out.  The other board seems like a fine board, but I am looking specifically at the MicroATX boards so I can decrease my PC's footprint in general.

Just curious, why do you plan on running 32 bit Linux on a 64 bit chip?

-peter

---

### Post by mrsticks on 2008-04-15
I bought the Biostar NF61S Micro AM2 SE.  Everything worked flawlessly, right out the box.  Compiz, ethernet, sound, video, everything was detected, no problems.  I installed from the 7.10 64bit LiveCD  For future reference, here is my lspci

```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
```

---

