---
title: "Broadcom BCM4352 wifi disabled, only works on wake from suspend"
date: 2015-03-25
forum: Hardware
---

### Post by skdd on 2015-03-25
So, today i got Ubuntu-trusty into my laptop DELL M3800 and it has some strange out of some nightmare issue with the wireless driver. 

Guys this is driving me crazy i'm all out of answers and I hope the community could help. :-s[-o<[-o<

To start this are my distro:
```

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty

```

Below is the specs on my wifi card:

```

$ sudo lshw -C network
 *-network               
       description: Wireless interface
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 03
       serial: ac:d1:b8:c0:ec:bd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.1.126 latency=0 multicast=yes

```

Before there was not a driver for it the card installed out of the box so i had to go hunt for it and got the wl driver that makes the wifi networking appear into the active connections, also blacklisted b43 from loading  ```
  bcmwl-kernel-source 
```

I should also mention that I upgraded my kernel in advance because at first I though it was a kernel issue but it didn't seem to matter after all. 

```

$ uname -r
3.16.0-33-generic

```

one more this is that it might be relevant is this:

```

$ lsmod | grep wl
wl                   6367833  0 
cfg80211              521225  1 wl

```


```

$ dmesg | grep wl
[    3.823612] wl: module license 'MIXED/Proprietary' taints kernel.
[    3.825614] wl: module verification failed: signature and/or  required key missing - tainting kernel
[    3.827203] wl 0000:06:00.0: enabling device (0000 -> 0002)
[    3.856486] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   30.251505] wl 0000:06:00.0: no hotplug settings from platform

```

[SIZE=3]Now to my problem:[/SIZE] 

So after all this the wireless network appeared and the problem was that it was disabled by hardware and i got this from my rfkill

```

$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: [COLOR="#FF0000"]YES[/COLOR]
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

I tried many things and searched all over the place but I wasnt able to fix. Time passed and the computer went to sleep as I went to sob. [SIZE=3][COLOR="#000080"]**When I came back and woke the computer from suspend the wifi was magically working. **[/COLOR][/SIZE]

```

$rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

The problem is that I have to do this over and over again. So for example if i reboot my computer it disables the wifi but it gets enabled only if i suspend it and wake it up after. 

Has somebody encounter this? maybe i am using the wrong driver or doing something wrong. 

How can i have the wireless enabled at all times? unless i explicitly disable it.

I know this is a long post I wanted to be as detailed as possible, I hope some brave soul can help me with this. 

thanks

---

