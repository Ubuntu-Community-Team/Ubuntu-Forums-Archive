---
title: "Cannot print, cannot see Printers menu element"
date: 2009-12-14
forum: Hardware
---

### Post by patocardo on 2009-12-14
Suddently, two days ago, I couldn't print anymore. Printer is fine (it passed the auto-test), but no printer icon appears when I try to print a document. It happens in all applications.
Moreover, "Printer" menu element in System>Administration does not appear any mores.
Anybody can help me?

---

### Post by Chesamo on 2009-12-14
This sounds pretty serious. Try```
sudo apt-get purge cupsys cupsys-client
sudo apt-get install cupsys cupsys-client
```which will purge and reinstall CUPS (the printing system that Ubuntu uses).

This may shed some light as well:
[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

---

### Post by patocardo on 2009-12-15
There still are not printers menu

---

### Post by patocardo on 2009-12-21
I've installed Ubuntu 9.10 and the problem has gone

---

### Post by hansheijmans on 2009-12-30
I've got the same problem in 9.10. At a certain moment I wasn't able to print anymore. Tried de-installing and installing the printer, but nothing worked. Then I re-installed all cups and hplip related items in Synaptic, but that didn't work out as well. Then I made the mistake by de-installing cups and hplip in Synaptic without making notes which elements were actually de-installed. By that time the "Printers" menu-item was gone. Also after installing as much cups and hplip I could remember I was able to use the printer (at least one problem solved!) but the "Printers" menu item was still gone!
 
Does anyone know what I should mark within Synaptic to get "Printers" back?

---

### Post by hansheijmans on 2009-12-30
Hi all,

I had a look at my laptop's configuration and added the Printing menu item to my desktop (right-click - "Add this launcher to desktop"). Then right-click on it and selected Properties to find out which command is invoked.

Then on my desktop computer I issued the same command with sudo:

```
$ sudo system-config-printer
```And my Printing menu item was back !!!

---

### Post by col48 on 2010-04-29
Thankyou, Hans.

That tip was just what I needed.  Having problems with the scanner function of my MFP and someone had uninstalled various bits and pieces including cups and hplip.  And they thought they'd reinstalled everything, but they hadn't.  Somewhere in the line the printing function had got lost as well, taking with it (or vice versa) the System > Administration > Printing [NB in my case, not Printers] menu.

I installed and ran system-config-printer, which restored the menu and then found two or three cups and hplip packages which needed restoring and suddenly the print queue poured out onto paper.  

Wonderful.

[Still no progress on the scanning, though :(]
[Scanning reappeared when I loaded the latest version of hplip over the one offered by Synaptic.  hp site said ver>2.8.1 was needed, Synaptic gave me 2.6.x]

---

### Post by Ni-el on 2010-06-06
```
apt-get install system-config-printer-gnome
```


Yep, that worked to get the menu item back.
I had uninstalled Ubuntu 10.04 x64, and reinstalled with x32.
For some reason it did not completely install Gnome.
Gracias, Hans

---

