---
title: "Belkin wifi Adaptor PCMCIA and Ubuntu 8.10"
date: 2009-04-07
forum: Hardware
---

### Post by spnoe on 2009-04-07
I tried a friends Belkin Wifi adaptor and after ashort while Ubuntu informed me a third party driver was available and once  downloaded the adaptor worked with out a problem. So spurred on by this I bought a Belkin G notebook card and while the lights come on and it is recognised it does not work. I assume that the chip in my adaptor is different to my freinds.
The model no. is F5D7010. I think it may be version 7. 
Could someone advise me on how to configure this?

Any help much appreciated.

Steve

---

### Post by spnoe on 2009-04-08
Someone informed me that if I install RT2500-Linux-STA-1.4.6.2.tar.gz then my wifi adaptor will work. I have downloded the driver and it is sitting on my desktop. Could some inform me how to install this???

Help much appreciated.

Steve

---

### Post by coffeecat on 2009-04-08
A few comments:

If that Belkin card has the rt2500 chipset then it should simply work out of the box, and that tarball would be unnecessary.

Belkin change the chipset they use every so often without changing the model number. As far as I know, they haven't used the rt2500 chipset for at least a couple of years.

To find which chipset your pcmcia card is using, open a terminal and post the output of:

```
lspci
```

---

### Post by spnoe on 2009-04-08
> **coffeecat said:**
> A few comments:

If that Belkin card has the rt2500 chipset then it should simply work out of the box, and that tarball would be unnecessary.

Belkin change the chipset they use every so often without changing the model number. As far as I know, they haven't used the rt2500 chipset for at least a couple of years.

To find which chipset your pcmcia card is using, open a terminal and post the output of:

```
lspci
```
Thanks for that coffeecat. This is the responcestephen@stephen-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:00.0 Ethernet controller: Belkin Device 701f (rev 20)
stephen@stephen-laptop:~$

---

### Post by coffeecat on 2009-04-08
> **spnoe said:**
> 02:00.0 Ethernet controller: Belkin Device 701f (rev 20)
stephen@stephen-laptop:~$

