---
title: "!No internet on new laptop!"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by taishi28012 on 2007-05-16
I have recently acquired a new laptop and neither wired or wireless works on it.

Here are the specs:
          Acer Aspire 5100-5033
          AMD Turion 64 X2 TL-50 1.6G
          ATI Radeon Xpress 1100 IGP

Here is a link to the exact product on newegg:  [http://www.newegg.com/Product/Product.asp?Item=N82E16834115348](http://www.newegg.com/Product/Product.asp?Item=N82E16834115348)

lspc: -vv returnes this on the controllers:

02:00.0 Ethernet controller: Atheros Communications, Inc.  Unknown device 001c (r
ev 01)
              Subsystem:  AMBIT Microsystem Corp.  Unknown device 0428
              Control: I/O- Mem- BusMaster-SpecCycle-MemWINV- BGASnoop- ParErr- Step
ping- SERR- FastB2B-
               Status: Cap+66MHz- UDF- FastB2b- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- >SERR- <PERR-
               Interrupt: pin A routed to IRQ 217
               Region 0: Memory At 52000000 (64-vit, non-prefetchable) [disabled] [size
=64K]
                Capabilities: [40] Power Management version 2
                             Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME (D0-,D1-,D3h
ot+,D3cold-)
                              Status: D0 PME-Enable- DSel+0 DScale=0 PME-
                 Capabilities: [50] Message Signalled Interrupts: 64bit- Queue=0/0 Enable
-
                                Address: 00000000  Data: 0000
                  Capabilities: [60] Express Legacy Endpoint IRQ 0
                                 Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                                 Device: Latency L0s <512ns, L1 <64us
                                 Device: AtnBtn- AtnInd- PwrInd-
                                 Device: Errors: Correctable- Non-Fatal- Fatal- unsupported-
                                 Device RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
                                 Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
                                 Link: Supported Speed 2.5Gb/s, Width x1 ASPM L0s L1, Port 0
                                 Link: Latency L0s <512ns, L1 <64us
                                 Link: ASPM Disabled RCB 128 Bytes CommClk- ExtSynch-
                                 Link: Speed 2.5Gb/s, Width x1
                   Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
                                  Vector table: BAR=0 offset=00000000
                                  PBA: VAR=0 offset=00000000
                    Capabilities: [100] Advanced Error Reporting
                   Capabilities: [140] Virtual Channel




And  


06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139
C+ (rev 10)
              Subsystem: Acer Incorporated [ALI] Unknown device 009f
              Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR-  FastB2B-
               Status: Cap+ 66MHz- UDF-  FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
                Latency: 64 98000ns min, 16000ns max)
                Interrupt: pin A routed to IRQ 50
                Region 0: I/O ports at a000 [size=256]
                Region1: Memory at b03000000 932-bit, non-prefetchable) [size=256]
                Capabilities; [50] Power Management version 2
                               Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME (D0-,D1+,D2+,D3h
oot+,D3cold+)
                               Status: D0 PME-Enable- DSel=0 DScale=0 PME-




Any and all help will be greatly appreciated.  Thanks in advance.

---

### Post by scrooge_74 on 2007-05-17
maybe you need the correct drivers for it, which version of Ubuntu are you using?

---

### Post by taishi28012 on 2007-05-17
Im using 6.10.

---

### Post by scrooge_74 on 2007-05-17
You should check if you need to replace the open drivers that came with Edgy for some proprietary drivers, maybe you will need to use ndiswrapper or madwifi.

I think madwifi is the workaround to Atheros chipsets and with ndiswrapper you use the windows drivers

---

### Post by taishi28012 on 2007-05-17
How do i get madwifi
everything ive found on it is not working 
please help

---

