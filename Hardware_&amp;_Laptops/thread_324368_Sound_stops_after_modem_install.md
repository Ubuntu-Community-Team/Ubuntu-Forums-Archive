---
title: "Sound stops after modem install"
date: 2006-12-23
forum: Hardware &amp; Laptops
---

### Post by yendor56 on 2006-12-23
Machine is an Acer Aspire 5102wlmi. I ran the cnxtinstall.run script from linuxant.com. It detected and installed a hsf driver. This is some errors reported.

&#65279;Warning: Module snd_hda_intel is in use
Warning: Module snd_hda_codec is in use by snd_hda_intel
done.

Warning: no device detected by hsf driver - HDA modems may require reboot

Note: kernel module snd-via82xx-modem overridden by hsfmc97via
Note: kernel module snd-intel8x0m overridden by hsfmc97ich hsfmc97sis
Note: kernel module snd-atiixp-modem overridden by hsfmc97ati 

After reboot sound no longer works and kppp reports modem busy.

 
hsfconfig --dumpdiag is here.

[http://homepages.slingshot.co.nz/~rmcb/home_files/hsfdiag.txt](http://homepages.slingshot.co.nz/~rmcb/home_files/hsfdiag.txt)

Thanks

---

### Post by Tteddo on 2007-04-01
I have this exact same problem, did you figure it out?

---

### Post by irw on 2007-04-16
Bump - I also have the same probem on an HP dv8396 laptop.

I am still fiddling, but heve yet to find a cure.

At the moment sound is more important than the modem, but after 3 months time i will be needing the modem as well!

---

### Post by Tteddo on 2007-04-16
I ended up reinstalling Ubuntu as I needed the sound more than the modem. Now, of course, I am afraid to try the modem script until I have a means to recover the sound if it happens again.

---

### Post by irw on 2007-04-16
You can just uninstall the hsf modem driver ( I installed it from the .deb from the linuxant site) and re-isntall the alsa driver as described here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

If you are doing that a few times, it gets tiresome, so you could use "checkinstall" instead of "make install" to create .deb files for quicker re-installation of the alsa modules

---

### Post by Tteddo on 2007-04-16
Thanks for the link! That will come in handy. I have a card that uses snd-atiixp but I am sure I can use that link to get it to work once I try it again.
If I get the modem to work I'll post back here.

---

