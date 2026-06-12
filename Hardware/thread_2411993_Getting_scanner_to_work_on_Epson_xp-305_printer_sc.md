---
title: "Getting scanner to work on Epson xp-305 printer scanner"
date: 2019-02-06
forum: Hardware
---

### Post by Euanbuntu on 2019-02-06
I've just re-installed Ubuntu 18.04.1 and a few days later gone to install the printer driver for an XP-305 printer/scanner but I have not been able to get the scanner to work.

I've downloaded two packages from the Epson website:

epson-inkjet-printer-escpr_1.6.35-1lsb3.2_amd64.deb

and

epson-printer-utility_1.0.2-1lsb3.2_amd64.deb

and I also got iscan-bundle-1.0.4.x64.deb.tar.gz, I think also from the Epson website.

Once I'd unpackaged the .tar.gz and tried to follow the README.rst file but I think I may have made a mistake somewhere along the line and, to be fair, I am now pretty lost with it all.

I would hugely appreciate someone's help to with the iscan bundle to get the scanner utility on the printer/scanner to work.

Please help if you can!

---

### Post by Claus7 on 2019-02-07
Hello,

scanners seem to be an issue for ubuntu 18.04 lately. I do not know about the model of your printer/scanner, yet you could try to use: 
[https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git)

ppa, reboot and check if your scanner is detected. You might have to open a couple of times your scanner as well, until you make it working.

Hope it helps,
Regards!

---

