---
title: "Installing Canon PIXMA MX 430 printer"
date: 2017-01-17
forum: Hardware
---

### Post by nikimoore007 on 2017-01-17
Hi there - I have been running a Canon Pixma MX 430 printer on my computer.  Sometimes the computer and the printer don't talk to each other, and when that happens I uninstall the printer and then install it again.  On Monday morning the printer did not respond to a print request, so I uninstalled it.  However, when I wanted to add it again, I got a completely different message to what I usually get: instead of detecting the printer and asking if I wanted to install it, the little window asked for a URI.  I have no idea what this is.  Why is it not detecting my printer?  I have tried rebooting, unplugging and replugging, downloading drivers, changing cables, etc.  I even phoned the Canon helpline who, after half an hour of trying various things, eventually gave up and told me that Canon does not support Ubuntu.  This is rubbish - my printer has been working for years until Monday!  How do I get my computer and my printer talking to each other again?

---

### Post by pdc on 2017-01-17
what drivers do you use? ........... wondering if you use the Canon drivers that they supply? 

....... this is a USB connection ? If you open a terminal, and type > lsusb . do you see a Canon listed there? if you could paste this command in too please > /usr/sbin/lpinfo -v

It is likely the best bet is to open your PRINTERS folder, and delete the existing entry for your MX430; and recreate it; 

Canon supply a debian package cnijfilter-mx430series-3.70-1-deb.tar.gz from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100412601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100412601.html) ........ is that what you have used before?

---

