---
title: "Hosed my video driver on Acer Aspire 5100"
date: 2009-05-01
forum: Hardware
---

### Post by klaasvanschelven on 2009-05-01
Hi,

Ubuntu 9.04 was working quite well on my Acer Aspire 5100. Videodriver worked out of the box, except for an issue described here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/370441](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/370441)

However, in an attempt to get flash sound in Firefox to work I tried this tip: [http://ubuntuforums.org/showpost.php?p=6077691&postcount=2](http://ubuntuforums.org/showpost.php?p=6077691&postcount=2) (installing ATI sound driver using envyng-gtk) which hosed my video altogehter. Uninstalling left me with a generic videodriver (I assume) since the resolution is wrong and none of the Desktop effects work anymore. Any ideas how I can get my videodriver back? I've included results of sudo lspci -vvv below.

Any help is appreciated, I'd be glad to provide other necessary details.

regards,
Klaas

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
        Subsystem: Acer Incorporated [ALI] Device 009f              
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
        Latency: 64                                                                                           
        Kernel modules: ati-agp                                                                               

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64                                                                                           
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64                                         
        I/O behind bridge: 00009000-00009fff                                                                  
        Memory behind bridge: b0100000-b01fffff                                                               
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff                                  
        Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-      
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-                                         
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-                                           
        Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+                                         
        Capabilities: [b0] Subsystem: Acer Incorporated [ALI] Device 009f                                     
        Kernel modules: shpchp                                                                                

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 0, Cache Line Size: 32 bytes                                                                
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0                                         
        I/O behind bridge: 0000f000-00000fff                                                                 
        Memory behind bridge: 8c000000-8c0fffff                                                              
        Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff                                 
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-       
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-                                        
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-                                          
        Capabilities: [50] Power Management version 3                                                        
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)                   
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-                                                  
        Capabilities: [58] Express (v1) Root Port (Slot+), MSI 00                                            
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us                        
                        ExtTag+ RBE- FLReset-                                                                
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-                           
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+                                         
                        MaxPayload 128 bytes, MaxReadReq 128 bytes                                           
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-                          
                LnkCap: Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <64ns, L1 <1us             
                        ClockPM- Suprise- LLActRep- BwNot-                                                   
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+                              
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-                                       
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-           
                SltCap: AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surpise+                            
                        Slot #  0, PowerLimit 25.000000; Interlock- NoCompl-                                 
                SltCtl: Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-                      
                        Control: AttnInd Off, PwrInd Off, Power- Interlock-                                  
                SltSta: Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-                         
                        Changed: MRL- PresDet+ LinkState-                                                    
                RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-                      
                RootCap: CRSVisible-                                                                         
                RootSta: PME ReqID 0000, PMEStatus- PMEPending-                                              
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-                      
                Address: 00000000  Data: 0000                                                                
        Capabilities: [b0] Subsystem: ATI Technologies Inc Device 5950                                       
        Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+                                        
        Kernel driver in use: pcieport-driver                                                                
        Kernel modules: shpchp                                                                               

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 0, Cache Line Size: 32 bytes                                                                
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0                                         
        I/O behind bridge: 0000f000-00000fff                                                                 
        Memory behind bridge: fff00000-000fffff                                                              
        Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff                                 
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-       
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-                                        
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-                                          
        Capabilities: [50] Power Management version 3                                                        
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)                   
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-                                                  
        Capabilities: [58] Express (v1) Root Port (Slot+), MSI 00                                            
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us                        
                        ExtTag+ RBE- FLReset-                                                                
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-                           
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+                                         
                        MaxPayload 128 bytes, MaxReadReq 128 bytes                                           
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-                          
                LnkCap: Port #247, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <64ns, L1 <1us           
                        ClockPM- Suprise- LLActRep- BwNot-                                                   
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-                              
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-                                       
                LnkSta: Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-          
                SltCap: AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surpise+                            
                        Slot #  0, PowerLimit 0.000000; Interlock- NoCompl-                                  
                SltCtl: Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-                      
                        Control: AttnInd Off, PwrInd Off, Power- Interlock-                                  
                SltSta: Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-                         
                        Changed: MRL- PresDet- LinkState-                                                    
                RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-                      
                RootCap: CRSVisible-                                                                         
                RootSta: PME ReqID 0000, PMEStatus- PMEPending-                                              
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-                      
                Address: 00000000  Data: 0000                                                                
        Capabilities: [b0] Subsystem: ATI Technologies Inc Device 5950                                       
        Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+                                        
        Kernel driver in use: pcieport-driver                                                                
        Kernel modules: shpchp                                                                               

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])                                                                                                                            
        Subsystem: ATI Technologies Inc IXP SB400 Serial ATA Controller                                                      
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-                
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-               
        Latency: 64, Cache Line Size: 32 bytes                                                                               
        Interrupt: pin A routed to IRQ 22                                                                                    
        Region 0: I/O ports at 8440 [size=8]                                                                                 
        Region 1: I/O ports at 8434 [size=4]                                                                                 
        Region 2: I/O ports at 8438 [size=8]                                                                                 
        Region 3: I/O ports at 8430 [size=4]                                                                                 
        Region 4: I/O ports at 8400 [size=16]                                                                                
        Region 5: Memory at b0004000 (32-bit, non-prefetchable) [size=512]                                                   
        [virtual] Expansion ROM at 8c100000 [disabled] [size=512K]                                                           
        Capabilities: [60] Power Management version 2                                                                        
                Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)                                   
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-                                                                  
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-                                      
                Address: 00000000  Data: 0000                                                                                
        Kernel driver in use: sata_sil                                                                                       

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
        Subsystem: Acer Incorporated [ALI] Device 009f                                          
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64, Cache Line Size: 64 bytes                                                                
        Interrupt: pin A routed to IRQ 19                                                                     
        Region 0: Memory at b0005000 (32-bit, non-prefetchable) [size=4K]                                     
        Kernel driver in use: ohci_hcd                                                                        

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
        Subsystem: Acer Incorporated [ALI] Device 009f                                          
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64, Cache Line Size: 64 bytes                                                                
        Interrupt: pin A routed to IRQ 19                                                                     
        Region 0: Memory at b0006000 (32-bit, non-prefetchable) [size=4K]                                     
        Kernel driver in use: ohci_hcd                                                                        

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20)
        Subsystem: Acer Incorporated [ALI] Device 009f                                           
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64, Cache Line Size: 64 bytes                                                                
        Interrupt: pin A routed to IRQ 19                                                                     
        Region 0: Memory at b0007000 (32-bit, non-prefetchable) [size=4K]                                     
        Capabilities: [dc] Power Management version 2                                                         
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)                    
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-                                                   
                Bridge: PM- B3+                                                                               
        Kernel driver in use: ehci_hcd                                                                        

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
        Subsystem: Acer Incorporated [ALI] Device 009f                 
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Region 0: I/O ports at 8410 [size=16]                                                                 
        Region 1: Memory at 8c180000 (32-bit, non-prefetchable) [size=1K]                                     
        Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+                                         
        Kernel driver in use: piix4_smbus                                                                     
        Kernel modules: i2c-piix4                                                                             

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 82 [Master PriP])
        Subsystem: Acer Incorporated [ALI] Device 009f                                                  
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64                                                                                           
        Interrupt: pin A routed to IRQ 16                                                                     
        Region 0: I/O ports at 01f0 [size=8]                                                                  
        Region 1: I/O ports at 03f4 [size=1]                                                                  
        Region 2: I/O ports at 0170 [size=8]                                                                  
        Region 3: I/O ports at 0374 [size=1]                                                                  
        Region 4: I/O ports at 8420 [size=16]                                                                 
        Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-                       
                Address: 00000000  Data: 0000                                                                 
        Kernel driver in use: pata_atiixp                                                                     

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
        Subsystem: Acer Incorporated [ALI] Device 009f                                        
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 64, Cache Line Size: 32 bytes                                                               
        Interrupt: pin ? routed to IRQ 16                                                                    
        Region 0: Memory at b0000000 (64-bit, non-prefetchable) [size=16K]                                   
        Capabilities: [50] Power Management version 2                                                        
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)                  
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-                                                  
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-                      
                Address: 0000000000000000  Data: 0000                                                        
        Kernel driver in use: HDA Intel                                                                      
        Kernel modules: snd-hda-intel                                                                        

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Acer Incorporated [ALI] Device 009f                    
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0                                                                                            

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64                                                                                           
        Bus: primary=00, secondary=06, subordinate=08, sec-latency=64                                         
        I/O behind bridge: 0000a000-0000afff                                                                  
        Memory behind bridge: b0300000-b03fffff                                                               
        Prefetchable memory behind bridge: 88000000-8bffffff                                                  
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-      
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-                                         
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-                                           

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-   
        Capabilities: [80] HyperTransport: Host or Secondary Interface                                         
                !!! Possibly incomplete decoding                                                               
                Command: WarmRst+ DblEnd-                                                                      
                Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=8                               
                Link Config: MLWI=16bit MLWO=16bit LWI=16bit LWO=16bit                                         
                Revision ID: 1.02                                                                              

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Capabilities: [f0] Secure device <?>                                                                 
        Kernel driver in use: k8temp                                                                         
        Kernel modules: k8temp                                                                               

