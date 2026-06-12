---
title: "problem with synaptic"
date: 2005-12-08
forum: Installation &amp; Upgrades
---

### Post by picaboo on 2005-12-08
hi.
i've installed libfontconfig1-dev and libqt3-mt-dev from a deb file which i get from debian. I know it's wrong. Now when I trying install something synaptic talk to me that I must remove this packages: gtk2-engines-dev libbonoboui2-dev libfontconfig1-dev libglade2-dev libgnomecanvas2-dev libgnomeui-dev libgtk2.0-dev libpango1.0-dev libqt3-mt-dev libxft-dev
please help me

---

### Post by 23meg on 2005-12-08
What are you trying to install? Anyway it's not good in general to mix in Debian repositories. Try removing what you installed from Debian, doing ```
sudo apt-get -f install
sudo apt-get update
``` and see if it changes anything.

---

### Post by picaboo on 2005-12-08
the packages libfontconfig1-dev and libqt3-mt-dev i got from: [http://packages.debian.org](http://packages.debian.org) and now when i'm trying remove or install something by synaptic or apt-get command i get a message that this: gtk2-engines-dev libbonoboui2-dev libfontconfig1-dev libglade2-dev libgnomecanvas2-dev libgnomeui-dev libgtk2.0-dev libpango1.0-dev libqt3-mt-dev libxft-dev must be removed.

---

### Post by 23meg on 2005-12-08
Remove all Debian repos from your sources.list, do ```
sudo apt-get -f install
sudo apt-get update
```and then remove any packages marked "broken", if any.

---

### Post by picaboo on 2005-12-09
Work great. Big thanks for Your help and patience.
Now I have another problem. When I'm trying install Kadu [most popular IM in Poland] i get message from synaptic that libc6 must be in 2.3.2.ds1-21 version or better but I have 2.3.2.ds1-20ubuntu14 and Kadu won't be install.

---

