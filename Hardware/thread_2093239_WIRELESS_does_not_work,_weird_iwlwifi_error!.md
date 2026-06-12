---
title: "WIRELESS does not work, weird iwlwifi error!"
date: 2012-12-10
forum: Hardware
---

### Post by hashbrown on 2012-12-10
Hi ):P

I have bought a new laptop Samsung Series 5 Ultrabook (64bit) and installed linux side by side windows.
But I am not able to get the wifi to work yet with this laptop.

I am using wicd and it is not detecting any wireless network. 

1) When I issue [ifconfig -a], it shows me this (showing only the wlan0 interface part)
```

wlan0     Link encap:Ethernet  HWaddr c4:85:08:05:71:16  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

2. If I issue the command, [iwconfig wlan0], it shows me this
```

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```
3. [ifup] reports the interface wlan0 is already configured.
4. I checked [lspci -v] to check network bus, and here is the output:
```

01:00.0 Network controller: Intel Corporation Device 088e (rev 24)
	Subsystem: Intel Corporation Device 4060
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f0500000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 16-71-05-ff-ff-08-85-c4
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

``` 

Btw, my network card is, Intel Centrino Advanced-N 6235. Why does it just show " Intel Corporation Device 088e (rev 24)"?

5. Next I looked into [dmesg | grep -i "iwlwifi"] and saw many errors. The entire output is attached here. One of the lines in the output say:

> iwlwifi 0000:01:00.0: Microcode SW error detected.  Restarting 0x2000000.

By the way, this wireless is working properly in Windows O/S. Now given my limited knowledge in Linux, at this point I am completely lost on what should be my next step to fix this problem.
Any idea/help/suggestion would be very much appreciated?

Thanks in advance!
#brown

---

### Post by ahallubuntu on 2012-12-10
You didn't say which version of Linux you were using.  According to this, iwlwifi supports your card only with kernel 3.2 and later:

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

---

### Post by hashbrown on 2012-12-10
> **ahallubuntu said:**
> You didn't say which version of Linux you were using.  According to this, iwlwifi supports your card only with kernel 3.2 and later:

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

I am on 3.2.6

---

