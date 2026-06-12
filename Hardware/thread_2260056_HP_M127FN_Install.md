---
title: "HP M127FN Install"
date: 2015-01-08
forum: Hardware
---

### Post by rick.eee.13 on 2015-01-08
I am running ubuntu 14.04 and trying to install an HP MFP, M127FN as a network connected printer.  I have downloaded and installed the latest version of HPLIP, 3.14.10.  The install seemed to go correctly but when I try to print the resulting job is created but left in a processing state.

---

### Post by rick.eee.13 on 2015-01-09
I checked further and found out Simple Scan works with the installed M127FN.  I also copied a page to show that the paper and ink supplies were set properly.  However, the print job remains in a "Processing page 1 state".

---

### Post by Accidntl on 2015-01-09
I don't have this printer, but I've been reading about it - because I'm on the verge of buying it.
I've come across the following info to prep me for the purchase - maybe you can find the answer in the following?

HP confirms system compatibility:

[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_pro_mfp_m127fn.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_pro_mfp_m127fn.html)

Link to specific HP drivers:

[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?cc=us&lc=en&product=5318094](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?cc=us&lc=en&product=5318094)

Also came across this:  
"But for the network scanner capabilities, you need to install some HP  extension plugin, downloaded during the driver installation process ...  and for me the plugin download failed most of the time."
[http://bernaerts.dyndns.org/linux/74-ubuntu/197-ubuntu-install-hp-printer](http://bernaerts.dyndns.org/linux/74-ubuntu/197-ubuntu-install-hp-printer)

Also came across these tips in feedback from a customer on Newegg:

   "All I really wanted was a network scanner with Linux support. Did my homework, HPLIP support with a plugin (automatic download)
Just check your distro for the "hp-setup" command.
Just assign an IP from the front panel and hp-setup setup everything automatically!
Disable "Smart Install" before setup it makes Linux go loopy on USB.
All software was included in Ubuntu 14.04, I can print, print-to-fax, and scan over network from any computer in my house! It also cranks out multipage PDF's from all pages in the sheet feeder! Even if you never print, at this price it's worth it just for the scanning support.”

Hope your answer is in there somewhere.
Look forward to what you find, as I am very close to purchasing this gadget.

thanks

---

### Post by rick.eee.13 on 2015-01-09
Thank you Accidental for the info.  I also found all these links and that is what persuaded me to buy the printer.  After a lot of playing around I contacted HP and found out that having and incorrect date, 03/31/2000, and time causes problems.  I reset them and things started printing.  I also found a setting in the printer setup that starts the printer based on the type of print job, network, usb and/or web.  I set it to the network option and things really started working.  My advice to you is to get the latest hplip version and not the one on your system.  Then follow the install instructions.  It is too bad that I had these problems but hopefully my experience can help future users.  I would recommend the device.

---

### Post by Accidntl on 2015-01-09
Thanks for the quick reply [**[COLOR=#000000]rick.eee.13[/COLOR]**]("http://ubuntuforums.org/member.php?u=1015977") !

Also thanks for sharing what worked for you.

I will place my order for this printer tonight!!

---

### Post by mihai2 on 2015-08-25
Hi,
I cannot make it print from ubuntu any version, I tried 14.04 x64, 14.04 x32, 12.04 x32. it doesn't print, I am usign the latest hp plugin, from windows runs perfectly, from  ubuntu no chance... 
I am wondering how did you find? "I also found a setting in the printer setup that starts the printer  based on the type of print job, network, usb and/or web.  I set it to  the network option and things really started workin" can you explain where exactly did you find that config?

---

