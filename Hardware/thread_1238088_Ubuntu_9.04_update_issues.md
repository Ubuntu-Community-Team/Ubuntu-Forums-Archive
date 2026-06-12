---
title: "Ubuntu 9.04 update issues"
date: 2009-08-12
forum: Hardware
---

### Post by cezarica on 2009-08-12
Hi, I've recently upgraded to 9.04 and problems started to pop-up over the sudden:

1. Printer.. my printer was working fine with Cups and HPLip. After the update to current version 1.3.9-17ubuntu3.2 for Cups and 3.9.2-3ubuntu4 for HPlip when I run 'hp-check -t' i get an error:

```

error: Unable to locate models.dat file

HP Linux Imaging and Printing System (ver. 0.0.0)
Dependency/Version Check Utility ver. 14.1

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.
2. Run-time check mode (-r or --run): Use this mode to determine if a distro
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball
has the proper dependencies installed to successfully run.
3. Both compile- and run-time check mode (-b or --both) (Default): This mode
will check both of the above cases (both compile- and run-time dependencies).

Saving output in log file: hp-check.log

Initializing. Please wait...                                   |Traceback (most recent call last):
  File "/usr/bin/hp-check", line 199, in <module>
    core.init()
  File "/usr/share/hplip/installer/core_install.py", line 386, in init
    self.distro_name = self.distros_index[self.distro]
KeyError: 0

```

2. If I restart the PC then the Samba service doesn't start or something, I have to manually restart it in order to work.

3. I connect to the headless PC via a VNC server so I use the keyboard, monitor and mouse attached to the PC I'm connecting from. Before the upgrade the keyboard was running fine, had no issues with it, but now some keys are mixed between each other while some continue to work properly. At System > Preferences > Keyboard then 'Layouts' tab I see a US 105-key keyboard there. Keyboard model is 'Generic Keyboard'. Tried with a different layout but nothing changed.

What should I do now? :confused:

Edit:

Cups was bitching about not finding the /etc/hp/hplip.conf file. I copied the existing /etc/hp/hplip.conf.dpkg-dist to /etc/hp/hplip.conf and now is working. :D

But now I have a different issue with it. Upon a 'hp-check -r' it warns me:
```

Aug 12 10:53:08 Delta python: hp-check[30736]: warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

```
so, from Cups web gui if I modify the printer HP LaserJet P3005 to be device "HP Laserjet P3005 USB CNF1B32557 HPLIP (HP LaserJet P3005)" i get this:
```

Aug 12 10:53:08 Delta python: hp-check[30736]: warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
Aug 12 10:54:25 Delta kernel: [61529.550374] usblp0: removed

```
and now the printer doesn't do anything, unless I replug the USB cable attached to it. If I'll modify the device from Cups web gui as "HP LaserJet P3005 USB #1 (HP LaserJet P3005)" it's working fine with no issue, apart that 'hp-check -r' warning.

In both cases it's the same Manufacturer "HP" and Model "HP LaserJet p3005 hpijs (en)".

Later edit: Let's say I've *fixed* the 3rd issue. I just purchased a KVM Switch from D-Link, connected all the cables and the keyboard is working fine when I'm switching to it.

Now I need some help with that Samba service..

---

