---
title: "Lexmark E210 on Ubuntu Dapper beta"
date: 2006-04-24
forum: Hardware &amp; Laptops
---

### Post by tachum on 2006-04-24
I have used this laser printer for 4 or 5 years and never had any problems in 32 bit linux OS systems. The computer is 64 bit AMD 3000+ and the only 64 bit OS that actually got the Lexmark going was Mandrake 2006 64.

The Lexmark worked in the previous 2 Ubuntu versions but is totally inert in the 32 bit Dapper beta. Previously, Ubuntu identified the hardware. This time it didn't and I selected the driver manually. But it still didn't work. I have checked the connections etc but they are fine. 

Where does one start???

Thanks

---

### Post by tachum on 2006-04-24
I continue to have no luck. When adding the printer, the options are:

1. Local Printer
2. Detected printer (none shown)
3. Use another printer by specifying the port (there is a message here saying "HP no device found")

Options 1 and 3 are auto selected by default, so I wonder if this confuses the system since you cannot have just one of the 3 selected. The cups log files are full of references to the HP issues. But does this line suggest there is a firewall problem to port 631??

E [24/Apr/2006:11:16:56 +1000] CUPS-Add-Printer: Unauthorized 

Any help appreciated.

---

### Post by tachum on 2006-04-30
I am still puzzled as to why my Lexmark printer won't work, everything else does, and it did work in previous version of Ubuntu.

An update: I have been doing all the updates to the beta version, and it now appears to be running Beta 2. In installing all the CUPS files via apt-get, I noticed the following error:

[B]*** glibc detected. double free or corruption.  (prev): 0x0816e838***
unable to read printer database. Please ensure the "foomatic -db" package is installed properly. [/B]

I uninstalled foomatic then reinstalled it. Still no go.

I take it the problem is that ubuntu cannot read the printer driver files, although the problem seems more serious that this, because normally ubuntu detects the E210 printer automatically, without me having to tell it what type of printer is attached locally. 

Thoughts??

---

### Post by Sef on 2006-04-30
check out this Linuxprinting page:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-E210]("http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-E210")

---

