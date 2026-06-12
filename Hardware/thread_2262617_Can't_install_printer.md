---
title: "Can't install printer"
date: 2015-01-26
forum: Hardware
---

### Post by MikeFinlay2 on 2015-01-26
Hi. I'm running ubuntu 14.04lts and for a while everything was fine.  I'm now getting the following error message when I try to open printers.    "CUPS server error. There was an error during the CUPS operation: 'Success'."    I'm trying to install a Canon MG5550 printer on a wireless network but can't get past this error message.   I also have a laptop running ubuntu without any problems.  Any guidance would be greatly appreciated. Thanks in advance.  P.S. I'm a novice user.

---

### Post by slickymaster on 2015-01-26
*Moved to the ***Hardware*** sub-forum*

---

### Post by pdc on 2015-01-26
So Mike: all these wireless printers need to be connected directly to your router first of all; so the print message sent goes to the router; and is sent to the printer from there; even if using a laptop with wireless ......................

Canon supply a very detailed guide [http://support-asia.canon-asia.com/contents/ASIA/EN/0301258301.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0301258301.html) to help you connect printer to router; if you haven't got that all done; I enclose a thumbnail;

can we clarify if you have got that stage done please ............ 

________

next step after that would be help you get the drivers Canon supply for you to be installed

---

### Post by MikeFinlay2 on 2015-01-27
Hi.  Thanks for your response.  The printer is definitely connected to the router correctly.  My laptop is running the same version of ubuntu and can connect to the printer without any problem.  The problem is when I try to connect to the printer from the desktop.  I click on 'system settings', then on 'printers', to add a new printer.  That's when the error message appears.  The error message only has an 'OK' button which closes the message and I can't get any further.

---

### Post by plucky on 2015-01-27
> **MikeFinlay2 said:**
> Hi.  Thanks for your response.  The printer is definitely connected to the router correctly.  My laptop is running the same version of ubuntu and can connect to the printer without any problem.  The problem is when I try to connect to the printer from the desktop.  I click on 'system settings', then on 'printers', to add a new printer.  That's when the error message appears.  The error message only has an 'OK' button which closes the message and I can't get any further.

Try using the CUPS interface.

From your web browser ```
http://127.0.0.1:631/
``` will open the CUPS interface.

Good Luck

---

### Post by MikeFinlay2 on 2015-01-28
Hi. plucky.  I've tried your suggestion and nothing happens. The browser just gets it's wee thinking symbol going and stays blank and that's it, no matter how long I leave it.  I've tried uninstalling CUPS using Synaptic Package Manager then re-installing. To no avail. Maks no difference.

---

### Post by SeijiSensei on 2015-01-28
Can you ping the printer's IP address from the laptop?   If so, what happens if you run "telnet ip.addr.of.printer 631" in a terminal window on the laptop?  You should see a "Connected to ip.addr.of.printer" response.  

```

$ telnet 192.168.10.6 631
Trying 192.168.10.6...
Connected to 192.168.10.6.
Escape character is '^]'.

```

This is the reply from my networked Brother laser printer.

Does the printer have a web-based administrator?  What if you point a browser at [http://ip.addr.of.printer/?](http://ip.addr.of.printer/?)

---

