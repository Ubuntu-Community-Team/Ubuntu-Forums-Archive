---
title: "Printer's install script and &quot;printers&quot; applet can't find wifi printer"
date: 2015-03-18
forum: Hardware
---

### Post by spectatorx on 2015-03-18
Lubuntu 14.10 i386.
I have installed .deb packages for device canon pixma mg3255. Now i'm trying to connect this device via wifi but i have no idea how. First i started with "Printers" applet available by default in os, when i clicked add->network printer->find network printer->find, it returns me a message "network printer can't be found at this address".
When i run install script install.sh it ends up with similar result which is "device can't be found".

MG3255 has built in wifi module, under windows it can be easily found as network printer/scanner but under lubuntu it just can't be found, do not know why. Any suggestions?

---

### Post by Vladlenin5000 on 2015-03-18
Use the printer's IP address when searching.

---

### Post by spectatorx on 2015-03-18
What in case if i do not know its ip?

---

### Post by ajgreeny on 2015-03-18
You can probably find its IP from your router configuration page "Attached devices" or similar.  I have used several routers over the years and they have all had that page from which to find a machine's IP.

Once you have that it will be worth setting that IP as a reserved address for the printer so that it is always at the same IP address even after a restart.

---

### Post by spectatorx on 2015-03-18
Printer is not connected in any way to router, it has its own built-in wifi module.

---

### Post by weatherman2 on 2015-03-18
It's not working because you aren't using the printer in the way it was intended, at least in Linux.  You're talking about an ad-hoc connection to the printer via WiFi.  If you can get it to work that way (to print), you'll first need to make an ad-hoc WiFi connection to the printer, but that has nothing to do with the printer drivers you're trying to use.

[http://howtoubuntu.org/how-to-create-a-wireless-ad-hoc-network-in-ubuntu](http://howtoubuntu.org/how-to-create-a-wireless-ad-hoc-network-in-ubuntu)

I'm not aware of people using ad-hoc networks for printing.  It's not a practical way to print, because you can't use your WiFi connection to access the internet at the same time.  Ad-hoc networking to a printer is usually used only while you are setting it up (and have no USB cable to do so).

Sometimes people use bluetooth to connect wirelessly to their printer without using WiFi, but that Canon printer does not have bluetooth.

---

### Post by pdc on 2015-03-19
so I think we are all saying the same thing:

to connect a printer you need to do three things; in order:

1) establish a connection
2) install the drivers
3) register the printer: with your system;

__________

Canon supply an excellent how-to for 1): as you need to have your printer accepted by your router: the MG3200 series only does the WPS method: ie you get your printer to broadcast itself; you press the WPS button on your router to drop its defences; and the two quietly embrace wirelessly;

so here is the Canon link that tells you how to do that: [http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/mg3240_printer_wireless_connection_setup/](http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/mg3240_printer_wireless_connection_setup/)

________________

so that must be done first:

the Canon install script then does steps 2) and 3) automatically for you; (whereas Epson supply drivers and you need to ADD the Epson to your system);

______________

so is this a help? Have you created an entry for the MG3200 in your PRINTERS section..............? It might be best to delete that; 

Let's hear back from you and we can go from there

---