01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
        Subsystem: Acer Incorporated [ALI] Device 009f                            
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 66 (2000ns min), Cache Line Size: 32 bytes                                                   
        Interrupt: pin A routed to IRQ 11                                                                     
        Region 0: Memory at c0000000 (32-bit, prefetchable) [size=256M]                                       
        Region 1: I/O ports at 9000 [size=256]                                                                
        Region 2: Memory at b0100000 (32-bit, non-prefetchable) [size=64K]                                    
        [virtual] Expansion ROM at b0120000 [disabled] [size=128K]                                            
        Capabilities: [50] Power Management version 2                                                         
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)                    
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-                                                   
        Kernel modules: radeonfb                                                                              

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: AMBIT Microsystem Corp. Device 0428                                                         
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-  
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-   
        Latency: 0, Cache Line Size: 32 bytes                                                                  
        Interrupt: pin A routed to IRQ 16                                                                      
        Region 0: Memory at 8c000000 (64-bit, non-prefetchable) [size=64K]                                     
        Capabilities: [40] Power Management version 2                                                          
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)                   
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-                                                    
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-                        
                Address: 00000000  Data: 0000                                                                  
        Capabilities: [60] Express (v1) Legacy Endpoint, MSI 00                                                
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us                        
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-                                        
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-                             
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-                                           
                        MaxPayload 128 bytes, MaxReadReq 512 bytes                                             
                DevSta: CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-                            
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us             
                        ClockPM- Suprise- LLActRep- BwNot-                                                     
                LnkCtl: ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+                               
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-                                         
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-             
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1                                                      
                Vector table: BAR=0 offset=00000000                                                            
                PBA: BAR=0 offset=00000000                                                                     
        Capabilities: [100] Advanced Error Reporting <?>                                                       
        Capabilities: [140] Virtual Channel <?>                                                                
        Kernel driver in use: ath5k_pci                                                                        
        Kernel modules: ath_pci, ath5k                                                                         

