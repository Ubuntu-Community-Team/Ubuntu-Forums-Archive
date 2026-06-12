---
title: "HP deskjet 2510"
date: 2013-06-18
forum: Hardware
---

### Post by kapi on 2013-06-18
Hi, Bought new HP deskjet 2510 printer and installed it via the add new printer option but it won't print anything.

Any ideas please

---

### Post by Dave_L on 2013-06-19
Does that model have a network interface that you can access from a web browser, so that you can check its status?

There's also a package hplip-gui that provides similar functionality, if that model supports it.

---

### Post by squakie on 2013-06-19
also be sure the main hplip pacage s nstalled.

---

### Post by kurt18947 on 2013-06-19
If this is a new model or family, it may be necessary to download HPLIP & HPLIP-GUI from HP.  The version in the repositories may not be the most current.  This may help:
[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

---

### Post by Bucky Ball on 2013-06-19
* Install 'HPLip' from the repostitories (Synaptics or Software Centre);
* Go here: [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html) and find and install your driver. You will find the instructions for how in the 'Read Me' file you download;
* Printing>Add Printer. This time you should find the correct driver. Follow your nose.

You might make some slight detours and need to tweak these instructions a bit, but that should be basically it. Report back with any problems. Not sure if you need the printer plugged in during this or out. Do a bit of research in the manual. 

For everyone's information (FEI); this is an all-in-one USB printer, no network.

---

### Post by Yellow Pasque on 2013-06-19
Yes, you need hplip 3.12.6, and Ubuntu 12.04 only has 3.12.2 in its repo: [http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_2510_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_2510_series.html)

---

### Post by kapi on 2013-06-19
Thank you very much for the replies, will try in a few hours as am not at home at present. 

Although the printer is a brand new one bought straight from the shop I do think it's an older model.
The model only possesses a USB connection with no Ethernet connection or wireless capabilities.

I'll go to synaptic just as you guys suggested and see how I progress.

Thanks again for your time, much appreciated.

:-)

---

### Post by agillator on 2013-06-19
I would recommend you NOT go to synaptic for HPLIP. Go directly to HP for it. Often the ones provided for Ubuntu do not work for some reason while the ones downloaded directly from HP do. It will take a few minutes to install, but the automatic installation works nicely and your printer should then work.

---

### Post by kapi on 2013-06-19
will do thanks again

---

### Post by kapi on 2013-06-19
ok got it thanks to you all, simply restarted laptop

many thanks again

---

### Post by Bucky Ball on 2013-06-19
Good news. Please mark thread as solved by following the link in my signature. ;)

---

