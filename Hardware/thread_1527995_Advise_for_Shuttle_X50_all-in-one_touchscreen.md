---
title: "Advise for Shuttle X50 all-in-one touchscreen"
date: 2010-07-10
forum: Hardware
---

### Post by Jeff Baxter on 2010-07-10
I am brand new to Linux and Ubuntu (ver 10.04). I am working on a project where we would like our end product to be delivered on a Shuttle X50 all-in-one touchscreen pc running Unbuntu. Does anyone have any experience with this machine and Ubuntu? Below are the specs:


[LIST]
[*]Processor: Intel Dual Core Atom D510 (1.66GHz, 1MB Cache, FSB  667MHz)
[*]Chipset: Intel NM10
[*]Memory: 2x Slot, Support upto 4GB Memory
[*]Audio: IDT92HD81 2.1-Channel Audio CODEC; 2x 2W stereo speakers;  Electret Condenser Microphone
[*]Video: Intel GMA 3150 Graphics Controller
[*]Display: 15.6" WXGA(1366x768) 16:9 Single touch Widescreen LCD
[*]LAN: JMC261 Gigabit Ethernet; IEEE 802.11b/g/n Wireless LAN
[*]Drive Bays: Support 2.5" Hard Drive
[*]Ports: 4x USB 2.0 Ports; 1x VGA Port; 1x RJ45 LAN Port; Audio I/O  Jacks
[*]Camera: Build-in 1.3 Mpixel Web Camera
[*]Card Reader: 4-in-1 Card Reader; Support SD/MMC/MS/MS-pro
[/LIST]

Please let me know if I am bitting off more than I can chew (being a Newbie and all).

---

### Post by Nocturna on 2011-02-21
> **Jeff Baxter said:**
> I am brand new to Linux and Ubuntu (ver 10.04). I am working on a project where we would like our end product to be delivered on a Shuttle X50 all-in-one touchscreen pc running Unbuntu. Does anyone have any experience with this machine and Ubuntu? Below are the specs:


[LIST]
[*]Processor: Intel Dual Core Atom D510 (1.66GHz, 1MB Cache, FSB  667MHz)
[*]Chipset: Intel NM10
[*]Memory: 2x Slot, Support upto 4GB Memory
[*]Audio: IDT92HD81 2.1-Channel Audio CODEC; 2x 2W stereo speakers;  Electret Condenser Microphone
[*]Video: Intel GMA 3150 Graphics Controller
[*]Display: 15.6" WXGA(1366x768) 16:9 Single touch Widescreen LCD
[*]LAN: JMC261 Gigabit Ethernet; IEEE 802.11b/g/n Wireless LAN
[*]Drive Bays: Support 2.5" Hard Drive
[*]Ports: 4x USB 2.0 Ports; 1x VGA Port; 1x RJ45 LAN Port; Audio I/O  Jacks
[*]Camera: Build-in 1.3 Mpixel Web Camera
[*]Card Reader: 4-in-1 Card Reader; Support SD/MMC/MS/MS-pro
[/LIST]

Please let me know if I am bitting off more than I can chew (being a Newbie and all).

Hi there! I have the same one, as far as I can tell most of it should work after a bit of fiddling around. The only thing stumping me is that the JMicron JMC261 controller does not get an ip address after boot (you have to physically disconnect the cable and plug it back in for it to work).

For the touchscreen to work you can follow the following steps: [http://samiux.blogspot.com/2010/07/howto-ubuntu-1004-on-gigabyte-touchnote.html](http://samiux.blogspot.com/2010/07/howto-ubuntu-1004-on-gigabyte-touchnote.html) (minus the i8042.noloop=1 command, you don't need it)

I haven't looked into getting the wireless or webcam working but I'll let you know how far I get with those. The rest works out of the box.

Hope that helps!

Regards,

Rob.

---

