---
title: "scanner on lan"
date: 2008-09-26
forum: Hardware
---

### Post by atomo133 on 2008-09-26
hi..
i need help to use my scanner over lan...
i have a hp f2100 psc...
printer is working fine.... but when i  use xsane i get:
no devices available
what can i do??:confused:

---

### Post by phidia on 2008-09-26
With HP printers, all-in-ones, ect the best advice is to make sure you have the HPLIP Toolbox installed (install hplip-gui) and set up your device through that. HPLIP Toolbox will be accessible from System > Preferences.

Particularly for networked devices I have found that using hp's toolbox to be the surest way to get devices working correctly.

See the sane site [info on PSC HP printers]("http://www.sane-project.org/cgi-bin/driver.pl?manu=Hewlett-Packard&model=PSC+F2100&bus=any&v=&p=") too.

---

### Post by atomo133 on 2008-09-26
not working...thanx anyway...
ERROR : Device not found.Please chech connection and power-on device.
device is open and working(printng) over lan...
any ideas on how to add the uri of the device on xsane or another scanner program?
i ve tried to setup new device > wireless > find manually
it asks for hostname or ip address
and i gave 192.168.178.1(my router s ip) but nothing yet...

---

### Post by phidia on 2008-09-26
Did you install hplip-gui? That does find the IP address automatically on my systems.
Sometimes devices (because of how the router handles traffic?) change IP addresses.
The address you gave seems to have an extra digit.

---

### Post by atomo133 on 2008-09-26
> **phidia said:**
> Did you install hplip-gui? 
yes
im pretty sure thats my ip address btw...

---

### Post by atomo133 on 2008-10-19
noone uses scanner over lan ??

if you do ,  can you tell how you managed to do it??

---

### Post by atomo133 on 2008-10-22
still no luck??
nobody is using a network scanner??

---

### Post by Abdoo on 2008-10-22
Unfortunately, I haven't network scanner

---

### Post by Bucky Ball on 2008-10-22
> **atomo133 said:**
> 192.168.178.1

Where is extra digit?

---

### Post by atomo133 on 2008-10-22
there aren t extra digits
that s the right address

---

