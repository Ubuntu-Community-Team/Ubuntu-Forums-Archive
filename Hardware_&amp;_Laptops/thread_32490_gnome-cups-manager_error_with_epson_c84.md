---
title: "gnome-cups-manager error with epson c84"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by dwellersire on 2005-05-08
After following [directions](http://www.ubuntuforums.org/showthread.php?t=368&highlight=epson+c84) to get the printer to get drivers for my epson c84 printer, I get an error from gnome-cups-manager when I try to add it.

To reproduce:  
[list]
[*]run gnome-cups-manager
[*]Use detected printer (Epson Stylus C84) and hit forward
[*]hit apply
[*]the window disappears
[*]the printer does not show up
[/list]

Command line output:
```

** (gnome-cups-manager:22034): WARNING **: failed request with status 1030

** (gnome-cups-manager:22034): WARNING **: failed request with status 1030

** (gnome-cups-add:22049): WARNING **: failed request with status 1030

** (gnome-cups-manager:22034): WARNING **: failed request with status 1030
Selected ppd file = epson24.ppd
Selected ppd file = gimp-print/4.2/escp2-c84.ppd.gz

** (gnome-cups-add:22049): WARNING **: failed request with status 1030

** (gnome-cups-add:22049): WARNING **: failed request with status 1280

** (gnome-cups-manager:22034): WARNING **: failed request with status 1030

** (gnome-cups-manager:22034): WARNING **: failed request with status 1030

** (gnome-cups-manager:22034): WARNING **: failed request with status 1030

```

For some reason it worked find on my old PC (Pentium 3, Tyan Mobo) that run ubuntu (hard drive recently died) but will not work on my main PC (Athlon XP, Nforce2 Mobo).

Would appreciate a hand  :)

---

### Post by David Haas on 2005-05-09
Perhaps my summary of those early "directions" in the Forum might help you install the Epson Stylus C84--I used the following steps to install my Epson Stylus C82. I don't, however, understand the WARNING messages you noted. You should make sure that all the "cupsys" and "foomatic" packages are installed by checking this out in Synaptic package manager: System>Administration>Synaptic package manager. When they are installed--they probably already are--work next in the printer GUI--System>Administration>Printing--to select your printer under the "driver" heading and then click "install driver." Here you must click through the files menu to reach the PPD file for your printer. It's directory path is /usr/share/cups/model/gimp-print/4.2. In the 4.2 directory, you'll see the PPD file for your printer:  escp2-c84.ppd.gz.  Selecting this by clicking "open" will decompress the file and make it operative. Well, let us know how it goes. If this standard set-up doesn't work, then more-advanced users should be able to help you.
David

---

### Post by dwellersire on 2005-05-09
I tried browsing for the file like David said and came up with a dialog box:
 "Error - Line longer than the maximum allowed (255) characters) at 1:'/usr/share/cups/model/gimp-print/escp2-c84.ppd.gz'"

I tried going adding a Epson C82 and a C83 and both worked fine with no errors in the console, and they showed up immediately in gnome-cups-manager. (System>Administration>Printing)

However, I tried the C84 again and got: 
** (gnome-cups-add:16187): WARNING **: failed request with status 1280
and it did not show up.

So this time no 1030 status errors, just the 1280.

Package foomatic-db-engine is v3.0.2-2 and cupsys is v1.1.23-1ubuntu12

---

