---
title: "help with modem identification (ModemData.txt)"
date: 2006-10-05
forum: Hardware &amp; Laptops
---

### Post by eeried on 2006-10-05
Hello,

I'd like to help someone set up a dial-up connexion on his Ubuntu Dapper, through email which may not be the easiest thing of course. Once the modem is identified I'll turn to the Ubuntu doc (and I once installed the connexant limited drivers with success -- on Ubuntu Hoary).

This is a snippet of the ModemData file he sent me:
>  Ubuntu 6.06 LTS 
Linux version 2.6.15-26-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu
4.0.3-1ubuntu5)) #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006
 scanModem update of:  2006_September_13

USB modem not detected by lsusb

 Modem or host audio card candidates have firmware information:
 PCI ID     Subsystem  Name
 ---------- ---------  -----------------
 8086:2486  134d:4c21  Modem: Intel Corporation 82801CA/CAM AC'97 Modem
Controller 
Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
--Bootup Disablement problem-------
[17179573.812000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
---------------------------------

 For candidate modem in PCI bus:  0000:00:1f.6
   Class 0703: 8086:2486 Modem: Intel Corporation 82801CA/CAM AC'97 Modem
Controller 
      Primary PCI_id  8086:2486
    Subsystem PCI_id  134d:4c21 , 134d is an ALSA compatible
identification
    Softmodem codec or Vendor from diagnostics: SIL21, a Pctel type.
                              from    Archives: SIL21, a Pctel type.
      

 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic

 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	slmodemd

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-intel8x0m
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility: 
slmodemd

1. If I understand rightly this winmodem is a smartlink. Is it a real smartlink modem or is it one that can use the smartlink driver?

2. The report says the modem is compatible with ALSA which can give a low level of support. Does it mean the alsa drivers must still be installed first and then the smartlink drivers?

3. I suppose the owner of the laptop who uses a DSL connection at home could use his Wifi card while away from home if he's got one, couldn't he?

Many thanks in advance for your help!

---

