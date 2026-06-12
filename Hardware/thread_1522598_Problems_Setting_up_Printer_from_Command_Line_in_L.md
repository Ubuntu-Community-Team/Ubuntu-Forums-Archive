---
title: "Problems Setting up Printer from Command Line in Lucid"
date: 2010-07-02
forum: Hardware
---

### Post by lachild on 2010-07-02
Hey Everyone,

Was wondering if someone could give me hand.  I am attempting to install a printer via the command line and I keep running into an issue.  After installing the driver via dpkg and setting up the printer via lpadmin, I attempt to print a test page and the printer complains about the data it recieves.  Now the odd part is if I open up the printer screen in gnome and go to the properties screen for the printer a "Print test page" from here works.  Oddly enough after I print from the GUI without making any changes the printer works fine on the command line.

The problem is, this is going to be setup on a server with no GUI so I need this to work without having to first open the GUI's printer settings.

Does anyone have any idea what the GUI is changing or setting that lpadmin is not?

I've checked lpoptions before opening the GUI and after and they are both identical.

Here's the commands to setup:
1. Install the .deb packages
2. Run the following commands

```

#setup the printer
lpadmin -p "QL-580N" -E -v usb://Brother/QL-580N -m brql580n.ppd -o media=38X90 -o BrPriority=BrQuality -o media-default=38X90 -o BrPriority-default=BrQuality

#print test page
lp -d QL-580N /usr/share/cups/data/testprint

```


Thanks in advance,
LaChild

---

### Post by dino99 on 2010-07-02
look at this link, scroll down to "printers"

[http://www.mygooglest.com/fni/ubuntu.html](http://www.mygooglest.com/fni/ubuntu.html)

---

### Post by lachild on 2010-07-02
Thanks for the response.  I guess I could use the web client.  I was kind of hoping to set this up in an install script of some kind as I have over a dozen of these systems that I need to setup. 

Do you know if there is something the GUI (system-config-printer) app does to ppd file?  It's an old ppd file, so I'm wondering if it just corrects it or upgrades the file to one the current version of cups understands?

It just seems so weird that the printer won't print until I print a test page from the GUI.

Thanks again,
LaChild

---

