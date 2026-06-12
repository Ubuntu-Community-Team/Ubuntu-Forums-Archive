---
title: "Epson NX415 Debian/Gnome mini-Howto"
date: 2010-03-30
forum: Hardware
---

### Post by addux on 2010-03-30
First off, The reason I like gutenprint better than any other I have tried, is that for this printer, gutenprint's driver offered the most options for print quality settings and things like this.
Also....I am using Debian 5.04 and Gnome but this should be very similar for Ubuntu

This is what worked VERY well for me:

Install the latest version of gutenprint via synaptic or download it from their website <----(requires you to build from source)
Install CUPS
Install sane and sane-utils via synaptic
Download and install iscan ([http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do))
 -The Scanner drivers are at the bottom of the page

**Setting up Permissions is Crucial for Success**
[B]System
Administration
Users and Groups[/B] (enter password)
Highlight your user
[B]Properties
User Privileges[/B]
If all is well you will see some checked and unchecked boxes.  Find the ones that say '**Use Scanners**' and '**Configure Printers**'
Maker sure there is a check in each of these
Restart cupsd and saned

Ubuntu:
$ sudo /etc/init.d/cupsd restart
$ sudo /etc/init.d/saned restart
Debian:
# /etc/init.d/cupsd restart
# /etc/init.d/saned restart


Go to CUPS 'homepage' in you favorite web browser@ 127.0.0.1:631
[B]Administration
Find New Printers[/B]
You should see something along these lines as an option:
"EPSON USB2.0 MFP(Hi-Speed) (Gutenprint USB Printer #1)"
Click '**Add this Printer**'
Name it whatever you want-**Continue**
Now you will see a large list; choose:
"Epson Stylus NX415-CUPS+Gutenprint v5.2.5(en)"
or whatever is the latest version that you have is

It will ask for a password
You should be good from there

If there is anything wrong with this in Ubuntu let me know an I can fix the howto, if it works let me know too!

It is also worth noting that Ubuntu does a pretty good job automagically installing this printer if you are connected to the internet.  But as stated by other people it will try and re-install the printer every time you unplug and plug back in.

---

### Post by addux on 2010-03-31
I guess it is worth adding that plugging in this printer while running Debian 'Testing' "just worked".  Default install of Debian and gnome...maybe I am a little behind the times!

---

