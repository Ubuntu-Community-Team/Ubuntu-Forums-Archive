---
title: "Linksys Wireless Print Server"
date: 2005-11-24
forum: General Help
---

### Post by hollinch on 2005-11-24
Hi, I have a Linksys WPS54GU2 Wireless print server, but can't seem to be able to use it from Ubuntu. From Windows it works fine. I have tried setting up a Cups lpd print queue, pointing to lpd://<ip address of print server>/P1, but it doesn't work. Has anyone come across a similar issue?? Linksys are not very helpful, I tried to chat with support and apparently they are not permitted to assist with linux issues. Great.

---

### Post by waldorf on 2005-12-14
I have the exact same problem.

Please can anyone help!

BTW I have an HP 6210, but even with windows I need to use the driver for an HP deskjet 990c.

---

### Post by rayl on 2006-01-09
Hollinch-have you tried pinging the server to see if you can communicate with it?  What type of printer do you use?  I have a d-link print server and was able to set up through the printers applet

Waldorf-I use an HPDeskjet 845c and I found these settings through the printers applet worked.  Choose your printer model from the list for the drivers (Ubuntu seems to have a great selection of HP printers).  Under the connection tab choose network printer and I had an option of "HP Jetdirect" in the drop down.  This automatically filled in the port box as 9100 and the "host" box should be the IP for your print server.  I hope this helps.

---

