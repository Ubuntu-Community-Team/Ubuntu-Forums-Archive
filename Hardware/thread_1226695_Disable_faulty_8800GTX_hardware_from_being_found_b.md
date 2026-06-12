---
title: "Disable faulty 8800GTX hardware from being found by Ubuntu Linux"
date: 2009-07-29
forum: Hardware
---

### Post by dsplabs on 2009-07-29
I use Dell M1730 XPS laptop. It comes with dual 512MB NVIDIA GeForce 8800M GTX SLI cards. For a long time these worked flawlessly under Windows XP, Windows Vista and Ubuntu Linux, with or without SLI mode enabled (and with NVIDIA drivers). Recently, however, the laptop screen just goes blank after NVIDIA drivers get loaded (i.e. with the drivers that worked previously). Same issue happens under both Linux and Windows! I have traced this down to the second SLI card being faulty. The fault happens when the second card gets initialised by the driver. The first card works fine. Dell is going to replace the faulty hardware, but apparently there is a "world wide shortage of 8800M GTX cards" (so I was told by Dell support) and thus it will take quite some time before they fix it.

In the mean time, under Windows my fix was to simply boot into safe mode, go to device manager, disable the second card, boot windows normally and then install NVIDIA driver. This works fine, 3D and all. My question is how do I do this under Ubuntu Linux. Modules can be disabled in /etc/modprobe.d/blacklist.conf, however, that won't work for me as I want to use NVIDIA module for the first card but not for the second card. I need to somehow prevent the system from registering the second card or get the NVIDIA driver to fully ignore it. The cards register on two different addresses on the PCI bus. Any ideas on how to get Linux to ignore the second card?

---

### Post by Shibblet on 2009-07-29
> **dsplabs said:**
> Any ideas on how to get Linux to ignore the second card?

Physically take it out, then you don't have to worry about any Operating System recognizing it.

---

### Post by dsplabs on 2009-07-29
Hi Shibblet, if it was a desktop PC that would be the way to go, but with a laptop it is a lot tougher. I would have to pull the whole thing apart to get to the display cards and then put it all back together (this would be quite painful -- the laptop is huge! I have seen a Dell technician replace a motherboard on one of these, it is involved; plus the warranty could then be considered void).

It must be possible to disable a PCI bus device under Linux, I mean come on... it is possible under windaz :P

BTW, this is how the blacklisting is done: [http://thoughtsbyclayg.blogspot.com/2008/01/ubuntu-disable-hardware.html](http://thoughtsbyclayg.blogspot.com/2008/01/ubuntu-disable-hardware.html)

I also have found this: [http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17834.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17834.html) info on how to unbind PCI based USB device. I'll have a look if that would work for the NVidia card. I suppose this would have to be done after the device get detected during boot but before the NVidia driver gets loaded :S

---

