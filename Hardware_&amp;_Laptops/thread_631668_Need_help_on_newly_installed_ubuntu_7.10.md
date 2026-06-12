---
title: "Need help on newly installed ubuntu 7.10"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by CarstenA on 2007-12-04
Hi

I just installed above version and had it restarted 3 times (1 time because I changed to the closed nvedia driver and wanted to be sure it was working) 1 time to do updates where out of 110 updates it only got 18 updates installed before it all of a sudden rebooted.. and now I am having problems, it seems to have ****** my screen and graphics driver settings because I can only run in low res unlike after the first reboot where it looked nice...

But now:
When trying to update I get this:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Trying this in a terminal:
carsten@carsten-laptop:~$ su dpkg --configure -a
su: unrecognized option `--configure'

Usage: su [options] [LOGIN]

Options:
  -c, --command COMMAND         pass COMMAND to the invoked shell
  -h, --help                    display this help message and exit
  -, -l, --login                make the shell a login shell
  -m, -p,
  --preserve-environment        do not reset environment variables, and keep
                                the same shell
  -s, --shell SHELL             use SHELL instead of the default in passwd

carsten@carsten-laptop:~$ 

Hardware is a acer aspire notebook 1522WLMI 

Can someone tell me exactly what to do? I am rather new at this...

Ow / funny, keyboard layout is for some reason changed after update from danish to US english... odd...

---

### Post by Yellow Pasque on 2007-12-04
Use sudo in Ubuntu instead of su.

```
sudo dpkg --configure -a
```

---

### Post by CarstenA on 2007-12-08
Thanks, it worked quite well :)

But now a few days later I got different kind of problem because my laptop shut down due to overheating while upgrading open office... and now I got this:

carsten@carsten-laptop:~$ sudo dpkg --configure -a
[sudo] password for carsten:
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gnome
 openoffice.org-impress
 openoffice.org-base
 openoffice.org-math
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-calc
 openoffice.org-writer
 python-uno
carsten@carsten-laptop:~$

What command should I use to "redo" them ?

Thanks in advance!

---

### Post by Yellow Pasque on 2007-12-08
Do a:
```
 sudo apt-get clean 
```
and then try proceeding with openoffice install.

---

### Post by CarstenA on 2007-12-08
Many thanks :)

---

### Post by ctt1wbw on 2007-12-08
Also, did you check out the ubuntuguide for installation help?  Just google it or find it on Ubuntu homepage.  It's a great help.

---

