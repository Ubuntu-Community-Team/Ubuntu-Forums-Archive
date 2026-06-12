---
title: "Installing HPLIP 2.7.6 via automated installer - cups-devel dependancy problem"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by thingy on 2007-07-22
Just thought I'd let people know that if they are going to download and install the HPLIP  2.7.6 software via the automatic installer HP provide, they may run into a problem with it complaining about a missing cups-devel dependency.

I looked at the python code that was doing the checking and it seems that it wanted cups-bsd installed (lpr) as well as the libcupsys2-dev which it knows to install to satisfy the cups-devel dependency. 

Specifically the line that causes the problem is: (in the hplip-2.7.6/installer/dcheck.py file)

> def check_cups_devel():
    return check_file('cups.h') and bool(utils.which('lpr'))
See, the libcupsys2-dev file provides the cups.h file and the condition is met, but as I did not have cupsys-bsd installed or another lpr program installed, the second condition failed and hence the statement returned false. I.e. no cups-devel found. Bah!

Oh, I would recommend you have a proper cups installation before installing the HPLIP stuff. I.e. apt-get install cupsys

---

