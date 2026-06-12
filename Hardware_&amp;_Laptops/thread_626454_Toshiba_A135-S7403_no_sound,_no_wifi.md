---
title: "Toshiba A135-S7403 no sound, no wifi"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by asplodzor on 2007-11-29
Hey there everyone, I'm a several-hours old linux user and I've run into a couple problems trying to install Ubuntu on my new laptop.

Problem # 1: No sound

As far as I can understand, Ubuntu is not seeing my soundcard. I've tried to follow the steps outlined here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and here: [http://ubuntuforums.org/showthread.php?t=539595](http://ubuntuforums.org/showthread.php?t=539595) but am getting stuck trying to run the command:

```
sudo ./configure --with-cards=hda-intel 
```

When I type it in, I get this returned:

```
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

So far as I understand it, this is a problem with make and not an issue with my soundcard configuration, though the fact that typing aplay -l returns device_list:204: no soundcards found... indicates to me that make isn't my only problem.

Problem # 2: No Wifi

lspci returns:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

Here's ifconifig:
```
eth0      Link encap:Ethernet  HWaddr 00:1B:38:4A:34:93  
          inet addr:192.168.7.59  Bcast:192.168.7.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe4a:3493/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5385 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8591148 (8.1 MB)  TX bytes:837023 (817.4 KB)
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

I've poked around the forums for a while and tried googling the problem, but have not found a solution. Any suggestions?

Much thanks in advance.

---

### Post by asplodzor on 2007-11-29
Oh, perhaps I should add that my on-board wireless card is a Atheros AR5006EG, and that my lshw -C network output is: ```
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:4a:34:93
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.7.59 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
```

---

### Post by Defrector on 2007-11-29
This might sound silly, but have you tried running "sudo apt-get upgrade" and after updating completely shutting down the machine and restarting it?

I had the same problem with sound and wifi (tonight actually) installing fresh to Toshiba laptop and after running updates the sound didn't kick in until I cold-booted. It's important that everything is updated first though.

As for the wifi, I am in the same boat. It sees it in the PCI but iwconfig says 'no wireless extensions.' NDIS drivers/restricted drivers don't seem to be solving the problem.

---

### Post by Defrector on 2007-11-29
Regarding the wifi:

First use 

ndiswrapper -l 

then... 
ndiswrapper -r [whatever the driver name mentioned using the previous command]

to make sure you current driver is cleared out. I don't know if it causes problems but I doubt it solves any being there.


Check this out:
[http://ubuntuforums.org/showthread.php?t=512828&highlight=HOWTO+wifi+blacklist+ath_pci](http://ubuntuforums.org/showthread.php?t=512828&highlight=HOWTO+wifi+blacklist+ath_pci)

Then this:
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)
... if you have a WPA secure network, it can look like you don't have a detectable network at all unless you get WPA support going. (and can give the impression that the interface or driver isn't working)

It seems to be fixing at my end; hope it helps the same, or at least gives good clues.

---

### Post by art.by.bec.com on 2007-12-01
i have a new toshiba laptop too.
I just got sound going with info from another discussion on the forum, but i dont know how to get my mic, internal cam and memory stick slot to be functional. Anyone know???? Thanks bec

---

### Post by Tedificator on 2007-12-03
Ack, I have the same computer and the same problem, unfortunately, I'm new to linux.

I've tried a few fixes that had worked for other computers (in particular, the other A135's) but I didn't have much luck.

I've tried the "complete guide" that has been bumped up on this forum, didn't work for me, but I believe I must have done something wrong.

good luck!  we're all in this together!  Please, please let me know if you get it to work :KS, and how.

-Tedificator

extra observation below:
What's weird is that right now ubuntu senses the volume dial (when I scroll it, the screen shows the speaker icon,  Maybe it was like that fresh, maybe it's something I've done, I dunno.  I've spent 2 whole days learning about ubuntu/linux now and I'm ready to take a break and get back to school work.

---

### Post by Tedificator on 2007-12-05
I haven seen anybody on this forum get this specific model to work.  If you did, did you please tell me 
(us) know which how-to you used?

-A real noob

---

### Post by prog101 on 2007-12-05
hi guys, 

I got a new one yesterday, and have so far got sound and wifi working.
The following posts are very useful.

[http://ubuntuforums.org/showthread.php?t=572541](http://ubuntuforums.org/showthread.php?t=572541)
[http://ubuntuforums.org/showthread.php?t=590093](http://ubuntuforums.org/showthread.php?t=590093)

I have to now set up the mic to get skype running.
Also, it is now restarting automatically, though still shutdown and manual poweron still works.

I also got virtualbox running inside ubuntu, and windows XP runs well as a virtual machine. I used some online tutorials to get it done and needed minimal tweaking.

cheers,
prog

---

### Post by Tedificator on 2007-12-06
Hurray!!

Thanks prog!  That's very good news.  Keep me updated, as I will be dedicating full time to getting ubuntu to work on this laptop after I'm done with finals.

---

### Post by jsharkey on 2007-12-21
Hey all, just a heads up that I've been working on this same exact laptop with Gentoo linux.  I've detailed everything I've done over at the Gentoo wiki.

[http://gentoo-wiki.com/HARDWARE_Toshiba_Satellite_A135](http://gentoo-wiki.com/HARDWARE_Toshiba_Satellite_A135)

The guide above talks about using ndiswrapper for the built-in wireless, but there is a brand new patch to madwifi that makes it work with the build-in Atheros wireless.  Here's a link to the patch:

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

Also to get sound working I had to play with latest unstable ALSA (kernel module, not compiled in), and I had to use "model=lenovo" to get the sound to auto-detect when I plugged in my headphones.  With the default configuration it would otherwise ignore when I plugged in headphones.

---

