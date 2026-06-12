---
title: "Docuprint  CP105b"
date: 2012-03-22
forum: Hardware
---

### Post by ksadil on 2012-03-22
Hey, I bought one of these FujiXerox DocuPrint CP105 b printers, looks like it is a GDI printer without cups support. There is a  i386 rpm supplied driver. Not sure what's happening for support, but had an idea for an interim work around. The plan is: 
(1)Print pdf files to s shared drive on windows
(2) Have a python script running on the windows box to poll for pdf files in the shared directory and print them if they appear



Graham King's blog has some code to print in windows here:
[http://www.darkcoding.net/software/printing-word-and-pdf-files-from-python/](http://www.darkcoding.net/software/printing-word-and-pdf-files-from-python/)

Thoughts? Are there better alternatives?

Thanks,
Kim

---

### Post by _salem_ on 2012-08-19
I have just bought this printer too. Didn't check compatibility first though :(

Any news on drivers for this in ubuntu/linux since March?

---

### Post by ksadil on 2012-08-19
Unfortunately I did not find a solution. I have tried the printer under Ubuntu, Win7 and OSX; and OSX works the best.

---

### Post by _salem_ on 2012-08-19
yeah I spent hours last night trying all sorts of other Xerox drivers and manual driver pull aparts and reassemble. no luck. So I'm just going to install Windows xp on an old netbook I never use anymore and use it as a Wi-Fi print server.

---

### Post by ksadil on 2012-08-19
I  tried the same thing bit the combination of netbook and printer kept locking up. Now hooked up to a Mac.

---

### Post by hermantog on 2012-10-06
just use xerox phaser 6000b driver

---

### Post by ksadil on 2012-10-06
> **hermantog said:**
> just use xerox phaser 6000b driver

but... there is no 64bit 6000b driver :(

---

### Post by Anthony Fok on 2013-09-01
Hello,

You might also like to read this thread:
* Fuji Xerox DPCM205FW laser multifunction: [http://forums.whirlpool.net.au/archive/1792647](http://forums.whirlpool.net.au/archive/1792647)

And search for either "CP205" or "foo2hbpl". It turns out that, in Ubuntu 13.04, the printer-driver-foo2zjs package comes with /usr/bin/foo2hbpl2 and has experimental support for CP205 (and presumably CP105b and CP205w too).

See also the upload to Debian (hence Ubuntu) which added CP205 support:
* [http://lists.debian.org/debian-printing/2013/03/msg00030.html](http://lists.debian.org/debian-printing/2013/03/msg00030.html)

Cheers,
Anthony

---

### Post by Anthony Fok on 2013-09-01
Sorry, I should have read more carefully... I just noticed on [http://foo2hbpl.rkkda.com/](http://foo2hbpl.rkkda.com/) this piece of information:

[INDENT]Fuji-Xerox cp105b: Unsupported. Uses HBPL version 1[/INDENT]

Don't know if there is new development since then, but worth trying to see if CP105b works or not...

Nevertheless, if it indeed does not yet work, sorry for giving you false hope.

But perhaps you could help with development using /usr/bin/hbpldecode ?  :-)  <grin, duck, run>...

---

### Post by Iowan on 2013-09-01
Closed - old thread.

---

