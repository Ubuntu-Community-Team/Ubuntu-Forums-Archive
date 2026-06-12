---
title: "Datacolor Spyder 5 Software"
date: 2017-12-15
forum: Hardware
---

### Post by uwe-bungto on 2017-12-15
I have a datacolor Spyder 5 What color management software is required to get it working

---

### Post by uwe-bungto on 2017-12-16
It looks like displaycal will will work with the spyder.
however when I try it I get a warning
> pb@maple:~$ /usr/bin/displaycal
displaycal 3.1.0.0 2016-02-01T00:59:52.487617Z
Ubuntu 16.04 xenial x86_64
Python 2.7.12 (default, Nov 20 2017, 18:23:56)
 [GCC 5.4.0 20160609]wxPython 3.0.2.0 gtk2 (classic)
Encoding: UTF-8File system encoding: UTF-8
Connection to 127.0.0.1:54947 failed: [Errno 110] Connection timed out
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/DisplayCAL/main.py", line 264, in main    from DisplayCAL import main
  File "/usr/lib/python2.7/dist-packages/DisplayCAL/DisplayCAL.py", line 130, in <module>    from wxProfileInfo import ProfileInfoFrame 
 File "/usr/lib/python2.7/dist-packages/DisplayCAL/wxProfileInfo.py", line 27, in <module>    from wxLUTViewer import LUTCanvas, LUTFrame 
 File "/usr/lib/python2.7/dist-packages/DisplayCAL/wxLUTViewer.py", line 30, in <module>    import wxenhancedplot as plot 
 File "/usr/lib/python2.7/dist-packages/DisplayCAL/wxenhancedplot.py", line 132, in <module>    raise ImportError,
 "Numeric,numarray or NumPy not found. \n" + msgImportError: Numeric,numarray or NumPy not found. 

            This module requires the Numeric/numarray or NumPy module, 
           which could not be imported.  It probably is not installed 
           (it's not part of the standard Python distribution). 
See the            Numeric Python site ([http://numpy.scipy.org](http://numpy.scipy.org)) for information on
            downloading source or binaries.Gtk-Message: 
Failed to load module "atk-bridge"

Any ideas?

---

### Post by Holger_Gehrke on 2017-12-16
I'd do just as it says and install Numerical Python (package python-numpy). If you installed displaycal (probably an older version, still called dispcalgui) from the repositories, it would have installed numpy as a dependency. And it probably also would have installed the display calibration software - argyll - for which displaycal is only a front end. According to what I've read, you need at least version 1.7 of argyll with the Spyder 5. For XUbuntu  17.04 - which I'm using - the version of argyll in the repositories is 1.9.something, but I don't know about 16.04.

Holger

---

### Post by uwe-bungto on 2017-12-17
> **Holger_Gehrke said:**
> I'd do just as it says and install Numerical Python (package python-numpy). If you installed displaycal (probably an older version, still called dispcalgui) from the repositories, it would have installed numpy as a dependency. And it probably also would have installed the display calibration software - argyll - for which displaycal is only a front end. According to what I've read, you need at least version 1.7 of argyll with the Spyder 5. For XUbuntu  17.04 - which I'm using - the version of argyll in the repositories is 1.9.something, but I don't know about 16.04.

Holger
I have dispcalgui 3.1.0.0-1, argyll 1.8.3+repack-2,
Python-numpy 1:1.11.0-1ubuntu1 is installed. The discription note > Numpy replaces the python-numeric and python-numarray modules which arenow deprecated and shouldn't be used except to support older
software.
is there a PPA where I can install numpy from. 
'http://ppa.launchpad.net/pmjdebruijn/argyll-testing/ubuntu xenial' does not work anymore.

I also have 2 monitors in use which makes things more complicated for me at least.

---

