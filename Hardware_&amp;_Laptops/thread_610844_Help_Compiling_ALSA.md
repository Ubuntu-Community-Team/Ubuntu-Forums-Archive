---
title: "Help Compiling ALSA"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by lwylie on 2007-11-12
Hey everyone,

     I'm in the process of recompiling/installing the latest 1.0.15 version of alsa, however, I've hit a problem on the alsa-utils-1.0.15 package.  After extracting the tarball I ran:

```
./configure
make
```

Unfortunately I received the following error:

```

Making all in include
make[1]: Entering directory `/home/lwylie/tmp/alsa-fix/alsa-utils-1.0.15/include'
make  all-am
make[2]: Entering directory `/home/lwylie/tmp/alsa-fix/alsa-utils-1.0.15/include'
make[2]: Leaving directory `/home/lwylie/tmp/alsa-fix/alsa-utils-1.0.15/include'
make[1]: Leaving directory `/home/lwylie/tmp/alsa-fix/alsa-utils-1.0.15/include'
Making all in alsactl
make[1]: Entering directory `/home/lwylie/tmp/alsa-fix/alsa-utils-1.0.15/alsactl'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \
        then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT state.o -MD -MP -MF ".deps/state.Tpo" -c -o state.o state.c; \
        then mv -f ".deps/state.Tpo" ".deps/state.Po"; else rm -f ".deps/state.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT names.o -MD -MP -MF ".deps/names.Tpo" -c -o names.o names.c; \
        then mv -f ".deps/names.Tpo" ".deps/names.Po"; else rm -f ".deps/names.Tpo"; exit 1; fi
gcc  -g -O2   -o alsactl  alsactl.o state.o names.o  -lasound -lm -ldl -lpthread
make[1]: Leaving directory `/home/lwylie/tmp/alsa-fix/alsa-utils-1.0.15/alsactl'
Making all in alsaconf
make[1]: Entering directory `/home/lwylie/tmp/alsa-fix/alsa-utils-1.0.15/alsaconf'
Making all in po
make[2]: Entering directory `/home/lwylie/tmp/alsa-fix/alsa-utils-1.0.15/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/lwylie/tmp/alsa-fix/alsa-utils-1.0.15/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lwylie/tmp/alsa-fix/alsa-utils-1.0.15/alsaconf'
make: *** [all-recursive] Error 1

```

Any recommendations would be greatly appreciated :)

---

### Post by lwylie on 2007-11-12
Well after searching around a bit I found a great HOWTO and am now listening to music with the headphone jack working :guitar:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Although its for the HDA Intel chipset it should for for compiling ALSA in general.

---

### Post by ukripper on 2007-12-04
> **lwylie said:**
> Well after searching around a bit I found a great HOWTO and am now listening to music with the headphone jack working :guitar:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Although its for the HDA Intel chipset it should for for compiling ALSA in general.

Use latest version of alsa your sound will be fixed [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

