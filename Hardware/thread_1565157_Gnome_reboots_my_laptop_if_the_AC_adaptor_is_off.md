---
title: "Gnome reboots my laptop if the AC adaptor is off"
date: 2010-08-31
forum: Hardware
---

### Post by luis.linietsky on 2010-08-31
Hi, 

Hope this is the right place and procedure for posting this issue, otherwise, my apologies.

I also searched for the same bug but didn't find anything like what happens to me.

I have a laptop, it is an _[HP Pavilion Dv4 2013la]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01884730&cc=es&dlc=es&lc=es&jumpid=reg_R1002_ESES#N799")_. (Click to see technical specs)

The issue is the following:

I have installed Ubuntu 10.4 recently, and noticed that when I unplug the AC adaptor, the laptop restarts itselve.

After it boots on Ubuntu again, if the AC adaptor is still unplugged, it gets to the login screen, freezes for a few seconds and reboots itselve again. And this keeps happening for ever, until I plug the AC adapor again.

However, I also have a Windows 7 installation in the same laptop, and this is not happening there. And previously I had an Ubuntu 9.10, where this has never happened, so that tells me that it is an issue with Ubuntu 10.4.

I did an apt-get update followed by an apt-get dist-upgrade to see if this was a fixed bug, but the issue still happens.

The computer is new, I have it since last november, the battery is OK, and again, it worked OK on Windows 7 and a previous release of Ubuntu.

I hope someone could tell me how to fix this or how to check if this is in fact a bug in Ubuntu in order to report it.

Thanks!

---

### Post by ajgreeny on 2010-08-31
From the stickies on the general section of the forum is this information:-

> **[COLOR=DarkRed]Ubuntu shuts down after unplugging Laptop power cord[/COLOR]**
A problem known with MSI wind and some Vostro users.

Current workaround is to open **gconf-editor** and browse to:
     Code:
     /apps/gnome-power-manager/general 
And de-select the option **use_time_for_policy**

There is no need to restart, just close the configuration editor.
Not the same model as yours I admit, but worth a try.

It is always worth looking at the various sections of the forum, and reading the stickies at the top of each section, if you have a problem.

---

### Post by luis.linietsky on 2010-09-01
Hi Ajgreeny,
Thanks for your response.
However, I had seen and tested that with no succes before posting this issue.
Are there any debug data/logs I may search and post here to let anyone find the bug ?
Thanks

---

