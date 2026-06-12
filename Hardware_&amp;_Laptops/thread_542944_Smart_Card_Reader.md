---
title: "Smart Card Reader"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by mepaco on 2007-09-04
I'm trying to get my Cherry ST-1000U Smart Card Reader working under Ubuntu 7.04.  I've searched around and installed a few things but so far I'm not having any luck.  It is the only thing that makes me boot into Windows sometimes so I would love to get it working.  Basically, I have two questions:

1) If I get it working, will the terminal services client forward the device to the server.  The Windows client allows the server to access the card reader so I can login to the server using the smart card.  If the Ubuntu client doesn't support that then there really isn't any point in trying to get it to work.

2) What all should I have installed to get this working?  So far I have added (through the repositories) libccid as well as pcsc and some related tools.  I really have no idea what I should be installing here so any help is welcomed.

Thanks in advance for any assistance you can provide.

-Paco

---

### Post by mepaco on 2007-09-05
Really ... nobody?!  Is there a more appropriate place to ask for smart card reader help?  Can anybody even point me in the right direction?

-Paco

---

### Post by PeterF on 2007-09-05
> **mepaco said:**
> Really ... nobody?!  Is there a more appropriate place to ask for smart card reader help?  Can anybody even point me in the right direction?

-Paco

A quick google didn't return a simple answer (I assume you did it yourself). From what I found it's a USB device you can use the lsusb command in the terminal to see if the reader is recognized and with the result from that google for a driver.
I own a 6 in 1 card reader where I can't find a driver for, by searching this way I found I wasn't the only one so I gave up.

---

### Post by mepaco on 2007-09-05
> **PeterF said:**
> A quick google didn't return a simple answer (I assume you did it yourself). From what I found it's a USB device you can use the lsusb command in the terminal to see if the reader is recognized and with the result from that google for a driver.
I own a 6 in 1 card reader where I can't find a driver for, by searching this way I found I wasn't the only one so I gave up.

Yeah, I definitely spent some time with Google.  'lsusb' shows the device as a Omnikey AG Cardman 2020 and I found what appear to be drivers [at this site]("http://www.linuxnet.com/sourcedrivers.html").  I followed the directions but when I ran the install script I got the following error:

[INDENT]Installing OMNIKEY Cardman USB Smartcard reader...

At this time the Kernel 2.6.20-16-generic is not supported!
Please contact OMNIKEY AG for further details.
(e-mail: [email]Thomas.Bruendl@omnikey.com[/email])
[/INDENT]

So, I'm stuck as well.  I'll see if I can get any help from that site but I was thinking it might be something with how it sees my kernel (the whole generic thing).  Anyway, thanks for the advice.  If anyone has any other suggestions, I'm willing to try about anything at this point.

-Paco

---

### Post by kukaraja on 2007-09-09
Try here: [http://omnikey.aaitg.com/index.php?id=69](http://omnikey.aaitg.com/index.php?id=69)

They have newer drivers, also for 2.6.x kernel

---