Oh dear, I thought that might happen. :( We need to dig deeper. Now try;

```
lspci -v
```Dig out the bit about Belkin and post that only. My Belkin PCI card gives:

> 01:05.0 Ethernet controller: Belkin Device 700f (rev 20)
    Subsystem: Belkin Device 700f
    Flags: bus master, medium devsel, latency 32, IRQ 16
    I/O ports at bc00 [size=256]
    Memory at fdeff000 (32-bit, non-prefetchable) [size=512]
    Capabilities: <access denied>
    Kernel driver in use: rtl8180
    Kernel modules: rtl8180but we need to see what driver (if any) is in use for the 701f device.

---

### Post by spnoe on 2009-04-08
> **coffeecat said:**
> Oh dear, I thought that might happen. :( We need to dig deeper. Now try;

```
lspci -v
```Dig out the bit about Belkin and post that only. My Belkin PCI card gives:

but we need to see what driver (if any) is in use for the 701f device.
02:00.0 Ethernet controller: Belkin Device 701f (rev 20)
	Subsystem: Belkin Device 701f
	Flags: bus master, medium devsel, latency 64, IRQ 10
	I/O ports at 1400 [size=256]
	Memory at 24000000 (32-bit, non-prefetchable) [size=512]
	Capabilities: <access denied>
	Kernel driver in use: rtl8180
	Kernel modules: rtl8180

Thank you for your time and help.

---

### Post by coffeecat on 2009-04-08
OK, your system is trying to use the same driver as mine, but whether the actual chipsets are the same is another matter. :?

Actually, I'm having trouble too (I'm using a wired connection atm). I know this card connected just fine before this, but whether it's because I'm using a different wireless router today, or using Jaunty, I don't know.

I've got to go out soon, but when I get back in a couple of hours, I'll experiment in 8.10 and with the router than I am sure does work, and I'll post back.

---

### Post by coffeecat on 2009-04-08
Well - the modem-router I was using three hours ago has been giving me odd problems recently. I've switched to the other, newer one, and both Intrepid (8.10) and Jaunty connect via my Belkin PCI card no trouble at all. As I thought they would. WPA as well. I'm posting now, connecting wirelessly with the Belkin card.

**spnoe**, assuming my and your cards have the same chipset, your card should work out of the box in Ubuntu 8.10. Let's go back to basics. Apart from the autodownloaded driver for the first Belkin device, have you installed anything else for wireless? Have you been doing any tweaking with ndiswrapper, wicd, madwifi or anything else?

You say the notebook card does not work. Have you clicked on the network-manager applet (top-right) to see if it can see your network?

---

### Post by spnoe on 2009-04-08
> **coffeecat said:**
> Well - the modem-router I was using three hours ago has been giving me odd problems recently. I've switched to the other, newer one, and both Intrepid (8.10) and Jaunty connect via my Belkin PCI card no trouble at all. As I thought they would. WPA as well. I'm posting now, connecting wirelessly with the Belkin card.

**spnoe**, assuming my and your cards have the same chipset, your card should work out of the box in Ubuntu 8.10. Let's go back to basics. Apart from the autodownloaded driver for the first Belkin device, have you installed anything else for wireless? Have you been doing any tweaking with ndiswrapper, wicd, madwifi or anything else?

You say the notebook card does not work. Have you clicked on the network-manager applet (top-right) to see if it can see your network?

Yes I downloaded the ndiswrapper and madwifi, in case I needed them and prior to buying this card I did try a USB dongle but could not get that working either.
As for the network manager, yes if I click on this the network is visable and the lights on the card are also eluminated. One light is yellow and flashes the other green and stays on.When I click the network icon top right, it will try to connect and after a while a window will open asking for the passphrase: I have entered this a dozen times and checked the spelling and all is well but still no connection.

I am pleased you have had success with your system.
Steve

---

### Post by coffeecat on 2009-04-08
What I suggest you do is to boot up from the live Ubuntu 8.10 CD and see if you can connect with the pcmcia card running live. The reason I asked you about ndiswrapper, etc is that some or all of those other things may be interfering with network-manager and the working drivers for this card that come with a default install.

If you can connect with the live CD, I'm not sure what the next step would be, but it would be interesting to try.

**Edit:** thanks for being pleased, but I didn't try this for my benefit - it was for you. :wink: I wanted to be sure that this chipset does work with Ubuntu Intrepid - which it clearly does.

---

### Post by spnoe on 2009-04-08
> **coffeecat said:**
> What I suggest you do is to boot up from the live Ubuntu 8.10 CD and see if you can connect with the pcmcia card running live. The reason I asked you about ndiswrapper, etc is that some or all of those other things may be interfering with network-manager and the working drivers for this card that come with a default install.

If you can connect with the live CD, I'm not sure what the next step would be, but it would be interesting to try.

**Edit:** thanks for being pleased, but I didn't try this for my benefit - it was for you. :wink: I wanted to be sure that this chipset does work with Ubuntu Intrepid - which it clearly does.

I will try as you suggest and thank you so much for your time,effort and patience. I do appreciate your help. Thank you.

Steve

---

### Post by spnoe on 2009-04-08
> **spnoe said:**
> I will try as you suggest and thank you so much for your time,effort and patience. I do appreciate your help. Thank you.

Steve

Just for your interest I tried the Ubuntu boot disk and it still did not work.

---

### Post by coffeecat on 2009-04-08
I'm sorry to hear it. Perhaps you could search the forums for rtl8180 - someone may have an answer to this. If I come across something, I'll post it.

Alternatively, is there another wireless network you can try? By doing that you'd be trying to connect to a different (hopefully) make of network access point. I'd heard of odd incompatibilities before between wireless nic and wireless routers - that may be what's going on. Witness my experience today. I couldn't connect to my old Linksys router, but the newer one was OK. Despite the fact that I'm using the same SSID, same WPA passkey and same wireless channel on both. (Obviously only one at a time.) All very odd.

---

