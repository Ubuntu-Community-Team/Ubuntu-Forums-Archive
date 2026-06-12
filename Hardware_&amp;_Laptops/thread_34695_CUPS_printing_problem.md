---
title: "CUPS printing problem"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by toran on 2005-05-16
Well, I'm having trouble getting a printer working.

I have cups installed, and all, and I went to the printing manager in the KDE control center and clicked "add printer". I chose "local printer", and then chose the USB device corresponding with the printer I was setting up. I then chose the correct driver, and completed the setup. Everything seems to be going fine at this point. Then I try to print a test page. And nothing happens.

A quick look at /var/log/cups/error_log shows the following error:

```

E [16/May/2005:01:15:27 -0500] [Job 1] Unable to open USB device "usb://Brother/HL-5040%20series": No such device
E [16/May/2005:01:15:28 -0500] PID 7386 stopped with status 9!

```

what's going on? I know that there is a device such as " usb://Brother/HL-5040%20series", it's the one I chose from the list when I set up the printer! What's going on?

---

### Post by agds on 2005-05-16
I print to a network UNIX printer, so I can't address your specific question.  However, you may want to have a look at /etc/cups/printers.conf, which helped me in configuring my printing.

---

### Post by lorap on 2005-05-16
hi friend!
all the information about cups printing services you can get here.

[http://www.cups.org/doc-1.1/sum.html](http://www.cups.org/doc-1.1/sum.html)

it's complete source.
have a nice day.
pavel

---

### Post by David Haas on 2005-05-16
Hi toran--What PPD file did you select after selecting your printer model? In Ubuntu Hoary 5.04, I see the following PPD files listed in /usr/share/cups/model/foomatic-ppds/Brother for HL -5040 models: Brother-HL-5040-hl1250.ppd.gz, Brother-HL-5040-hpijs.ppd.gz, Brother-HL-5040-lj5gray.ppd.gz, Brother-HL-5040-ljet4.ppd.gz, Brother-HL-5040-pxlmono.ppd.gz. 
David

---

