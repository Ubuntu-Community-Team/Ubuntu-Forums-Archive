---
title: "Laptop Wireless Card"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by dannol on 2007-07-23
Hi everyone,

I'm having some trouble getting my inbuilt wireless card to work with ubuntu. I am running the latest version of ubuntu 7.04 (32bit). My laptop is a Novatech Revo 420 Elite. It has a Celeron M processor, 1gb Ram, Ati Graphics and has a Ralink 802.11g Mini Card Wireless Adapter.

Every time I try and connect to the network nothing happens. Ubuntu detects my wireless network and signal strength. As soon as I click to connect nothing happens. If I hover over the icon it says Connected to network but signal strength is 0%.

This doesn't make sense as it says that the signal strength is around 90% before I click connect and then as soon as I click the network the singal strength says 0 but yet it says it is connected. I know that it is not connected as my router says that it isn’t.

I have removed all security from my network. Does anyone know how to solve this problem?

Thanks very much!

---

### Post by walkerk on 2007-07-23
maybe [this]("http://ubuntuforums.org/showthread.php?t=478612") will help..? ralink cards need to be manually brough up after each boot. wifi-radar will do this if you alter the config file like the the thread linked..

or manually in terminal:
```
ifup wlan0
```

did this help?

---

### Post by dannol on 2007-07-23
I'm completely new to the terminal. I typed in what you said and it came back with:

```
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
```

Any ideas?

---

### Post by MrFSL on 2007-07-23
I reply to a lot of these wireless posts and see similar posts again and again.... So forgive me if this answer seems snide.... but really I am trying to help everyone that comes to this forum unable to connect to their wireless device

1) There are probably THOUSANDS of posts on this forum already on this subject. Search the forum and search [http://help.ubuntu.com](http://help.ubuntu.com) !!

2) Your wireless card makes up only 50% of the equation. Your wireless AP makes up the other half. So configure it to remove as many variables as possible. For Instance - Make sure to remove encryption (WEP/WPA/etc) from your wireless AP first and then try again. Make sure that DHCP is enabled on the router/ap unless you have to/choose to use static IPs. - Likewise, if you choose to use static IP's make sure that you understand TCP/IP networking standards.

3) If you are successful connecting to an unencrypted network, but not an encrypted network. I would suggest using WICD. If you need to do some troubleshooting I would read the documentation for your CLI wireless tools such as iwconfig and iwlist. Here is a link for WICD - 

[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

It has made 90% of my wireless woes go away.

---

### Post by dannol on 2007-07-23
I currently have no encryption on my network. I tried to download that program that you said but it says that the download server is currently down.

I think I will have a go at installing wifi-radar.

I have attached a screenshot of my network settings. Is there something wrong as I only have one wireless card, yet it is showing two wireless connections?

---

### Post by MrFSL on 2007-07-23
Well if wifi radar works for you then cheers! I could never get it to work reliably.

Here is a direct link to the wicd download from sourceforge. Doesn't appear to be down for me... you might want to choose a different mirror.

[https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=521838](https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=521838)

---

### Post by dannol on 2007-07-23
Thanks for the link. I have downloaded the file but it says "Error: Conflicts with the installed package 'network-manager'." And it wont let me continue.

---

### Post by imdano on 2007-07-23
You have to uninstall network-manager and network-manager-gnome before you can use it.  You can do it using apt-get or with Synaptic Package Manager.

---

### Post by MrFSL on 2007-07-23
Thats absolutely correct:

```

# The following kills the network manager applet
sudo killall nm-applet

# The following removes those conflicting packages
sudo apt-get -y remove network-manager

```

---

### Post by dannol on 2007-07-24
Thanks for the information on how to install it. I have now successfully installed Wicd. It detects my network but gets stuck on obtaining the IP Address. DHCP is enabled on the router so I don’t understand why none of the applications will connect.

---

### Post by MrFSL on 2007-07-24
What is your signal strength? If it is low this can affect if you are able to obtain an IP address.

Also what is the channel you are using for your wireless network?

If there is another network using the same channel (or interference of some sort) this can also create the situation with obtaining IP addresses.)

You should be using Channel 1, 6, or 11 since these are the only non-overlapping wireless channels.

Lastly what happens when you enter a static IP? Does it claim to be associated yet show a signal strength of 0% ? I have found this very indicative to the above mentioned reasons.

---

### Post by dannol on 2007-07-24
My signal strength before I connect is about 90% as I am trying to connect right next to it.
My network is on channel 3. I will try chainging it but I don't think thats a problem as it connects ok in XP.

I did try entering a static IP with the built in ubuntu network-manager, however I have not tried it yet with Wicd.

I will get back to you shortly with the results.

---

### Post by dannol on 2007-07-24
I have now changed the channel to 6 and tried connecting with a static IP. This connects almost instantly, however it still says connected at 0% signal. I know that it is not really connected to my router as the router does not display my laptop as being connected.

*Just thought that I would add that my signal strength is now showing up as -1% before I connect.*

---

### Post by imdano on 2007-07-24
Part of your problem (like the strength showing up as -1) is related to having a card that uses ralink drivers.  Ralink cards don't provide link quality information when running iwlist scan.  You also won't be able to connect to encrypted networks using most network managers (although a new version of wicd is being released today that adds experimental support).  However not being able to connect to an unencrypted network makes me think something else could be causing problems.  What's the output of ```
sudo lshw -C network
```

---

### Post by dannol on 2007-07-24
This is the output:

```
daniel@daniel-laptop:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@08:06.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:4c:d7:f3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:a000-a0ff iomemory:c0100c00-c0100cff irq:20
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:13:d3:7e:06:24
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
daniel@daniel-laptop:~$ 


```

---

### Post by imdano on 2007-07-24
While you were troubleshooting, did you mess around at all with your wireless driver?  According to that there isn't a driver associated with your card.  What's the output of ```
lspci -nn
```

---

### Post by dannol on 2007-07-24
No I have not touched the drivers.

Here is the output of lspci -nn:

```
daniel@daniel-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc Unknown device [1002:5a31] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:12.0 IDE interface [0101]: ATI Technologies Inc ATI 4379 Serial ATA Controller [1002:4379] (rev 80)
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200M] [1002:5a62]
08:05.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
08:05.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 01)
08:05.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
08:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
daniel@daniel-laptop:~$ 

```

---

### Post by MrFSL on 2007-07-24
no I'm really confused because i don't even see your wireless adapter listed.

How about posting the output of:
```
sudo lspci -v
```

---

