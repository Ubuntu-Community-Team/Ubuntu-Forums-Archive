---
title: "usb printer kills usb wifi device"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by nikkkko on 2007-09-20
I have today installed a HP Laserjet 2605 - connected by usb - which I had previously read worked perfectly under linux.  It does, but only at the expense of my Netgear WG121 usb wifi adaptor, (working with ndiswrapper).  Basically, both usb devices power up fine together but as soon as I print a page, I lose my wifi connection.  If I go to console and type 'ndiswrapper -l', I get total freeze and have to pull the plug. I'm also running a wireless keyboard and mouse over usb and these are unaffected when I print.

I previously had a HP psc1315 running over usb and this worked fine alongside my adaptor. Weird.

Any clues would be welcome as I have a lot of printing to do and also need my connection.

---

### Post by jnorthr on 2007-09-20
You may get some further ideas as to the cause of the problem by using a terminal command line to try
dmesg
then scroll to the bottom where you will see more recent messages from the kernel. Also you can check System>Administration>System Log to review several log files that may provide further clues a to the cause of this behavior.

---

### Post by ddrichardson on 2007-09-20
I'd be inclined to change the wireless channel. The new printer is I take it seperately powered, so interference needs to be eliminated by changing channels. Printers and microwaves are surprisingly good at interfering with wireless.

---

### Post by dcstar on 2007-09-21
> **nikkkko said:**
> I have today installed a HP Laserjet 2605 - connected by usb - which I had previously read worked perfectly under linux.  It does, but only at the expense of my Netgear WG121 usb wifi adaptor, (working with ndiswrapper).  Basically, both usb devices power up fine together but as soon as I print a page, I lose my wifi connection.  If I go to console and type 'ndiswrapper -l', I get total freeze and have to pull the plug. I'm also running a wireless keyboard and mouse over usb and these are unaffected when I print.

I previously had a HP psc1315 running over usb and this worked fine alongside my adaptor. Weird.

Any clues would be welcome as I have a lot of printing to do and also need my connection.

The new USB printer device may be drawing more power from the USB port and overloading it with the Wireless device (which are really power hungry - I had to remove an external USB hub to make mine reliable).

Try swapping the USB connections around to see if you can share the power load more evenly.

---

### Post by nikkkko on 2007-09-21
Thanks for the suggestions everyone.

> I'd be inclined to change the wireless channel.
Not only is the connection dropped, but the device itself dies. I think if it were an interference problem I would probably still be able to talk to the device.

> The new USB printer device may be drawing more power from the USB port and overloading it
I read a couple of posts about usb and power problems, however my motherboard has four usb ports as standard and I am only using three for the moment, (I have disconnected the second printer while I try and resolve this issue).  It's possible that the usb setup is underpowered, but short of digging out the technical specs for the motherboard I don't know how I'm going to find out.  Also, surely the printer, which has it's own power source, isn't pulling any more power from usb?

Here's the output of dmesg, starting with neither wifi or printer connected :

1 Connect wifi device
```
[ 8794.621254] usb 3-1: new high speed USB device using ehci_hcd and address 15
[ 8794.753713] usb 3-1: configuration #1 chosen from 1 choice
[ 8794.945088] usb 3-1: reset high speed USB device using ehci_hcd and address 15
[ 8795.086936] ndiswrapper: driver netwg121 (NETGEAR, Inc.,10/16/2003, 0.11.0.1) loaded
[ 8797.188095] wlan0: ethernet device 00:09:5b:a2:96:9a using NDIS driver: netwg121, version: 0xb00, NDIS version: 0x501, vendor: 'NETGEAR WG121 802.11g Wireless USB2.0 Adapter', 0846:4210.F.conf
[ 8797.188161] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[ 8799.190820] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

2 Connect printer
```

[ 8818.044699] usb 3-5: new high speed USB device using ehci_hcd and address 16
[ 8818.179539] usb 3-5: configuration #1 chosen from 1 choice
[ 8818.185536] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 16 if 0 alt 0 proto 2 vid 0x03F0 pid 0x3617
[ 8820.519315] wlan0: no IPv6 routers present

