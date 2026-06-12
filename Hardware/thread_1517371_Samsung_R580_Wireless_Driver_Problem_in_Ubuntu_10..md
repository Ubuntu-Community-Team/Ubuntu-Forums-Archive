---
title: "Samsung R580 Wireless Driver Problem in Ubuntu 10.04"
date: 2010-06-24
forum: Hardware
---

### Post by moddinman on 2010-06-24
I've tried different solutions. I still can't get it working. I've tried installing the windows wireless driver. That didn't work. It shows that the hardware is present but doesn't work for some reason. It's not showing my ssid. Even if I try to enter it manually it doesn't work. Please help.

---

### Post by OxentroT on 2010-06-25
Have you tried 

```
iwconfig
```

---

### Post by moddinman on 2010-06-25
No how would I go about doing this. I'm great at windows but new to this.

I typed it in and got 

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:65 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I've done a little reading and found out this can help set your ssid, channel, and other settings. I've played around with it a little and still no luck. I've entered 

iwconfig wlan1 essid test (which is my test network) 

Then typed in

ifconfig wlan1 up

Checked to see if it made a change with

iwconfig

Still getting 

root@ubuntu:/home/nbcr# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:65 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by moddinman on 2010-06-25
I've been going through the trouble shooting steps and have more information to include.

-network
                description: Wireless interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan1
                version: 01
                serial: b4:82:fe:5e:00:7f
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+net819xp driverversion=1.55+Realtek Semiconductor Corp. latency=0 link=no multicast=yes wireless=IEEE 802.11g
                resources: irq:16 ioport:3000(size=256) memory:f0700000-f0703fff

---

### Post by OxentroT on 2010-06-25
Ubuntu sometimes doesn't readily recognize some brands of modem and WLAN adapters. When this is the case, chances are it can in fact be resolved with a little tweaking.  Fret not. I was completely new to Linux a couple years ago and knew nothing. I had problem after problem in migrating all of my machines to ubuntu to run smoothly. But that was a real help in learning. And I am still learning and experimenting with this fantastic OS. 


What comes up when you run the command

```
lspci
``` ?



I'm trying to see what make of wireless device is installed in that model machine.

---

### Post by moddinman on 2010-08-05
Thanks for the help, but I've decided (like many) to revert back to windows after a catastrophic failure in which the computer wouldn't even boot up. They really need to work out the compatibility issues before this becomes a mainstream product. Windows may have it's flaws but it's familiar and much easier to work with.

---

