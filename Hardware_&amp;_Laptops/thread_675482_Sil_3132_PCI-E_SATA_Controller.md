---
title: "Sil 3132 PCI-E SATA Controller"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by scoleman43 on 2008-01-22
I recently installed the latest version of Mythubuntu. I added a Sil 3132 PCI-E SATA Controller ([http://www.siliconimage.com/products/product.aspx?id=32](http://www.siliconimage.com/products/product.aspx?id=32)) after the initial install and the OS won't reconignize it or the attached drives. Is this controller supported? I am new to ubuntu so any help is appreciated. 

Thanks,

SC

---

### Post by Yellow Pasque on 2008-01-22
The drivers on their site look like they're only made to work with Red Hat, Fedora, and SuSe. I suppose you could try building one of those drivers.

Does lspci find the device?
```
sudo update-pciids
sudo lspci
```

---

### Post by scoleman43 on 2008-01-22
Thanks for your help. lspci does not see the device. See the output below. I can see the controller and attached drive load during the BIOS boot. I never built a driver before, it's probable beyond my Linux experience.       

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Contro
ller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra                                          nsport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address                                           Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Con                                          troller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscella                                          neous Control
00:19.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra                                          nsport Technology Configuration
00:19.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address                                           Map
00:19.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Con                                          troller
00:19.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscella                                          neous Control
05:04.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416)                                           MPEG-2 Encoder (rev 01)
05:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Cont                                          roller (PHY/Link)
0a:00.0 VGA compatible controller: nVidia Corporation NV37GL [Quadro PCI-E Serie                                          s] (rev a2)

---

### Post by electromage on 2008-04-28
Any updates? I'm thinking of purchasing one. Can anybody tell me if Hardy supports this chipset?

---

### Post by tuckie on 2008-06-23
I've been using this chipset in a raid card for well over a year with ubuntu.  Just make sure to update the firmware on the card before using it, I've heard that some early versions can have problems.  The only odd thing about it is that the built in utility (accessed at boot) cannot see the drives I have attached, even though ubuntu sees them fine.  Because of this, it sits at the splashscreen for the card a bit longer than I would like.

---

### Post by breuerp on 2008-07-12
What utility are you using to update the BIOS?  Silicon Images has a Windows and a DOS utility.  The Windows utility doesn't seem to work and the DOS utility wants to know what BIOS chip is installed (I have no idea).  The card I'm using is a Masscool XWT-PCIE10.  Any ideas/suggestions?

---

