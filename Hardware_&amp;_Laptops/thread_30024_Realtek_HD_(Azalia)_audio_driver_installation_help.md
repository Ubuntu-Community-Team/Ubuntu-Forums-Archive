---
title: "Realtek HD (Azalia) audio driver installation help"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by TheRealEdwin on 2005-04-26
I just noticed Realtek released some drivers for my sound card of my laptop (ASUS Z71V) and wanted to try them out as I have no sound. I've only been using linux for a little bit (1 month) and still do not fully grasp all concepts, so I turn to you guys for help. Everything was going on till I got here.

```
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/edwin/Desktop/sound/alsa-driver-1.0.4
checking cross compile...
checking for directory with kernel source... /usr/src/linux
_**checking for kernel version... The file /usr/src/linux/include/linux/version.h d oes not exist.**_
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
root@Doomhammer:/home/edwin/Desktop/sound/alsa-driver-1.0.4 # make
find: /home/alsa-driver-1.0.4: No such file or directory
find: /home/alsa-driver-1.0.4/alsa-kernel/: No such file or directory
find: /home/alsa-driver-1.0.4: No such file or directory
find: /home/alsa-driver-1.0.4/alsa-kernel/: No such file or directory
find: /home/alsa-driver-1.0.4: No such file or directory
find: /home/alsa-driver-1.0.4/alsa-kernel/: No such file or directory
make dep
find: /home/alsa-driver-1.0.4: No such file or directory
find: /home/alsa-driver-1.0.4/alsa-kernel/: No such file or directory
find: /home/alsa-driver-1.0.4: No such file or directory
find: /home/alsa-driver-1.0.4/alsa-kernel/: No such file or directory
find: /home/alsa-driver-1.0.4: No such file or directory
find: /home/alsa-driver-1.0.4/alsa-kernel/: No such file or directory
make[1]: Entering directory `/home/edwin/Desktop/sound/alsa-driver-1.0.4'
make[2]: Entering directory `/home/edwin/Desktop/sound/alsa-driver-1.0.4/acore'
Makefile:5: /home/alsa-driver-1.0.4/toplevel.config: No such file or directory
Makefile:6: /home/alsa-driver-1.0.4/Makefile.conf: No such file or directory
Makefile:11: /home/alsa-driver-1.0.4/alsa-kernel/core/Makefile: No such file or directory
Makefile:15: /home/alsa-driver-1.0.4/Rules.make: No such file or directory
make[2]: *** No rule to make target `/home/alsa-driver-1.0.4/Rules.make'.  Stop.
make[2]: Leaving directory `/home/edwin/Desktop/sound/alsa-driver-1.0.4/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/edwin/Desktop/sound/alsa-driver-1.0.4'
make: *** [include/sndversions.h] Error 2
root@Doomhammer:/home/edwin/Desktop/sound/alsa-driver-1.0.4 # make install
find: /home/alsa-driver-1.0.4: No such file or directory
find: /home/alsa-driver-1.0.4/alsa-kernel/: No such file or directory
find: /home/alsa-driver-1.0.4: No such file or directory
find: /home/alsa-driver-1.0.4/alsa-kernel/: No such file or directory
find: /home/alsa-driver-1.0.4: No such file or directory
find: /home/alsa-driver-1.0.4/alsa-kernel/: No such file or directory
find /lib/modules/2.4.21-4.EL/kernel/sound -name 'snd*.*o' | xargs rm -f
find: /lib/modules/2.4.21-4.EL/kernel/sound: No such file or directory
make[1]: Entering directory `/home/edwin/Desktop/sound/alsa-driver-1.0.4/acore'
Makefile:5: /home/alsa-driver-1.0.4/toplevel.config: No such file or directory
Makefile:6: /home/alsa-driver-1.0.4/Makefile.conf: No such file or directory
Makefile:11: /home/alsa-driver-1.0.4/alsa-kernel/core/Makefile: No such file or directory
Makefile:15: /home/alsa-driver-1.0.4/Rules.make: No such file or directory
make[1]: *** No rule to make target `/home/alsa-driver-1.0.4/Rules.make'.  Stop.
make[1]: Leaving directory `/home/edwin/Desktop/sound/alsa-driver-1.0.4/acore'
make: *** [install-modules] Error 1
root@Doomhammer:/home/edwin/Desktop/sound/alsa-driver-1.0.4 # ./snddevices
Creating /dev/mixer?... done
Creating /dev/sequencer... done
Creating /dev/midi0?... done
Creating /dev/dsp?... done
Creating /dev/audio?... done
Creating /dev/sndstat... done
Creating /dev/music... done
Creating /dev/dmmidi?... done
Creating /dev/dmfm?... done
Creating /dev/amixer?... done
Creating /dev/adsp?... done
Creating /dev/amidi?... done
Creating /dev/admmidi?... done
create symbolic link `/dev/mixer' to `/dev/mixer0'
create symbolic link `/dev/midi' to `/dev/midi00'
create symbolic link `/dev/dsp' to `/dev/dsp0'
create symbolic link `/dev/audio' to `/dev/audio0'
create symbolic link `/dev/sequencer2' to `/dev/music'
create symbolic link `/dev/adsp' to `/dev/adsp0'
create symbolic link `/dev/amidi' to `/dev/amidi0'
Creating /dev/snd/control?... done
Creating /dev/snd/seq... done
Creating /dev/snd/timer... done
Creating /dev/snd/hw??... done
Creating /dev/snd/midi??... done
Creating /dev/snd/pcm??p... done
Creating /dev/snd/pcm??c... done
ALSA loader devices
Creating /dev/aload?... done
Creating /dev/aloadSEQ... done

```

Any suggestions or ideas?

---

### Post by K_Factor on 2005-05-14
I had the same problem, the official drivers are made for kernel 2.2-2.4 and that's why they couldn't compile.

You have to download, compile and install the latest version of ALSA,
run alsaconf and everything will work fine. ;-)

---

### Post by Caligatio on 2005-06-03
I'm painfully new to everything Linux so I stumbled into a problem.  First of all, APT only has 1.0.8  Do I have to uninstall this before using 1.0.9?  I went to uninstall but it said it had to uninstall like 15 other things.

Second, I ran the config on the 1.0.9 and it complained it couldn't find the Linux source... where is this?

---

### Post by ewerx on 2005-07-09
If you resolved this issue, any chance you can post the steps you took? I'm also trying to get sound working on my Z71V and don't know where to begin...

---

### Post by antip8dean on 2005-11-12
Hi

I also have had this problem, if you could let me know what steps you took to install the Azalia driver for linux, that would be good too.

I am in deep need for getting sound to go on the ubuntu platform.

cheers

---

### Post by ctothej on 2006-04-30
Anyone solve this problem yet?

---

### Post by AkashChandrashekar on 2006-07-05
Hi guys, 

It appears as if the kernel-headers file is a mis-match to the actual kernel you are operating in . so.... 

do a sudo uname-a to get the kernel version you are running against. 

Then pay close attention to the last thre or four numbers...the kernel number/version. 

Install the EQUIVALENT kernel headers against synaptic and try again. 

Id even do a make clean before trying to compile again. It should fix the issues

---

### Post by amaan on 2007-02-24
i'm a complete n00b to linux and i have an asus w7j machine without sound, i believe what you said may work, although i don't understand what that means

is there a guide i can follow that would make everything easier?

thanks in advance, really looking forward to getting sound on my ubuntu machine :)

---

