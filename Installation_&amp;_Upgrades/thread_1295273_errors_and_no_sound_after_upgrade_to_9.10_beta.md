---
title: "errors and no sound after upgrade to 9.10 beta"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by earthmumma on 2009-10-19
I've just upgraded to Kubuntu 9.10 64bit

When I start up I get 2 of these popup messages:

> No command arguments supplied! Usage: kdesudo [-u <runas>] <command>
 KdeSudo will now exit...
and a one 



> KDE detected that one or more internal sound devices were removedDo you want KDE to permanently forget about these devices?
This is the list of devices KDE thinks can be removed:

[LIST]
[*]Capture: NVidia CK804 with ALC850
[*]Output: NVidia CK804 with ALC850
[/LIST]


and then a :

> Kernel problem

Your System encountered a serious kernel problem




My sound doesn't work, aplay -l gives :


> **** List of PLAYBACK Hardware Devices ****
aplay: device_list:244: snd_ctl_pcm_next_device

and lspci -v doesn't show any sound device see below:


> 00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. Device 815a                          
        Flags: bus master, 66MHz, fast devsel, latency 0                      
        Capabilities: <access denied>                                         

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
        Subsystem: ASUSTeK Computer Inc. Device 815a            
        Flags: bus master, 66MHz, fast devsel, latency 0        

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: ASUSTeK Computer Inc. Device 815a  
        Flags: 66MHz, fast devsel, IRQ 11             
        I/O ports at e400 [size=32]                   
        I/O ports at 4c00 [size=64]                   
        I/O ports at 4c40 [size=64]                   
        Capabilities: <access denied>                 
        Kernel driver in use: nForce2_smbus           
        Kernel modules: i2c-nforce2                   

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10)
        Subsystem: ASUSTeK Computer Inc. Device 815a                                 
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20                     
        Memory at c5004000 (32-bit, non-prefetchable) [size=4K]                      
        Capabilities: <access denied>                                                
        Kernel driver in use: ohci_hcd                                               

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20)
        Subsystem: ASUSTeK Computer Inc. Device 815a                                 
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21                     
        Memory at feb00000 (32-bit, non-prefetchable) [size=256]                     
        Capabilities: <access denied>                                                
        Kernel driver in use: ehci_hcd                                               

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Device 815a                                        
        Flags: bus master, 66MHz, fast devsel, latency 0                                    
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]                                                                                                                                                                         
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]                                                                                                                                                                         
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]                                                                                                                                                                         
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]                                                                                                                                                                         
        I/O ports at f000 [size=16]                                                                                                                                                                                                                         
        Capabilities: <access denied>                                                                                                                                                                                                                       
        Kernel driver in use: pata_amd                                                                                                                                                                                                                      
                                                                                                                                                                                                                                                            
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])                                                                                                                                              
        Subsystem: ASUSTeK Computer Inc. Device 815a                                                                                                                                                                                                        
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23                                                                                                                                                                                            
        I/O ports at 09f0 [size=8]                                                                                                                                                                                                                          
        I/O ports at 0bf0 [size=4]                                                                                                                                                                                                                          
        I/O ports at 0970 [size=8]                                                                                                                                                                                                                          
        I/O ports at 0b70 [size=4]                                                                                                                                                                                                                          
        I/O ports at d800 [size=16]                                                                                                                                                                                                                         
        Memory at c5002000 (32-bit, non-prefetchable) [size=4K]                                                                                                                                                                                             
        Capabilities: <access denied>                                                                                                                                                                                                                       
        Kernel driver in use: sata_nv                                                                                                                                                                                                                       
                                                                                                                                                                                                                                                            
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])                                                                                                                                              
        Subsystem: ASUSTeK Computer Inc. Device 815a                                                                                                                                                                                                        
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22                                                                                                                                                                                            
        I/O ports at 09e0 [size=8]                                                                                                                                                                                                                          
        I/O ports at 0be0 [size=4]                                                                                                                                                                                                                          
        I/O ports at 0960 [size=8]                                                                                                                                                                                                                          
        I/O ports at 0b60 [size=4]                                                                                                                                                                                                                          
        I/O ports at c400 [size=16]                                                                                                                                                                                                                         
        Memory at c5001000 (32-bit, non-prefetchable) [size=4K]                                                                                                                                                                                             
        Capabilities: <access denied>                                                                                                                                                                                                                       
        Kernel driver in use: sata_nv                                                                                                                                                                                                                       

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01)
        Flags: bus master, 66MHz, fast devsel, latency 0                     
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=128       
        I/O behind bridge: 0000a000-0000afff                                 
        Memory behind bridge: c3000000-c4ffffff                              
        Prefetchable memory behind bridge: 80000000-800fffff                 

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. Device 8141                 
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23     
        Memory at c5000000 (32-bit, non-prefetchable) [size=4K]      
        I/O ports at b000 [size=8]                                   
        Capabilities: <access denied>                                
        Kernel driver in use: forcedeth                              
        Kernel modules: forcedeth                                    

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
        Flags: bus master, fast devsel, latency 0                
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>                               
        Kernel driver in use: pcieport-driver                       
        Kernel modules: shpchp                                      

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: c0000000-c2ffffff
        Prefetchable memory behind bridge: 00000000a0000000-00000000bfffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel
        Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Kernel driver in use: k8temp
        Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
        Subsystem: XFX Pine Group Inc. Device 219c
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at c0000000 (32-bit, non-prefetchable) [size=16M]
        Memory at a0000000 (64-bit, prefetchable) [size=512M]
        Memory at c1000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at c2000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nvidiafb

05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
        Subsystem: ASUSTeK Computer Inc. Device 808b
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at c4008000 (32-bit, non-prefetchable) [size=2K]
        Memory at c4004000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: ohci1394
        Kernel modules: firewire-ohci, ohci1394

05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
        Subsystem: ASUSTeK Computer Inc. Device 811a
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
        Memory at c4000000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at a000 [size=256]
        [virtual] Expansion ROM at 80000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: skge
        Kernel modules: skge


Any suggestions, except "it's a beta - s**t happens"?


cheers

---

### Post by dabl on 2009-10-19
It's never good when lspci does not show an audio chip .... I would not hold my breath in expectation of a breakthrough on this one between now and the end of the month.  

However, here are a couple of bug reports that may shed light:

[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/136601](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/136601)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/371380](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/371380)

---

### Post by earthmumma on 2009-10-19
The joys of Beta versions - did a cheeky update and bingo! the sound is back as is the sound card in lspci -v result.:P

cheers

---

