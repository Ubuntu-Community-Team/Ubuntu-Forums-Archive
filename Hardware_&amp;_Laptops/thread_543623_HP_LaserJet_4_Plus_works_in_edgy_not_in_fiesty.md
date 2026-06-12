---
title: "HP LaserJet 4 Plus works in edgy not in fiesty"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by jeremycobert on 2007-09-05
Re: HP LaserJet 4 Plus not working (did work with edgy)
I have a  HP Laserjet 4-Plus its connected through my local network (tcp/ip).i am able to send pages that print correctly on my edgy machine, but my fiesty machine will not print correctly with any of the supplied drivers. is it possible for me to somehow copy the drivers from my edgy machine and use them in the fiesty machine ?
thanks for any insight


 I tried to send a test page with three different drivers: Postscript, hpijs, and ljet4, but not worked satisfactorily. One causes the printer to spew page after page of garbage, another causes it to complain about insufficient memory on the printer display, and yet another causes the printer to ask for A4 paper even though I told both the printer and the printer config dialog to use Letter.

---

### Post by jrusso2 on 2007-09-05
This is a postscript printer?  The linux printing database shows it should be using the postscript ppd?

[http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4_Plus](http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4_Plus)

Hmm...

I found something that indicates there was a bug 

[https://bugs.launchpad.net/ubuntu/+source/foomatic-filters-ppds/+bug/3020](https://bugs.launchpad.net/ubuntu/+source/foomatic-filters-ppds/+bug/3020)

[https://lists.ubuntu.com/archives/ubuntu-bugs/2006-August/267092.html](https://lists.ubuntu.com/archives/ubuntu-bugs/2006-August/267092.html)

---

### Post by PeterF on 2007-09-05
The Laserjet 4 is supported by [HPLIP]("http://hplip.sourceforge.net/supported_devices/laser.html") (site is a bit slow in building the list),
 I don't know how your network setup is but my Officejet had no problems after installing HPLIP in Synaptic and configuring it in the terminal with:
```
sudo hp-setup
```

---

### Post by jeremycobert on 2007-09-06
> **PeterF said:**
> The Laserjet 4 is supported by [HPLIP]("http://hplip.sourceforge.net/supported_devices/laser.html") (site is a bit slow in building the list),
 I don't know how your network setup is but my Officejet had no problems after installing HPLIP in Synaptic and configuring it in the terminal with:
```
sudo hp-setup
```

it may be supported, but it no longer works in fiesty.

 as per my original question is it possible to use the drivers from my edgy machine (somehow extract them) and use them on the fiesty machine ? this is my only printer and my wifes not happy with ubuntu right now! i gotta get this printer driver fixed or i may have to format and switch my laptop back to edgy.

thanks for any insight !

---

### Post by Mikster on 2008-06-12
> **jeremycobert said:**
> Re: HP LaserJet 4 Plus not working (did work with edgy)
I have a  HP Laserjet 4-Plus its connected through my local network (tcp/ip).i am able to send pages that print correctly on my edgy machine, but my fiesty machine will not print correctly with any of the supplied drivers. is it possible for me to somehow copy the drivers from my edgy machine and use them in the fiesty machine ?
thanks for any insight


 I tried to send a test page with three different drivers: Postscript, hpijs, and ljet4, but not worked satisfactorily. One causes the printer to spew page after page of garbage, another causes it to complain about insufficient memory on the printer display, and yet another causes the printer to ask for A4 paper even though I told both the printer and the printer config dialog to use Letter.

I just upgraded my old desktop from Knoppix to Ubuntu Hardy. I also have a Laserjet 4 Plus connected via the network, and just now got it working 100%. Here's what I did:

First, edit /etc/papersize to contain "letter" (instead of what's probably in there now, "a4")

Next, make sure that when you put in the network address of the printer, that you set the port number to 2501, rather than the default (1900, I think).

Using the default driver, (CLIPS + Gutenprint 5.0.2), I was able to quickly print a clear, crisp test page.

Be sure to install the gnome-cups-manager package... IMO it's a much nicer printer management tool.

Finally, point your browser at [http://localhost:631](http://localhost:631), and it will connect you to a nice set of control pages for your CUPS system, which will, among other things, give you useful status messages when you're trying to print something and there's a problem.

Hope this helps...

---

