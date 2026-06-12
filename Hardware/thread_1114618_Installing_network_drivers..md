---
title: "Installing network drivers."
date: 2009-04-02
forum: Hardware
---

### Post by ScornForSega on 2009-04-02
This is Ubuntu 6.06 running a 2.6.24.3 kernel on a headless Sun Cobalt Raq4.

LSPCI responds that the network cards are 8255xER/82551IT which my research says uses the Intel E100 driver.

I've compiled the module to run and I've got my e100.ko file.

sudo modprobe e100.ko returns FATAL: Module e100.ko not found

Insmod e100.ko returns:

kobject_add failed for e100 with -EEXIST, don't try to register things with the same name in the same directory.

The last line reads:

insmod: error inserting 'e100.ko': -1 File exists


I think this might be due to a botched install, but I can't figure out where the old e100.ko is.

sudo find / -name e100.ko only returns the recently compiled module in my home directory.

---

