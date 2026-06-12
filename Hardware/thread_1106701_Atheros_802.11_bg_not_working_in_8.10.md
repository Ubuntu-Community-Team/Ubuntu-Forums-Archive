---
title: "Atheros 802.11 b/g not working in 8.10"
date: 2009-03-26
forum: Hardware
---

### Post by eristikophiles on 2009-03-26
my new Toshiba Satellite (L305D-S5914) has an Atheros 802.11 b/g wifi card built-in, but it doesn't seem to be recognized by kubuntu 8.10 (Intrepid Ibex). plugging in an ethernet cable to eth0 works fine though. i've been told that often driver issues arise in these cases- does anyone know about a driver i can use for the card?

or, if it's not a driver issue, and you know the trick to fix it, that'd be cool too. :)

---

### Post by luks911 on 2009-03-26
Please, in a terminal type ```
lspci
``` and post the result.

---

### Post by eristikophiles on 2009-03-26
i did lspci -vv, and here's the results for that device (not the whole thing):

04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Askey Computer Corp. Device 7128
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at 8b100000 (64-bit, non-prefetchable) [disabled] [size=64K]
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
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM unknown, Latency L0 <512ns, L1 <64us
                        ClockPM- Suprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk-
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
                Vector table: BAR=0 offset=00000000
                PBA: BAR=0 offset=00000000
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Virtual Channel <?>
        Kernel modules: ath_pci

---

### Post by SuperSonic4 on 2009-03-26
[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html) 

worked for my atheros card and should work for yours since it's a 242x chip. Method 2 worked for me

---

### Post by eristikophiles on 2009-03-27
so i followed the link and got ahold of the latest compat-wireless bz2, but it doesn't want to be made (i have the required build-essential package installed)

here's the error i get:
make -C /lib/modules/2.6.27-7-generic/build M=/home/eristikophiles/files/installs/system/compat-wireless-2009-03-27 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'                                                      
  CC [M]  /home/eristikophiles/files/installs/system/compat-wireless-2009-03-27/drivers/misc/eeprom/eeprom_93cx6.o         
In file included from <command-line>:0:                                                                                    
/home/eristikophiles/files/installs/system/compat-wireless-2009-03-27/include/net/compat.h:6:35: error: linux/compat_autoconf.h: No such file or directory
make[3]: *** [/home/eristikophiles/files/installs/system/compat-wireless-2009-03-27/drivers/misc/eeprom/eeprom_93cx6.o] Error 1                           
make[2]: *** [/home/eristikophiles/files/installs/system/compat-wireless-2009-03-27/drivers/misc/eeprom] Error 2                                          
make[1]: *** [_module_/home/eristikophiles/files/installs/system/compat-wireless-2009-03-27] Error 2                                                      
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'                                                                                      
make: *** [modules] Error 2


anyone know what to do about this? the file it wants doesn't appear anywhere. ;p

--
update: i tried method 2, and as far as i can tell there's no noticable change. ubuntu doesn't autodetect the wifi device and i can't find it in /dev (then again, i'm used to bsd, so i don't know what all of the things in /dev are anymore)

---

### Post by eristikophiles on 2009-03-29
so one thing i've noticed while trying to get this working: in Method 2, there's a mention of System/Administration/Hardware Drivers and making sure that the Atheros driver is enabled. i opened the app and tried to enable it but it says "This driver was just disabled but is still in use." next to the driver name, where there was a circle-icon, there's a 'refresh'-looking icon (an arrow curling on itself).

i'm not sure what that icon means or what this message means. i get it when i click on the 'enable' button; it doesn't seem like that would disable the driver. the app also says "No proprietary drivers are in use on this system." but that might not mean much since it also says the Atheros driver isn't proprietary (it says "License: Free").

there also isn't any line "blacklist ath5k" to comment out in /etc/modprobe.d

so now i'm really confused. ;p

---

### Post by eristikophiles on 2009-03-29
this might be unrelated, but while ifconfig returns eth0 and lo, ifconfig -a also returns pan0.. there's no /dev/pan0 though. here's the output section:

pan0      Link encap:Ethernet  HWaddr [MAC address removed]
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

so what is pan0? is this my wifi card, or is this something else entirely? i just googled and found out that it might be a bluetooth device. i didn't realize this laptop had any bluetooth ability though (as far as i know it doesn't?)

---

### Post by eristikophiles on 2009-03-29
solved!

method 1 worked in the end; the problem (which i pasted above) was that the UID/permissions were being preserved from the original archive. they were set to 1012. since i have no UID or group 1012, this wasn't working.. sudo chown -R on the install dir solved it, and i'm now using wifi. :)

thanks for y'all's help

---

