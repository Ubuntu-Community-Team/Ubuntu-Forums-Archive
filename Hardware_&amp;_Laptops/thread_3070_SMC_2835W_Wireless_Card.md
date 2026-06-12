---
title: "SMC 2835W Wireless Card"
date: 2004-11-03
forum: Hardware &amp; Laptops
---

### Post by kmf on 2004-11-03
I recompiled my kernel for monitor support in kismet
When I insert my card (the SMC) ... it asks for firmware.
So ... it worked in the stock kernel ... I know how to get it working with Slackware.

But how will it work with my recompiled kernel?

Karl

---

### Post by kmf on 2004-11-04
My SMC requires firmware which is currently located in /lib/hotplug/firmware/
Since my firmware, cannot be compiled I need to add is somehow for my card to work.

So I copied my orginal firmware file "isl3890" to /lib/hotplug/firware/.
And Ta-Da it worked then
I checked summed my orginal file and the one that came with Ubuntu
The Checksum was the same.

And so it worked

Karl

---

### Post by anklator on 2004-11-07
i got really weird problems with that card, i think it must be something with iwconfig or powersaving, it loads correctly the firmware, but when it tryes to link with the acces point, both lights go off, on gentoo i have similar problem, but power only goes off ramdonly for 3-10 secs, and then it returns again just enough for my mule and messenger, but what makes me go mad is that it works perfect on winbug$ #-o 

heeeelp

pd: i forgot, on gentoo i use my custom kernel, at first i though that i did something bad, but after seeing that when i use ubuntu it doesnt even work(and kernel is a prebuilt one) iget mad!

---

### Post by kmf on 2004-11-08
hmm did you type dmesg in a shell somewhere, 
**My card does that only when it can't find a access point.**

btw my card worked out of the box(tm) with ubuntu.

Let's wait a while and see who else posts. :)

---

### Post by anklator on 2004-11-08
by the way, can u tell me if u had the card inserted when u installed ubuntu, and if it was inserted, did ubuntu detected as a network interface during the installation?

thanks

---

### Post by kmf on 2004-11-09
No I inserted it after installation.
Remeber unlike Windows, the Linux  kernel would have most of the drivers allready "installed" by default (Not really installed) so when you insert the card the kernel picks it up and loads the right driver(module) for it.

So it doesn't matter if the card was plugged in or not.
We know the Ubuntu Kernel has the Driver. We just need to figure out why it's not working for you.

Karl

---

### Post by anklator on 2004-11-09
i think i spotted the problem;):

Loaded prism54 driver, version 1.2
PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 5 (level, low) -> IRQ 5
eth1: islpci_open()
eth1: resetting device...
eth1: uploading firmware...
eth1: firmware uploaded done, now triggering reset...
eth1: expecting oid 0xff020003, received 0x2009806.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x10000002, received 0x19000001.
eth1: timeout waiting for mgmt response
eth1: Out of memory, cannot handle oid 0x00000400
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: Out of memory, cannot handle oid 0x00000300
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0xff020003, received 0x12000007.
eth1: timeout waiting for mgmt response
eth1: mgt_commit has failed. Restart the device
eth1: no IPv6 routers present

