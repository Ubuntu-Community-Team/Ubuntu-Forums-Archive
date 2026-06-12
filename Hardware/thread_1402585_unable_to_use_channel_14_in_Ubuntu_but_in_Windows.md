---
title: "unable to use channel 14 in Ubuntu but in Windows"
date: 2010-02-09
forum: Hardware
---

### Post by utileria on 2010-02-09
My Asus 900HA can use WiFi channel 14 in Windows, but when trying to use it in Ubuntu Remix 9.10 it cannot access it (only usable channels 1-13 in Ubuntu).

I have also a desktop with a SMC wireless PCI adapter (model SMCWPCI-G2) that can access channel 14 both in Windows and in Ubuntu 9.10. 

The router is a Linksys WRT54GL with a dd-wrt firmware.

Any technical suggestion how I can fix this technical issue?

Thank you very much!

$ iwlist channel
lo        no frequency information.

eth0      no frequency information.

wmaster0  no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency=2.484 GHz (Channel 14)

tun0      no frequency information.

---

