---
title: "Printing via lpr"
date: 2005-09-13
forum: Hardware &amp; Laptops
---

### Post by kamstrup on 2005-09-13
I've done a server install, and configured my printer through my browser on localhost:631 (by adding the *cupsys* user to the *shadow* group). When I print a test page from the CUPS web interface everything works fine, but when I "lpr myfile.ps" from the command line, the printer just prints out the post script commands; ie.

```

%!PS-Adobe-3.0
%%Title: stdin
%%For: Mikkel Kamstrup Erlandsen
%%Creator: a2ps version 4.13
...

```
Printing from Abiword does the same, though printing from Gnumeric does work :-S I don't get it...

Is there something about that lpr must point to a cups-version of lpr (my memory is bad...)?? Anyway 
```
ls -l /usr/bin/lpr
-rwsr-sr-x  1 root lp 24120 2005-05-03 11:27 /usr/bin/lp
```

Any hints (or suggestions) on how to get my printer back on track is appreciated!

PS: Not that I think it matters but my printer is a HP LaserJet 4P, and has been working fine under Linux for many years.

EDIT: When using XFCE as my desktop I am able to print from Mousepad when I set CUPS as my printing system from the XFCE control panel.

---

### Post by kamstrup on 2005-10-25
I *finally* sorted this out myself...

I had to install the cupsys-bsd package. It provides another lpr-command which talks correctly to cupsd.

So basically do:
```
sudo apt-get cupsys-bsd
```
and you're set.

---

