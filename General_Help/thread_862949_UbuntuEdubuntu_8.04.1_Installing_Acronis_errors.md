---
title: "Ubuntu/Edubuntu 8.04.1 Installing Acronis errors"
date: 2008-07-18
forum: General Help
---

### Post by sigala on 2008-07-18
rying to install Acronis Image Server for linux in Ubuuntu 8.0.4.1
during the install it cannot find the compiled imapapi module,

in contacting Acronis they told me to download the snapapi26 module and run the commands as shown. since Ubuntu uses .deb files, I tried to install the rpm package manager and then the commands, I could not get this to work,
where should I download the file to
I made a directory in Home eg. Acronis
and just copied the file there and tried to run the rpm, no luck.
from the terminal I cd to this directory typed the rpm command
it said no file or directory? thou ls shows it there.
any help with this. as its suppose to fix the Acronis complile error 2 and allow complete installation?

From Acronis Tech support:
You should do the following in order to solve the issue:
download the snapapi26_module they gave me a link!
and then do the following in order

snapapi26_modules-0.7.39-1.noarch.rpm
# rpm -Uvh &#65279;snapapi26_modules-0.7.39-1.noarch.rpm
# dkms ldtarball --archive=/usr/lib/Acronis/kernel_modules/snapapi26-0.7.39-all.tar.gz
# apt-get install linux-source-2.6.24
# cd /usr/src
# tar jxf &#65279;&#65279;&#65279;linux-source-2.6.24.tar.bz2
# dkms build -m snapapi26 -v 0.7.39 -k 2.6.24-19-generic --config /boot/config-2.6.24-19-generic --arch i686 --kernelsourcedir /usr/src/linux-source-2.6.24
&#65279;# dkms install -m snapapi26 -v 0.7.39 -k 2.6.24-19-generic --config /boot/config-2.6.24-19-generic --arch i686 --kernelsourcedir /usr/src/linux-source-2.6.24

Ubuntu uses.deb file, so I tried installing the RPM package manager, and tried all the above, Still awaiting an answer from Tech support since they are in Moscow? a dya later I get a response from Acronis, this is during the day here in Florida? no 
local support?

---

