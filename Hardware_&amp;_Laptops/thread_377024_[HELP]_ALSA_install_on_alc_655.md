---
title: "[HELP] ALSA install on alc 655"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by klez on 2007-03-05
Hi everybody.
I need help with one of my last ubuntu installs. I installed ubuntu in an amilo pro 2055.
It has an integrated audio controller named ALC 655 by via.
It isn't completely supported by the actual stable ALSA (it has the famous headphone issue) in ubuntu's reps.)
I already know that the only possible solution consist of installing latest ALSA (at least 1.0.13) .

Could somebody please explain me (step-by-step, possibly) how to compile/install the latest stable alsa?

Thanks,
Claudio :)

---

### Post by klez on 2007-03-06
UP!

Chipset is VIA VT82xx.
Tried the alsa guide, but didn't work.

---

### Post by klez on 2007-03-09
Please, help me i'm still having the same issue.
Help me reinstalling alsa, please! :(

---

### Post by chepotenza on 2008-04-11
I cite extract the content of one of the scripts suggested by Temujin in:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

The instructions you need are:
```

echo "downloading alsa packages..."
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2

echo "extracting alsa packages..."
tar -xjf alsa-driver*.tar.bz2
tar -xjf alsa-lib*.tar.bz2
tar -xjf alsa-utils*.tar.bz2
rm alsa*.tar.bz2

echo "setting up alsa for compilation"
mkdir -p /usr/src/alsa
mv alsa-* /usr/src/alsa

#alsa-driver
cd /usr/src/alsa/alsa-driver*

#./configure --with-cards=hda-intel --prefix=/usr
# to compile all the modules, you can neglect the last line and do:

./configure --prefix=/usr
make
make install

#alsa-lib
cd /usr/src/alsa/alsa-lib*
./configure --prefix=/usr
make
make install

#alsa-utils
cd /usr/src/alsa/alsa-utils*
./configure --prefix=/usr
make
make install

```

---

