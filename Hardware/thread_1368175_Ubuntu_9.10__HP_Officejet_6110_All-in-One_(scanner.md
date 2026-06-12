---
title: "Ubuntu 9.10 / HP Officejet 6110 All-in-One (scanner not working)"
date: 2009-12-30
forum: Hardware
---

### Post by Beniamin on 2009-12-30
Hello all,

The printer indicated in the title is printing just fine, but when I open XSane to try scanning it gives me the following error:

```
Failed to open device `hpaio:/usb/OfficeJet_6100_Series?serial=MY367F74NY2R': Error during device I/O.
```

A while back I looked into this and I think I discovered that it was a bug, and I couldn't find any way around it.  However, if any of y'all have insight as to how I could get it to work, it would be much appreciated!  Thanks.

---

### Post by exup1000 on 2010-01-06
Hi

I too also have the same error but with an HP Officejet 6210.
I have posted this issue on the printer/scanner tutorial but no one so far can help or suggest troubleshooting steps.

I have also tried this gksudo xsane but no joy.

I have also logged it with the HPLIP website, but not had a response there either.

I am running 9.10.

See here [https://answers.launchpad.net/hplip/+question/94636](https://answers.launchpad.net/hplip/+question/94636)
and here [http://ubuntuforums.org/showthread.php?t=184838&page=15]("http://ubuntuforums.org/showthread.php?t=184838&page=15")

---

### Post by bhmildy on 2010-06-30
This may not help you, but I'm running 10.04, and OJ 6210 installed automatically.  I've also run it under 9.10 without problems.
I always go to HP and download and install latest hplip (because I like to know the ink levels, although that stopped working recently).  Works like a charm.

Both my OS installs were format/reinstalls.  No upgrading.  10.04 I've downloaded most recent x-sane. (What v. are you using?)  Also works with simple scan (which I don't like as much because the beta would only let me rotate the first page to landscape, not the following pages.)

---

