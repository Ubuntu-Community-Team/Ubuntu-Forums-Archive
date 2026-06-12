---
title: "Problem with Epson EPL-5800L"
date: 2009-02-07
forum: Hardware
---

### Post by kryddan on 2009-02-07
Ubuntu 8.10 (and Vista) has drivers for Epson EPL-5800, but not 5800L (which doesn't support PCL). I found the following driver at [http://downloads.sourceforge.net/epsonepl/epsoneplijs-0.4.1.tgz?modtime=1215220428&big_mirror=0](http://downloads.sourceforge.net/epsonepl/epsoneplijs-0.4.1.tgz?modtime=1215220428&big_mirror=0).

Since I'm a linux noob, I fail to install the driver. I don't know how cups and foomatic work. When I try to choose a PPD file, it fails to read it. Depending on which PPD file I choose, there's different error messages. Does anyone have a solution to this problem?

---

### Post by antony_css on 2009-02-10
Similar thread:
[http://ubuntuforums.org/showthread.php?t=531949]("http://ubuntuforums.org/showthread.php?t=531949")

---

### Post by antony_css on 2009-02-10
Actually, I am now using the same model...
Ubuntu does not support this model, so you have to install the driver yourself.

In case you do not know it, foomatic scripts and cups are for configuration and management of printers. This is possible only if you have the background engine installed ( that is the driver ).

You can look up informations from this page:
[http://www.openprinting.org/show_printer.cgi?recnum=Epson-EPL-5800L]("http://www.openprinting.org/show_printer.cgi?recnum=Epson-EPL-5800L")
Be reminded that in ubuntu/linux you usually need to compile sources (tarball) to executables before you can install them.

I installed the driver last year on the Hardy version. I should have saved a backup deb package... Please give me time while I am looking for it...

---

### Post by antony_css on 2009-02-10
Here is the compiled executables...

But I suggest you to compile it yourself according to this thread:
[http://ubuntuforums.org/showthread.php?t=901529]("http://ubuntuforums.org/showthread.php?t=901529")

This is how you install **build-essential**:
> sudo apt-get install build-essential

Sadly, the foomatic does not work for me. Every time when I print a document, I have to first save it as a .ps file and then change it to a .epl file before I can feed it to the printer...

You may look for detailed instruction inside README once you downloaded the package *epsoneplijs-0.4.1.tgz*.

---

