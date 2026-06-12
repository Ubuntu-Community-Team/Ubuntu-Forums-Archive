---
title: "Logitech MX 310 not working"
date: 2004-12-30
forum: Hardware &amp; Laptops
---

### Post by Peke on 2004-12-30
I have tried to use mouse with PS/2 adaptor and in USB. In PS/2 port the mouse doesn't work at all, I have tried ImPS/2, ExplorerPS/2 and PS/2.. So I plugged it to USB. My USB responses to the plugging:

 > hub1-0:hub1.0: Cannot enable port 4.  Maybe the USB cable is bad?

Module is ohci_hcd. The mouse works with scroll perfectly in Debian Woody with 2.4 kernel in PS/2 port. I prefer PS/2 over USB, but if the USB is the only way to go I have to use it.. I don't use other USB devices. I read the  [thread](http://www.ubuntuforums.org/showthread.php?t=4357), but if my USB mouse doesn't even have light so the problem is elsewhere..  

The mouse is the only problem I have in Ubuntu. The other devices are working including integrated Realtek sound and Gigabit ethernet..

My machine:

AMD64 + MSI K8N NFORCE 250 Gb mobo + 512 MB DDR400
GF4 Ti4200
80 GB Maxtor 7200 rpm IDE + 80 GB Seagate 7200.7 SATA (ubuntu on SATA)
Ubuntu64 "Warty"

edited: I also get this error (dmesg):

> usb usb3: string descriptor 0 read error: -19

---

### Post by Peke on 2005-01-04
So the main problem is non-working USB. I have tried both USB2.0 and USB1.1 ports (EHCI-HCD & OHCI-HCD) and the mouse doesn't work.  There isn't any errors if the mouse is unplugged so something happens.. But the mouse led doesn't have light.

---

### Post by tiiim on 2005-01-04
[QUOTE=Peke]So the main problem is non-working USB. I have tried both USB2.0 and USB1.1 ports (EHCI-HCD & OHCI-HCD) and the mouse doesn't work.  There isn't any errors if the mouse is unplugged so something happens.. But the mouse led doesn't have light.[/QUOTE]

I got a similar problem with my mouse and we are trying to solve it on this [thread](http://www.ubuntuforums.org/showthread.php?t=9887&page=1&pp=10) 

at time of writing still not fixed but if you follow it through you maybe able to resolves yours before you get to my stage...!

---

### Post by tiiim on 2005-01-04
[QUOTE=Peke] But the mouse led doesn't have light.[/QUOTE]


ah ha if your mouse dont have light (mine does) could be a problem with the port have you tried it on other USB ports?

---

### Post by tiiim on 2005-01-04
[QUOTE=tiiim]ah ha if your mouse dont have light (mine does) could be a problem with the port have you tried it on other USB ports?[/QUOTE]
 but mouse works now we just fixed it see if other ports. See if another mouse works on your computer if not follow the other thread at the end of ours it was as simple as adding something  to the XF86Config file.

---

### Post by Peke on 2005-01-05
None of the USB ports works. For example if i plug the digital camera, there comes an error message posted above "Cannot enable USB port...". The problem is elsewhere than in protocol.

---

### Post by tiiim on 2005-01-05
[QUOTE=Peke]None of the USB ports works. For example if i plug the digital camera, there comes an error message posted above "Cannot enable USB port...". The problem is elsewhere than in protocol.[/QUOTE]
 then yes if you sort the usb ports out then it prob work cos logitech is quite supported. so either its another prototical or your usb have gone...

---

### Post by Peke on 2005-01-14
I haven't found any solution to this problem, usb doesn't work. I am still thinking, why the mouse is working with ps/2 adaptor in Debian + 2.4.18 kernel. I am using older microsoft scroll mouse in ps/2 port and it works perfect, but i don't like to use it.

Is this a kernel issue or something random, because the error messages are so rare (difficult to find any information)?

---

### Post by tiiim on 2005-01-16
[QUOTE=Peke]I haven't found any solution to this problem, usb doesn't work. I am still thinking, why the mouse is working with ps/2 adaptor in Debian + 2.4.18 kernel. I am using older microsoft scroll mouse in ps/2 port and it works perfect, but i don't like to use it.

Is this a kernel issue or something random, because the error messages are so rare (difficult to find any information)?[/QUOTE]

if it worked on Debain then could be kernel issue i dont think i can help try emailing the Ubuntu mailing list or even the Debian lists.

---

### Post by hardcandy on 2005-01-16
Does Computer-->System Configuration-->Device Manager show your USB controller?

---

### Post by Peke on 2005-01-17
> Does Computer-->System Configuration-->Device Manager show your USB controller? 

Yes. NVIDIA USB Root Hub x 2, but there is "Unknown vendor", but this doesn't seem to be problem. There comes an error message to console if I plug any USB device. Everything seems working if there is nothing plugged, no errors.

---

### Post by ember on 2005-01-24
[QUOTE=Peke]Yes. NVIDIA USB Root Hub x 2, but there is "Unknown vendor", but this doesn't seem to be problem. There comes an error message to console if I plug any USB device. Everything seems working if there is nothing plugged, no errors.[/QUOTE]
 I have a MX 310 mouse too and was stuck with a non-moving cursor. You might want to take a look at that page:
[http://bradthemad.org/tech/notes/logitech_mx310_fedora.php](http://bradthemad.org/tech/notes/logitech_mx310_fedora.php)

For me the unplug-plug technique worked, yet I didn't pursue it, because I switched to USB. You'll have to see how to pass that boot-param to the kernel. Editing menu.lst didn't work for me.

Best,
ember

---

