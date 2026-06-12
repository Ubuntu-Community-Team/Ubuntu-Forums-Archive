---
title: "List of hardware"
date: 2010-09-22
forum: Hardware
---

### Post by jmdlcar on 2010-09-22
Is there a program or a command I could get to list all the hardware in my computer?

---

### Post by Toz on 2010-09-22
You can try the ls set of commands (from a terminal window):

lshw = list hardware (you can also install the package lshw-gtk for a grpahical view of this data)
lspci = list pci devices
lsusb = list usb devices
lshal = list hal devices
lscpu = list cpu devices
lspcmcia = list pcmcia devices 

/ToZ

---

### Post by metalf8801 on 2010-09-22
Install Sysinfo it's in the Software Center

---

### Post by lisati on 2010-09-22
[dmidecode]("http://www.nongnu.org/dmidecode/") (which comes as standard with Ubuntu) gives a bunch of info from an "as seen by BIOS" perspective.

---

### Post by SaintDanBert on 2010-09-23
There is another package **hwinfo** also in the repositories.

(heavy sigh) I have yet to find a linux "report" similar to what I get with the free tool, Belarc Advisor [http://www.belarc.com/free_download.html](http://www.belarc.com/free_download.html) for win-doze. [highlight]sysinfo[/highlight] comes very close, though.

~~~ 0;-Dan

---

