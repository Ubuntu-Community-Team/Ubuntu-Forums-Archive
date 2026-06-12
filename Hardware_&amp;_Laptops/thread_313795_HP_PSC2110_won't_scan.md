---
title: "HP PSC2110 won't scan"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by nkkromhof on 2006-12-06
I'm running Edgy, and I've been having trouble getting my HP PSC2110 All-in-one printer to run properly. I'm working on migrating to Ubuntu and ditching WinXP altogether, one of the last steps is getting my printer to work, it will print just fine, but I can't get it to scan...

Trying to install HPLIP using the automated installer works like a charm until I get the following error:

0
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
error: <b>No devices found.</b><p>Please make sure your printer is properly connected and powered-on.
Done.

It will then open the Add Printer dialog and allow me to add a printer without any trouble, I can print just fine, but when I start Xsane it auto-detects my devices and I select my scanner it tries to initialize the scanner and eventually I get an error (see attachment)

I have (almost all) hplip packages installed (see other attachment), I've tried following Leech's Howto ([http://ubuntuforums.org/showthread.php?t=121896](http://ubuntuforums.org/showthread.php?t=121896)) to install the device too, that didn't work either... The only step that was different for me there was the one where you select the driver from /usr/share/ppd/hplip, that directory doesn't exist for me, which might be linked to the output of the apt-get I got:
            Reading package lists... Done
            Building dependency tree       
            Reading state information... Done
            hplip is already the newest version.
            hplip-data is already the newest version.
      --->  Note, selecting hpijs-ppds instead of hplip-ppds  <---
            hpijs-ppds is already the newest version.

Any insights/help/divine intervention is more than welcome, if more info is needed please let me know.

Thanks in advance

---

### Post by Sef on 2006-12-07
Take a look at the [Sane-Project]("http://www.sane-project.org/cgi-bin/driver.pl?manu=HP&model=PSC+2110&bus=any&v=&p=").

---

### Post by nkkromhof on 2006-12-07
Hi, thanks for your input.

I've taken a look at the website you mentioned, but all it does is point me back to the same HPLIP page on SourceForge.net...

Any other suggestions?

---

### Post by jedibrand on 2008-01-23
Unbelievable--turns out all you had to do was recycle power for the printer (unplug, it's safest):

[http://osdir.com/ml/drivers.hpofficejet.devel/2004-01/msg00028.html]("http://osdir.com/ml/drivers.hpofficejet.devel/2004-01/msg00028.html")
 
At the same time, I did install a bunch of related packages and made a number of (possibly) attendant modifications. If anything, try running the HPLIP automated installer (fyi, installing hplip via synaptic--command-line or otherwise--defaults to hpijs, which appears to predate hplip, though not sure whether that impacts this particular installation in any significant way):

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

Finally, if you're still faced with a defiantly unsympathetic system, send me an email. Maybe I can point you to some of the sites I stumbled upon in troubleshooting.

---

