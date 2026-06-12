---
title: "HP NC6220, enable wifi"
date: 2011-10-11
forum: Hardware
---

### Post by thusgaard on 2011-10-11
Hi 

I just reinstalled my ubuntu 11.04, that was working perfectly. 
It still works, but WIFI dosn't work. 

I've been looking around and it looks like it's my button to turnon wifi that dosn't work. Here is what I've found out: 

**iwconfig**
```
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**rfkill**
```

:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: **[COLOR="Red"]yes[/COLOR]**
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: [COLOR="red"]**yes**[/COLOR]
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: [COLOR="red"]**yes**[/COLOR]
```

**lspci**
```
:~$ lspci -nnk | grep -iA2 net
02:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Hewlett-Packard Company Compaq nw8240/nx8220 [103c:12f6]
    Kernel driver in use: ipw2200
--
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express [14e4:167d] (rev 11)
    Subsystem: Hewlett-Packard Company Device [103c:0944]
    Kernel driver in use: tg3

```


It seams to me that the key to remove the blocking dosn't work. Even though it worked before I reinstalled (Same Ubuntu version). 


Kind Regards J;-)

---

### Post by thusgaard on 2011-10-11
Did the BIOS thingy mentioned on this page: [https://wiki.archlinux.org/index.php/HP_Compaq_nc6220](https://wiki.archlinux.org/index.php/HP_Compaq_nc6220)

> Troubles with wireless

The default BIOS settings maximize power savings by only allowing either power to be given to the wireless card or the Ethernet card. Either disable the "LAN/WLAN Switching" in the BIOS, eject the "tg3" module when you want to use the wireless card, or unplug the Ethernet cable. 

This machine was installed connected to wired network. I usually only use wireless. But this time I was at a remote location and only had wired network. This might have caused the wireless to act up. 

J;-)

---