either the firmware is corrupt(i dont think so), or it tryies to use ipv6 protocol(my network is ipv4), it happens same with wired network, i ll try to reinstall ubuntu connected to the net, and i ll give a try again
 :-({|=

---

### Post by anklator on 2004-11-09
After reinstalling ubuntu, and leaving all confs as they are i get this:
ACPI: Battery Slot [BAT1] (battery present)
ACPI: AC Adapter [ACAD] (on-line)
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ACPI: Lid Switch [LID]
mtrr: 0xf0000000,0x4000000 overlaps existing 0xf0000000,0x80000
Loaded prism54 driver, version 1.2
PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 5 (level, low) -> IRQ 5
eth1: islpci_open()
eth1: resetting device...
eth1: uploading firmware...
eth1: firmware uploaded done, now triggering reset...
eth1: expecting oid 0xff020003, received 0x2009806.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x10000002, received 0xff020003.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x12000002, received 0x10000002.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x12000007, received 0xeedbc04b.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0xff020003, received 0x12000007.
eth1: timeout waiting for mgmt response
eth1: mgt_commit has failed. Restart the device
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: Out of memory, cannot handle oid 0x00000200
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x17000013, received 0x0.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1a000002, received 0x0.
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: no IPv6 routers present
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x16000003, received 0x17000013.
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1c000042, received 0x0.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x10000001, received 0x1c000042.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x17000013, received 0x0.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x16000003, received 0x0.
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x17000013, received 0x0.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1a000002, received 0x0.
eth1: timeout waiting for mgmt response
eth1: Out of memory, cannot handle oid 0x55cfc8c6
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x17000013, received 0x0.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1a000002, received 0x0.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1c000042, received 0x16000003.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x10000001, received 0x1c000042.
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1a000002, received 0x16000003.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1c000042, received 0x3edac046.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x10000001, received 0x1c000042.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x17000013, received 0x0.
eth1: timeout waiting for mgmt response
eth1: islpci_close ()
eth1: islpci_open()
eth1: resetting device...
eth1: uploading firmware...
eth1: firmware uploaded done, now triggering reset...
eth1: expecting oid 0xff020003, received 0x0.
eth1: timeout waiting for mgmt response
eth1: Out of memory, cannot handle oid 0x455cc352
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x12000002, received 0x10000002.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x12000007, received 0x0.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0xff020003, received 0x12000007.
eth1: timeout waiting for mgmt response
eth1: mgt_commit has failed. Restart the device
eth1: expecting oid 0x1c000042, received 0x0.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x10000001, received 0x1c000042.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x17000013, received 0x16000003.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1a000002, received 0xdac8c04a.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1c000042, received 0x0.
eth1: no IPv6 routers present
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x17000013, received 0x0.
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x17000013, received 0x0.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1c000042, received 0xc1db204a.
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x17000013, received 0xdac8c04a.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x16000003, received 0x17000013.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1a000002, received 0x16000003.
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: Out of memory, cannot handle oid 0x9e20c85b
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1a000002, received 0x0.
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: Out of memory, cannot handle oid 0x9e20c85b
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x17000013, received 0x0.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1a000002, received 0x0.
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: Out of memory, cannot handle oid 0x95a0c85b
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x17000013, received 0x0.
eth1: timeout waiting for mgmt response
eth1: Out of memory, cannot handle oid 0x9730c68e
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1c000042, received 0x0.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x10000001, received 0x1c000042.
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1c000042, received 0x0.
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x17000013, received 0x0.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x16000003, received 0x17000013.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1a000002, received 0x0.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1c000042, received 0x0.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x10000001, received 0x1c000042.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1c000042, received 0x0.
eth1: timeout waiting for mgmt response
eth1: Out of memory, cannot handle oid 0x9420c85b
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1a000002, received 0x5bcf204a.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1c000042, received 0x1a000002.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x10000001, received 0x1c000042.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1a000002, received 0x30c10000.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x1c000042, received 0x7eda4041.
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x10000001, received 0x1c000042.
eth1: timeout waiting for mgmt response
eth1: Out of memory, cannot handle oid 0x06d550bf
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response
eth1: expecting oid 0x16000003, received 0x0.
eth1: timeout waiting for mgmt response
eth1: errant PIMFOR application frame
eth1: timeout waiting for mgmt response 1000, triggering device
eth1: timeout waiting for mgmt response

my mainboard??  it says running not 100% native mode when i boot

---

### Post by anklator on 2004-11-09
i just solved it while i was tweaking powersave, i read in this forums that powernow-k7 doesnt load by default, so i added to /etc/modules, and now it works, the only problem is that i have to write everytime i boot

ifconfig eth0 up && dhclient eth0, and that is too boring...

---

### Post by kmf on 2004-11-10
Dude
This is good news.
Hmm can't you setup that up via the Network Tools? 
I'm sure it will make your life easier :)

But luckily the card works now :)

Karl

---

### Post by anklator on 2004-11-10
the network config freezes when i try to save & exit, i was thinking in a initscript, but.. :D  its working, and that is good ;)

---

### Post by kmf on 2004-11-10
Mine does it as well.
But it's still working.

Karl

---

### Post by Razvan on 2004-11-19
[QUOTE=kmf]Mine does it as well.
But it's still working.

Karl[/QUOTE]
 the network config tool just looks like freezing...it tries to ifup all the devices...that just takes some time

---

### Post by kmf on 2004-11-20
I guess the fact that "Force Quit" comes up means nothing. ;)
This is reproducable but it only sometimes wants to "Force Quit" 

Karl

---