06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Acer Incorporated [ALI] Device 009f                                     
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64 (8000ns min, 16000ns max)                                                                 
        Interrupt: pin A routed to IRQ 21                                                                     
        Region 0: I/O ports at a000 [size=256]                                                                
        Region 1: Memory at b0300000 (32-bit, non-prefetchable) [size=256]                                    
        Capabilities: [50] Power Management version 2                                                         
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)                  
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-                                                   
        Kernel driver in use: 8139too                                                                         
        Kernel modules: 8139too, 8139cp                                                                       

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
        Subsystem: Acer Incorporated [ALI] Device 009f                         
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 168, Cache Line Size: 128 bytes                                                              
        Interrupt: pin A routed to IRQ 20                                                                     
        Region 0: Memory at b0301000 (32-bit, non-prefetchable) [size=4K]                                     
        Bus: primary=06, secondary=07, subordinate=07, sec-latency=176                                        
        Memory window 0: 88000000-8bfff000 (prefetchable)                                                     
        Memory window 1: 90000000-93fff000                                                                    
        I/O window 0: 0000a400-0000a4ff                                                                       
        I/O window 1: 0000a800-0000a8ff                                                                       
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+                                 
        16-bit legacy interface ports at 0001                                                                 
        Kernel driver in use: yenta_cardbus                                                                   
        Kernel modules: yenta_socket                                                                          

06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
        Subsystem: Acer Incorporated [ALI] Device 009f                                       
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64 (250ns min, 1000ns max), Cache Line Size: 32 bytes                                        
        Interrupt: pin B routed to IRQ 10                                                                     
        Region 0: Memory at b0300400 (32-bit, non-prefetchable) [size=128]                                    
        Capabilities: [80] Power Management version 2                                                         
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)                    
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-                                                   

06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: Acer Incorporated [ALI] Device 009f                                                            
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64 (8000ns min, 18000ns max), Cache Line Size: 32 bytes
        Interrupt: pin B routed to IRQ 23
        Region 0: Memory at b0300800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci

06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
        Subsystem: Acer Incorporated [ALI] Device 009f
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64 (250ns min, 1000ns max), Cache Line Size: 32 bytes
        Interrupt: pin B routed to IRQ 10
        Region 0: Memory at b0300c00 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
        Subsystem: Acer Incorporated [ALI] Device 009f
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin B routed to IRQ 23
        Region 0: Memory at b0300100 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci

```

---

### Post by klaasvanschelven on 2009-05-01
BTW, any ideas on the original problem (sound in flash) would be aprreciated as well.

---

### Post by klaasvanschelven on 2009-05-01
for those who come on this path in the future...

changing

```

Driver  "vesa"
```

into 

```
Driver  "ati"
```

in xorg.conf fixed it.

---

