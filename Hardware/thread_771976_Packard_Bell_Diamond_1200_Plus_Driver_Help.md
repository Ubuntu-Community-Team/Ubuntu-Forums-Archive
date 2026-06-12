---
title: "Packard Bell Diamond 1200 Plus Driver Help"
date: 2008-04-28
forum: Hardware
---

### Post by VickiAnn on 2008-04-28
I have this scanner and want to install it.

It is compatible and I downloaded the driver from here:
[http://www.sane-project.org/cgi-bin/driver.pl?manu=Hewlett+Packard&model=&bus=usb](http://www.sane-project.org/cgi-bin/driver.pl?manu=Hewlett+Packard&model=&bus=usb)

Then I've been trying to follow the instructions from here:
[http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)

BUT even when I do the command
[php] sudo su root [/php]
and enter my password and therefore should have admin rights, it either says I don't have permission to create the directory or says it already exists (?), when it clearly doesn't.

I can't put the .usb file where it needs to go and so can't install my scanner - has anyone got any ideas?
I've tried logging in as root after enabling the account, but it says the administrator can't login from this screen (the login screen).

I'm super confused and would really appreciate some help.

Thank you!

---

### Post by VickiAnn on 2008-04-28
Just as a quick update.

By fiddling with the permissions, I have managed to finally create the directory and copy across the file I needed.
I've had to keep the permissions for the driver file at ugo+rwx but I can't see how that will cause a problem long term and it means I can use my scanner so I don't mind.

---

### Post by babusar on 2009-03-04
I found that if I ran Firefox as root and downloaded the files directly into /qt68xx then there wasn't a problem with permissions. The scanner now works great!

---

