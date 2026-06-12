---
title: "Problem with Smartlink modem (again)"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by EcliptuX on 2005-06-06
Hi,

I read a lot of topic about the smartlink problems but I didn't find a soluce :(
I had installed kernel-header-2.6.10-386, sl-modem-source and sl-modem-daemon
I run module-assistant and everything work well !
I run gnome-ppp and the connexion work

But after a reboot, the modem refuse to work again !
 ```
root@Narayan:/dev # apt-get install sl-modem-daemon Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
 sl-modem-daemon
0 upgraded, 1 newly installed, 0 to remove and 34 not upgraded.
Need to get 0B/413kB of archives.
After unpacking 1020kB of additional disk space will be used.

Preconfiguring packages ...
Sélection du paquet sl-modem-daemon précédemment désélectionné.
(Lecture de la base de données... 101228 fichiers et répertoires déjà installés.)
Dépaquetage de sl-modem-daemon (à partir de .../sl-modem-daemon_2.9.9a-1ubuntu4_i386.deb) ...
Paramétrage de sl-modem-daemon (2.9.9a-1ubuntu4) ...
Starting SmartLink Modem driver for: slamr0.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.

root@Narayan:/dev # ll ttySL*
ls: ttySL*: Aucun fichier ou répertoire de ce type
root@Narayan:/dev # wvdial
--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
root@Narayan:/dev #
``` 

I don't have /dev/ttySL0 peripheral

How can I solve this problem ?

---

### Post by az on 2005-06-06
You are still using a 386 kernel?

---

### Post by EcliptuX on 2005-06-07
[QUOTE=azz]You are still using a 386 kernel?[/QUOTE]
 For the moment, yes.
I prefere to use the modem with succes with a 386 kernel before to try to use it with a k7 kernel (I have a Athlon +2800 processor)

---

### Post by Exigen on 2005-06-14
You're lucky, I can't even get it to work at all.

---

