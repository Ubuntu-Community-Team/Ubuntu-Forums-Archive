---
title: "ISAPnP snd-cmi8330 and Breezy 5.10"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by sb73542 on 2005-11-15
Hi,

Has anyone managed to get the miserable old CMI8330 onboard ISAPnP soundcard working with Breezy?  On SuSE 10.0 it gets auto-detected, and on Mandriva 2006 you simply have to "modprobe snd-cmi8330" and "modprobe snd-pcm-oss".  On Hoary final and also the Breezy **preview release** I tried, all manner of hacking produced no results.  The alsa module will not load, "device not found" errors, even after specifying all the irq and port numbers.  I filed [http://bugzilla.ubuntu.com/show_bug.cgi?id=15384](http://bugzilla.ubuntu.com/show_bug.cgi?id=15384) , but basically they aren't too interested in fixing it.  I was just curious to know if this problem has magically fixed itself for the final release of Breezy, or if anyone has any tricks with this card?

Thanks for the help!

---

### Post by sb73542 on 2005-11-16
Oooops.  Moderator, could you please move this thread to the Breezy section?  Thanks!

---

