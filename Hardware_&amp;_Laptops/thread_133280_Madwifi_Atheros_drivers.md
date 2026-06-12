---
title: "Madwifi Atheros drivers"
date: 2006-02-19
forum: Hardware &amp; Laptops
---

### Post by caston on 2006-02-19
Hello,

I'm running kubuntu on a Twinhead Durabook 14k   
I initially had the 2.6.12 voltage pcmcia issue (the one where it can't turn off power to the pcmcia slot) so upgraded to 2.6.15-1-k7   
from sid.    
   

I'm using a  650G TP-LINK 108mb pcmcia card with the Atheros chipset.   
  
I downloaded the mad wifi drivers using subversion and the following  
instructions:  
  
[http://ubuntuforums.org/showthread.php?t=105437&highlight=madwifi+ng](http://ubuntuforums.org/showthread.php?t=105437&highlight=madwifi+ng)  
  
dmesg now gives me:  
  
pccard: card ejected from slot 0  
ACPI: PCI interrupt for device 0000:02:00.0 disabled  
pccard: CardBus card inserted into slot 0  
yenta EnE: chaning testregister 0xC9, 04 -> 04  
PCI: Enabling device 0000:02:00.0 (0000 -> 0002)  
ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 169  
wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps  
wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps  
36Mbps 48Mbps 54Mbps  
wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps  
wifi0: H/W encryption support: WEP AES AES_CCM TKIP  
wifi0: mac 7.9 phy 4.5 radio 5.6  

wifi0: Use hw queue 1 for WME_AC_BE traffic  
wifi0: Use hw queue 0 for WME_AC_BK traffic  
wifi0: Use hw queue 2 for WME_AC_VI traffic  
wifi0: Use hw queue 3 for WME_AC_VO traffic  
wifi0: Use hw queue 8 for CAB traffic  
wifi0: Use hw queue 9 for beacons  
  
/var/log/messages  
 
eb 19 21:26:03 localhost kernel: wifi0: H/W encryption support: WEP AES 
AES_CCM TKIP 
Feb 19 21:26:03 localhost kernel: wifi0: mac 7.9 phy 4.5 radio 5.6 
Feb 19 21:26:03 localhost kernel: wifi0: Use hw queue 1 for WME_AC_BE traffic 
Feb 19 21:26:03 localhost kernel: wifi0: Use hw queue 0 for WME_AC_BK traffic 
Feb 19 21:26:03 localhost kernel: wifi0: Use hw queue 2 for WME_AC_VI traffic 
Feb 19 21:26:03 localhost kernel: wifi0: Use hw queue 3 for WME_AC_VO traffic 
Feb 19 21:26:03 localhost kernel: wifi0: Use hw queue 8 for CAB traffic 
Feb 19 21:26:03 localhost kernel: wifi0: Use hw queue 9 for beacons 
Feb 19 21:26:03 localhost kernel: wifi0: Atheros 5212: mem=0x22000000, irq=169 
Feb 19 21:26:04 localhost pci.agent[8061]:      ath_pci: already loaded 
 
 
 
 
iwconfig  
  
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
sit0      no wireless extensions. 
 
wifi0     no wireless extensions. 
 
Warning: Driver for device ath0 has been compiled with version 19 
of Wireless Extension, while this program supports up to version 18. 
Some things may be broken... 
 
ath0      IEEE 802.11b  ESSID:"" 
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00 
          Bit Rate:0 kb/s   Tx-Power:50 dBm   Sensitivity=0/3 
          Retry:off   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
 
Despite this I cannot find any available wireless networks under kwifimanager. 
 
Am I perhaps missing something?

---

### Post by Robgould on 2006-02-20
I use an Atheros card on my lpatop.  The driver is included by default as part of the linux-restricted-modules that is available through synaptic.  After you install that you should see your card.  From the wifi configuration panel select ath0.  You have to configure it and then enable it.

---

### Post by davinci on 2006-02-20
I use 2.6.15 with the latest SVN Atheros drivers too. Works perfectly but I have not used kwifimanger for configuration. Have you tried to set your parameters (IP, ESSID, WEP key, etc.) manually in /etc/network/interfaces?

Do you see your access point/router ? iwlist scan ath0

---

