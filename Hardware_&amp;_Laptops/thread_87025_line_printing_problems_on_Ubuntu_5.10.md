---
title: "line printing problems on Ubuntu 5.10"
date: 2005-11-07
forum: Hardware &amp; Laptops
---

### Post by awilpert on 2005-11-07
Hi,

I have a Samsung ML-1510 attached (USB) to a linux box running Ubuntu 5.10. I managed to configure the printer as to be able to print from a graphical application, like OpenOffice or Firefox. The problem is that I do not get any output when I issue the following command in a shell:

lpr
test
^D

The printer gets activated and it actually outputs a page, but nothing is printed on it. The printing system installed is CUPS (automatically selected by the standard Ubuntu installation).

I tried SuSE 9.3 and did not have any problem printing from the command line, so I guess I can discard my printer as the source of this problem.

Any hints on how to solve it? Many thanks in advance,

Alexis

---

### Post by awilpert on 2005-11-07
Hi again,

searching the forums, I found a thread called "Printing via lpr". There it is said that some problems might be solved installing the cupsys-bsd package. I will try it as soon I get to my linux box.

Greetings,

Alexis

---

### Post by awilpert on 2005-11-07
Hi,

unfortunately, the package cupsys-bsd was installed from the beginning and my line (command-line) printing problems are still there. I think it is very strange that the printer gets activated and even outputs a page without anything printed on it. Can anybody help?

Thanks in advance,

Alexis

---

### Post by isoaglib on 2006-01-04
Look at the following link to another thread in the forums:
[http://ubuntuforums.org/showthread.php?p=452874#post452874](http://ubuntuforums.org/showthread.php?p=452874#post452874)

I installed the Samsung driver for the same model - and it works fine. The CUPS driver had some problems with GDI, so that the printout was distorted.

The print quality of the Samsung driver is fine.
Try this out.

---

