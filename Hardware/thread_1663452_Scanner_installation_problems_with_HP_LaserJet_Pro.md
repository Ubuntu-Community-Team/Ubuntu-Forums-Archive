---
title: "Scanner installation problems with HP LaserJet Pro M1212nf MFP"
date: 2011-01-09
forum: Hardware
---

### Post by MyLander on 2011-01-09
Dear all,

I purchased an all-in-one Office Printer/Scanner/Fax from HP "LaserJet Pro M1212nf MFP".

Printing under Linux is possible with Foo2xqx driver.

But I am not successful in installing the scanner. In a terminal window, I called as root user the function 'sane-find-scanner' and got the following response:
[INDENT]found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x052a [HP LaserJet Professional M1212nf MFP]) at libusb:002:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
[/INDENT]So, this does not look bad. But when I type in 'scanimage -L', then the response I get is always:
[INDENT]No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
[/INDENT]I assume that Sane cannot not identify the scanner now or does not find the needed driver software
I think that the driver for HP M1120 would be sufficient, because HP M1212 and HP M1120 scanner methods seems to be similar. But how to convince sane to use the HP M1120 driver? Or is there another 'trick'?

In addition: Does anyone know how to get the Fax-function running?

Thanks for your help,
best regards,
MyLander

---

### Post by Brando753 on 2011-01-10
Hey there, I just purchased today a similar model HP M1536dnf which prints, copies, and even duplexes fine in ubuntu. However when I try to scan with sane (through Xsane or Simple Scan) I Just get scanner not found. sane-find-scanner finds the scanner as well while scanimage -L gives the same response. :( any help would be greatly appreciated. :confused:

---

### Post by IcarusR on 2011-01-10
None of the MFPs mentioned in the previous two posts are listed as supported by sane, ie they may be seen by 'sane-find-scanner' but there is no driver (backend).

See the sane supported devices page for support status

[http://www.sane-project.org/sane-supported-devices.html]("http://www.sane-project.org/sane-supported-devices.html")

---

### Post by MyLander on 2011-01-10
Hi Brando753,

what do you mean by 
>  I just purchased today a similar model HP M1536dnf which prints, copies, and even duplexes fine in ubuntu.?

How did you get the HP device to copy (?) and duplex (?) under ubuntu?

Thanks and best regards,
MyLander

---

### Post by Brando753 on 2011-01-10
Hi MyLander,

When I said copies I was referring to copying by placing the sheet in and hitting copy. However for duplexing I simply would print like normal but go to page setup and under two sided select Long Edge (Standard) which would cause it to print on both sides. However I have not gotten the scanner to work :(. Check to make sure your model has automatic duplex. I will look into finding or making if I must a scanner back end, However it will be my first so Im not looking forward to it:(.

Best regards,

Brando753

---

### Post by MyLander on 2011-01-11
Hi Brando753,

I found under [https://alioth.debian.org/frs/?group_id=30186](https://alioth.debian.org/frs/?group_id=30186) in section "sane-backends 1.0.21" the c-source code of the driver software for the HP M1005 and M1120, which might be compatible to your and mine HP devices ("hpljm1005.c" downloadable under [https://alioth.debian.org/tracker/?func=detail&group_id=30186&aid=304559&atid=410366](https://alioth.debian.org/tracker/?func=detail&group_id=30186&aid=304559&atid=410366)).


Its years ago that I compiled my last c-programme ... Let's see.

I have no better news.

Best regards,
MyLander

---

### Post by Brando753 on 2011-01-16
I am looking at that code now :D.

Thanks for the link will be seeing if it is usable or if any modification I can add to make it work. Will keep you informed.

Any SANE developer feel free to add your 2cents still rather new at coding :/

Good Luck,

Brando753

---

### Post by mikebravo on 2011-01-16
MyLander, you said "I purchased an all-in-one Office Printer/Scanner/Fax from HP "LaserJet Pro M1212nf MFP".

Printing under Linux is possible with Foo2xqx driver."

                ------------------------------
I have the same printer and Ubuntu 10.10. I do not care about the scanning but I would like to have printing. Would someone please point me to some noob level instructions for making this printer work?

---

### Post by Brando753 on 2011-01-25
Well the new HPLIP driver seems to have fully supported my printer now and lets me scan as well :) MyLander you should head to the hplip website and install the driver from their site and see if it works.

Best regards,

Brando753

---

### Post by PePas on 2013-04-30
For future reference: printing and scanning worked after running:
/usr/bin/hp-diagnose_plugin
(It installs a plugin that apparently is necessary.)

---

### Post by oldos2er on 2013-05-01
Old thread closed.

---