### Post by scrooge_74 on 2007-05-17
[http://www.madwifi.net/](http://www.madwifi.net/)

Check their site for more info.

Also in the repositories there is a madwifi package which since you dont have conection you will have to download de deb package and do a manual install

---

### Post by stchman on 2007-05-17
> **taishi28012 said:**
> I have recently acquired a new laptop and neither wired or wireless works on it.

Here are the specs:
          Acer Aspire 5100-5033
          AMD Turion 64 X2 TL-50 1.6G
          ATI Radeon Xpress 1100 IGP

Here is a link to the exact product on newegg:  [http://www.newegg.com/Product/Product.asp?Item=N82E16834115348](http://www.newegg.com/Product/Product.asp?Item=N82E16834115348)

lspc: -vv returnes this on the controllers:

02:00.0 Ethernet controller: Atheros Communications, Inc.  Unknown device 001c (r
ev 01)
              Subsystem:  AMBIT Microsystem Corp.  Unknown device 0428
              Control: I/O- Mem- BusMaster-SpecCycle-MemWINV- BGASnoop- ParErr- Step
ping- SERR- FastB2B-
               Status: Cap+66MHz- UDF- FastB2b- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- >SERR- <PERR-
               Interrupt: pin A routed to IRQ 217
               Region 0: Memory At 52000000 (64-vit, non-prefetchable) [disabled] [size
=64K]
                Capabilities: [40] Power Management version 2
                             Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME (D0-,D1-,D3h
ot+,D3cold-)
                              Status: D0 PME-Enable- DSel+0 DScale=0 PME-
                 Capabilities: [50] Message Signalled Interrupts: 64bit- Queue=0/0 Enable
-
                                Address: 00000000  Data: 0000
                  Capabilities: [60] Express Legacy Endpoint IRQ 0
                                 Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                                 Device: Latency L0s <512ns, L1 <64us
                                 Device: AtnBtn- AtnInd- PwrInd-
                                 Device: Errors: Correctable- Non-Fatal- Fatal- unsupported-
                                 Device RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
                                 Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
                                 Link: Supported Speed 2.5Gb/s, Width x1 ASPM L0s L1, Port 0
                                 Link: Latency L0s <512ns, L1 <64us
                                 Link: ASPM Disabled RCB 128 Bytes CommClk- ExtSynch-
                                 Link: Speed 2.5Gb/s, Width x1
                   Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
                                  Vector table: BAR=0 offset=00000000
                                  PBA: VAR=0 offset=00000000
                    Capabilities: [100] Advanced Error Reporting
                   Capabilities: [140] Virtual Channel




And  


06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139
C+ (rev 10)
              Subsystem: Acer Incorporated [ALI] Unknown device 009f
              Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR-  FastB2B-
               Status: Cap+ 66MHz- UDF-  FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
                Latency: 64 98000ns min, 16000ns max)
                Interrupt: pin A routed to IRQ 50
                Region 0: I/O ports at a000 [size=256]
                Region1: Memory at b03000000 932-bit, non-prefetchable) [size=256]
                Capabilities; [50] Power Management version 2
                               Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME (D0-,D1+,D2+,D3h
oot+,D3cold+)
                               Status: D0 PME-Enable- DSel=0 DScale=0 PME-




Any and all help will be greatly appreciated.  Thanks in advance.

The Realtek 8139 will work out of box.  My laptop has an 8139 and desktop has 8169 and both worked with Edgy right away.

As far as wireless you probably need madwifi.  Follow my procedure to get madwifi installed.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

This should work.

---

### Post by taishi28012 on 2007-05-17
Thanks for the guide but despite trying it multiple times it didn't work.  And just so you know there is a misspelling here:  

 cp /home/joe/download/madwifi-0.9.3.tar.gz /urs/src

it should be /usr/

---

### Post by stchman on 2007-05-18
> **taishi28012 said:**
> Thanks for the guide but despite trying it multiple times it didn't work.  And just so you know there is a misspelling here:  

 cp /home/joe/download/madwifi-0.9.3.tar.gz /urs/src

it should be /usr/

Thank you very much.  I will correct the spelling error.  Spell checkers cannot really catch those kinds of errors as they think all folder nomenclature is a misspelled word.  The procedure I have there worked on my laptop that ran Edgy and a friends laptop as well.  The Atheros card in my laptop was a 5006EG.

I have since upgraded to Feisty and the Atheros wireless worked out of the box.  Feisty installs a restricted module for Atheros cards.

---

### Post by taishi28012 on 2007-05-18
Your welcome and thank you. Ill try doing a clean install of 7.04.

---

### Post by shpez on 2007-05-31
stchman, I did everything on your site to see if I can get my wifi to work... everything seemed to install fine but it is still not detecting my atheros card.   Any other suggestions would be helpful.  That stats on my laptop are very similar to the original post.

---

