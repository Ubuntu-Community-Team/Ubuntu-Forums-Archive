---
title: "ImageClass MFW Scanner"
date: 2015-04-13
forum: Hardware
---

### Post by brian58 on 2015-04-13
Hi all,

I managed to install my Canon imageClass multifunction printer using the Linux drivers available on the Canon website and building a .deb package. The printing works great. However, I was wondering if scanning would work as well. The driver is supposed to be a multifunction driver which includes printer, scanner, and fax drivers all in one. Under Windows I get to name each driver installation as a separate thing so I can identify the printer, scanner, etc. However, under Ubuntu I'm not sure how that works. 

Anyway, there are two ways the scanner can work. It can connect to the computer via USB and I can select the computer as my source from the scanner. It then saves it to a particular location. Otherwise, I can do remote scan which uses remote scanning software which is Windows only to connect to the printer remotely and pull the scans down to the connecting computer.

I know there may be multiple ways to do this such as running Wine (to run the remote scanning software possibly) or even run VirtualBox to run a Windows VM but I figured I'd keep the complications to a minimum especially since I plan on installing a Ubuntu image on FreeNAS as a jail (which further complicates things and not sure how VM's would work in such a situation). Thanks for all the help!

---

### Post by pdc on 2015-04-14
Hi Brian;

you don't mention which Canon MF you have ................. that might have helped a bit!

From here [http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON](http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON) the sane development listing, some are supported

_________---

all the development work to support scanning with sane is done by volunteers; you can see entries that say > Testers are needed! ........ you have the hardware.

If your device is not supported (yet); can I suggest you join the sane development list; they are an energetic and helpful group; you can help them help you 

[http://lists.alioth.debian.org/mailman/listinfo/sane-devel](http://lists.alioth.debian.org/mailman/listinfo/sane-devel)

---

### Post by brian58 on 2015-04-14
I apologize for the oversight. It's the Canon ImageClass MF4890DW Multifunction printer. It's relatively new so it wasn't listed on the supported hardware list. Thanks for the help.

---

### Post by pdc on 2015-04-15
thanks brian;

I would say the 4890 is in the 4800 series; on the sane development list, [http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON](http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON) it says the 4800 is completely supported

__________

one can access this by adding the Rolf Bensch ppa: Rolf maintains the latest sane releases

this link [http://forums.linuxmint.com/viewtopic.php?f=51&t=194081](http://forums.linuxmint.com/viewtopic.php?f=51&t=194081) is from the Mint forum; 2 days ago; details of how to access Rolf's ppa; by using that, it should give you the latest sane...and allow you to run your very fine MF4890

Earl also nicely detailed how to ensure a wireless device is seen 

______

let us know how it goes

---

### Post by brian58 on 2015-04-15
I don't see it listed from the supported model list despite having a Linux printer driver. Maybe I'm missing something? [http://www.sane-project.org/man/sane-pixma.5.html](http://www.sane-project.org/man/sane-pixma.5.html)

I've added the PPA just in case.

---

### Post by pdc on 2015-04-15
Hi Brian

> I don't see it listed from the supported model list 

I was using the sane development listing..............where they seemed to say the MF4800 series was supported;

what does ```
lsusb
``` give ....assuming it is usb-connected............so we can see the ID of your device 

.........I am guessing that what appears in the sane backpage may apply to the stable release...................... but that is a guess............... 

_______________

[http://lists.alioth.debian.org/mailman/listinfo/sane-devel](http://lists.alioth.debian.org/mailman/listinfo/sane-devel)

this is the sane list that anyone can join; 

what does ```
sane-find-scanner
``` and ```
scanimage -L
``` give with your MF plugged in and switched on? Oh, and ```
scanimage -v
```

---

### Post by brian58 on 2015-04-20
could not open USB device 0x8087/0x8001 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 003:001: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc52b at 002:004: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc52b at 002:003: Access denied (insufficient permissions)
could not open USB device 0x04a9/0x2773 at 002:008: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

---

### Post by brian58 on 2015-04-20
It finds the device listed as USB on Port 2: Bus 002 Device 009: ID 04a9:2773 Canon, Inc.

---

### Post by pdc on 2015-04-20
my apologies: I don't know how I misread it but you are right: the MF4890 is not mentioned in the sane listings;

do join the sane development list: they will be glad of your help and they should be able; as you have the hardware; to get it working

---

