---
title: "HPLIP install printer: localhost:631 Admin tasks disabled"
date: 2005-08-03
forum: Hardware &amp; Laptops
---

### Post by Brachabre on 2005-08-03
HEYLO! I love Ubuntu! Linux is the best! :)  OOOOOK...Let's see... This ubuntu install is for personal use (not serving anybody or on network) I'm trying to get my hp officejet 6210 printer setup. It works fine when I select (System-->Administration-->Printers)  and choose the default 6200 driver and was able to print and all w/ that driver BUT (being a geeker) I found that HP has HPLIP for printer support under Linux. So I did all the prereq stuff they say to do. Everything went fine...I'm now at the last step of their install method....I am able to reach [http://localhost:631](http://localhost:631)  (ALso have made the necessary additions @LOCAL in various designated places to cupsd.config   or watever that cupsd cfg is named)

::::::Red message at the top saying::::::: 

"Administrative tasks have been disabled for security reasons"

I know that ubuntu (or atleast debian-based distros? Hell maybe All linux) is tight on security when making .conf changes and stuff; asking for passwords and what not. I've been searching around for a couple of hours now using the Linux Google search and so far still don't know how to enable the rights to choose my correct printer via CUPS 

cupsd seems to be running ok w/ that message saying something about "Children 98!"

I saw something about adding "broadcast blah blah" somewhere in that config file too but this sounds like if I was running a server or something?   Sorry if I sound ignorant it's because I'ma NEWBIE!!!! YAAAAY :D    Also Greetings to all who support Ubuntu!!! This rocks totally. Open Source all the way!  Oh and Thanks for the time spent reading my dumb post(s).

---

### Post by MrCheese on 2005-08-03
> I am able to reach [http://localhost:631](http://localhost:631)  (ALso have made the necessary additions @LOCAL in various designated places to cupsd.config   or watever that cupsd cfg is named)

::::::Red message at the top saying::::::: 

"Administrative tasks have been disabled for security reasons"

(1) add user "cupsys" to the shadow group using the user manager

(2) edit the /etc/cups/cupsd.conf file and amend the section Location as below:

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>

---

