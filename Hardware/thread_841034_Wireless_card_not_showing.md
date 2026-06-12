---
title: "Wireless card not showing"
date: 2008-06-26
forum: Hardware
---

### Post by rickymare on 2008-06-26
I have a compaq laptop evo n610c, few years old... it is showing the regarding nic card but it is not showing the wireless card... how would i go about this?

the specs are...

pentium 4 1.7
ATI Mobility Radeon 7500 Graphics Controller with 32 MB of DDR video RAM.
14.1-inch SXGA+ or 14.1-inch XGA display
1024 MB DDR RAM (266 MHz), 
80g hdd
Integrated modem and NIC

here is the link to the specs. 

[http://h18000.www1.hp.com/products/quickspecs/11382_div/11382_div.HTML]("http://h18000.www1.hp.com/products/quickspecs/11382_div/11382_div.HTML")

My windows XP would keep giving me the bluescreen on boot only at my house so i decided to go with linux and so far everything is keen.

---

### Post by flerp on 2008-06-26
this link might help:

[https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200]("https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200")

I've just done an 8.04 install on the same hardware, i haven't got it working just yet though...

Let us know how you get on...

---

### Post by ukripper on 2008-06-26
> **rickymare said:**
> I have a compaq laptop evo n610c, few years old... it is showing the regarding nic card but it is not showing the wireless card... how would i go about this?

the specs are...

pentium 4 1.7
ATI Mobility Radeon 7500 Graphics Controller with 32 MB of DDR video RAM.
14.1-inch SXGA+ or 14.1-inch XGA display
1024 MB DDR RAM (266 MHz), 
80g hdd
Integrated modem and NIC

here is the link to the specs. 

[http://h18000.www1.hp.com/products/quickspecs/11382_div/11382_div.HTML]("http://h18000.www1.hp.com/products/quickspecs/11382_div/11382_div.HTML")

My windows XP would keep giving me the bluescreen on boot only at my house so i decided to go with linux and so far everything is keen.

Can you go into Application-->Accessories-->terminal and type following commands and post the output here:
```
lspci
```

```
iwconfig
```

---

### Post by rickymare on 2008-06-26
Thanks a lot for the help! i will try this when i get off of work.

---

### Post by rickymare on 2008-06-26
Also i have feist with that system... if that helps

---

### Post by rickymare on 2008-06-26
when i typed in lspci this came up.

00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:04.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:06.0 CardBus bridge: Texas Instruments PCI1420
02:06.1 CardBus bridge: Texas Instruments PCI1420
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 42)
02:0e.0 USB Controller: NEC Corporation USB (rev 41)
02:0e.1 USB Controller: NEC Corporation USB (rev 41)
02:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02)

when i typed in iwconfig this came up

lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by rickymare on 2008-06-26
i have tried that link listed above but it cant find that hard ware... i dont think that i have that hardware because it says something about usb. i can get on when i am connected wired but... i want to use my wireless so when i am out or not right next to the router.

---

### Post by Rexcon on 2008-06-26
Ladies And Gents 

Im new on Ubuntu, need help with my wireless connection  Network controller: Intel Corporation PRO/Wireless 3945ABG Network
I have a Lenovo T60 loptop
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"wmbw"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:E5:CA:E7   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

is not working for me can some one help me  please 

I have no clue what is wrong the mac is configure on the router... secure connection.
I hope Im on the right place

---

### Post by flerp on 2008-06-27
> **rickymare said:**
> i have tried that link listed above but it cant find that hard ware... i dont think that i have that hardware because it says something about usb. i can get on when i am connected wired but... i want to use my wireless so when i am out or not right next to the router.

You have an n610c? With a bulge on the lid? I was surprised as well, actually the adapter is internally wired via USB.. 

I downloaded and compiled the driver, I managed to get it to radio on, but the gui tool for setting up wifi failed dismally. Using the commandline tools (iwconfig, dhclient), i got it to work (sort of). That said, my access point only uses mac filtering, nice and easy. Getting it to work with WPA might be a bit harder.

---

### Post by ikxgamex on 2008-06-27
Hi. I have a compaq Evo n160 that I got from a friend. I decided to install ubuntu on it and hook up a wireless card. I first installed hardy, which did not recognize my wireless adapters (rt73, rt2500) like it should have. Ndiswrappr also was unsuccessful. I then installed gusty and attempeted to use the same wireless adapters. Once again, the adapters that WERE detected on my pc running ubuntu 7.04 WERE NOT detected on my laptop. Is there any explination for wireless cards not being detected? Whenever I do lsusb or lspci, I can see my device listed. They are, however, completely unusable. 

Any help or input would be appriciated =]

---

### Post by ukripper on 2008-06-27
> **flerp said:**
> You have an n610c? With a bulge on the lid? I was surprised as well, actually the adapter is **internally wired via USB.. **



Laptops maker have lost a plot i guess! They started doing this dirty stuff using USB to masquerade the wireless chipset.

 How stupid of them!

---

### Post by ukripper on 2008-06-27
Can you run this command:
```
lsusb -v
```

and post output here

---

### Post by flerp on 2008-06-27
some success, I now have a stable system on my n610c running Gutsy...

with the base install , i had 2 problems:

1/wifi
2/desktop effects (direct rendering)

solutions (a bit crude maybe)

1/ installed the 1297 driver as per[ https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200]("https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200")
Setup a button to run a shell script on one of the panels to kill nm-applet and then do a manual dhclient eth1 (the network-manager was crashing my machine upon getting a dhcp address, though the AP association seemed to be automatic)

```
kill `ps -ef | grep nm-applet | grep -v grep | awk  '{ print $2  }'`
dhclient eth1
```

2/ To get desktop effects to work added some lines to /etc/X11/xorg.conf in the device section describing my ati radeon 7500:

```
Option          "GARTSize" "64"
Option          "AGPMode" "4"
```

A bit kludgy, but functional.

---

### Post by rickymare on 2008-06-27
my desktop effects seem to be working fine but i will try out what you mentioned. thank you so much!

---

### Post by rickymare on 2008-06-27
all right i tried the lsusb -v and this came up... pretty long..

Bus 003 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

---

### Post by josevtome on 2008-10-14
Hi! need a little help! I installed 7.10 and the wireless worked fine, but when upgraded to 8.04 it stoped working. It appears that the proprietary drivers for my wireless device are gone and I can see all wireless in my radio, but can't connect to any of them (including my own). Mine keeps asking for the wep key. And it doesn't matter if I configure my wireless without a wep key or any kind of protection, it doesn't work.

I have a Lenovo T60 laptop. Take a look at this:
jtomev01@rachel:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller


jtomev01@rachel:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
irda0     no wireless extensions.
cipsec0   no wireless extensions.

I'm also having problems configuring my EvDO Sierra Wireless device. I have an AirCard 580 and can't get it to work, or I don't know if it's just me so dumb to get online with it. :lolflag:

Any ideas? :D

---

