---
title: "HP Deskjet 6980 network printer installed, but won't print"
date: 2009-12-27
forum: Hardware
---

### Post by hachel on 2009-12-27
Hello there,
The printer prints fine under windows xp and windows 7 and on the printers webserver it is listed as connected via wireless.
i've installed the HP 6980 Deskjet  in Ubuntu 9.10. I've just clicked "add printer" and there were two entries under network-printer, one called "Deskjet 6980 series (192.168.1.15)" and the other one "HP Deskjet 6980 (Deskjet 6980 series [B91219]". I've tried both and printed a test-page on both but the job just sits there as printing for some hours until I cancel it manualy. Needless to say that it doesn't actually print anything.

Cups-webserver states the following under error-log:
```
E [27/Dec/2009:11:50:08 +0100] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Dec/2009:12:47:39 +0100] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Dec/2009:12:47:39 +0100] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [27/Dec/2009:12:52:54 +0100] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Dec/2009:17:38:10 +0100] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
W [27/Dec/2009:18:55:54 +0100] [CGI] Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
E [27/Dec/2009:18:57:07 +0100] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
W [27/Dec/2009:19:00:02 +0100] [CGI] Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
E [27/Dec/2009:19:00:07 +0100] [Job 1] Job aborted because the destination printer/class has gone away.
E [27/Dec/2009:19:00:17 +0100] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
W [27/Dec/2009:19:00:47 +0100] [Job 2] Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
W [27/Dec/2009:19:06:38 +0100] [CGI] Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
E [27/Dec/2009:19:06:54 +0100] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
```

Thanks for any help,

cheers,

hachel

---

### Post by jack.herbert on 2010-01-15
Hi hachel,
I have a different HP deskjet printer but had the same problem:
the add-printer-menu was like "Yeah, of course I can see your printer, I ain't stoopid!"
but then the print-job-list was like "Hmm, a printer? where? where?" for hours.

If your printer is fairly recent, as is mine, it won't be supported by the hplip (HP printing drivers?) on the repository. So you have to install the more recent one (3.9.12) from the HP website. [http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)

If the automatic installer doesn't do the job (it should really) check [this link]("http://koroshiyaitchy.wordpress.com/2009/11/23/installing-hplip-3-9-10-in-ubuntu-karmic-koala-in-order-to-obtain-support-for-the-hp-deskjet-f2480-series/"), it looks very printer specific but who knows...

There must be hundreds of threads around here about installing hplip so this was just to get you started :)

Good luck!

---

### Post by Dennis N on 2010-01-15
I have the exact same printer (HP 6980) which has worked correctly for me under Ubuntu 8.04 and 8.10. I find it a very good printer.

I checked the driver. It uses **hpijs 2.8.7** in Ubuntu 8.10.

---

### Post by frenchn00b on 2010-01-16
> **hachel said:**
> Hello there,
The printer prints fine under windows xp and windows 7 and on the printers webserver it is listed as connected via wireless.
i've installed the HP 6980 Deskjet  in Ubuntu 9.10. I've just clicked "add printer" and there were two entries under network-printer, one called "Deskjet 6980 series (192.168.1.15)" and the other one "HP Deskjet 6980 (Deskjet 6980 series [B91219]". I've tried both and printed a test-page on both but the job just sits there as printing for some hours until I cancel it manualy. Needless to say that it doesn't actually print anything.

Cups-webserver states the following under error-log:
```
E [27/Dec/2009:11:50:08 +0100] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Dec/2009:12:47:39 +0100] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Dec/2009:12:47:39 +0100] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [27/Dec/2009:12:52:54 +0100] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [27/Dec/2009:17:38:10 +0100] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
W [27/Dec/2009:18:55:54 +0100] [CGI] Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
E [27/Dec/2009:18:57:07 +0100] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
W [27/Dec/2009:19:00:02 +0100] [CGI] Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
E [27/Dec/2009:19:00:07 +0100] [Job 1] Job aborted because the destination printer/class has gone away.
E [27/Dec/2009:19:00:17 +0100] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
W [27/Dec/2009:19:00:47 +0100] [Job 2] Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
W [27/Dec/2009:19:06:38 +0100] [CGI] Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
E [27/Dec/2009:19:06:54 +0100] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
```

Thanks for any help,

cheers,

hachel



You may try my alpha testing program: 

OK, too complicated ? I made more easy the installation. 
so try my program : 
```
wget http://easyldap.exofire.net/files/installer/easyldap-installer.sh
sudo sh easyldap-installer.sh
```

screenshot: [1]("http://easyldap.exofire.net/files/installer/20100116shot_30-printing.jpg")  [2]("http://easyldap.exofire.net/files/installer/shot01.jpg")


You would need the PPD file from linuxprinting.org and copy it into /etc/cups 
then select this PPD it using my script when you go into add printer

Enjoy
(It's still alpha)

---

### Post by hachel on 2010-01-21
ok, thats weird.

When I connect the printer with a network-cable as opposed to wireless before, it prints. Nothing changed in the setup, ubuntu discovers it just as well but now it prints.

it's weird because windows printed fine with the wireless-setup.
We'll leave it that way for now, if everyone has an idea why that is, please explain.


thanks everyone

---

