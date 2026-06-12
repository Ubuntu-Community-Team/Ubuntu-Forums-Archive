---
title: "xubuntu install hosed by apt-get"
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by noalternative on 2006-01-31
I have bad sources.  I can't cut and paste them from the net either because we haven't installed xfce yet. I can't install xfce.  I am stuck at the command line.

This is part of the error.

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy updates Release.gpg

us.archive.ubuntu.com:80 {1.0.0.0}.-connect (113 No route to host)

[COLOR="Red"]UPDATE I tried, the sources wizard, but those sources wouldn't work either.  It was actually a problem with the settings on my actiontec dsl modem. It is actually the use of dhcp with my actiontec modem that was causing the problem with the univeral repositories. It seem that dhcp causes the first nameserver in resolv.conf, to be the same as the default gateway, 192.168.0.1 . If this happens certain debian repositories, will give gpg errors.

I tried editing my resolv.conf file, to comment out # the first nameserver, but dhcp would overwrite it at boot. I configured my network card manually with the help of my isp, and now I no longer have problems. [/COLOR]:cool:

---

### Post by noalternative on 2006-02-01
no advise?

---

### Post by noalternative on 2006-02-01
mid day kick.  Still need help on this matter.

---

### Post by Taino on 2006-02-01
edit source.list from command line with nano editor (or vim editor similar)

sudo nano /etc/apt/sources.list

uncomment the ## from infront of the  ## deb repository adresses so instead of
## deb
its
deb

then

sudo apt-get update

then

sudo apt-get install xubuntu-desktop

its pretty straight forward, you can continue following from here,
[https://wiki.ubuntu.com/InstallingXubuntu?highlight=%28xubuntu%29](https://wiki.ubuntu.com/InstallingXubuntu?highlight=%28xubuntu%29)
its best done following the wiki example install, just skip the parts that dont pertain to your particular install or hardware setup...

if you like you can also copy the sources.list file to another computer and edit/add in new repositories there, then copy the file back over overwriting the old sources.list file (if it makes the editing easier for you that is).

---

### Post by kaamos on 2006-02-01
If your list is totally screwed up, you can generate a sources.list here -> [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
Copy (use usb-drive or floppy or something to transfer or just copy by hand..) over the file the old one with "sudo nano /etc/apt/sources.list"

---

### Post by noalternative on 2006-02-17
[QUOTE=noalternative]I have bad sources.  I can't cut and paste them from the net either because we haven't installed xfce yet. I can't install xfce.  I am stuck at the command line.

This is part of the error.

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy updates Release.gpg

us.archive.ubuntu.com:80 {1.0.0.0}.-connect (113 No route to host)

[COLOR="Red"]UPDATE I tried, the sources wizard, but those sources wouldn't work either.  It was actually a problem with the settings on my actiontec dsl modem. It is actually the use of dhcp with my actiontec modem that was causing the problem with the univeral repositories. It seem that dhcp causes the first nameserver in resolv.conf, to be the same as the default gateway, 192.168.0.1 . If this happens certain debian repositories, will give gpg errors.

I tried editing my resolv.conf file, to comment out # the first nameserver, but dhcp would overwrite it at boot. I configured my network card manually with the help of my isp, and now I no longer have problems. [/COLOR]:cool:[/QUOTE]


KICK

---

