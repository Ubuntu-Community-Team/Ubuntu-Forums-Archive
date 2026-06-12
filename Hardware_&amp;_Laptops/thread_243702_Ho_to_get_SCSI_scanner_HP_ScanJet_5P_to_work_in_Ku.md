---
title: "Ho to get SCSI scanner HP ScanJet 5P to work in Kubuntu 6.06?"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by zeroconf on 2006-08-25
I wrote full story here:
[http://kubuntuforums.net/forums/index.php?topic=8244.0](http://kubuntuforums.net/forums/index.php?topic=8244.0)

Does anybody have any idea to get it work? I'm stuck...

This scanner and SCSI adapter worked in Edubuntu 5.10.

Now also SCSI adapter works fine but scanner is not recognized :(

Any help would be appreciated!

I also tried to build xsane but no success - [http://ubuntuforums.org/showthread.php?t=197067](http://ubuntuforums.org/showthread.php?t=197067)

---

### Post by loockb on 2006-10-05
Hi,

I got a bit further. I'm using SimplyMepis 6 (based upon Dapper).
Xsane is version 0.97, sane is 1.0.14-1.

1) I defined in /etc/udev/rules.d/50-mepis-overrides.rules :

# hp scanner
BUS="scsi", SYSFS{model}="C5110A*", KERNEL="sg*", NAME="%k", SYMLINK="scanner", MODE="0666"

2) In /etc/modules :

sym53c416


Results :

a) Running sane-find-scanner, it shows the scanner (twice) :
found SCSI processor "HP C5110A 3701" at /dev/scanner
found SCSI processor "HP C5110A 3701" at /dev/sg1

b) But 'scanimage -L' hangs.

c) However, when running : scanimage -d "hp:/dev/scanner" > image.pnm
it actually made the scanner scan the page.

d) I could run once : xsane "hp:/dev/scanner"
It was as root, but I'm not sure this has a real effect. I could not do it twice.

Remark : my hp printer often takes a page when running the xsane or scanimage -L command.

Cheers, Ben

---

### Post by loockb on 2006-10-07
Hi again,

I have now xsane working with the HP Scanjet 5P. 

As the problem is with the searching after scanning devices, I tried the following : limit the search for devices. Adding the scanner to the cmdline does not seem to limit the search. 

So, 

-> edit /etc/sane.d/dll.conf, so it only contains now one entry : 

hp

-> edit /etc/sane.d/hp.conf, it only contains : 

/dev/scanner

-> removed (or rename) the directory /etc/sane.d/dll.d


After this :

$ scanimage -L
device `hp:/dev/sg1' is a Hewlett-Packard C5110A flatbed scanner
device `hp:/dev/scanner' is a Hewlett-Packard C5110A flatbed scanner

:) 

Cheers, Ben

---

