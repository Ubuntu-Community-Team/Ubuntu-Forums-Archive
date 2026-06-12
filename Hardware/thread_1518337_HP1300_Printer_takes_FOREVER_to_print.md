---
title: "HP1300 Printer takes FOREVER to print"
date: 2010-06-26
forum: Hardware
---

### Post by kmkrause on 2010-06-26
Is there a driver that I need to update? My printer can take 3 minutes to print a simple google maps page. I tried printing a more complex image that was in a PDF file and it never came through. 

This is a recent development.

---

### Post by Jordanwb on 2010-06-26
Interesting. I'm having a similar problem with my HP Laserjet 2100. Are you by chance running 10.04?

---

### Post by kmkrause on 2010-06-26
Yes I am. I can't remember if the problem started when I upgraded but it's possible.

---

### Post by oldsoundguy on 2010-06-26
Recent updates in cups were not written properly.  They installed and removed the old cups info, but failed to hook up or hook up properly to printers.

RE_BOOTING solves MOST of the issues.  Would suggest that before you start mucking around in terminal.

---

### Post by cusinmex on 2010-06-26
I thought i was the only one as well with the Laserjet 2100 :S

Mine never prints Openoffice documents, and takes forever to
print anything else

---

### Post by jwolf on 2010-07-08
> **Jordanwb said:**
> Interesting. I'm having a similar problem with my HP Laserjet 2100. Are you by chance running 10.04?

I too am having this problem. My HP 2100M with PS module is going on 43 minutes to print a single page PDF with graphics.

---

### Post by jwolf on 2010-07-08
I found a solution in another thread that I will repeat here for the other HP owners. I simply switched drivers from the Foomatic/Postscript driver to the CUPS/Gutenprint driver and the same file I was waiting 40+ minutes for printed in seconds.

---

### Post by feistybird on 2010-12-30
I've having the same problems with my HP-1200 and 1300 printers since Ubuntu 6.10, finally I've found a solution, FYR. :

[http://ubuntuforums.org/showpost.php...57&postcount=2](http://ubuntuforums.org/showpost.php...57&postcount=2)

Just change the driver to be generic, and then PCL 5e Foomatic/hpijs-pcl5e

---

### Post by John Coulthard on 2011-11-19
Same problem with an HP Laserjet 1012. I also got PCL XL InsufficientMemory errors with some jpg's. Taking a hint from [http://ubuntuforums.org/showthread.php?t=1625874](http://ubuntuforums.org/showthread.php?t=1625874) I experimented with different drivers. The CUPS-Gutenberg v5.2.6 driver worked the best.

---

