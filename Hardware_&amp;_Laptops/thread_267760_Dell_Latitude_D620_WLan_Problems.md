---
title: "Dell Latitude D620 WLan Problems"
date: 2006-09-29
forum: Hardware &amp; Laptops
---

### Post by theodize on 2006-09-29
Hello,

I don't get WLan access under Ubuntu.
Using the Network-dialog it doesn't work. 

I tried to install my WLan card on Ubuntu.
*ndiswrapper* says:
[FONT="System"]Installed ndis drivers:
bcmwl5          driver present, hardware present[/FONT]
8) 

In the Device Manager of Ubuntu it is written (net.interface is set to strlist eth1):
BCM4310 UART
  WLan Interface 
8) 

But with *dmesg* I get:
[FONT="System"]bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not availabl e or load failed.[/FONT]
:-k 

And in iwconfig I can see:
```
eth1      IEEE 802.11b/g  ESSID:"ap-849"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


Does that mean that the driver is installed correctly?

And why can't I connect to the wlan I can connect to under Windows?

Any ideas?

Thanks a lot! :-D

---

### Post by theodize on 2006-09-29
Ok.

I got my card installed with the following guidance:

[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

Very good!

But I'm still trying to get access to the WLan (in windows it works)...

---

