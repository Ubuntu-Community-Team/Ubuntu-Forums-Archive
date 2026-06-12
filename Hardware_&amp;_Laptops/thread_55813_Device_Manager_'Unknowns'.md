---
title: "Device Manager 'Unknowns'"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by Subfix on 2005-08-10
Hi, I just installed Hoary (5.04) and when I open the Device Manager is see this in the bottom fields:

Unknown (0x0080)
Unknown (0x0084)
Unknown (0x0085) <- This one contains the info for the IDE controller...
Unknown (0x0087)
-PCI Device 10de:0087 (nVidia Corporation)
Unknown (0x0087)
-PCI Device 10de:0087 (nVidia Corporation)
Unknown (0x0088)
-PCI Device 10de:0088 (nVidia Corporation)
Unknown (0x008a)
Unknown (0x008b)
-Unknown (0x3119)
-ICE1712 [Envy24] PCI Multi-Channel I/O Controller
Unknown (0x008e) <- This one contains the info for the SCSI controller...

Anyways, are these 'Unknown' entries correct/normal? Could they be the reason why my Audiophile 2496 doesn't work (All I get are beeps from the internal speaker).

Above the 'Unknown' entries it has all of the nForce2 chipset stuff, and all the Processor/BIOS stuff seems right but the "Device" tab reads the Vendor and Device as Unknown for everything but the nForce2 stuff (AMD Sempron 3000+, etc).

---

### Post by TristanMike on 2005-08-11
Yeah, I was wondering that for a while now too.  Are all of the Unknown's normal?

EDIT: I have poor grammer

---

### Post by TristanMike on 2005-08-31
*bump* What's up with the Device Manager Unknowns? How do I get them known?

---

### Post by ry_ry on 2005-09-01
To get my unknown devices listed and named correctly, I first make a connection to the internet, then open a terminal window, then type "sudo update-pciids" and let that download the new information, then after that gets done, then type "sudo update-usbids" and let that download the new information.

Now type "lspci" in the terminal and see if your devices are listed and named correctly.

Hope this helps.  :)

---

### Post by matthew on 2005-09-01
[QUOTE=ry_ry]To get my unknown devices listed and named correctly, I first make a connection to the internet, then open a terminal window, then type "sudo update-pciids" and let that download the new information, then after that gets done, then type "sudo update-usbids" and let that download the new information.

Now type "lspci" in the terminal and see if your devices are listed and named correctly.

Hope this helps.  :)[/QUOTE]
Hey, cool! Thanks.

---

### Post by TristanMike on 2005-09-01
[QUOTE=ry_ry]To get my unknown devices listed and named correctly, I first make a connection to the internet, then open a terminal window, then type "sudo update-pciids" and let that download the new information, then after that gets done, then type "sudo update-usbids" and let that download the new information.

Now type "lspci" in the terminal and see if your devices are listed and named correctly.

Hope this helps.  :)[/QUOTE]Thanx alot, those commands are cool, you're awesome man. Those won't mess anything up tho, will they? Just update names on my current configuration, I just wanna make sure there is minimal danger, sorry if I seem paranoid.

---

### Post by rjwood on 2005-09-01
thanks ry_ry..
btw how do you folks get those little sayings on the bottom of your posts?

---

### Post by matthew on 2005-09-01
[QUOTE=rjwood]thanks ry_ry..
btw how do you folks get those little sayings on the bottom of your posts?[/QUOTE]
Look near the upper right (not all the way up, though) of the forum page, right below the welcome message. Click on Quick Links->Edit Signature.  Type what you want and you are good to go.

---

### Post by rjwood on 2005-09-01
thanks matthew

---

### Post by matthew on 2005-09-01
[QUOTE=rjwood]thanks matthew[/QUOTE]
Glad to help out.

---

