---
title: "[SOLVED] &amp;quot;failed dependencies&amp;quot; - what does it mean and what can I do ?"
date: 2008-08-22
forum: General Help
---

### Post by worksofcraft on 2008-08-22
the manual says to log in as root and run:
rpm -Uhv VMware-<xxxx>.rpm

Afer sudo apt-get install rpm, I replace the <xxxx> with appropriate version and then get

"error: Failed dependencies:
    /bin/sh is needed by VMwareWorkstation-6.0.4-93057.i386"

There is however a /bin/sh on my Ubuntu 8.04 (32 bit generic) :confused:
Can anyone help me with what this means and what I need to do to fix it?

ty in advance

---

### Post by DirtDawg on 2008-08-22
It's not clear, are you trying to install an rpm package? If that's the case, and you cannot find an equivalent deb package, you should use 'alien' to convert the rpm in question into a deb file, then install the deb file. 

Install alien:
```
sudo apt-get install alien
```

Convert the rpm into a deb:
```
alien -k /path/to/package.rpm
```

This will create a new deb package, which you can then install:
```
sudo dpkg -i /path/to/package.deb
```

---

### Post by worksofcraft on 2008-08-22
:-) I used
alien -k --scripts ./VMware-w*.rpm
and it compiled all sorts of things to fit with my kernel then said it was installed and to enjoy...
sadly when I ran it all I got was:

Failed to open file '/usr/lib/vmware/share/EULA.txt': No such file or directory
so that's the next hurdle - OK solved that with
sudo touch /usr/lib/vmware/share/EULA.txt
... and then accepting a blank text box :/

p.s. then VMware-workstation works and I created a virtual guest machine running Windows (TM) hosted on my Ubuntu real machine...
however Windows (TM) tells me that the number of installations with my key have been exceeded... and I can only use it for 30ndays :(
I mean does that corporation seriously expect me to buy another license for every virtual machine I want to run on my fully licensed desktop :@

---

