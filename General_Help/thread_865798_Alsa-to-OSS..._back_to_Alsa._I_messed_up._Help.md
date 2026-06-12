---
title: "Alsa-to-OSS... back to Alsa. I messed up. Help?"
date: 2008-07-21
forum: General Help
---

### Post by Roasted on 2008-07-21
I installed OSS under the notion that it typically sounds better than Alsa. After finding that statement false, I decided to go back to Alsa for the fact that with Alsa, things just... worked. Youtube, flash, whatever. Everything just worked.

Now, I can't get it to work for the life of me. I have no clue what I'm doing or how to fix it.

I started by downloading the latest alsa packages. I extracted them all and went to ./configure the drivers package. K, great. Worked. I went to make, and kicked back some error.



make[2]: Leaving directory `/home/jason/Desktop/drivers/pcmcia'
make[2]: Entering directory `/home/jason/Desktop/drivers/misc'
make[2]: Leaving directory `/home/jason/Desktop/drivers/misc'
make[1]: Leaving directory `/home/jason/Desktop/drivers'
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/jason/Desktop/drivers  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/jason/Desktop/drivers/soc/soc-dapm.o
In file included from /home/jason/Desktop/drivers/soc/soc-dapm.c:2:
/home/jason/Desktop/drivers/soc/../alsa-kernel/soc/soc-dapm.c: In function ‘dapm_pop_time_store’:
/home/jason/Desktop/drivers/soc/../alsa-kernel/soc/soc-dapm.c:834: error: implicit declaration of function ‘strict_strtoul’
make[3]: *** [/home/jason/Desktop/drivers/soc/soc-dapm.o] Error 1
make[2]: *** [/home/jason/Desktop/drivers/soc] Error 2
make[1]: *** [_module_/home/jason/Desktop/drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [compile] Error 2
jason@jason-hardy:~/Desktop/drivers$ 




In short, how do I get alsa working again?

---

### Post by Roasted on 2008-07-21
sudo dpkg --remove --force-depends --force-remove-reinstreq oss-linux

I used that command to get rid of oss, and it uninstalled, it seems. Now under sys-pref-sounds, alsa isn't listed under devices.

In fact, nothing is listed under devices. So... I'm essentially starting over from scratch.

So at this point, how do I get alsa installed? Running ./configure + make to the driver package of the latest alsa driver yields the SAME error I got above. Is the alsa driver in the repos? I found utils and tools, but not the driver... How else can I get this to work?

---

### Post by sydbat on 2008-07-21
ALSA should be in the repos...try a search in Synaptic...I found alsa-base, which looks like the stuff you need.

---

### Post by Roasted on 2008-07-21
I installed that, however, now that I think about it I don't think I installed it AFTER doing the removal of OSS. Would that have made a difference? 

Since removing OSS, if I go home right now and install alsa-base, would that be sufficient to what I need?

---

### Post by Roasted on 2008-07-21
Aight, guys. I've gone crazy without music, so I reinstalled. It's currently installing as we speak (oh the good side of having a laptop around.)

But, I'm STILL bothered. I hate resorting to reinstalling to fix a problem. It's not fixing the problem to me. How would I fix this issue had I still been dealing with it? I'd still like to find some sort of an answer, despite the fact reinstalling will solve it. Any ideas?

---

### Post by applezip on 2008-07-22
I got around the compilation error by configuring to only compile for my card. I'm not sure why it worked, but it did...

I have an ICE1724 based card, you could try it with your card's driver in place of it.

```

./configure --with-cards=ice1724 --with-sequencer=yes
```

Good luck

---

### Post by fung on 2008-07-29
What would I type in the terminal to find out which card driver I supposed to put in? Sound currently works but I get an error compiling alsa version 1.0.17. Is it asoundconf something something..?

---