```
3 Hit print

```
[ 8906.229201] drivers/usb/class/usblp.c: usblp0: removed
[ 8920.414668] ndiswrapper (iw_get_freq:327): getting configuration failed (00010003)
[ 8922.413596] ndiswrapper (iw_get_freq:327): getting configuration failed (00010003)
[ 8924.412576] ndiswrapper (iw_get_freq:327): getting configuration failed (00010003)
[ 8926.411561] ndiswrapper (iw_get_freq:327): getting configuration failed (00010003)
[ 8928.411376] ndiswrapper (iw_get_freq:327): getting configuration failed (00010003)
[ 8930.409575] ndiswrapper (iw_get_freq:327): getting configuration failed (00010003)
[ 8932.408593] ndiswrapper (iw_get_freq:327): getting configuration failed (00010003)
[ 8934.407611] ndiswrapper (iw_get_freq:327): getting configuration failed (00010003)
```

From here there's no rescuing the wifi device, both it and the printer must be unplugged and plugged back in again.

---

### Post by ddrichardson on 2007-09-21
That reads like a power saving problem, can you try turning off the power saving and then printing```
sudo iwconfig wlan0 power off
```

---

### Post by nikkkko on 2007-09-21
I've had this box for about 4 years and I've never played with the power saving.  I think there's a power saving option in the bios, which I should be able to switch off.  Is that what you mean?

---

### Post by ddrichardson on 2007-09-21
No switch off the wireless powersaving by the command I gave and try printing.

---

### Post by nikkkko on 2007-09-21
Same result as before - adaptor immediately drops dead, same dmesg output as before.

---

### Post by ddrichardson on 2007-09-21
That eliminates power saving - what happens if you disconnect the third printer?

---

### Post by nikkkko on 2007-09-21
I have only had three devices connected whilst trying to sort this out: wifi adaptor, new printer and a wireless keyboard.

---

### Post by ddrichardson on 2007-09-21
Have you tried changing the wireless channel?

---

### Post by nikkkko on 2007-09-21
Ok, so I changed the channel a couple of times, but with no success.  I also swapped the usb connections around to see if power load could be better balanced, (as someone suggested earlier), but that made no difference either. 

Here's the output of syslog from the point where I connect the printer :
```
Sep 21 13:15:02 whitecube kernel: [16401.380086] usb 3-1: new high speed USB device using ehci_hcd and address 33
Sep 21 13:15:02 whitecube NetworkManager: <debug info>^I[1190373302.675943] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3617_00CNCW7303LP'). 
Sep 21 13:15:02 whitecube NetworkManager: <debug info>^I[1190373302.807404] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0'). 
Sep 21 13:15:02 whitecube kernel: [16401.515682] usb 3-1: configuration #1 chosen from 1 choice
Sep 21 13:15:02 whitecube kernel: [16401.522466] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 33 if 0 alt 0 proto 2 vid 0x03F0 pid 0x3617
Sep 21 13:15:02 whitecube NetworkManager: <debug info>^I[1190373302.876318] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0_printer_noserial'). 
Sep 21 13:15:02 whitecube NetworkManager: <debug info>^I[1190373302.946273] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3617_00CNCW7303LP_if1'). 
Sep 21 13:15:02 whitecube NetworkManager: <debug info>^I[1190373302.987279] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3617_00CNCW7303LP_usbraw'). 
Sep 21 13:15:46 whitecube hpiod: removing usblp driver interface=0 for hp:/usb/HP_Color_LaserJet_2605?serial=00CNCW7303LP io/hpiod/device.cpp 504 
Sep 21 13:15:46 whitecube NetworkManager: <debug info>^I[1190373346.716294] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0_printer_noserial'). 
Sep 21 13:15:46 whitecube kernel: [16445.557775] drivers/usb/class/usblp.c: usblp0: removed
Sep 21 13:15:59 whitecube kernel: [16458.461016] ndiswrapper (iw_get_freq:327): getting configuration failed (00010003)
Sep 21 13:16:01 whitecube kernel: [16460.460104] ndiswrapper (iw_get_freq:327): getting configuration failed (00010003)
Sep 21 13:16:03 whitecube kernel: [16462.459258] ndiswrapper (iw_get_freq:327): getting configuration failed (00010003)
Sep 21 13:16:05 whitecube kernel: [16464.458293] ndiswrapper (iw_get_freq:327): getting configuration failed (00010003)
```

---

### Post by nikkkko on 2007-09-21
Ok, so here's something else.  I printed, lost my adaptor as before, but this time did

```
sudo modprobe -r ndiswrapper
ndiswrapper -l
```

which showed everything ok.  Then

```
sudo modprobe ndiswrapper
```

and my device comes back.

Does that help at all?

---

### Post by nikkkko on 2007-09-21
The more I think about this, the more I remeber how many hours I've lost to ndiswrapper. I am tempted to buy a new pci wifi adaptor but as I have only had a 50% success rate with ndiswrapper, I'm worried I'll end up with another desk ornament.  I would try and buy a natively supported device but I'm in France and the chances of my local retailer knowing which chipset is in which version of the boxes on the shelves are roughly zero.

---

### Post by ddrichardson on 2007-09-21
I'd be inclined to try a powered external USB hub if you can get hold of one.

---

### Post by nikkkko on 2007-09-21
Resisting the urge to buy stuff, I attached  both the printer and adaptor to an unpowered hub to see what would happen.  I can print and remain connected with this setup, although it is not a very elegant solution.

---

### Post by ddrichardson on 2007-09-21
Curious. It must be interference (not the rf emitted from the device type) with the internal USB hub, either that or its the hubs own ability to manage its power.

---

### Post by nikkkko on 2007-09-21
The four built in usb ports are positioned with two at the front and two at the back of the box, and I've tried the devices in different positions so I don't think it's going to be interference.

One thing I notice is that when plugged directly into a usb port, the device will take a number which starts with a '3', no matter which port I use.  E.g.,

usb 3-2: new high speed USB device using ehci_hcd and address 46
or
usb 3-6: new high speed USB device using ehci_hcd and address 14

whereas when I use the hub, it shows up as, 

usb 1-3: new full speed USB device using ohci_hcd and address 4
usb 1-3: configuration #1 chosen from 1 choice
hub 1-3:1.0: USB hub found
hub 1-3:1.0: 4 ports detected
usb 1-3.4: new full speed USB device using ohci_hcd and address 5

I see I am using ohci instead of ehci. Whatever that means.

---

### Post by ddrichardson on 2007-09-21
It wont matter if the ports are in different positions if the problem lies in the host.

OHCI is Open Host Controller Interface, EHCI is Enhanced HCI. Broadly speaking this is equivalent to USB 1.1 and 2.0 respectively.

---

### Post by nikkkko on 2007-09-21
Is it worth pursuing?  I will pursue it if it helps improve stability for other people, but if it's an idiosyncrasy of my setup, then I'll let it go. (And get used to having another wire trailing across my desk).

As you can tell, I am no expert in this area.

---

### Post by ddrichardson on 2007-09-21
I'd say its an idiosyncrasy with your USB hub.

---

### Post by nikkkko on 2007-09-22
I was planning on upgrading to Gutsy next month so I'll wait until then to see what happens.  I have done the smallest amount of scratching around and it seems I'm not alone with this type of problem, but it's not exactly critical.

---

### Post by thruhike98 on 2008-01-08
I am having the exact issue **nikkkko** describes, with a desktop pc.  This is a +/-3 year old Dell, w/ a good deal of ram and processor power running a fresh install of fedora 8.  I'm using a new linksys wireless usb adapter and a new lexmark 5400 printer in two of about seven available usb ports.

Plugging in the printer's usb cable causes a great deal of flakiness.  The wireless connection drops, shutdown doesn't work, if shutdown rebooting is verrrrrrry slow (+/-15 minutes), stalls at login screen and says "...user will be loggedin in -203 seconds," etc.

Unplugging the printer cable fixes all issues.  Does anyone have experience w/ this or know of a fix?  Cheers!

---

### Post by nikkkko on 2008-01-09
As you can see from my last post, I gave up trying to fix this, preferring to work around it with an external hub.  I eventually bought a pci wireless adaptor, ditched the hub and the usb wifi adaptor and now everything is working almost perfectly.

I say, almost, because from time to time I get a usb lock up and can no longer see the printer.  The only remedy for this is a hard reboot, by which I mean I have to shutdown the computer and also switch off the computer mains at the back of the box.  Apparently, even when the computer is off, with the on/off swith in the on position, the usb must be getting some power and retains some kind of setting.  Hard switching off and on again reboots the usb and everything returns to normal.

---

### Post by zipperback on 2008-01-09
Are you using the most current version of the ndiswrapper? If not, perhaps you might want to update your ndiswrapper to the most current version.


[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)


- zipperback
:popcorn:

---

### Post by thruhike98 on 2008-01-09
Thanks for the ideas **nikkkko** and **zipperback**.

**nikkkko**: *"As you can see from my last post, I gave up trying to fix this, preferring to work around it with an external hub."*

I wasn't able to discern that from your last post:
[I]"I was planning on upgrading to Gutsy next month so I'll wait until then to see what happens. I have done the smallest amount of scratching around and it seems I'm not alone with this type of problem, but it's not exactly critical."
[/I]
I did see that you were going to install a new release a month after that last post, and wondered whether that made a difference.

Thanks for mentioning switching off the computer mains at the back of the box - I would not have thought of that.  The ndiswrapper is the current version.  I think I'll try the hub option, and get a powered USB hub.  It seems like this might be more hardware-related than O.S.  Thanks again.

---

### Post by nikkkko on 2008-01-09
**thruhike98**
> I wasn't able to discern that from your last post:
You're right, it wasn't my last post, it was the one before. ;).  In any event, the installation of Gutsy and my buying a pci wifi adaptor happened at the same time so I can't say if Gutsy made a difference on that machine.  However, I am fairly convinced this is an idiosyncrasy of the usb hardware.

My Netgear WG121 usb adaptor now works with native drivers following one of many driver updates and is now happily installed on another computer, running Kubuntu Dapper. I run four boxes in total, two with Ubuntu Gutsy, one with Xubuntu Gutsy and one with Kubuntu Dapper.  On the second of my Ubuntu boxes I recently added a wifi usb adaptor, (rt based), and am having no end of trouble.  There are only two ports - one mouse the other wifi - and the wifi locks up regularly.  Hard re-booting, (I actually have to pull out the plug as there's no on/off switch), is the only way to reset the usb.

That's probably the last usb wifi adaptor I buy.

---

