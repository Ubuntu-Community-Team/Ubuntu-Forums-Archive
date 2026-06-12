---
title: "Coluld not install ubuntu 10.04.1"
date: 2010-08-30
forum: Hardware
---

### Post by nikR on 2010-08-30
I am trying to instaal ubuntu 10.04.1 via a USB stick on my VAIO VPCCW13EG laptop.
 
When I try to run ubuntu live without installing or when I install, some lines are displayed, then the screen turns off. I have already tried **vga=771 noapic nolapic** on boot prompt, but it does not work for me.
 
Here are the details:
 
Version: Ubuntu 10.04.1 amd64
Laptop: VAIO VPCCW13EG
Manufacturer: Sony
CPU: 64 bit
Graphics Card: NVIDIA GeForce G210M (Generic PnP Monitor)
 
Please help. I need to install ubuntu asap.

---

### Post by odinfromvalhalla on 2010-08-30
this could be of some use: [http://ubuntuforums.org/showthread.php?t=1336694](http://ubuntuforums.org/showthread.php?t=1336694)

---

### Post by nikR on 2010-08-31
Thanks for the quick reply.
 
But that solutions applies if I've already installed ubuntu. But in my case I could not even install ubuntu.

---

### Post by amirrezas on 2010-10-22
I have the same problem and every where i search they are saying: "Open a terminal...".
I have GeForce G210M NVIDIA graphic card and trying to install ubuntu 10.04 desktop version on my VAIO laptop. if i select normal boot of ubuntu the screen will cut off! i only can access the GNU GRUB command page.
does anyone know how to fix my problem?

thanks,
-----
p.s.: I am new to ubuntu!

---

### Post by tosk on 2010-10-22
Do you know what your wifi chipset is? There was an issue, that I had at least, booting 10.04 with a Broadcom wifi chipset.

---

### Post by tosk on 2010-10-22
Try doing what's in this post and see if it works for you or if you at least get a better idea of what's up with why it won't boot.

[http://ubuntuforums.org/showpost.php?p=9287817&postcount=9](http://ubuntuforums.org/showpost.php?p=9287817&postcount=9)

---

### Post by amirrezas on 2010-10-22
> **tosk said:**
> Do you know what your wifi chipset is? There was an issue, that I had at least, booting 10.04 with a Broadcom wifi chipset.

I read this from system properties: Intel(R) WiFi Link 5100 VGN

---

### Post by sikander3786 on 2010-10-22
Try adding the paramater **nomodeset** when booting.

You can hit enter at the screen with a man in circle and a keyboard, after you see the menu, press F6 and select **nomodeset**. Does that help?

---

