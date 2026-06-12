---
title: "Dell Latitude D630 WiFi"
date: 2011-07-15
forum: Hardware
---

### Post by keni0902 on 2011-07-15
Just installed ubuntu on my laptop... but the Wifi driver is not initially working, so I connected to the web via LAN cable, after downloading the driver and restarting, its still not working.
 
Help needed please.

---

### Post by ajgreeny on 2011-07-15
Can you post the output of ```
lspci
``` and ```
ifconfig
``` and finaly ```
iwconfig
```
That will tell us the exact hardware you are using in the laptop.

---

### Post by rev.elation on 2011-07-15
I myself have a D630 although I don't have linux on it right now but when I used to I had problems with the wireless too, I started using nm-applet as my network-manager and then it started working fine.

so try:
[FONT=Courier New][B]sudo apt-get install nm-applet

sudo nm-applet[/B][/FONT]

---

### Post by keni0902 on 2011-07-15
> **rev.elation said:**
> I myself have a D630 although I don't have linux on it right now but when I used to I had problems with the wireless too, I started using nm-applet as my network-manager and then it started working fine.
 
so try:
[FONT=Courier New]**sudo apt-get install nm-applet**[/FONT]
 
**[FONT=Courier New]sudo nm-applet[/FONT]**
 
 
Quite new to Linux... how exactly do I do that... :) Please walk me through.

---

### Post by rev.elation on 2011-07-16
Open up a Terminal.

enter: [FONT=Courier New]**sudo apt-get install nm-applet**[/FONT]
press enter and enter your password and confirm the download.
nm-applet is a NetworkManager.
to start the networkmanager you should now (still in the terminal) enter: [FONT=Courier New]**sudo nm-applet**[/FONT]

then look for the new Icon among the other running programs and search for your wireless network.

---

