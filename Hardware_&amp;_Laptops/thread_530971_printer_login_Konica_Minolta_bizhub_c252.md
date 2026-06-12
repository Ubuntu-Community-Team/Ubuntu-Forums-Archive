---
title: "printer login: Konica Minolta bizhub c252"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by hippojazz on 2007-08-21
Hi, 
I'm trying to print to a Konica Minolta bizhub c252, it requires user authentication but I can't find anywhere in the printer settings to include my username and password (as set on the printer, not my system). 
I'm using kubuntu gutsy (had same problem on feisty). 
in the system settings I can add the printer using 'other printer types' for the backend selection, and it finds socket://xxx.xxx.xxx.xxx  (xx... is correct ip address). 

I can view the job queue on the printer's http page, and the print jobs are sent, but return the error:

job no | user name | document name | result
1854   | PRINT        |   ********          |  Deleted Due To Error

from the printer control panel I found out that this error is a 'login error'. for the windows drivers there is a user authentication panel in the configuration, but there is no such option in the cups drivers. 

does anyone know how to get user authentication working for this printer with linux?

---

### Post by Damopuff on 2007-08-23
Very same issue here with the Konica Minolta C252.

Have tried many things such as passing the username along with the URI:
[http://username@printer:631/ipp](http://username@printer:631/ipp), lpd://username@printer, etc.
but no luck, still comes up as username PRINT

So the next step was to cheat and add a user called 'PRINT' to the printer.
Well, it gets further but unhappily, it brings up an error on the panel saying 'no account set for group auth'.  I've been searching high and low for anything regarding this error and coming up empty handed.

Of course, works all well when we have user authentication disabled but we won't go there.

If anyone has any further ideas, I'd be really keen to hear them as well.

 - Damian

---

### Post by ejolson on 2007-10-31
We have a bizhub 750 here.  I can totally confirm this problem.

---

### Post by Damopuff on 2007-10-31
Forgot to chronicle the last attempts to get our BizHub C252 printing like a real office printer from CUPS:

The aforementioned 'no account set for group auth' turned out to be due to colour printing restrictions.  It was a bad way of saying, "you're trying to print colour and not permitted" so when I set CUPS to only print Black & White and had the user "PRINT" set up on the printer, it prints (But obviously in B&W).  Changing permissions on the the Konica's PRINT user to allow colour also works but makes the whole printer logging in redundant as there would be nothing stopping the rest of the office goons using the username 'PRINT' to get colour.

While I can print in B&W and Colour if really needed, I chalk all this up to being wonky drivers from Konica Minolta.

---

### Post by dad1001 on 2007-11-28
You need to contact your KMBS customer service reps and get the Konica Minolta Print Utility (KP). It's free and specifically designed for the Linux user who wants all the functionality of their copier available.
-d

---

### Post by Damopuff on 2007-11-29
Cheers for the input - I found and downloaded the KP Print Utility for UNIX.
There is version 1.5 for debian version 2.x and a 'new' version of 1.6 for RPM-based and Solaris (SPARC-only) systems.

I picked up the version 1.6 package.  Humourously, this package was "KONICAMINOLTA Print Utility for UNIX ver1.6.exe".  Luckily, this was simply a self-extracting zip and unzippable via wine.  After installing using alien+dpkg, I inspected the installed binaries and accompanying pdf/readme documentation.  However, it would appear to only work on LPR/LPRng systems and in addition to this, I cannot find information regarding setting authentication options such as username/passwords in the provided information which are required for our printer setup (and if it wasn't, we'd be content with just the PPD which prints out fine using aforementioned hackery)

 - Damian

---

### Post by tbook on 2008-02-06
I am having the same problem - it would be good if there were authentication support built into ubuntu.  Should this be listed as a bug / feature request somewhere?

---

### Post by Damopuff on 2008-02-06
> **tbook said:**
> I am having the same problem - it would be good if there were authentication support built into ubuntu.  Should this be listed as a bug / feature request somewhere?
I dare say that this is pretty much a printer or printer driver issue and not Ubuntu/CUPS' fault.  It's just Konica Minolta not putting any effort into supporting linux.  I mean - you have this business printer and it'll let you print but when you go and set up fairly important settings such as user authentication it all goes out the window.

As stated before, the best/worst workaround is setting up the printer with a user called PRINT and have no password on it.  If your business is using authentication to simply lock down colour printing, this works ok and if you *really* need colour and simply can't use a windows client, log into the printer administration control panel and remove the colour restriction (of course, no good if you have no access to the printer's administrative features).

We're sorta stuck for now, folks.  Of course, if anyone does come up with a magical solution I am more than all ears.

---

### Post by luispinho on 2008-02-18
Download this file 

[http://download2.konicaminoltaeurope.com/C1256F57004A7C1A/LogDwl?OpenAgent&07E8CB8CFCDC2E27C125731E00329AF4/$File/dbhc252psc201en.tgz]("http://download2.konicaminoltaeurope.com/C1256F57004A7C1A/LogDwl?OpenAgent&07E8CB8CFCDC2E27C125731E00329AF4/$File/dbhc252psc201en.tgz")

extract the files and do the manual installation.
The way to configure the driver is very bad, the driver only accepts numbers for names and passwords, but it works.

regards

---

### Post by Damopuff on 2008-02-18
Much appreciated.  Works a treat.

Of course, after all that I/we really should have asked our reps directly.

More importantly, it works - thanks luispinho

---

### Post by GoCool on 2008-04-12
Thank you luispinho, you really don't know what your help meant to me. I thought I was fighting a losing battle to convince my non profit organization to go with ubuntu. And configuring bizhub250 was the biggest hurdle, even though I did get the ppd file for 250, it did not have the authentication in it.
After reading your article, I went ahead and configured the c252 drivers for c250 and it worked like a charm.
Thanks again.

---

