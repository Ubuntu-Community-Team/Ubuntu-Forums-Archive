---
title: "Toshiba Satellite U405D-S2852 - no network devices found"
date: 2008-09-30
forum: Hardware
---

### Post by Objekt on 2008-09-30
Booting the Kubuntu 8.04.1 64 bit Live CD on the Toshiba Satellite U405D-S2852, everything went well until I got to the desktop and found that Kubuntu detected NO networking devices of any kind.  Not even the wired NIC.

I really need to get the wireless networking device functional; else, I'll have to try another flavor of Linux.

I don't know what wireless chipset, or wired NIC, this computer has.  It's not specified in the documentation as far as I've seen, though the brand  might be visible in the BIOS menu.  The computer isn't mine; it belongs to someone in another city, so I can't check now.

---

### Post by lisati on 2008-09-30
From the terminal (on the Applications->accessories menu), you could type in ```
lspci | grep Ethernet
``` to see some of the network devices that are there (if they are recognized).
The "lspci" is a useful command for discovering what hardware your copy of Ubuntu recognizes.

---

### Post by jcathey on 2008-09-30
Your wired card is most likely a marvel yukon ethernet controller.  And if you have a newer toshiba laptop your wireless is most likely atheros possibly 5007eg.  Google for specs for your laptop via its model number.

If you need your wired card up, then follow these steps.

Run all of this as root user by entering sudo before each command.

# rmmod sky2 (it is ok if this does not show as inserted)
# cd /lib/modules/2.6.24-16-generic/kernel/drivers/net (the 2.6.24-16-generic folder might vary in number depending on your kernel)
# cp -p sky2.ko{,.orig}
# perl -pe 's/\0\0\x6c\x43/\0\0\x55\x43/g' sky2.ko.orig > sky2.ko

After doing these commands run the following command to insert the sky2 module:

modprobe sky2

This should have your card up and running, but when you reboot you will have to run modprobe sky2 again unless you add "sky2" to the end of the /etc/modules file.

This worked great for me and if you need to know how to get the atheros 5007eg wireless card working if you have that one i can help with that too.

I hope this helps,

Jeremy

---

### Post by Objekt on 2008-10-02
Thanks.  Guess I'll print this out, or boot into Vista to access the forums next time I'm there.

---

### Post by pashabear on 2008-10-03
> **jcathey said:**
> Your wired card is most likely a marvel yukon ethernet controller.  And if you have a newer toshiba laptop your wireless is most likely atheros possibly 5007eg.  Google for specs for your laptop via its model number.

If you need your wired card up, then follow these steps.
...

Thanks for that info, I'll be using it to get my wired connection working once I get this machine properly sorted out (just got it, on the road).  

Here are the specifics of the Network adapters:
Atheros AR5007EG Wireless Network Adapter
Marvell Yukon 88E8040T PCI-E Fast Ethernet Controller

Cheers!
Pashabear

---

