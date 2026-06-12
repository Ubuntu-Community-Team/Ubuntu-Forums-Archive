---
title: "Hauppauge WinTV Nova-T Stick is not detected"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by hefsgaard72 on 2008-02-20
Hi, I'm trying to get my Hauppage WinTV Nova-T stick to work, and I have read other posts about this. However i have not found a solution to my problem. so here goes:

When i plug in the stick in the USB,  DMESG does not show:
dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware 

as it should, but only :

[  145.360000] usb 4-4: new high speed USB device using ehci_hcd and address 3
[  145.492000] usb 4-4: configuration #1 chosen from 1 choice

So what do I do next?? 

Ohh, if I look under HARDWARE INFORMATION the Stick is shown.

thanks 
Jan

---

### Post by flosoft on 2008-03-13
Hi,

did you ever get it to work?

---

### Post by zylche on 2008-05-29
bump
I'm also falling victim to this, I've searched all over the net and can't find a way to fix this. I've installed dvb-usb and loaded all of the modules required as well as putting in the correct firmware in place yet dvb-usb isn't on the dmesg, I assume I have missed something significant which the other guides do not say.
Is there any way to fix this?

---

### Post by zylche on 2008-05-29
Sorry for double posting, solution has been found.
Just follow the guide at [http://ubuntuforums.org/showthread.php?t=752968](http://ubuntuforums.org/showthread.php?t=752968) most guides forget to mention "sudo make unload", a reboot helps as well. :)

---

