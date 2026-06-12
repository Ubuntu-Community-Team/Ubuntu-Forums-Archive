---
title: "Use all functions from a HP multifunction printer"
date: 2008-11-09
forum: Hardware
---

### Post by Hercule_Savinien on 2008-11-09
Hi,


I have a HP multifunction printer/scanner/fax/... (hp psc 950). The printer is working perfectly (using cups+foomatic+hpijs), I never had any trouble with it.

Now i'm trying to use the scanner, but i'm stuck. I tried a bunch of softwares, but I never manage to scan something (well actually, I scanned something one, and I could scan anything else either 10s later or the day after).

I also would like to use the card reader, but I didn't find any suitable tutorial.  I would like to make it work like a USB key (insert a card, and then let it be mount automagically under /media).

I was advised to use the hp-toolbox tool for both. Unfortunately, this doesn't work. Here is what it gives when I run it from the terminal : 

```
hp-toolbox

HP Linux Imaging and Printing System (ver. 2.8.6b)
HP Device Manager ver. 14.0

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Unable to communicate with device (code=12): hp:/usb/PSC_950?serial=ES19RAG1H3WP
warning: Device not found
```

Now, I don't know what I should do next. Am i missing something ?

Thanks,
Hercule.

---

### Post by starcannon on 2008-11-09
Have you tried XSane?

Its in a default install at:
Applications->Graphics->XSane

I have run several different HP multi function printers and XSane has worked on all of them.

GL and let us know.

---

### Post by Hercule_Savinien on 2008-11-11
Hi,

Thanks for your answer.


With xsane, I have the same error : Device not found (this time in a X window, not in a terminal).

---

### Post by Hercule_Savinien on 2008-11-13
Do you think it's a lost cause ? :(

---

### Post by phubert28 on 2010-11-18
I don't doubt this thread is dead, but under 64 but Ubuntu 10.10 I'm having exactly the same problem with Xsane and my HP Officejet 8500 Pro multifunction!

NO help at the SANE site.

I tried registering to report an unsupported device and, although the site said I was successful (email confirmation), when I followed the confirming link all I got was "username not found"

Cool.

Does NOTHING work under Linux????????


Looks like Apple may be my next stop...

---

