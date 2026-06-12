---
title: "ES1887 card not recognized"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by dub_u on 2008-03-20
Hi, I need help with Xubuntu not recognizing my sound card.

The computer is an old Compaq Presario 4860 (333Mhz & 320Mb RAM) with ESS es1887 on-board card.

I tried to follow the instructions at [http://www.alsa-project.org/main/index.php/Matrix:Module-es18xx]("http://www.alsa-project.org/main/index.php/Matrix:Module-es18xx")
using version 1.0.16 of alsa-driver alsa-lib and alsa-utils, since it was listed as the most recent stable one.

```
bunzip2 alsa-driver-xxx
tar -xf alsa-driver-xxx
cd alsa-driver-xxx
./configure --with-cards=es18xx --with-sequencer=yes ; make ; make install
```
After looking on this forum, as well as others, the es1887 is defined as an ISA-card, therefore I added the line > --with-isapnp=no to the configure command.

Everything seemed to go well until the following lines
> The snddevices script sets the permissions for the devices it creates to root.
If you use devfs then you should not run the snddevices script.
Otherwise run:

       chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi 


Running that command I got an error message telling "directory doesn't exist".
Since I'm not sure whether I use devfs I decided to give it a go anyway.
```
cd ..
bunzip2 alsa-lib-xxx
tar -xf alsa-lib-xxx
cd alsa-lib-xxx
./configure ; make ; make install

```

and
```
cd ..
bunzip2 alsa-utils-xxx
tar -xf alsa-utils-xxx
cd alsa-utils-xxx
./configure ; make ; make install
```

and
```
modprobe snd-es18xx ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
```

completed without any error messages, but yet
```
aplay -l

```
returns "no such device".

I am stuck, so if anyone has got an idea, please help.

Being new to linux, there may be something obvious that I missed, but I can't figure out how to do this differently to get it work...

---

