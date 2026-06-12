---
title: "Motherboard Asus M5A97 EVO R2.0 Compatibility?"
date: 2013-06-10
forum: Hardware
---

### Post by Simon G Best on 2013-06-10
Hello!

I'm considering using the [Asus M5A97 EVO R2.0]("http://uk.asus.com/Motherboards/AMD_AM3Plus/M5A97_EVO_R20/") motherboard, and was wondering what, if any, compatibility problems there might be with Ubuntu.

I'm particularly interested in the USB 3.0 ports at USB 3.0 speeds, and am also interested in the eSATA and IEEE 1394 ports as well.  I don't want to buy a motherboard that has ports that aren't going to work in practice.  While I'm unlikely to ever use the IEEE 1394 ports, and am unlikely to use the eSATA ports either, I'm intending to use the USB 3.0 ports.

(Yes, I've searched these forums, but not very successfully.)

I gather there have been problems with ASMedia USB 3.0 ports in the past.  I've searched for up-to-date information, but haven't found anything that clearly confirms that there aren't any such problems.  I haven't even managed to determine which specific USB 3.0 controllers are used, except that they're ASMedia controllers.  The only ASMedia USB 3.0 controller I could find on ASMedia's website is the ASM1042.

The motherboard manual indicates that the eSATA controller is an ASMedia ASM1061, which is consistent with the fact that that's what's on ASMedia's website as their eSATA controller.  The IEEE 1394 controller is a VIA 6308P.

Does anyone have relevant experience with this motherboard?  Can anyone kindly link to anything confirming compatibility or problems with this motherboard, especially in relation to the USB 3.0 ports?  Links regarding the eSATA and IEEE 1394 ports would also be appreciated.

Thank you!

Simon

---

### Post by MrBackhand on 2013-06-10
I use this motherboard in my Mythbuntu 12.04 setup as my living room HTPC.  The only problem I had with it was the RTL8189 driver that I had to blacklist and install the RTL8188 driver or the gigabit network would drop regularly, especially when copying larger files across the network.    I am only using two USB connections, one for a Bluetooth adapter for a mouse and keyboard for remote access and the other a Cideko Air Keyboard Conqueror 2.4GHz adapter that is also used as a controller & keyboard.  I am using multiple SATA hard drives but not in a RAID setup and the speed and compatibility is great.  Two of the hard drives are IDE/PATA with converters to SATA and they are fast enough to record one program while watching another.

Hope this helps!

---

### Post by Simon G Best on 2013-06-11
> **MrBackhand said:**
> The only problem I had with it was the RTL8189 driver that I had to blacklist and install the RTL8188 driver or the gigabit network would drop regularly, especially when copying larger files across the network.

Thanks for your post!  After a bit of searching, I gather this has been a common problem with the RealTek RTL8111F ethernet controller.  I'm intending to use at least Ubuntu 13.04, so I'm hoping such problems have since been fixed.  But at least such problems can be solved if not already fixed in Ubuntu.

> I am only using two USB connections, one for a Bluetooth adapter for a mouse and keyboard for remote access and the other a Cideko Air Keyboard Conqueror 2.4GHz adapter that is also used as a controller & keyboard.

It's specifically the USB 3.0 ports (two blue ones on the back panel) I'm concerned about, since I'm intending to use USB 3.0 devices with them at USB 3.0 speeds.  Though I will be using a USB keyboard and mouse as well, through the USB 2.0 ports.

> I am using multiple SATA hard drives but not in a RAID setup and the speed and compatibility is great.

I'm guessing that's the internal SATA ports?  It's the (two, red) eSATA ports on the back panel I'm concerned about, though only because I might one day wish to use external eSATA devices.

Anyway, it's good to know that the motherboard generally works well.

Thanks again for your post!

---

