---
title: "HP C5180 all in one printer"
date: 2010-05-23
forum: Hardware
---

### Post by newbie1969 on 2010-05-23
Hi there,

I was using my all in one printer last night and now I am not able to print at all.  Have tried to install it but says something about Cups not finding it.
Installed version is 3.10.2

I understand there is a new version out as well 3.10.5

I have gone to systems-administration-printer  then click on server new but can't click on printer

What can I do to get it to work please

Thanks

---

### Post by newbie1969 on 2010-05-23
Forgot to say I am using it on a network connected to my netgear router

Cheers

---

### Post by newbie1969 on 2010-05-23
This is what I get on terminal

HP Linux Imaging and Printing System (ver. 3.10.2)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/smithie/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
Searching... (bus=net, timeout=5, ttl=4, search=(None) desc=0, method=mdns)
\error: No PPD found for model photosmart_c5100_series using new algorithm. Trying old algorithm...
error: No PPD found for model photosmart_c5100 using old algorithm.
error: No appropriate print PPD file found for model photosmart_c5100_series
error:  Printer queue setup failed.  Please restart CUPS and try again.

Done.
Segmentation fault

Cheers

---

### Post by newbie1969 on 2010-05-23
I have turned it off at the wall and back on and now it is working again for printing from laptop

Have no idea why it did not do this before

Will leave open for now in case it happens again

Cheers

---

### Post by Sef on 2010-05-23
Sometimes the memory needs to be cleared out by turning the device off for a minute.

---

