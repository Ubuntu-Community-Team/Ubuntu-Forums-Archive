---
title: "Easy to install printer recommendation"
date: 2013-08-12
forum: Hardware
---

### Post by foxy123 on 2013-08-12
I need to recommend a printer to my relative for whom I have installed Ubuntu on her laptop. As she is no good with computers at all, I need a printer which she would buy, plug it in her laptop and it would work. Should be also widely available and cheap as she needs it only for an occasional use. Thanks a lot in advance for your advice.

---

### Post by mastablasta on 2013-08-12
i suggest laser B&W from HP or Samsung. Samsung needs drivers installed - the default ones that come with printer have issues but a PPA was made and you just add the PPA and it works like a charm. HP has HP lip and also plenty of their drivers are already included in Ubutnu.

Laser printers because their dust doesn't dry out as easy as ink. i have a very old HP inkjet (maybe 20 years old) that still works well for text, but the preblem with it is that i didn't use it often enough and it keep getting dry (and those ink cartridges are expencive nowadays).i took 

samsung now (the kind with scanner) because it was smaller and slightly cheaper (and i dint' realyl need fax the HP was offering). otherwise if i had more printing to do and a bit more space i would definatelly go with HP again. or maybe if you need printer without scaner HP is also very good choice.

---

### Post by foxy123 on 2013-08-12
> **mastablasta said:**
> i suggest laser B&W from HP or Samsung. Samsung needs drivers installed - the default ones that come with printer have issues but a PPA was made and you just add the PPA and it works like a charm. HP has HP lip and also plenty of their drivers are already included in Ubutnu.

Laser printers because their dust doesn't dry out as easy as ink. i have a very old HP inkjet (maybe 20 years old) that still works well for text, but the preblem with it is that i didn't use it often enough and it keep getting dry (and those ink cartridges are expencive nowadays).i took 

samsung now (the kind with scanner) because it was smaller and slightly cheaper (and i dint' realyl need fax the HP was offering). otherwise if i had more printing to do and a bit more space i would definatelly go with HP again. or maybe if you need printer without scaner HP is also very good choice.

Thanks a lot for the reply. Samsung is out of question as it will require some installation (same with Canon). I will look at HP as they have some cheap models and I guess you just plug them in and they work. 

If anyone could recommend any specific model it would be also great.

---

### Post by Cheesemill on 2013-08-12
The last printer I purchased was an HP Deskjet 2510 AIO in the sales for £25 and it really was plug-and-play.

No drivers, no commands, just plug in the USB cable and the printer and scanner worked straight away.

---

### Post by kurt18947 on 2013-08-12
Yes, I think to have absolutely NO additional software required, HP is probably your best bet.  Although I have a Brother MFC-7820N multifunction (no longer available) which had all the drivers present by default, I just had to install them.  I agree about laser for infrequent use; inkjets do need to be exercised every week or two in order for the nozzles to remain clear of dried ink.

I don't know how up-to-date this is but here are printers that I think shouldn't require outside support:

[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

Here's a tip if you're using Ubuntu or Gnome-shell.  The default printers app is pretty limiting IMO.  You can add & remove and that's about it.  The older app used by Xubuntu & Lubuntu is available in the repositories.  It gives much more control IMO.  "system-config-printer-udev".  To open it, you can either use a terminal and type "system-config-printer" or search for the app.

---

### Post by Cheesemill on 2013-08-12
Although most HP printers work out of the box it's worth checking on the website which version of hplip a particular printer needs...
[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

New model printers may require a later version of hplip than the one that comes with your version of Ubuntu, you can check the Ubuntu version of hplip here...
[http://packages.ubuntu.com/search?keywords=hplip&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=hplip&searchon=names&exact=1&suite=all&section=all)

It's no big deal to install newer version of hplip from the website but if you are after a truly plug-and-play solution then make sure your HP printer is supported by the hplip version that comes with your version of Ubuntu.

---

