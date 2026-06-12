---
title: "&quot;Incomplete&quot; xorg.conf ?"
date: 2010-01-02
forum: Hardware
---

### Post by pmooney78 on 2010-01-02
I just reinstalled Ubuntu 8.10 last night. Previously, I had a wide selection of display resolution options in the "Screen Resolution" applet, but don't see much anymore. Both the external monitor (a KDS Avitron) and the internal laptop monitor have maximum resolutions of 1024 x 768 or so.

"Hardware Drivers" doesn't show any available drivers related to video card/driver.

When I run sudo nvidia-xconfig in a terminal, I get this:

```

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

patrick@liniscient:~$ gksu nvidia-settings
patrick@liniscient:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

I have no idea how to add a driver line to the xorg.conf file (well ... I can edit text files if given directions about what to type, but wouldn't know what to enter or where to enter it).

Here's the output from running xrandr in a terminal:

```

Screen 0: minimum 320 x 200, current 1856 x 768, maximum 2384 x 776
VGA connected 832x624+1024+8 (normal left inverted right x axis y axis) 300mm x 230mm
   1360x768       59.8
   1024x768       85.0     85.0     75.1     75.0     70.1     60.0
   832x624        74.6*
   800x600        85.0     85.1     72.2     75.0     60.3     56.2
   640x480        85.0     85.0     75.0     72.8     75.0     59.9
   720x400        85.0     70.1
   640x400        85.1
   640x350        85.1
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1024x768       60.0*
   800x600        60.3
   640x480        59.9
TMDS-1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)

```

And here's the output of lspci -vv:

```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Dell Device 01d6                                                                                    
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-          
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-           
        Latency: 0                                                                                                     
        Capabilities: <access denied>                                                                                  
        Kernel driver in use: agpgart-intel                                                                            
        Kernel modules: intel-agp                                                                                      

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Dell Device 01d6                                                                                              
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-                    
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-                     
        Latency: 0                                                                                                               
        Interrupt: pin A routed to IRQ 11                                                                                        
        Region 0: Memory at eff00000 (32-bit, non-prefetchable) [size=512K]                                                      
        Region 1: I/O ports at eff8 [size=8]                                                                                     
        Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]                                                          
        Region 3: Memory at efec0000 (32-bit, non-prefetchable) [size=256K]                                                      
        Capabilities: <access denied>                                                                                            
        Kernel modules: intelfb                                                                                                  

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Dell Device 01d6                                                                                           
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-                 
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-                  
        Latency: 0                                                                                                            
        Region 0: Memory at eff80000 (32-bit, non-prefetchable) [size=512K]                                                   
        Capabilities: <access denied>                                                                                         

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Dell Device 01d6                                                                   
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 0, Cache Line Size: 64 bytes                                                                
        Interrupt: pin A routed to IRQ 21                                                                    
        Region 0: Memory at efebc000 (64-bit, non-prefetchable) [size=16K]                                   
        Capabilities: <access denied>                                                                        
        Kernel driver in use: HDA Intel                                                                      
        Kernel modules: snd-hda-intel                                                                        

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 0, Cache Line Size: 64 bytes                                                                
        Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0                                         
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-       
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-                                        
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-                                          
        Capabilities: <access denied>                                                                        
        Kernel driver in use: pcieport-driver                                                                
        Kernel modules: shpchp                                                                               

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 0, Cache Line Size: 64 bytes                                                                
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0                                         
        Memory behind bridge: efd00000-efdfffff                                                              
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-       
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-                                        
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-                                          
        Capabilities: <access denied>                                                                        
        Kernel driver in use: pcieport-driver                                                                
        Kernel modules: shpchp                                                                               

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 0, Cache Line Size: 64 bytes                                                                
        Bus: primary=00, secondary=09, subordinate=09, sec-latency=0                                         
        Memory behind bridge: efc00000-efcfffff                                                              
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-       
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-                                        
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-                                          
        Capabilities: <access denied>                                                                        
        Kernel driver in use: pcieport-driver                                                                
        Kernel modules: shpchp                                                                               

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
        Subsystem: Dell Device 01d6                                                           
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0                                                                                            
        Interrupt: pin A routed to IRQ 20                                                                     
        Region 4: I/O ports at bf80 [size=32]                                                                 
        Kernel driver in use: uhci_hcd                                                                        
        Kernel modules: uhci-hcd                                                                              

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
        Subsystem: Dell Device 01d6                                                           
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0                                                                                            
        Interrupt: pin B routed to IRQ 21                                                                     
        Region 4: I/O ports at bf60 [size=32]                                                                 
        Kernel driver in use: uhci_hcd                                                                        
        Kernel modules: uhci-hcd                                                                              

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
        Subsystem: Dell Device 01d6                                                           
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0                                                                                            
        Interrupt: pin C routed to IRQ 22                                                                     
        Region 4: I/O ports at bf40 [size=32]                                                                 
        Kernel driver in use: uhci_hcd                                                                        
        Kernel modules: uhci-hcd                                                                              

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
        Subsystem: Dell Device 01d6                                                           
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0                                                                                            
        Interrupt: pin D routed to IRQ 23                                                                     
        Region 4: I/O ports at bf20 [size=32]                                                                 
        Kernel driver in use: uhci_hcd                                                                        
        Kernel modules: uhci-hcd                                                                              

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
        Subsystem: Dell Device 01d6                                                                      
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0                                                                                            
        Interrupt: pin A routed to IRQ 20                                                                     
        Region 0: Memory at ffa80000 (32-bit, non-prefetchable) [size=1K]                                     
        Capabilities: <access denied>                                                                         
        Kernel driver in use: ehci_hcd                                                                        
        Kernel modules: ehci-hcd                                                                              

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 0                                                                                           
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=32                                        
        I/O behind bridge: 00002000-00002fff                                                                 
        Memory behind bridge: efb00000-efbfffff                                                              
        Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff                                 
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-     
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-                                        
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-                                          
        Capabilities: <access denied>                                                                        

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
        Subsystem: Dell Device 01d6                                                  
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0                                                                                            
        Capabilities: <access denied>                                                                         
        Kernel modules: iTCO_wdt, intel-rng                                                                   

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Device 01d6                                                                                  
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-        
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-       
        Latency: 0                                                                                                   
        Interrupt: pin A routed to IRQ 16                                                                            
        Region 0: I/O ports at 01f0 [size=8]                                                                         
        Region 1: I/O ports at 03f4 [size=1]                                                                         
        Region 2: I/O ports at 0170 [size=8]                                                                         
        Region 3: I/O ports at 0374 [size=1]                                                                         
        Region 4: I/O ports at bfa0 [size=16]                                                                        
        Kernel driver in use: ata_piix                                                                               
        Kernel modules: ata_piix                                                                                     

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Dell Device 01d6                                            
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin B routed to IRQ 5                                                                      
        Region 4: I/O ports at 10c0 [size=32]                                                                 
        Kernel modules: i2c-i801                                                                              

