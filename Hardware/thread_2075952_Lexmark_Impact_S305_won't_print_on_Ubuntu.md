---
title: "Lexmark Impact S305 won't print on Ubuntu"
date: 2012-10-25
forum: Hardware
---

### Post by Ericj1186 on 2012-10-25
I hate printers a lot. For whatever reason, I have the worst luck with them.

I bought this printer about a year ago. It worked fine on Windows for a while, but despite saying compatible with Linux, I could ever get it to work on Linux at all. Wifi printing is a bust.

After setting up the wifi on the printer via Windows, I downloaded the three driver files from the [Lexmark website]("http://support.lexmark.com/index?page=product&segment=DOWNLOAD&productCode=LEXMARK_IMPACT_S305&locale=en&userlocale=DE#1"), one for the scanner, one for the printer, and one for the PPD, titled Lexmark Injet Legacy. Since I am on Ubuntu 12.10, I had to get the files for 12.04. I installed the drivers, and the only difference is I can see the printer via the Printing set up under settings. I try to print, and I received a status of "Stopped - Printer Warning" The only other information in this window is "Printer 'Lexmark S300-400 Series': 'cups-insecure-filter.'" Under "Printing" the printer logo has a green check in the top left corner of the image and a red exclamation point in the bottom right of the same logo.

Per one set of instructions, I ran

```

sudo chown -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/backend

```

This had helped a lot of people with this error, but mine persisted. A variation of this I tried was

```

sudo chown -hRv root /usr/lib
sudo chgrp -hRv root /usr/lib

```

I am still having the same printer lockup. Can anyone help me out?

EDIT: I plugged the printer into my laptop, and the printer shows up under Printing, but it has the red exclamation point. The errors are the same.

---

### Post by StaRetji on 2012-10-25
Same problem here with S305, going nuts...

---

### Post by Ericj1186 on 2012-10-25
What have you tried?

I have never had any success with this printer either wifi or plugged, so I'd love to hear if I have done everything.

---

### Post by DJ_Max on 2012-11-12
I thought this was just me, after I upgraded to Ubuntu 12.10 from 12.04, my Lexmark Impact S305 refuses to print. I re-installed the drivers from Lexmark.com to no avail. My guess is we have to wait unti Lexmark releases drivers for 12.10.

---

### Post by offgridguy on 2012-11-12
Trying to get a printer to work with linux can be a frustration, mainly due to lack
of linux compatible drivers or problems getting them installed.
      I don't have a lexmark myself but did a thread search using lexmark printer
and found quite a few threads there.  You may want to check it out.
  Good luck.

---

### Post by massasauga on 2013-01-06
I'm running into the same problem. I have a Lexmark Impact S305. It worked flawlessly on previous versions of Ubuntu. I also had it working with Linus Mint, until I tried setting it up on Linux Mint with KVM. I'm not sure if it is Lexmark's newest driver, or Ubuntu 12.10. I hadn't been having problems like this prior to upgrading Ubuntu to 12.10, but the driver I downloaded before was older and the utility used to show ink levels. So something changed with Lexmark, or the Ubuntu internal printer setup has changed.

---

### Post by djjackobyte on 2013-01-21
> **massasauga said:**
> I'm running into the same problem. I have a Lexmark Impact S305. It worked flawlessly on previous versions of Ubuntu. I also had it working with Linus Mint, until I tried setting it up on Linux Mint with KVM. I'm not sure if it is Lexmark's newest driver, or Ubuntu 12.10. I hadn't been having problems like this prior to upgrading Ubuntu to 12.10, but the driver I downloaded before was older and the utility used to show ink levels. So something changed with Lexmark, or the Ubuntu internal printer setup has changed.

[http://ubuntuforums.org/showthread.php?t=2082570](http://ubuntuforums.org/showthread.php?t=2082570)

See the bottom of this thread.  Remove the printer and re-install.

Worked for me.

---

