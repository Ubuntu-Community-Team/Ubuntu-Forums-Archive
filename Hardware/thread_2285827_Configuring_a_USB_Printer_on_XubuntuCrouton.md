---
title: "Configuring a USB Printer on Xubuntu/Crouton"
date: 2015-07-08
forum: Hardware
---

### Post by Ambrosiaster on 2015-07-08
Good morning all,

I've been having a lot of difficulty configuring a USB printer (an HP Deskjet F4480) on an Acer Chromebook running Crouton. I followed all of the instructions on the Crouton wiki ([https://github.com/dnschneid/crouton/wiki/Printing):](https://github.com/dnschneid/crouton/wiki/Printing):)

> [COLOR=#333333][FONT=Helvetica Neue]You want to print from your crouton?[/FONT][/COLOR]
[LIST=1]
[*]Install cups and related packages: sudo apt-get install cups system-config-printer-gnome 
*To get a working lpr command, also install cups-bsd. You'll also want to installhplip if you're using an HP printer. Get the latest hplip package and make from[http://hplipopensource.com/](http://hplipopensource.com/). There maybe other packages necessary for other printers, please add them here.*

[*]Add yourself to the lpadmin group: sudo adduser <username> lpadmin

[*]init scripts don't work right in crouton so we need to start cups somehow. One way is to edit /etc/rc.local and add: /usr/sbin/cupsd

[*]If you want to connect to remote CUPS servers, install cups-browsed, put your configuration into /etc/cups/cups-browsed.conf, and in /etc/rc.local add:/usr/sbin/cups-browsed &

[*]Log out of your crouton and back in.

[*]Add or configure printers using either system-config-printer-gnome, or using the CUPS web interface -- open a browser window and type [http://localhost:631](http://localhost:631).
[/LIST]


I installed all of the files and edited /etc/rc.local by adding /usr/sbin/cupsd to the bottom of the txt file. Still, there's no option to print when I click Ctrl+P in my Crouton system. I tried to do another install of HPLIP (as indicated here - [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)), but since Crouton isn't supported, all of my attempts are failing? I'm not sure where to go from here to get a USB Printer to be successfully configured on a Chromebook running Crouton.

Thanks all and any help would be appreciated.

---

### Post by Vladlenin5000 on 2015-07-08
```
6. Add or configure printers using either system-config-printer-gnome, or  using the CUPS web interface -- open a browser window and type [http://localhost:631](http://localhost:631).
```

Did you?

---

