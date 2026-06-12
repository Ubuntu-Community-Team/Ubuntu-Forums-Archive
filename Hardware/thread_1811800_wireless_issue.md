---
title: "wireless issue"
date: 2011-07-25
forum: Hardware
---

### Post by cdesc on 2011-07-25
Hi everyone, 

I have a problem with my wireless on U 11.04.. During installation everything was fine, but now i can not enable the wireless.. 

I checked using lspci and the network controller is a realtek semiconductor RTL8188CE..

Can someone help?

---

### Post by pritam18 on 2011-07-25
I am having the same problem with my **Ubuntu 10.10** After enabling the wireless driver,connections are available but it is not getting connected.
Can somebody plz help me with this.
Thanx in advance.

---

### Post by seawolf167 on 2011-07-25
Take a look at [this link ]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE")for the driver, and [this link ]("http://ubuntuforums.org/showthread.php?t=1580036")(especially post #7 for installation instructions)

---

### Post by cdesc on 2011-07-25
Thank you for your answer.. I installed the driver and tried to turn the wifi on using ifconfig.. 

It is saying "operation not possible due to RF-kill". 

The outcome of rfkill list all is  says that :

soft blocked  : no
hard blocked : yes

I don't know what to do next??

---

### Post by grahammechanical on 2011-07-25
Hard blocked: yes, means that the wireless adapter is switched off in hardware. It this machine a laptop? Do you have to press a key combination to switch on wireless? Do you have another operating system installed and did you switch off wireless using that OS before restarting and loading Ubuntu?

The answers to those questions will tell you why Ubuntu is not detecting a working wireless adapter. This command might help:

```
rfkill unblock wifi
```

Regards.

---

### Post by seawolf167 on 2011-07-25
Echoing the above post - there is usually either some type of switch or button on the top or front/sides of the laptop to turn on the WiFi. You may also be able to actually turn in on permanently in BIOS depending on depending on your particular BIOS features.

---

### Post by cdesc on 2011-07-26
I tried rfkill unblock all, and then rfkill unblock wifi
..it runs but there is no change, the hard is still blocked.. The strange thing is there is a combination that should turn wireless on (FN+F8,) but none of the combination are working except one (for volume!)..

---

### Post by cdesc on 2011-07-26
maybe this speaks to someone.. i ran iwconfig wlan0

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off


I continued running sudo lshw -C Network

  *-network DISABLED      
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:6d:04:bd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=2.6.38-10-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:3000(size=256) memory:c3200000-c3203ff

Is it possible that this wireless doesn't work because of the width?? I'm using 32 bits.. 

Thanks in advance..:P

---

