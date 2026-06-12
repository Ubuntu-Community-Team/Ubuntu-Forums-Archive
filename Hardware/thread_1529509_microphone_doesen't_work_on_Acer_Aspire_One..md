---
title: "microphone doesen't work on Acer Aspire One."
date: 2010-07-12
forum: Hardware
---

### Post by krestensb on 2010-07-12
Hi,

I have just brought myself an Acer Aspire One d250 laptop. Nice to be running linux again after long time breake. 

I have got a microphone issue. It doesn't work, and I can't figure out how. Please help me.

It's not supposed to work out of the box,but there is a fine guide how to get it working.

[https://help.ubuntu.com/community/AspireOneAOD250?action=show&redirect=AspireOne%2FAOD250](https://help.ubuntu.com/community/AspireOneAOD250?action=show&redirect=AspireOne%2FAOD250)

It holds nine step and I did them all one a new ubuntu 10.04 system. They all worked except for the last one: sudo make install.

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
tar xjvf alsa-driver-1.0.20.tar.bz2
cd alsa-driver-1.0.20
sudo apt-get install build-essential module-assistant
sudo m-a update
sudo m-a prepare.
./configure --with-cards=all
make

sudo make install


I get this message: 





if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /home/kresten/alsa-driver-1.0.20/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
find /lib/modules/2.6.32-21-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.32-21-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.32-21-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.32-21-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/home/kresten/alsa-driver-1.0.20/acore'
mkdir -p /lib/modules/2.6.32-21-generic/kernel/sound/acore
cp snd-hrtimer.ko snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-timer.ko snd.ko /lib/modules/2.6.32-21-generic/kernel/sound/acore
cp: cannot stat `snd-hrtimer.ko': No such file or directory
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/kresten/alsa-driver-1.0.20/acore'
make: *** [install-modules] Error 1



Could someone help me out, I would be more than greatefull.

Best regards
Kresten Buch, Denmark

---

