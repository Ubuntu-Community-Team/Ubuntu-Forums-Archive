---
title: "Skystar2 PCI DVB card"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by mad_alfred on 2005-06-21
hi!

is there any way of getting to work a skystar2 dvb card with ubuntu? i can see that ubuntu found it with the dmesg and lsmod commands but really have no idea on how to configure it properely to watch FTA channels...because of this i still have to stick to windows, arrgghh!  ](*,) 

googling around i came up to some guides, but they seem for FC3 only :(

any help?

thanks

ubuntu rocks!

---

### Post by buntus on 2005-08-02
Hi,
[http://www.ubuntu-forum.de/thread.php?threadid=975](http://www.ubuntu-forum.de/thread.php?threadid=975)

Script to /etc/init.d written:

sudo gedit /etc/init.d/dvb

#!/bin/bsah
#/etc/init.d/dvb

#get rid of old DVB API devices; do it twice for good measure...

rm -rf /dev/ost
rm -rf /dev/ost
rm -rf /dev/dvb
rm -rf /dev/dvb

for major and minor devicenumber see here
#vi /usr/src/linux/Documentation/devices.txt

cd /dev
mkdir dvb
chmod 755 dev/dvb
cd dvb
mkdir adapter0
cd adapter0
mknod -m 0660 frontend0 c 212 3
mknod -m 0660 demux c 212 4
mknod -m 0660 dvr0 c 212 5
mknod -m 0660 ca0 c 212 6
chown root.video /dev/dvb/adapter0/*' '
chmod 744 /etc/init.d/dvb

save
done

#update-rc.d dvb defaults

#sudo apt-get install xine-ui dvb-utils

#cp /usr/share/doc/dvb-utils/channels.conf-dvbs-astra.gz ~/.xine/channels.conf

[#ALT#]+[#F2#]

xine dvb://

if Xine not work, then: in root termial:

zcat /usr/share/doc/dvb-utils/examples/channels.conf-dvbs-astra.gz > channel
szap -c channel -n 1 -r

another root terminal open:

xine stdin:// < /dev/dvb/adapter0/dvr0

---

### Post by buntus on 2005-08-02
Hi,
[http://www.ubuntu-de.org/wiki/treiber:tv:skystar2_installation](http://www.ubuntu-de.org/wiki/treiber:tv:skystar2_installation)
good luck.

---

