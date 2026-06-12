---
title: "I need help to install network driver!!"
date: 2009-02-17
forum: Hardware
---

### Post by Christopher8827 on 2009-02-17
How do install a network driver? My Ubuntu OS can't connect to the internet without it. I got these .tar.gz files I downloaded from the web,and they 'should' contain the drivers. plz help. I'm a Windows user.

---

### Post by x33a on 2009-02-17
is it for your lan card or wireless?

---

### Post by Christopher8827 on 2009-02-17
It is for my wireless card. It works on my Windows OS.

Ubuntu doesnt seem to recognise it because i cant select connect to Wireless network.

---

### Post by trepid666 on 2009-02-18
what type of card is it?

post output of 

```
lspci
```

---

### Post by Christopher8827 on 2009-02-18
The card is a Linksys Wireless-G pci adapter. Its model no. is WMP54G

if u found the drivers for it, plz post the link. I dont thinks its the right one.

here is the output:
> master@ubuntu:~$ lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:05.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation Device 0605 (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation Device 0605 (rev a2)
03:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
03:07.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
03:08.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
master@ubuntu:~$ 


thx.

---

### Post by x33a on 2009-02-18
hi, since you have an ethernet card, then you can first connect to the net through that. 

try sudo pppoeconf in a terminal to configure your ethernet connection. 

if you manage to connect to the net, then take a look here to get your wireless working:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)[COLOR=white][FONT=monospace]**35**[/FONT][/COLOR]

---

### Post by Christopher8827 on 2009-02-18
Ubuntu seems to be unable to detect the wireless card. I don't want to connect to my ethernet card, I want to connect to my Wireless Card.

---

### Post by trepid666 on 2009-02-18
```
03:08.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

I think you actually have a Broadcom BCM4306 card


You're better off to plug in your ethernet first, update, and click on System ---> Administration ----> Hardware Drivers  and enable the restricted driver.
After that, your wireless will work.

Heres a link that may help you compile but its alot more work [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

---

### Post by Christopher8827 on 2009-02-19
> **trepid666 said:**
> ```
03:08.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

I think you actually have a Broadcom BCM4306 card


You're better off to plug in your ethernet first, update, and click on System ---> Administration ----> Hardware Drivers  and enable the restricted driver.
After that, your wireless will work.

Heres a link that may help you compile but its alot more work [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

i cant. Only the nvidia drivers are showing up. How do i log in as Admin?

---

### Post by trepid666 on 2009-02-20
at login screen:

username: root
password: "your root password"

i don't recommend it though, you can really screw things up if you modify the wrong files.

u can also type

```
sudo 
```

and then the command in Terminal. then it will prompt you for your password.

---

### Post by NexusZA on 2009-02-20
> **Christopher8827 said:**
> i cant. Only the nvidia drivers are showing up. How do i log in as Admin?

What these guys are saying is temporarily connect to the Internet using your wired network. Its not a permanent fix but if you can get that machine online that way it can ultimately help resolve the issue you are having.

Once you are online and you have installed all existing updates to Ubuntu you can then go to System > Administration > Hardware Drivers.

As far as Admin user is concerned you don't need to login as admin ever on a Desktop version of Ubuntu. Its for your own safety and one of the biggest reasons why Ubuntu has fewer virus issues than other OS's because apps cannot install themselves into your critical system areas without you saying ok by entering your password in the prompt that pops up.

If you want to run a command in the terminal as a root user you can do it temporarily for just that command with sudo:

```

sudo apt-get install package-name-here

```

as an example

---

### Post by Christopher8827 on 2009-02-20
How do I configure the ethernet? I can't click the Wired Connection.

---

### Post by trepid666 on 2009-02-20
Your ethernet should already be configured... but all you do is right-click the network applet then select edit or configure.

You want to set it up to use auto DHCP

Or you can go System-- Administration-- Network and configure there. You can also do that in Terminal

---

