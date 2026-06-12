---
title: "How to check ink levels Epson CX8400"
date: 2011-11-22
forum: Hardware
---

### Post by bluexrider on 2011-11-22
I have a Epson CX8400 all-in-one printer.

Printing works fine.
Scanner works fine.
Card reader works fine.

However cannot monitor ink levels.

Recommendations please.

---

### Post by Mark Phelps on 2011-11-23
Sorry, not at my Linux box, so I don't have the links, but I do have an Espon inkjet (R220) and have used all the following successfully to check ink levels:
1) mtink
2) escputil
3) ink  (command line)
4) Libinklevel

---

### Post by bluexrider on 2011-11-23
I've used:

inkblot=sits in the panel and doesn't connect with the printer

mtink=reads levels but reports inaccurate quantiles, says the printer has 6 colors only have 4

ink=command line excites printer but no report

escputil=doesn't work

Libinklevel5=suppose to work with cups but can't find any report


any more suggestions? need all the help I can get

---

### Post by bluexrider on 2011-11-23
> **Nightstrike2009 said:**
> Just found a GUI for it too (Stylus Toolbox):

from [http://sourceforge.net/projects/stylus-toolbox/files/](http://sourceforge.net/projects/stylus-toolbox/files/)

you need:
stylus-toolbox_0.2.7-1_all.deb     (Sourceforge)
python-pexpect_2.3-1_all.deb       (From Ubuntu repos)

Once downloaded and installed

1) CREATE A LAUNCHER (doesn't appear to install one by default)

Right click on desktop, then select "Create launcher"

Name :        Ink Level Monitor
Command:    /usr/bin/stylus-toolbox    

(Click Spring box to change Icon)

2) SET UP STYLUS TOOLBOX PREFERENCES

Device port:        /dev/usb/lp0
Model Settings:     (Select model from list)
External Programs:    /usr/bin/escputil


Thats it you now have a working ink monitor with GUI :smile:

Installed Stylus-Toolbox problem solved

---

