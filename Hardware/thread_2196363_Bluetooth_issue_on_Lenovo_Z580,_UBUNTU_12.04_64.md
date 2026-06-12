---
title: "Bluetooth issue on Lenovo Z580, UBUNTU 12.04 64"
date: 2013-12-29
forum: Hardware
---

### Post by kantor-d on 2013-12-29
Hi there, 

I'm a new Ubuntu user. After 5 months witch Ubuntu I cant imagine to turn back to Windows. However i have just one issue with this system: My bluetooth is not working. My computer is a Lenovo Z580, Pentium I3, 4GB Ram. System: Ubuntu 12.04 (64bit) The bluetooth was working under Windows 7. Here is what i have already tried:



[LIST=1]
[*]Checking if the BT is Enabled in BIOS - it is
[*]Checking the hardware switch: The hardware switch in Z580 is under Fn+F5, however in windows it worked for both: Bluetooth and WiFi. After pressing it a special window showed up where it was possible to turn WiFi and BT on/off. In Ubuntu it works just for WiFi. I tried to press it more times to find out if it will turn on - no success.
[*]Kernel was updated to 3.8.0-34 generic in hope that the newer one will help out. I also tried this on Ubuntu 13.10 Live cd, where the BT is still not working...
[/LIST]

rfkill list returns:


```

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Thanks for help!

---

