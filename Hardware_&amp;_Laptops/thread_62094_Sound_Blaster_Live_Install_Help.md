---
title: "Sound Blaster Live Install Help"
date: 2005-09-03
forum: Hardware &amp; Laptops
---

### Post by eduncan01 on 2005-09-03
Hi,

I just recently installed a sound blaster LIVE sound card on my PC.  I have tried the following (as suggested on the ALSA website for the driver after downloading the latest alsa-driver file)  

[COLOR=Red]Quick Install

NB. If you are using cvs then you need to type

         ./cvscompile "or" make build

instead of

         ./configure

In a shell type these commands:

Make a directory to store the alsa source code in.

        cd /usr/src
        mkdir alsa
        cd alsa
        cp /downloads/alsa-* .

Now unzip and install the alsa-driver package

        bunzip2 alsa-driver-xxx
        tar -xf alsa-driver-xxx
        cd alsa-driver-xxx
        ./configure --with-cards=emu10k1 --with-sequencer=yes;make;make install[/COLOR]


 sudo ./configure --with-cards=emu10k1 --with-sequencer=yes;make;make install

But I get the following error --

checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9b'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9b'

Please, run the configure script as first...

rm -f /snd*.*o /persist.o /isapnp.o
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9b/acore'
Makefile:6: /usr/src/alsa/alsa-driver-1.0.9b/Makefile.conf: No such file or directory
make[1]: *** No rule to make target `/usr/src/alsa/alsa-driver-1.0.9b/Makefile.conf'.  Stop.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9b/acore'
make: *** [install-modules] Error 1

I have even tried ./configure by itself, but receive the same error.

Is there another way of installing the drivers for the LIVE card in Ubuntu?  If not, can someone help with the Alsa issue I am having.  I appreciate any suggestions.

Rock On!
Eric

---

### Post by MrJack on 2005-09-03
Firstly you need the build-essential package

```
apt-get install build-essential
```.
then try again.

---

### Post by eduncan01 on 2005-09-04
I'll give it a try.

Thanks!
Eric

---

