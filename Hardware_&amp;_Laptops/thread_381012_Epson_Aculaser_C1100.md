---
title: "Epson Aculaser C1100"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by derfinsterling on 2007-03-10
Ok, I'm lost.

Yesterday I got my new computer and gladly installed Ubuntu 6.10. The last time I was using Linux at home was with SuSe 8.1 (I think).

So there were some problems with setting everything up, but I managed to solve most of it.
Not the least with the help of this forum here.

But still there's one thing I can't get to work. My printer.

I'm running 6.10, my printer (Epson Aculaser C1100) is plugged in via USB to my Asus router. This works like a charm under Windows, but no dice in Ubuntu.

I used the driver available from Epson (well, actually, the site they link to). Installed the ppd-file, Set up the printer - it won't print.
I tried it with CUPS. I tried it with HP direct. Tried it with LPD. Printer's installed, but it simply won't print.
So I hit the forum here.
Found this:
[http://ubuntuforums.org/showthread.php?t=105590&highlight=aculaser](http://ubuntuforums.org/showthread.php?t=105590&highlight=aculaser)
Tried that, doesn't work, because I have no cups-config. Tried to install that, didn't find it in Synaptic.
I searched more and found this:
[https://launchpad.net/ubuntu/+bug/68183](https://launchpad.net/ubuntu/+bug/68183)
Doesn't work because I don't have those files anywhere on my computer.

What else could I try?

---

### Post by derfinsterling on 2007-03-11
Nobody?

---

### Post by ramjet_1953 on 2007-03-12
You probably haven't enabled the additional repositories in Synaptic.

To do so, follow this:

Click System>Administration>Synaptic Package Manager

It will ask you for your password. Enter it.

Synaptic will open

Click Settings>Repositories

A window will open, headed "Software Sources"

Click on all of the buttons which don't have an 'X" in them.

Click on the dropdown arrow headed "Download From" and select the server closest to you.

Close the window and then re-start Synaptic.

You should now be able to search for and install CUPS.

When you do search, use lower case ie cups

Good Luck!

Regards,
Roger :cool:

---

### Post by derfinsterling on 2007-03-12
Thanks, but I that didn't help:

I alread yhave cups listed in synaptic, I have it installed. Still, I get the error message when I try the solution from the first link, that there is no cups-config found.

Maybe Edgy doesn't have a cups-config anymore, I don't know, but the fact remains that I can't print.

Now I tried to connect to the printer over the good ol' parallel port. Doesn't work either.

Can I quote any logfile that would help?

---

### Post by derfinsterling on 2007-03-12
Ok, it's definitely the printer - I connected my old inkjet Epson Stylus and took a generic driver - it prints (the ink's dried out so I can't tell how good or bad, but the printer gets a signal).

Is there nothing to be done? Without a printer I can't use my computer.:(

---

### Post by derfinsterling on 2007-03-12
Trying to install gets the following output:

```
markus@scubuntu:~/Epson-ALC1100-filter-1.2$ sudo ./configure
Password:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... (cached) gawk
checking for rpmbuild... rpmbuild
checking for cups-config... no
./configure: line 2830: test: =: unary operator expected
configure: error: *** 'cups-config' missing, please install CUPS or fix your $PATH ***
markus@scubuntu:~/Epson-ALC1100-filter-1.2$ 
```

---

### Post by derfinsterling on 2007-03-13
Got it to work, finally!
After searching the forums a little more I could install the drivers using configure/make/make install, then adapted the .sh-file and then I connected not using CUPS, but HPdirect. Works like a charm.

Thanks!

---

### Post by DerBjoern on 2007-03-14
Hi!

And just in case for others who search for the util "cups-config". You need to install the CUPS development files, contained in the package **libcupsys2-dev**.
Got my Samsung ML 1610 working very nicely with Splix now. :-)

Greets,
Björn

---

