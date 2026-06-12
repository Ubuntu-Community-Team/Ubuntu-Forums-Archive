---
title: "Installing ALSA"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by vs292 on 2007-05-22
Hey there

I've recently got a Creative Audigy ZS 2 PCMCIA soundcard and want to get it working in Kubuntu Feisty.

I am in the process of installing the ALSA drivers with the appropriate module (emu10k1), and have hit my first main stumbling block.

According to the ALSA installation guide for this module:
> In a shell type these commands:

Make a directory to store the alsa source code in.

        cd /usr/src
        mkdir alsa
        cd alsa
        cp /downloads/alsa-* .

Now unzip and install the alsa-driver package

        bunzip2 alsa-driver-xxx
        tar -xf alsa-driver-xxx
        cd alsa-driver-xxx
        ./configure --with-cards=emu10k1 --with-sequencer=yes;make;make install


I got as far as the last line (and had append most of the lines with sudo) and received this message:
```
vs292@vs292:/usr/src/alsa/alsa-driver-1.0.9$ sudo ./configure --with-cards=emu10k1
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

I can't make head nor tail of the config.log. What modules do I need for this? According to Adept, I've got gcc, gcc-3.3-base, gcc-4.1 and gcc-4.1-base already installed.

I'm quite stumped!

Any help will be appreciated!
:)

---

### Post by cptcrunch on 2007-05-22
this how to should help you with installing the latest ALSA drivers. 

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

instead of sudo ./configure --with-cards=hda-intel try

./configure --with-cards=emu10k1 



Give er a go...

---

