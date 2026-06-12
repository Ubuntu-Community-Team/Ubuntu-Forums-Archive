---
title: "How to use HP Scanjet 3300 in ubuntu?"
date: 2005-01-09
forum: Hardware &amp; Laptops
---

### Post by giorgosc61 on 2005-01-09
Hi. How can I use my HP Scanjet in ubuntu?

---

### Post by randy on 2005-01-10
[http://www.sane-project.org/](http://www.sane-project.org/)

---

### Post by Wim Sturkenboom on 2005-01-11
Just busy with an HP 3400C. According to [HOWTO on sourceforge](http://sourceforge.net/docman/display_doc.php?docid=18356&group_id=36708), it's necessary to *remove a previously installed version of sane and all related packages*.
Using synaptic, I've found 5:
* libsane
* python2.3-imaging-sane
* python-imaging-sane
* xsane
* xsane-common
Do I have to remove all of these or can I keep i.e. the python-related ones?

---

### Post by alainhenry on 2005-01-12
Your system is probably already set up, and I do not think you need to reinstall sane, as it is installed from the base Warty system.   I have a USB Epson 1650 scanner, but sane does not find it.  See other thread 
[http://www.ubuntuforums.org/showthread.php?t=8779](http://www.ubuntuforums.org/showthread.php?t=8779)
and
[http://www.ubuntuforums.org/showthread.php?t=7930&highlight=scanner](http://www.ubuntuforums.org/showthread.php?t=7930&highlight=scanner)
I installed sane and sane-utils to have access to the facilities explained in those thread, but I still can't find the scanner.
Maybe re-installing sane might be useful, but I doubt it.  Apart from that, I am at a loss to propose anything.   
ideas, anyone? 
Alain

---

