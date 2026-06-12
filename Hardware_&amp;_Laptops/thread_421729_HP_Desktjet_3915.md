---
title: "HP Desktjet 3915"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by bren21 on 2007-04-24
Hi, I am having several issues with my HP Deskjet 3915 on Ubuntu. 

First, for some reason whenever it trys to print something it always prints slightly slanted

Next, after it prints something it wont let go of the paper and proceeds to rock it back and forth for several seconds. I have to remove it from the printer, because it thinks it is jammed.

The colors are also slightly messed up, however that is not as big of an issue.

I know the printer works fine, because whenever I print something with it on WIndows, it works perfectly.

If anyone has a fix for this,  I would appreciate the help.

---

### Post by bren21 on 2007-04-24
Anyone have a problem like this?

---

### Post by ramjet_1953 on 2007-04-25
How did you install this printer?

Go into Synaptic and ensure that the following packages are installed

[COLOR="Blue"]hpijs
hplip
hplip-data[/COLOR]

Also check if these packages are installed:

[COLOR="Blue"]python-qt3
python-qt3-gl[/COLOR]

If not, install them

Click on [COLOR="Blue"]System>Administration>Printin[/COLOR]g
A window should open, showing your installed printer.
[COLOR="Blue"]Right click on it[/COLOR] and when the box opens, [COLOR="Blue"]click on remove[/COLOR].

In a terminal type in [COLOR="Red"]sudo hp-toolbox[/COLOR]
HP Toolbox should open and tell you that you don't have any printers installed. Just follow the directions and you should be able to install your printer and also have full control over it, including the monitoring of ink levels, using HP Toolbox.

An icon for HPLIP Toolbox will be placed in either your [COLOR="Blue"]System>Preferences[/COLOR] or [COLOR="Blue"]SystemAdministration[/COLOR] Menu, depending upon the version of Ubuntu that you have installed.

Regards,
Roger :cool:

---

### Post by bren21 on 2007-04-25
Unfortunately, this did not work for me :(  The page still prints out slanted (although now it is slanted the other way) and still jams up at the end.

---

### Post by bren21 on 2007-04-28
Anyone else have an idea? It is annoying having to restart my comp and log into windows just to print a page of text:(

---

### Post by bren21 on 2007-05-02
Yeah...still no solution.

---

### Post by phidia on 2007-05-02
[http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_3915](http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_3915)

Try the above link and make sure you have the latest drivers installed.

---

