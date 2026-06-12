---
title: "WORKING ink monitor for Epson Stylus SX100 in Ubuntu 9.10?"
date: 2010-02-25
forum: Hardware
---

### Post by Nightstrike2009 on 2010-02-25
Hiya everyone 

This one is driving me mad, I have tried various ink monitors on Ubuntu (Inkblot & Mtink) to name just two, they either don't detect my printer or fail to realise its connected. This is one of the few programs I still have to use windoze to check and resent this fact, surely something like this should be built into Ubuntu as standard. (The SX100 is detected and prints in Ubuntu but cannot check the ink levels with the driver supplied)

Does anyone know of an ink monitor utility that actually works on Karmic 9.10?

---

### Post by Nightstrike2009 on 2010-02-25
Huh ignored again eh? never mind I ve found one :-)

Its called Escputil and is a terminal program (couldn't find a working GUI version)

From karmic repository you want to download & install these files:

escputil_5.2.4-0ubuntu2_i386.deb
libreadline5_5.2-6_i386.deb

Once installed then

TO CHECK PRINTER:

In terminal type:

sudo escputil -d -r /dev/usblp0

(Your printer should then show in terminal)

TO CHECK INK LEVELS

In terminal type

sudo escputil -i -r /dev/usblp0

That's the best I can find for now least i can check ink levels someway now ;-)

---

### Post by Nightstrike2009 on 2010-02-25
Just found a GUI for it too (Stylus Toolbox):

from [http://sourceforge.net/projects/stylus-toolbox/files/]("http://sourceforge.net/projects/stylus-toolbox/files/")

you need:
stylus-toolbox_0.2.7-1_all.deb     (Sourceforge)
python-pexpect_2.3-1_all.deb       (From Ubuntu repos)

Once downloaded and installed

1) CREATE A LAUNCHER (doesn't appear to install one by default)

Right click on desktop, then select "Create launcher"

Name :		Ink Level Monitor
Command:	/usr/bin/stylus-toolbox	

(Click Spring box to change Icon)

2) SET UP STYLUS TOOLBOX PREFERENCES

Device port:		/dev/usb/lp0
Model Settings: 	(Select model from list)
External Programs:	/usr/bin/escputil


Thats it you now have a working ink monitor with GUI :-)

---

