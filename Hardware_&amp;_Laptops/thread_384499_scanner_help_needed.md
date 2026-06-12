---
title: "scanner help needed"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by 900donuts on 2007-03-14
my familys canon scanner just got move off the computing front lines(its role filled by a new all in one printer)

this is good news beacuse that mean i can attach it to my linux pc :lolflag: 

i tried pluging it in and crossing my fingers no luck

how do i make this scanner work with ubuntu?

---

### Post by teaker1s on 2007-03-14
most scanners are supported by sane
take a look here
[http://www.sane-project.org/sane-mfgs.html#Z-CANON]("http://www.sane-project.org/sane-mfgs.html#Z-CANON")

---

### Post by stchman on 2007-03-14
> **900donuts said:**
> my familys canon scanner just got move off the computing front lines(its role filled by a new all in one printer)

this is good news beacuse that mean i can attach it to my linux pc :lolflag: 

i tried pluging it in and crossing my fingers no luck

how do i make this scanner work with ubuntu?

It should pop up on the desktop.  I had an old HP scanner and it just appeared.

---

### Post by 900donuts on 2007-03-14
i checked the link 

my scanner is a CanoScan FB 620P

i turned off my computer pluged the scanner back in and turned my computer back on tryed to run xsane and it couldn't find it

the web site said support for my scanner was only recently added 
how do i tell was version of xsane im running

---

### Post by teaker1s on 2007-03-14
is yours a SCSI scanner?

---

### Post by 900donuts on 2007-03-14
no a parrallel port

---

### Post by teaker1s on 2007-03-14
[http://www.sane-project.org/man/sane-canon_pp.5.html]("http://www.sane-project.org/man/sane-canon_pp.5.html")


> To enable automatic detection of your scanner, uncomment the "canon_pp"
       line from /usr/local/etc/sane.d/dll.conf

```
sudo gedit  /usr/local/etc/sane.d/dll.conf
```

---

### Post by 900donuts on 2007-03-15
i the file can't find the dll.conf or the sane.d file
i checked every thing installed about sane through synaptic
lets assume that until this date i hve never touched x sane or had never had any thing to do with scanners on this comupters no installing packages no nothing

---

### Post by 900donuts on 2007-03-15
i down loaded the sane file with the extra backends and found the dll.conf file(am i the only one who thinks this is odd?)

the contents do not seem to match your derections

what do i do now

---

### Post by teaker1s on 2007-03-16
I only quoted the sane manual page I gave you, have a read through it, not all linux distro's keep the files in same location.
what you are looking for is the config file for your scanner in the sane directory to configure it.

you ask about sane version you have
```
gksudo synaptic
```

SETTINGS>PREFERENCES>GENERAL

select show package properties in main window:) 

search "sane" or "xsane" and you will see version beside it and below will show package details and file locations

---

### Post by 900donuts on 2007-03-16
lets assume its not up to date (im away from my home and wont be near my computer for several hours)

what would i do in that case ?

where do i go to get the mpst up to date version?

---

### Post by teaker1s on 2007-03-16
first look in this directory as this is ware my sane config files are
/etc/sane.d
youi may find the config file
or failing that

you could compile from source from here
[http://www.sane-project.org/source.html]("http://www.sane-project.org/source.html")

I wouldn't recommend that you use the debian packages as they may break your system

---

