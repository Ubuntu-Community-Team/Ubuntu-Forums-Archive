---
title: "I see WIFI but cannot connect... xp lets me though"
date: 2008-10-06
forum: General Help
---

### Post by Deten on 2008-10-06
I am trying to connect to a wireless network, and while I am booted in XP it works fine, however if I am in ubuntu it just sits there trying to connect and never does.

I am new to wifi stuff, so I am using standard ubuntu settings and whatnot.  Is there a better software module better for connecting to wireless? 

I saw other people having the same problem and mention "ndiswrapper" and "wicd"... I dont know what these are nor how to use them.

---

### Post by Titan8990 on 2008-10-06
Post the outputs for the following commands:

lspci


iwconfig

---

### Post by Aximilli on 2008-10-06
also, what, if any, encryption is the network your trying to connect to using?

---

### Post by Deten on 2008-10-06
> **Aximilli said:**
> also, what, if any, encryption is the network your trying to connect to using?

None, and to clarify, I can use wireless with ubuntu... this is the only one I cannot connect to.

---

### Post by Deten on 2008-10-06
> **Titan8990 said:**
> Post the outputs for the following commands:

lspci


iwconfig

lspci
```
deten@deten-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
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
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
```

iwconfig
```
deten@deten-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Belkin_Pre-N_604146"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:24:F7:E3   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Titan8990 on 2008-10-06
Wireless "N" is not yet an IEEE standard. What this means is a Linksys Wireless N router can be fairly different from a Belkin Wireless N router. What this means is that if you buy a Belkin N wireless router you should also by a Belkin N reciever.

I think the issue you are having here is an incompatibility issue with the Intel card and the Belkin N router.

---

### Post by Deten on 2008-10-06
> **Titan8990 said:**
> Wireless "N" is not yet an IEEE standard. What this means is a Linksys Wireless N router can be fairly different from a Belkin Wireless N router. What this means is that if you buy a Belkin N wireless router you should also by a Belkin N reciever.

I think the issue you are having here is an incompatibility issue with the Intel card and the Belkin N router.

Its not a Belkin N router, its "pre-N" meaning abg or whatever.  

Furthermore, if it was N then my xp computer wouldnt be connecting because I dont have N compatability.

Could this be a software problem?

FYI: I am currently booted in XP and posting off that Belkin pre-N router.

---

### Post by Deten on 2008-10-06
bump for help :(

---

### Post by fragos on 2008-10-06
The Intel WiFi chip in your machine is one of the best supported by Linux. No special configuration or drivers are needed. I believe your issue is with the "pre-N" router. I have no problems connecting to dozens of different access points with a laptop that has the same chip as yours.

---

### Post by Deten on 2008-10-07
> **fragos said:**
> The Intel WiFi chip in your machine is one of the best supported by Linux. No special configuration or drivers are needed. I believe your issue is with the "pre-N" router. I have no problems connecting to dozens of different access points with a laptop that has the same chip as yours.

Its so strange that it would work with windows but not with ubuntu.  By pre-N I mean its A,B or G compatable... 

There has to be some way to get this running!

---

### Post by fragos on 2008-10-07
I haven't had any luck looking up that Belkin router. Not all routers are created equal. For example the FON router for example doesn't support the WiFi power saving protocol on my Nokia N810. What I would suggest is that you try some different routers to see if they work. I assume you have a laptop so finding free access is easy. Even without an account you can make the initial access the AT&T access points used at Starbucks. That would be enough to prove it works.

---

### Post by Deten on 2008-10-08
Any suggestion would be very appreciated.

---