02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
        Subsystem: Dell Device 01d6                     
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 168                                                                                          
        Interrupt: pin A routed to IRQ 19                                                                     
        Region 0: Memory at efb00000 (32-bit, non-prefetchable) [size=4K]                                     
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176                                        
        Memory window 0: 50000000-53fff000 (prefetchable)                                                     
        Memory window 1: 54000000-57fff000                                                                    
        I/O window 0: 00002000-000020ff                                                                       
        I/O window 1: 00002400-000024ff                                                                       
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+                                 
        16-bit legacy interface ports at 0001                                                                 
        Kernel driver in use: yenta_cardbus                                                                   
        Kernel modules: yenta_socket                                                                          

02:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 09) (prog-if 10)
        Subsystem: Dell Device 01d6                                                         
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64 (500ns min, 1000ns max)                                                                   
        Interrupt: pin B routed to IRQ 17                                                                     
        Region 0: Memory at efbff800 (32-bit, non-prefetchable) [size=2K]                                     
        Capabilities: <access denied>                                                                         
        Kernel driver in use: ohci1394                                                                        
        Kernel modules: ohci1394                                                                              

02:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18) (prog-if 01)
        Subsystem: Dell Device 01d6                                                                    
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64                                                                                           
        Interrupt: pin C routed to IRQ 18                                                                     
        Region 0: Memory at efbff700 (32-bit, non-prefetchable) [size=256]                                    
        Capabilities: <access denied>
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci

09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
        Subsystem: Dell Device 01d6
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 220
        Region 0: Memory at efcf0000 (64-bit, non-prefetchable) [size=64K]
        Expansion ROM at <ignored> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: tg3
        Kernel modules: tg3

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
        Subsystem: Dell Device 0007
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at efdfc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: wl
        Kernel modules: ssb, wl

```

Any help much appreciated! Running Ubuntu 8.10 on a Dell Latitude D420 with 1GB RAM and a 1.2 GHz Core Duo processor.

---

### Post by pmooney78 on 2010-01-03
Bump.

---

### Post by pmooney78 on 2010-01-05
Bump

---

