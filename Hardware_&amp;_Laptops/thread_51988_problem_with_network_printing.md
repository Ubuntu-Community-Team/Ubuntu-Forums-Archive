---
title: "problem with network printing"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by minghai on 2005-07-26
Hi all,

    I've happily installed Ubuntu on all 5 of my office machines and now I have a problem with printing.  All 5 machines are connected to a router via ethernet cables and a Lexmark printer is attached via USB cable to one of them.  Previously, I was using Mepis and it automatically detected the printer from all machines and they had no problems printing to it over the network.

    Now I cannot see the Lexmark printer from the other machines even after enabling "Detect LAN printers".  Is there some configuration I must do before all the machines can see this printer?  Thank you.

Ming Hai

---

### Post by minghai on 2005-07-26
Found the solution on the web that worked for me.

Backup your: /etc/cups/cupsd.conf and replace with the following:

==========================================

DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From @LOCAL
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>

==============================================

Go to: System / Administration / Printing -> Global Settings nd enable "Detect Lan Printers" 

sudo /etc/init.d/cupsys restart

Ming Hai

---

