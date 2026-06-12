---
title: "How to get Atheros ar5007 working"
date: 2008-08-17
forum: Hardware
---

### Post by cgarib on 2008-08-17
Hi, i have a Hp Pavilion dv6950la laptop runing Ubuntu 8.04 64 bits. My wireless connection is not working. I´ve been trying to fix it. And i've come to the solution. Madwifi supports my ar5007. But, because i been trying to fix it with other methods, when i'm installing madwifi i have this error:

cristobal@cristobal-laptop:~$ sudo modprobe ath_pci
[sudo] password for cristobal: 
WARNING: /etc/modprobe.d/blacklist line 42: ignoring bad line starting with '“blacklist

Is there a way of editing this blacklist?

---

### Post by pytheas22 on 2008-08-17
You can open the blacklist for editing with:
```

sudo gedit /etc/modprobe.d/blacklist
```

You want to remove the line(s) that says "blacklist ath_pci," if there is one.

Also I seem to think that this card is only supported by madwifi on 32-bit systems, and you have to compile madwifi from source because the version that Hardy uses does not support ar5007.  Take a look [here]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html").

If you're on 64-bit I think you have to use ndiswrapper to get this card working.

---

### Post by Hyper Tails on 2008-08-17
Try installing ndiswrapper

```
sudo apt-get install ndisgtk
```

then download the driver [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

heres a picture to help you
[http://ubuntuforums.org/attachment.php?attachmentid=73323&d=1212891748](http://ubuntuforums.org/attachment.php?attachmentid=73323&d=1212891748)

good luck

---

### Post by nicedude on 2008-08-19
Madwifi now has experimental support for Atheros chipsets and 64Bit OS but you must use hal 10.5.6 . I have not tested it with my AR5007 because I use 32 bit Ubuntu Hardy but it is supposed to work. I have a guide on the forums for how to install this adapter in Ubuntu Hardy 32bit but the driver I patched and have a download link to in my guide has the experimental hal 10.5.6 in it and therefore might very well work with 64bit if anyone wants to get a copy there. It is patched for aircrack injection and at least on 32bit works with both WEP & WPA flawlessly.

Like I said though I havn't tested the driver with 64bit I just saw on the Madwifi ticket for AR5007 adapter that it is supposed to support it with this new hal version, so if anyone with 64bit  tries my driver I would appreciate a PM to tell me if it works.

Heres a link to my guide

[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

---

