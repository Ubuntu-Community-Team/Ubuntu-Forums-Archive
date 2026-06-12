---
title: "Unrecognized Wifi Card - Presario V2000"
date: 2006-03-06
forum: Hardware &amp; Laptops
---

### Post by al_erola on 2006-03-06
Just bought a Compaq Presario v2000 with 1.5GB Celeron M.  It was priced well and based on success I read about with Ubuntu, I thought it would work.

PROBLEM
The laptop will not recognize the DWL-G630 card at all.  It doesn't show up on lspci, it does generate a message in /var/log/messages or dmesg when installed.  When in stalled the link light blinks every 3 seconds.  No other response.

Here's what I've done:
Added a Wifi card D-Link DWL-G630 and it works with Windows XP.
Resized NTFS Partition and installed Linux (Suse, Mandriva, Fedora Core 4, and finally Ubuntu).  Each install works very cleanly, internal LAN card works fine.  All the major distros have the bugs worked out.

Then I tried to install the Wifi card using madwifi, linuxant, and ndiswrapper.  Error message:  no device to attach to this driver. 

So how do I diagnose the problem?  I'm pretty sure it has to do with the IRQ.  In Windows the same IRQ 20 is assigned to LAN, Wifi and modem.

I cannot disable PnP BIOS setting on the BIOS, it has very few options.

---

### Post by al_erola on 2006-03-08
Memorandum for Record

I solved this one by further searching.  Apparently this is a bug in the Ubuntu kernel and others around handling pcmcia cards.  

The temporary workaround is to add the string "pci=assign-busses" to the end of the line of kernel start-up options in /boot/grub/menu.lst (if you use grub).

Check this line every time you install a kernel upgrade since you have to add the string manually.

After that I used an excellent tutorial on setting up ifplugd and wpasupplicant. [http://www.vollink.com/gary/deb_wifi.html](http://www.vollink.com/gary/deb_wifi.html)

Thanks for all you help al.
You're welcome :)

---

