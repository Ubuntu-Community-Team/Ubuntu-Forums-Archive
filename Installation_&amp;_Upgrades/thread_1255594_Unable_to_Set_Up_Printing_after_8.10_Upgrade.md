---
title: "Unable to Set Up Printing after 8.10 Upgrade"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by imsorryidontdowindows on 2009-09-01
Hello,

I just upgraded from 8.04 to 8.10 and it appears all of my printer settings are missing.

8.10 is supposed to have an easy printer add feature, yet when I go to 

Administration> System> Printing> and click on server>new>printer it is grayed out.

When I click on server>connect>Cups Server local host> i get an error of "httpconnectionencrypt failed".

Any assistance is appreciated. 

:D

---

### Post by Swagman on 2009-09-01
Switch the printer on ?

---

### Post by imsorryidontdowindows on 2009-09-01
[SOLVED]

After some more research I have "solved" the issue. Yes my printer was on :)

Note This Link:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/303730](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/303730)
"This is apparently because /etc/init.d/cups is a broken symbolic link. Other users on ubuntuforms.org have reported the same problem. This is with cups version 1.3.9-2ubuntu3."


I Then in a terminal ran: 

sudo apt-get remove cups
sudo apt-get clean cups
sudo rm /etc/init.d/cups
sudo apt-get install cups

I was then able to go to: Administration> System> Printing> and all my "old" printers were there. The default did not print a test page. So I simply went through the new printer set up. Found my driver: in my case and HP Office Jet J6400. Added it and printed a test page and wallla!




> **imsorryidontdowindows said:**
> Hello,

I just upgraded from 8.04 to 8.10 and it appears all of my printer settings are missing.

8.10 is supposed to have an easy printer add feature, yet when I go to 

Administration> System> Printing> and click on server>new>printer it is grayed out.

When I click on server>connect>Cups Server local host> i get an error of "httpconnectionencrypt failed".

Any assistance is appreciated. 

:D

---