### Post by karellen on 2008-10-03
[http://www.marvell.com/drivers/search.do](http://www.marvell.com/drivers/search.do) - they do offer drivers for Linux :)
(I have the same network adapter on my Satellite)

---

### Post by pashabear on 2008-10-03
Thanks for the info on the wired connection.

I found this page helpful for the wireless, even though it's referring to Feisty:

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

From there you can find the driver to use with the ndiswrapper

[http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

That's the 64-bit driver, so I think you'd need to be running a 64-bit OS - someone correct me if I'm wrong, excuse my ignorance!

Good luck!
pb

---

### Post by pashabear on 2008-10-04
Interesting, I just downloaded the beta of Intrepid (AMD64 version), looks nice.  When I booted into it I didn't have any connection, even though it seemed to recognize both the wired and wireless devices.  I don't have a wired connection, but couldn't get the wireless working either.  It says it has a driver for the wireless card, but when I click on the network icon it only shows the wired connection (which isn't plugged in, of course).  Any ideas?
pb

---

### Post by shane2peru on 2008-10-12
> **jcathey said:**
> Your wired card is most likely a marvel yukon ethernet controller.  And if you have a newer toshiba laptop your wireless is most likely atheros possibly 5007eg.  Google for specs for your laptop via its model number.

If you need your wired card up, then follow these steps.

Run all of this as root user by entering sudo before each command.

# rmmod sky2 (it is ok if this does not show as inserted)
# cd /lib/modules/2.6.24-16-generic/kernel/drivers/net (the 2.6.24-16-generic folder might vary in number depending on your kernel)
# cp -p sky2.ko{,.orig}
# perl -pe 's/\0\0\x6c\x43/\0\0\x55\x43/g' sky2.ko.orig > sky2.ko

After doing these commands run the following command to insert the sky2 module:

modprobe sky2

This should have your card up and running, but when you reboot you will have to run modprobe sky2 again unless you add "sky2" to the end of the /etc/modules file.

This worked great for me and if you need to know how to get the atheros 5007eg wireless card working if you have that one i can help with that too.

I hope this helps,

Jeremy

This worked!!!  Thanks!!!  My system has this ethernet card: ```
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4355 (rev 12)
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 508
	Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at a000 [size=256]
	Capabilities: [48] Power Management version 3
	Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [c0] Express Legacy Endpoint IRQ 0

```  Also on a Toshiba Satellite new laptop.  Thanks for this info.

Shane

---

### Post by Foxie299 on 2008-10-24
Thanks for the code.  I typed it all in, but when I got to the last line, I got, 'bash: permission denied'.  What do I need to do to get it to work? 

Perhaps more importantly, is it worth me doing all this, or should I wait until Intrepid comes out in a week or so?

Thanks in advance

---

### Post by shane2peru on 2008-10-24
> **Foxie299 said:**
> Thanks for the code.  I typed it all in, but when I got to the last line, I got, 'bash: permission denied'.  What do I need to do to get it to work? 

Perhaps more importantly, is it worth me doing all this, or should I wait until Intrepid comes out in a week or so?

Thanks in advance

This needs to be run like this:
```

sudo rmmod sky2 
```
```

cd /lib/modules/`uname -r`/kernel/drivers/net 

```
```
sudo cp -p sky2.ko{,.orig}
```
```
sudo perl -pe 's/\0\0\x6c\x43/\0\0\x55\x43/g' sky2.ko.orig > sky2.ko 
```
for the best results you should copy and paste them into the terminal to avoid typos.  
Then you will need to run:
```

sudo modprobe sky2
```

---

### Post by hwlinux on 2008-11-07
> **jcathey said:**
> . . .and if you need to know how to get the atheros 5007eg wireless card working if you have that one i can help with that too.

I hope this helps,

Jeremy

Hi, I would like that information if you could.

Thanks,

HW
:guitar:

---

### Post by Objekt on 2008-11-08
> **pashabear said:**
> Thanks for the info on the wired connection.

I found this page helpful for the wireless, even though it's referring to Feisty:

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

From there you can find the driver to use with the ndiswrapper

[http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

That's the 64-bit driver, so I think you'd need to be running a 64-bit OS - someone correct me if I'm wrong, excuse my ignorance!

Good luck!
pb

Correct.  Important note: you do NOT need to compile ndiswrapper if you're running Kubuntu 8.10 Intrepid Ibex.  ndiswrapper is in the repository, so you can simply run Adept Installer to install ndiswrapper.

That was key for me, because the compile instructions given in that thread simply don't work on my Satellite.  I have no idea how compiling things works in general, and have yet to do it successfully.

For what it's worth, somehow I've managed to enable the wireless networking on the titular Toshiba Satellite U405D-S2852.  At least, the wireless adapter shows up, and I can see some nearby networks.  Unfortunately, they're all password-protected, so I can't actually connect to anything to make sure it REALLY works.

---

