---
title: "Audigy LS revisited..."
date: 2005-02-09
forum: Hardware &amp; Laptops
---

### Post by sharkzf6 on 2005-02-09
I have unbuntu working nicely with all my hardware. My initial install was with my old SB Live 16 bit card due to known issues with Linux and 24 bit sound processing. I'm not sure this is a "real" issue however. Is it possible to get a 24 bit sound card working with Linux and, if so, how about the lower end Audigy LS card which offloads mixer duties to the CPU? After using unbuntu with the SB Live, then going back to XP with my Audigy, I realized how much better the Audigy sounds and would like to get it working with Linux if possible. Thanks.

---

### Post by sharkzf6 on 2005-02-09
So apparently, ALSA does support the Audigy LS based on what I just read on their web site. It looks like I have to build some modules and load them using the files from their site. Problem is, when I get to the step to actually build the modules, I get the following error after entering *./configure --with-cards=audigyls --with-sequencer=yes;make;make install* at the command prompt,

[b]checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.8rc2'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.8rc2'

Please, run the configure script as first...

rm -f /snd*.*o /persist.o /isapnp.o
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.8rc2/acore'
Makefile:6: /usr/src/alsa/alsa-driver-1.0.8rc2/Makefile.conf: No such file or directory
make[1]: *** No rule to make target `/usr/src/alsa/alsa-driver-1.0.8rc2/Makefile.conf'.  Stop.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.8rc2/acore'
make: *** [install-modules] Error 1[/b]

Anyone know what this is all about? Thanks.

---

### Post by sharkzf6 on 2005-02-09
I realize I'm anwering my own thread here but that's not uncommon in this forum ;)
It seems to me since ALSA support, version 1.0.6 is built into my kernel, 2.6.10, that all I need to do is figure out how to tell the ALSA driver that the card is there. Can anyone explain to me how this works or why new modules would have to be installed? I'm a newb...bet that was a tough one to figure out. Thanks.

---

### Post by sharkzf6 on 2005-02-09
Another interesting note: ALSA has detected the sound chip in my TV tuner/video capture card which is a Hauppauge with BT878 chipset. Of course, that's not a sound card in the conventional sense, it's part of the TV tuner/video capture device. LOL, too bad.

---

### Post by malegria on 2005-02-09
Ok. First of all. You will need to get the newest alsa drivers from ALSA (at their site). Also, make sure you have the source for your kernel (make sure it gets untared too when you get it) and install GCC Go to /usr/src and see it's name.

Now untar your alsa drivers.
Open a terminal and cd to the folder created when you untared the drivers.
run this: ```
./configure --with-cards=ca0106 --with-sequencer=yes --with-kernel=/usr/src/your_kernel_source
```
If all goes well, run ```
make
```

If that goes well, run: ```
sudo make install
```

If all goes well there, run: ```
sudo alsaconf

``` 

Reboot. When you're back run ```
alsamixer
```

Raise the volume of the bar saying "Analog F." Make sure your speakers are low, and don't put the volume about 70 or else the sound will crackle.

---

