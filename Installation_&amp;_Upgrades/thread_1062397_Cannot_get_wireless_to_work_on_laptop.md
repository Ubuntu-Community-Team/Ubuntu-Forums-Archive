---
title: "Cannot get wireless to work on laptop"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by primus454 on 2009-02-06
Okay so after several days I was able to install Hardy on my new laptop, but now I cannot get the wireless to work.

I am on an Asus x83vm with an Intel WiFi 5100 agn wireless card. It works fine on Windows Vista 64bit and I am running Hardy 32 bit.

Using the lspci command I get
```
03:00.0 Network controller: Intel Corporation Unknown device 4232

```

and lshw -C network returns
```
PCI (sysfs)  
  *-network DISABLED      
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:59:87:f0
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:23:54:f5:76:b0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=24.140.120.208 latency=0 module=r8169 multicast=yes
```

---

### Post by primus454 on 2009-02-06
I followed [http://www.connect-utb.com/index.php?option=com_content&view=article&id=46:get-intel-wireless-wifi-link-5100-working-on-ubuntu-804&catid=34:linux](http://www.connect-utb.com/index.php?option=com_content&view=article&id=46:get-intel-wireless-wifi-link-5100-working-on-ubuntu-804&catid=34:linux) 

and it still does not work.

---

### Post by trendyabinash on 2009-02-06
Hey I got my wireless working by using "ndisgtk" U can find it in the synaptic package manager. Install it and then go to administration windows wireless drivers and add your driver files, after that It will work.

Atleast It worked for me in this way.

And Yes you have to get the .inf file the setup.exe won't do the trick.

---

### Post by primus454 on 2009-02-06
I dont see any .inf. All I see are .ucaode

---

### Post by primus454 on 2009-02-06
Okay, through some searching I've come to think that it is a killswitch issue. I cannot get the wireless light to turn on. At this point it will show wireless networks but will not connect to them.

---

### Post by primus454 on 2009-02-07
Okay. So I have ran ndiswrapper and disabled IPv6 but my wireless is still terribly slow. It works fine on my other wireless laptop. I am getting download rates of ~54kb/s on this one. I forget what it is on my other. Pings on the other are around 60 on average and on this they average about 2000 but have been as high as 6000--and this is right next to the router.

---

### Post by jpeddicord on 2009-02-07
It's possible that the card is not really running at its full speed or even in N mode. Those speeds look worse than B mode, really. This isn't a great solution, but could you try it out with the laptop sitting really close to the router? If it runs faster there, then hopefully the only thing that needs to be done is turn up the signal power (though I'm not sure how to do that at the moment).

edit: never mind, was just told over irc that you tried this. :P

---

