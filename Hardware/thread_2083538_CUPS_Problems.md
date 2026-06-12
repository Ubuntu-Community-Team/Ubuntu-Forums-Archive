---
title: "CUPS Problems"
date: 2012-11-12
forum: Hardware
---

### Post by Rob Hodge on 2012-11-12
alright, i have a command-line only installation of 12.10 on this old laptop i need to use as a headless print server. it's old. pentium 3, 366mhz.  6 gig hard drive. 192mb ram.

i've done a net instal using the mini iso.  i then installed netatalk, ssh, and cups.
other than their dependancies, that's all that is installed. 

I'm trying to configure a Eltron (Zebra) 2442 label printer on the parallel port, using the web interface. i opened it up to allow me to access the admin screens from other machines on my network. 

i'm "tail -f"-ing the error log as i try to add the printer. the first page where i pick the port, it goes ok.

the second page where you put the name, description, location and if you share it, as soon as you hit the button on the webform this appears in the log:
E [12/Nov/2012:19:19:45 -0800] [cups-driverd] Bad driver information file "/usr/share/cups/drv/cupsfilters.drv"!
and the next page loads. 

when i pick the manufacturer, a similar error appears- 
E [12/Nov/2012:19:22:44 -0800] [cups-driverd] Bad driver information file "/usr/share/cups/drv/cupsfilters.drv"!

And when i pick the model on the next screen, the web page returns a blank page, and this appears in the log--
W [12/Nov/2012:19:23:43 -0800] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_Zebra2442

anyone have any pointers for me? 

I did manage to get it to add the printer using the command line, but was then unable to edit the settings and do much of the administration from the web interface, usually with similar errors.

---

