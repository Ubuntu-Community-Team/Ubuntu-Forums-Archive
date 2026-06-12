---
title: "Feisty + Bluetooth Printing?"
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by IntuitiveNipple on 2007-05-25
I'm having problems trying to print via Bluetooth on Feisty 32-bit.

I've installed the Bluez bluetooth stack and tools, as well as the gnome-applet, gnome-obex-server and so forth. I've successfully transferred files from a mobile phone, and paired several devices. Despite that I have not been able to successfully print to as HP Deskjet 995C printer.

**hcitool scan** finds it, and I've added it along with other devices to /etc/bluetooth/hcid.conf:
```
device 00:04:76:BB:2D:03 {
    name "DeskJet 995C";
    auth enable;
    encrypt enable;
}
```
I add it to CUPS via the new printer wizard as a network printer with the URI:

bluetooth://000476BB2D03/spp

But I have been unable to even print a test page, it just sits in the print queue. The LED on the printer should flash when receiving data but I haven't seen it do that.

The printer control/properties reports:

Status: Printing: Unable to lookup host 'bluetooth' - Unknown host

and the URI has had ipp:// prefixed:

ipp://bluetooth://000476BB2D03/spp

which seems to suggest the bluetooth:// protocol prefix is not recognised, despite what the only [documentation I can find](http://www.holtmann.org/linux/bluetooth/cups.html) on the subject says:
> bluetooth://device/service

---

### Post by IntuitiveNipple on 2007-05-25
After more searching I finally discovered a bug report dating back to October 2004 in gnome-cups-manager whereby it doesn't correctly handle alternative URIs.

[GUI does not accept all URL schemes accepted by CUPS itself](https://bugs.launchpad.net/ubuntu/+source/gnome-cups-manager/+bug/9373)

---

### Post by SundeepG on 2007-07-30
I've found a workaround for the meantime... use the web access GUI by directing your browser to [http://localhost:631/admin](http://localhost:631/admin) and then click printers, modify printer, and when u set the URL just remove the ipp:// prefix and the WEB interface will not automatically reattach it.

---

