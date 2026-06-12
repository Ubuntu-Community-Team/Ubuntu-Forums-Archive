---
title: "Wifi Suddenly Stops Functioning dv2000"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by loxician on 2007-08-20
Hello I'm using a dv2020us HP laptop with ndiswrapper.
I've previously used the information on this forum to help me set up my wireless card.

However, today my wireless card suddenly stopped functioning. 

When I issue the command, 
```
sudo iwconfig wlan0 ap xx-xx-xx-xx-xx-xx
```
I receive
```
wlan0     Interface doesn't support IP addresses
Error for wireless request "Set AP Address" (8B14) :
    invalid argument "xx-xx-xx-xx-xx-xx".
```

When I say that it stopped functioning, I mean that my network flux suddenly dropped to zero, so I ran the following script:
```
#!/bin/sh
sudo modprobe -r ndiswrapper;sleep 2
sudo modprobe ndiswrapper;sleep 1
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid xxxx
sudo iwconfig wlan0 ap xx-xx-xx-xx-xx-xx
sudo dhclient wlan0
```
After which the I recieved the previously mentioned error and dhclient timed out.

Here is dmesg when I modprobe ndiswrapper and try to bring up wlan0:
```
[ 3162.579086] usbcore: deregistering interface driver ndiswrapper
[ 3163.843697] ndiswrapper version 1.47 loaded (smp=yes)
[ 3163.870103] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[ 3163.873071] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[ 3163.873306] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LK2E] -> GSI 19 (level, high) -> IRQ 19
[ 3163.873344] PCI: Setting latency timer of device 0000:01:00.0 to 64
[ 3163.877131] ndiswrapper: using IRQ 19
[ 3164.053820] wlan0: ethernet device yy:yy:yy:yy:yy:yy using NDIS driver: bcmwl5, version: 0x4281300, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[ 3164.053853] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 3164.056619] usbcore: registered new interface driver ndiswrapper
[ 3318.606514] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```
More information available upon request - please help!  I'm worried that it's a hardware problem, have your laptops had similar symptoms?

---

### Post by serj_alligator on 2007-08-22
try setting
> sudo modprobe ndiswrapper;sleep 5
in script. I think what happens is that your laptop doesn't get enough time to bring up interface...

---

