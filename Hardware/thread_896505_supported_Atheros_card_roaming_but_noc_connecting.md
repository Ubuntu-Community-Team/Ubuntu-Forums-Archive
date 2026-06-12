---
title: "supported Atheros card roaming but noc connecting"
date: 2008-08-21
forum: Hardware
---

### Post by Marin85 on 2008-08-21
Hi,
I´m quite new to Linux and this forum and I´m currently looking for a little help on a somewhat weird issue with my wifi card in Ubuntu. Here is the story: I have recently installed Ubuntu 8.04 x86 in a dual-boot configuration with my Vista Business x86 setup on a ThinkPad Z61p having a ThinkPad Atheros 802.11abg wireless LAN mini PCI-Express adapter installed internally (if I remember correctly, the Atheros chipset must be AR5BXB6). The wifi card is listed as fully supported by madwifi and I´m pretty sure it´s not somewhat defective as it works flawlessly under Vista. Also the device is recognized by Ubuntu and seems to work without a scratch in roaming mode since Ubuntu is indeed able to localize a plenty of wireless networks around (even more than Windows is able to with the very same card). However, as soon as I try to connect to my home network or to other networks I have access to, Ubuntu just fails to establish connection regardless of the router or encryption type. Here is an output of iwconfig:

```
 
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:"novo.bg"  Nickname:""
          Mode:Managed  Frequency:5.32 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=9/70  Signal level=-88 dBm  Noise level=-97 dBm
          Rx invalid nwid:6552  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.


```

I´m pretty clueless about this issue and will appreciate any insights. Let me know if any logs are needed.

Thanks in advance

Marin

---

### Post by pro003 on 2008-08-21
ath0 is your wifi card showing activity... 
you only need to configure it in ***System > Administration > Network***

---

### Post by Marin85 on 2008-08-21
Well, you see, each time I have to connect to a wireless network with some kind of encryption I have to go through the manual configuration, so unfortunately this isn´t what "I only need to do" ;) I wish it was that simple. Even when trying to connect to free hotspots the tray icon shows a wireless connection established to the given network but there is no internet, nor Ubuntu can update. For the record, the Intel Wireless PRO 3945abg works out of the box in Hardy.
Any further insights?

Marin

@**moderators**: I just saw that I posted in the wrong section, so feel free to move this thread out to the network/wireless section. Thanks

---

