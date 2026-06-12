---
title: "HP Laptop -- Need help getting on-board wireless to work. &gt;_&lt;"
date: 2010-11-21
forum: Hardware
---

### Post by blenderfox on 2010-11-21
Hi there,

I'm new to Ubuntu, but I'm really liking it more than Windows. :)

I always have problems with hardware when switching OSes and unfortunately, Ubuntu has not been any different. Fortunately, most of the hardware has been detected, but there's one which is really driving me nuts. It's my builtin wireless card (I'm running a HP laptop)

I'm still a bit of a dunce with linux commands, so please bear with me.

I have a power button on my wireless, which I turn on (it turns on Bluetooth too)

Bluetooth works, and I can pair devices. No matter what I try, I cannot seem to get my wireless card to pick up any networks, nor can I see it in the Network applet.

I really could use some help. :P

---

### Post by roger_1960 on 2010-11-21
Hi

Could you open a terminal menu>acccessories>teminal

Enter the following

> iwconfig

and post the output here.  We will see if it is configured.

Have you right clicked on the network icon at top right and selected "enable wireless"?

Roger

---

### Post by roger_1960 on 2010-11-21
Hi

Could you open a terminal menu>acccessories>teminal

Enter the following

> iwconfig

and post the output here.  We will see if it is configured.

Have you right clicked on the network icon at top right and selected "enable wireless"?

Roger

---

### Post by blenderfox on 2010-11-21
> **roger_1960 said:**
> Hi

Could you open a terminal menu>acccessories>teminal

Enter the following



and post the output here.  We will see if it is configured.

Have you right clicked on the network icon at top right and selected "enable wireless"?

Roger


Here we go:

```
#: iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

```

Re your second point: "Enable Wireless" is not selectable.

---

### Post by blenderfox on 2010-11-22
Can I bump this topic? I'm still no closer to an answer than previously?

---

### Post by roger_1960 on 2010-11-23
Hi again

Sorry, have been travelling for a day!  Its not finding the hardware.  Could you post the output from 
> 
lspci

This will list the hardware in your PC.  We can the search the forums for any issues with this particular hardware.

---

### Post by blenderfox on 2010-11-23
Here you go:

```
yukinom@MOMOKO:~$ sudo lspci
[sudo] password for yukinom: 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
02:06.4 Communication controller: Texas Instruments PCIxx12 GemCore based SmartCard controller
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
08:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

---

### Post by blenderfox on 2010-11-23
In the time it took to get an answer on this, I've been able to find out, by chance what was going on. I had a hard and soft block on my wireless card, which I fixed by doing

```
sudo rfkill unblock 0
```

Where 0 was my wireless card id in the rfkill list. After that, I turned off and on my card and it worked.

---

### Post by roger_1960 on 2010-11-24
Hi again

Glad you solved it. I was about to say that your card - last line in you lspci list - is pretty standard and normally works OK.............

---

### Post by blenderfox on 2010-11-24
Thanks for your help -- you nudged me in the right direction by getting me to check the hardware. :)

---

