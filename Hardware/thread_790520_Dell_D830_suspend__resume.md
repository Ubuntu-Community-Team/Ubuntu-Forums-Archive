---
title: "Dell D830 suspend / resume"
date: 2008-05-11
forum: Hardware
---

### Post by frankdn on 2008-05-11
After a bit (no, a lot) of searching these fora & elsewhere for help getting hibernate & suspend to work on this laptop with 8.04, I can report partial success.

Suspend works (mostly).  The machine appears to go into sleep mode but 'resume' delivers only a blank white screen.  Guessing that there was a login screen behind it, I blindly typed my password, and voila got my desktop back.  Moreover, the one program I had running at suspend time, firefox, was still an active process.  BUT its display did not refresh: my desktop was blank.  I had to kill the process & restart.

Hibernate delivers essentially the same 'resume' behavior, except that I needed to type both my login name & password into the blank display.

Here's what I did:

edit /etc/default/acpi-support
change STOP__SERVICES=""
to STOP__SERVICES="networking"  <-- not sure this is really necessary

invoke System->Administration->Hardware Drivers
activate proprietary nvidia driver
reboot

Good luck with your own efforts, and if you get a bit further along than I have done, please share what you learn here, OK?

= = = = =
[I]Using 14.10 and default graphics drivers it all works fine.
Mörgæs 2014-12-19[/I]

---

