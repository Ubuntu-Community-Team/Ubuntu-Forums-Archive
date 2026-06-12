---
title: "Ubuntu 18.04 missing linux-firmware-nonfree"
date: 2018-10-12
forum: Hardware
---

### Post by mtbdrew on 2018-10-12
So have a tuner card that needs the nxt2004 firmware (dvb-fe-nxt2004.fw) that used to install as part of the linux-firmware-nonfree package. Unfortunately this doesn't appear to be supported anymore with Ubuntu 18.04 so anyone know how to get the firmware now?

---

### Post by DuckHook on 2018-10-12
A Google search turned up this: [https://github.com/OpenELEC/dvb-firmware/blob/master/firmware/dvb-fe-nxt2004.fw](https://github.com/OpenELEC/dvb-firmware/blob/master/firmware/dvb-fe-nxt2004.fw)

***BE CAREFUL.***

I have no knowledge of this file, no idea if it is legitimate and no knowledge of its author, its history or its pedigree. It could be a rootkit for all I know. Use at your own risk.

FWIW, I hate using binary blobs like this one that haven't the slightest vouching from the community. Speaking only for myself, I would rather change my tuner card than rely on unknown binary blobs from goodness-knows-where.com. It's one of the reasons I stopped using Windows. But to each their own.

---

### Post by Yellow Pasque on 2018-10-13
You can still get the file from the old Ubuntu Trusty/14.04 archive. [https://launchpad.net/ubuntu/+source/linux-firmware-nonfree](https://launchpad.net/ubuntu/+source/linux-firmware-nonfree)
Don't install the .deb. Just extract the particular file(s) you need from the .deb or .tar.gz
Unless the manufacturer has updated the firmware in the last 4 years (doubtful), that would be the ideal solution to me.

---

