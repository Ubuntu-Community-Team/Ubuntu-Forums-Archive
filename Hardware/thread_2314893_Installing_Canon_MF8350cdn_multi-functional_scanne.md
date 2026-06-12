---
title: "Installing Canon MF8350cdn multi-functional scanner on Sane"
date: 2016-02-24
forum: Hardware
---

### Post by willyn2 on 2016-02-24
Hi,

I am trying to get the scanner of my canon multi-functional mf8350cdn working via my network. I installed the latest Linux printer drivers of Canon and I found that the Canon i-sensys mf8300 series is supported via sane-pixma backend. The printer is working fine, but when I try to find my scanner via scanimage -L I get an error.  I followed all instruction available to install a network scanner and it seems to work fine except that I have an issue with the naming convention of sane-pixma. 

At the man page of the website [http://linux.die.net/man/5/sane-pixma](http://linux.die.net/man/5/sane-pixma) I read the following:
"[COLOR=#0000cd]Device names for BJNP devices is in the form pixma:aaaa_bbbbb where aaaa  is the scanners model and bbbb is the hostname or ip-adress.[/COLOR]"

However the separator : is the same as the one used to add a port to the scanner. So when I apply this syntax [COLOR=#0000cd](bjnp://pixma:mf8300_192.168.1.104)[/COLOR] in the pixma.conf, it doesn't find the scanner as it searches for the scanner "pixma" at port mf8300_192.168.1.104. If I use a _ instead of : it doesn't recognize it either or putting the string between brackets doesn't help too. 

Does anybody know what syntax I need to use in the pixma.conf to apply the right sane backend and get the scanner working?

---

### Post by calvinabice10 on 2016-02-25
[COLOR=#000000][FONT=Verdana]The imageRUNNER 5065 device is powered by Canon's imageCHIP system architecture, featuring exceptional multifunctional performance and reliability. The imageRUNNER 5065 offers a full range of document handling capabilities such as a standard Single Pass Duplex Scanner/Feeder, saddle stitch finishing, 2/3-hole punching, and a Document Insertion Unit with the ability to "C" and "Z" fold documents.[/FONT][/COLOR]

---

### Post by florian-p-nierhaus on 2016-03-07
[FONT=arial]I have that scanner and on Ubuntu 14.04 you need  to install more recent sane backends: e.g.
[https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git)

That said I only use usb (not via network). Good Luck, Florian

Notes:[/FONT]
[FONT=arial]You need to set the scanner to "Remote Scanner". There is also a "Computer" scan option, but that seems to tell the computer what to scan (e.g. PDF, email, save, ..) and that menu doesn't even come up using the sane backend.[/FONT]

---

