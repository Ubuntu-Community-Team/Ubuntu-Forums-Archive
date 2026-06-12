---
title: "PCMCIA on Travelmate 3260"
date: 2008-04-14
forum: Hardware &amp; Laptops
---

### Post by viniciuscarvalho on 2008-04-14
Hello there! It seems that my controller is not being detected by my ubuntu 7.10. I've already had problems with ALSA and my sound driver (had to compile and use a patch for acer) also, video card support is not full implemented (this not sucks for linux). Now, I can't get my firewire pcmcia work on linux. It does work on windows (damn I had to install a XP to check if it was hardware problems). I've read many topics, asked for help, but now I think the problem is the controller not being detected. At least a tool from KDE tells me that. When I insert a card nothing happens on the dmesg log, so it seems that the driver is not installed, but when I run lsmod | grep pcmcia I get this:

pcmcia                 41388  0 
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic

But since I'm a noob I can't understand it :(

May the problem be related to my controller? Does anyone knows how to install the right driver for this notebook?

Regards

---

