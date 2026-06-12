---
title: "Network printing from Fedora 5 to Ubuntu"
date: 2006-04-27
forum: Hardware &amp; Laptops
---

### Post by B7may on 2006-04-27
Ok,
I have been working on this for awhile with no success:

I have a Fedora 5 machine that I want to print to an Ebuntu Breezy machine.  I cannot get this to work.  I have searched the forums and changed the following things:

In /etc/cups/cupsd.conf
I changed:
Uncommented - #port 631
Commented - Listen 127.0.0.1:631

added the following line under <Location />
Allow From 192.168.1.0/24

Then restarted cups
It still does not work.  So I found a post that said I may need to change my
/etc/cups/printers.conf

Change the line:
DeviceURI ipp://<ip address>/ipp/printers/<queue name>
to
DeviceURI ipp://<ip address>/printers/<queue name>

The problem is, that this does not match what my file says?  My printers.conf file says:
DeviceURI usb://hp/LaserJet%201000

I am a little nervous about changing it because everything works great for printing from Windows machines to my edbunutu machine and this line is totally different.

Any ideas?

Thanks
Brian

---

### Post by sabitha on 2006-04-27
if the printer work on your breezy my suggestion is :
change /etc/cups/cupsd.conf on breezy to :
> DefaultCharset notused
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
Allow From 10.0.0.*
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

on <location/> change
Allow From 10.0.0.* to your IP on fedora 


then change the /etc/cups/client.conf on your fedora on section :

#ServerName myhost.domain.com
ServerName your breezy_IP


restart with 
# /etc/init.d/cupsys restart

that work for me 
i read that from another treath
sorry for the languages

---

