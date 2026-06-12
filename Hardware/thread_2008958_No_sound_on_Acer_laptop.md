---
title: "No sound on Acer laptop"
date: 2012-06-23
forum: Hardware
---

### Post by Do_Japan on 2012-06-23
I'm at my wit's end with this no sound issue.  Here what I've got: Acer Aspire 3000 just installed Xubuntu 12.04

lspci:

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)

I've tried MANY broken installs for sound card drivers, including the linux driver from the SiS website and Realtek's website.  These installs, and many others, inevitable produce many, many errors so I gave up.  Now I am trying to install the Alsa driver per these instructions:
[http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0)

So I get to the first substantial step, and here is the command line:

sudo ./configure --with-cards=intel8x0 --with-sequencer=yes ; make ; make install

The install starts out fine, but after a few pages of output this comes up:

make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.25/include/sound'
/bin/sh: 1: cannot create .includes.tmp: Permission denied
make[4]: *** [.includes.tmp] Error 2
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.25/include/sound'
make[3]: *** [.includes] Error 2
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.25/include/sound'
make[2]: *** [prepare] Error 2
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.25/include'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.25'
make: *** [include/sndversions.h] Error 2
if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /usr/src/alsa/alsa-driver-1.0.25/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
rm: cannot remove `/usr/include/sound/ainstr_fm.h': Permission denied
rm: cannot remove `/usr/include/sound/cs46xx.h': Permission denied
rm: cannot remove `/usr/include/sound/control.h': Permission denied
rm: cannot remove `/usr/include/sound/pt2258.h': Permission denied
rm: cannot remove `/usr/include/sound/tea575x-tuner.h': Permission denied

The Permission denied messages go on for several pages from there, and obvious the entire install is CRAP!  It shouldn't have to be this difficult.  I don't really think it helps that most of these install programs were written like 10 years ago!

Any ideas?

---

### Post by Do_Japan on 2012-06-23
I just tried OSS and the driver appeared to install successfully.  Reboot, and...

aplay -l:

aplay: device_list:252: no soundcards found...

Still no sound...

---

### Post by Do_Japan on 2012-06-26
Resolved: Not all of the commands on the same line were getting admin privilege.  Don't forget to use sudo for make and make install commands.

---

### Post by Joespower on 2012-07-09
Same laptop and same OS.  Forgive a newb for not understanding hwo you fixed it... Little help?

---

