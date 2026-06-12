---
title: "fn f5 / external display"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by cheiz on 2005-08-15
Hi all,
I'm trying to do a presentation but my fn f5 combination for changing the screen doesn't work. I'm Hoary on a Toshiba 5200, nvidia installed, fnfx for toshiba installed, but still no output. 
 :???: 
Changing brightness through function keys does seem to work though.

/usr/share/doc/acpi-support/README.toshiba gives help on enabling ACPI, but again, no fn f5 functionality for me :-x 

From [http://fnfx.sourceforge.net/](http://fnfx.sourceforge.net/) I gather that fn f5 may be quite hardware specific. 

Would anybody know how to proceed from here?

---

### Post by cheiz on 2005-08-17
Looked a bit further and am at a dead end now (and in a hurry...).

It seems to be a specific Toshiba crt_out problem. The video bus signal is send, but the status of crt_out does not change. Description of the problem can be found here:
[http://memebeam.org/toys/ToshibaAcpiVideo](http://memebeam.org/toys/ToshibaAcpiVideo)

I tried all ubuntu acpi_toshiba support (fnfx, toshset and the procedures in README.toshiba) to no avail. I then tried to compile a newer kernel, but the toshiba support in there had a version number older than the one already running  :roll: 
Besides that, compilation failed...

Sorry to say that I see no other option than recover my windows intallation; being able to do a presentation is a core function of my laptop.

---

### Post by coaxx on 2005-12-02
I have the same problem, anybody out there who managed to switch CRT->LCD or switch ON/OFF both?

---

### Post by sunny_nwho on 2006-01-20
I solved the problem but unfortunately my system is not a toshiba i have an ACER and i installed i810switch

---

### Post by Circleback on 2006-05-04
i installed that package i810 on my Acer 5502 laptop but cannot seem to get the switch to work. Any suggestions on how to configure it?

---

### Post by sunny_nwho on 2006-09-09
> **Circleback said:**
> i installed that package i810 on my Acer 5502 laptop but cannot seem to get the switch to work. Any suggestions on how to configure it?
you have to invoke the program explicitly running it

---

