---
title: "Linux driver for my HP 7850 printer?"
date: 2008-09-22
forum: General Help
---

### Post by mikebear45 on 2008-09-22
Hello fellow forum users!

I'm trying to find a workable driver in Linux for my HP Photosmart 7850 printer. I've checked the registry of the Synaptic Package Manager and there is quite a list of HP packages to choose from. Does anyone here have experience of knowing exactly which package I'll likely need, without having to install and remove each and every package till I find one that works?
                                  Thanks!
                                         mikebear45:confused:

Dell Dimension 4700
Ubuntu 8.04 LTS Hardy Heron
Intel P4 CPU 3.0 Ghz
Seagate 160GB HD
HP Photosmart 7850

---

### Post by Taxman415a on 2008-09-22
According to [http://hplipopensource.com/hplip-web/models/photosmart/photosmart_7800_series.html](http://hplipopensource.com/hplip-web/models/photosmart/photosmart_7800_series.html)  and  [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7850](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7850) it should work fine with the standard HPLIP/HPIJS driver. Try installing the hpijs-ppds packages and see if that works.

---

