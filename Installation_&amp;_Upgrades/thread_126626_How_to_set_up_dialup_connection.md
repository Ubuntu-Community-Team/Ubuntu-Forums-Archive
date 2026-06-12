---
title: "How to set up dialup connection"
date: 2006-02-07
forum: Installation &amp; Upgrades
---

### Post by mdsmith on 2006-02-07
I have a single computer connected to the internet  through an external modem with dialup.  At no point during the installation was I asked for the internet service provider or a phone number. I cannot find anything in the application or system menus to configure the connection or to make the connection after it is configured.. some time ago on my first try at installing Ubuntu I did find a network app which did take the phone no. and apparently dialed because the modem was active, however Firefox could find any sites.  How does the single user, no network, get connected. Thanks

---

### Post by jasmuz on 2006-02-07
open a terminal

$ sudo pppconfig

Use that utility to set a Dial-up connection. Then use the command 'pon' to connect and 'poff' to disconnect

---

### Post by mdsmith on 2006-02-08
Thanks for the reply Jasmuz. I did the config thing and it seemed to set up correctly but pon errormessaged. I worked a bit then decided to try a fresh install. This time I allowed it to set up networking and was able to set up the dialup connection with the network prog. When I tried to activate it dialed but got a telco message. I think this is because my local IP is in a different area code. One version of Mandrake had this problem and I had to get a different number for the IP. It worked but was a slow connection. I am going to do a search here on installing KDE along with Gnome and hopefully I will be able to use KPPP which I know works.  Don

---

