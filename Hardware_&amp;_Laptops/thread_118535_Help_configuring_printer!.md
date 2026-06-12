---
title: "Help configuring printer!"
date: 2006-01-17
forum: Hardware &amp; Laptops
---

### Post by gravediggers on 2006-01-17
Hi,

Have been trying to get printer working (Epson Sylus C61) from Print Manager in KDE desktop. Don't think I'm picking up a driver when running the wizard. I end up with Local Raw Printer.

Has anyone installed this or similar model, or does anyone know how I can find a driver? Is there a better way to install the printer?

Any help appreciated!:)

---

### Post by gravediggers on 2006-01-18
Here's what's happening.

The printer works, but is just printing pages of (postscript??) code. When I check the printer properties in the Print Manager, and look at the driver, it say Local Raw Driver. So I hit change, pick my printer from the database, choose foomatic+gimp-print(recommended), hit Next and get:

Unable to load the requested driver:
Unable to create the Foomatic driver [Epson-Stylus_C61,gimp-print]. Either that driver does not exist, or you don't have the required permissions to perform that operation.

So then I decided that I would try to configure it manually. I am looking at the CUPS Printing Setup Mini-HOWTO.

```
gravediggers@gandalf:~$ lpinfo -v
...............
direct parallel:/dev/lp0
...............
```

That makes sense cos it was working, even if printing crap!

Then the HOWTO says to check with "/proc/sys/dev/parport/parport?/autoprobe*"
so
```
gravediggers@gandalf:~$ sudo /proc/sys/dev/parport/parport?/autoprobe*
Password:
sudo: /proc/sys/dev/parport/parport0/autoprobe: command not found

```

Am I doing something wrong here?

Did ```
cat /proc/sys/dev/parport/parport*/autoprobe*
``` but that came back with nothing.

I was then instructed (if nothing returned) to reload relevant modules. First I checked they were there.
```
gravediggers@gandalf:~$ lsmod | grep  lp
lp                     11460  0
parport                32072  2 parport_pc,lp
gravediggers@gandalf:~$ lsmod | grep  parport*
parport_pc             31812  1
parport                32072  2 parport_pc,lp
```

It instructed me to do the following:
```
modprobe -r lp parport_pc parport
modprobe lp
```

Now I'm really getting confused - don't I need those other 2 modules (parport, parport_pc)??

---

### Post by Sef on 2006-01-18
From Linuxprinting.org:

> Epson Stylus C61	
Color inkjet printer, max. 5760x720 dpi, works Perfectly		
Recommended driver: gimp-print (Home page)
Generic instructions for: CUPS, LPD, LPRng, PPR, PDQ, no spooler

Link:  [http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C61]("http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C61")

---

### Post by gravediggers on 2006-01-19
Only got to read that reply 17 hours later! Haven't been able to get on to forum all day - must have been down.
 
Have checked out the above link already, but thanks anyway!:) 
 
I just really need to know two things:
1. Do I remove parport and parport_pc modules?
2. Why do I get the error message (that I posted above) from Print Manager?:confused:
 
I have found some info on another post on CUPS administrator lockout. I might check that out also.

---

### Post by gravediggers on 2006-01-19
May as well talk to myself!:( 

decided to try the CUPS web interface. had a few password probs but got them figured ok. 

found that for this printer I could only use CUPS+gimp-print v4.2.7, where as print manager said to use foomatic+gimp-print. I guess it was in the database but not installed. Printer now ok.:) 

pity that i didn't get a few more replies from u guys. I'm trying to learn a bit more about how to configure thing from command line and how things work, not looking for spoon feed to get it working. so i didn't learn a lot from this one.:( 

maybe next time...................?

---

### Post by MJN on 2006-01-20
Gravediggers, I need your help... although I wouldn't be surprised if you were reluctant to give it given you had to tread your path of discovery alone!

I've got a USB Epson Stylus Photo 810 and I'll be damned if I can get the bl00dy installed...

When I go through the Systems Settings > Printers palava and try and install the recommended foomatic driver I'm getting nowhere. Instead, I tried the CUPS+Gimp-Print v4.2.7 driver and whilst all seemed fine and dandy I can't print anything.

I've tried a few suggestions made by others (including the last-ditch-attempt resort to a reboot) but no joy...

Would you be so kind as to elaborate on how you got it working in the end? The bit about passwords for CUPS might be useful (I can browse to localhost:631 but can't authenticate)... Of course, your solution may be of no use to my setup but finger's crossed.. :smile: 

Mathew

---

### Post by gravediggers on 2006-01-20
I think I just fluked it!

what i did do first was:

```
sudo kwrite   /etc/group

```
found the line starting with  "shadow" and at the end added (with no spaces) the word cupsys

then:
```
sudo /etc/init.d/cupsys restart 
```
then went into localhost:631 and logged as root and my root password.
You might need to use your normal password, depending on how you have  setup sudo.

Once i got in to the CUPS thingo, it was easy!:)

---

### Post by MJN on 2006-01-20
Holy moly... The joy of Linux eh?

Just tried everything again, seemingly following exactly the same path as before, and I appear to be getting somewhere....

I used the CUPS+Gimp-Print driver again and this time when I tried a test print it worked! A lot of the ink was missing but I'm putting that down to it having been sat for weeks without being used... probably needs cleaning/purging.

So, for now, I think I'm okay... however I would still be intrigued as to what this CUPS web interface is all about and whether I ought to still be trying to use it, or just stick to using the K printer manager... :confused: 

Mathew

---

