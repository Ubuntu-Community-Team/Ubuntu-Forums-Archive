---
title: "Canon mg5250 pixma stopped printing, but scanner still works"
date: 2015-09-09
forum: Hardware
---

### Post by marym on 2015-09-09
[SIZE=4][/SIZE]  My canon pixma printer mg5250 has suddenly stopped printing, but the scanner works.

I have tried to download the drivers from the Canon site but this is what I am getting in the terminal:

Unpacking cnijfilter-common (3.40-1) ...
Replaced by files in installed package cnijfilter-common-64 (3.90-76~ubuntu14.04.1) ...
dpkg: dependency problems prevent configuration of cnijfilter-common:
 cnijfilter-common-64 (3.90-76~ubuntu14.04.1) breaks cnijfilter-common and is installed.
 cnijfilter-mg5200series-64 (3.90-76~ubuntu14.04.1) breaks cnijfilter-common and is installed.

dpkg: error processing package cnijfilter-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-common
Command executed = sudo dpkg -P cnijfilter-common
(Reading database ... 434720 files and directories currently installed.)
Removing cnijfilter-common (3.40-1) ...
Purging configuration files for cnijfilter-common (3.40-1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...

Please note I am less than a novice.

---

### Post by marym on 2015-09-13
A member of the Birmingham LUG solved the problem for me.  I post the solution here in case someone else faces the same problem.

[COLOR="#0000CD"][COLOR="#0000CD"]After a bit of messing about with this it seems the best way to do it is install libtiff4 from a debian repository.  I did the following:

I downloaded the driver from [http://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_mg_series/pixma_mg5250.aspx?type=drivers&language=&os=Linux%20%2864-bit%29](http://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_mg_series/pixma_mg5250.aspx?type=drivers&language=&os=Linux%20%2864-bit%29)

Then untarred the tar file and the deb.tar.gz file within it and changed directory to the cnijfilter-mg5200series-3.40-1-deb directory.

I downloaded the debian libtiff4 package:

wget [http://ftp.us.debian.org/debian/pool/main/t/tiff3/libtiff4_3.9.6-11_amd64.deb](http://ftp.us.debian.org/debian/pool/main/t/tiff3/libtiff4_3.9.6-11_amd64.deb)

And installed it:

sudo dpkg -i libtiff4_3.9.6-11_amd64.deb

Then run the install.sh file:

sudo ./install.sh

That installs the deb files and prompts you to connect to your printer.
[/COLOR][/COLOR]
End of instructions.

It worked for me :-)

---

