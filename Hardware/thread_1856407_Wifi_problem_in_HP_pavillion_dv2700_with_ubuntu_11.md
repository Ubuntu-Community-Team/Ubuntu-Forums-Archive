---
title: "Wifi problem in HP pavillion dv2700 with ubuntu 11.04"
date: 2011-10-08
forum: Hardware
---

### Post by Ajayreddy on 2011-10-08
Hello all,
            I recently installed ubuntu 11.04 on my hp pavillion dv2700 laptop. The problem is that the wifi is not working properly in the sense when i first installed STA driver, wireless worked but after few days its not working it shows that wireless is disabled by hardware switch, but that switch is enabled. So i removed that STA driver and again reinstalled it now it worked but after few days the same problem is occurring. So please help me out with this problem.
The result of:rfkill list all

0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
Thank you!

---

### Post by soap1 on 2011-12-29
try to download the b43 driver.  Open up your terminal and type in "sudo apt-get install firmware-b43-installer"

hope that helps.

---

