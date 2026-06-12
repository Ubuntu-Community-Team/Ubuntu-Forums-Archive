---
title: "nForce 2 /Realtek sound problem"
date: 2008-07-20
forum: Hardware
---

### Post by cobolt01 on 2008-07-20
The sound card shows to be working but there's no sound. I'm 80% sure that its Realtek AC'97 based on board sound. I tried installing the realtek drivers but I got this output. I've been struggling with this problem for over a year, please help.
```
.....Decompress Driver source v1.0.11-4.06a
.....Decompress ALSA Library source v1.0.9
.....Decompress ALSA Utility v1.09a
Remove old sound driver
Compile Driver........
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
find: /root/orig: No such file or directory
find: /root/orig/alsa-driver-1.0.14: No such file or directory
find: /root/orig: No such file or directory
find: /root/orig/alsa-driver-1.0.14: No such file or directory
find: /root/orig: No such file or directory
find: /root/orig/alsa-driver-1.0.14: No such file or directory
make dep
find: /root/orig: No such file or directory
find: /root/orig/alsa-driver-1.0.14: No such file or directory
find: /root/orig: No such file or directory
find: /root/orig/alsa-driver-1.0.14: No such file or directory
find: /root/orig: No such file or directory
find: /root/orig/alsa-driver-1.0.14: No such file or directory
make[1]: Entering directory `/home/emlyn/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a'
make[2]: Entering directory `/home/emlyn/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore'
Makefile:5: /root/orig/alsa-driver-1.0.14/toplevel.config: No such file or directory
Makefile:6: /root/orig/alsa-driver-1.0.14/Makefile.conf: No such file or directory
Makefile:16: /root/orig/alsa-driver-1.0.14/alsa-kernel/core/Makefile: No such file or directory
Makefile:28: /root/orig/alsa-driver-1.0.14/Rules.make: No such file or directory
make[2]: *** No rule to make target `/root/orig/alsa-driver-1.0.14/Rules.make'.  Stop.
make[2]: Leaving directory `/home/emlyn/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/emlyn/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a'
make: *** [include/sndversions.h] Error 2
find: /root/orig: No such file or directory
find: /root/orig/alsa-driver-1.0.14: No such file or directory
find: /root/orig: No such file or directory
find: /root/orig/alsa-driver-1.0.14: No such file or directory
find: /root/orig: No such file or directory
find: /root/orig/alsa-driver-1.0.14: No such file or directory
if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /root/orig/alsa-driver-1.0.14/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
find /lib/modules/2.6.15-1.2054_FC5/kernel/sound -name 'snd*.*o' | xargs rm -f
find: /lib/modules/2.6.15-1.2054_FC5/kernel: No such file or directory
find /lib/modules/2.6.15-1.2054_FC5/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find: /lib/modules/2.6.15-1.2054_FC5/kernel: No such file or directory
make[1]: Entering directory `/home/emlyn/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore'
Makefile:5: /root/orig/alsa-driver-1.0.14/toplevel.config: No such file or directory
Makefile:6: /root/orig/alsa-driver-1.0.14/Makefile.conf: No such file or directory
Makefile:16: /root/orig/alsa-driver-1.0.14/alsa-kernel/core/Makefile: No such file or directory
Makefile:28: /root/orig/alsa-driver-1.0.14/Rules.make: No such file or directory
make[1]: *** No rule to make target `/root/orig/alsa-driver-1.0.14/Rules.make'.  Stop.
make[1]: Leaving directory `/home/emlyn/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/acore'
make: *** [install-modules] Error 1
Creating mixer?...done.
Creating sequencer...done.
Creating midi0?...done.
Creating dsp?...done.
Creating audio?...done.
Creating sndstat...done.
Creating music...done.
Creating dmmidi?...done.
Creating dmfm?...done.
Creating amixer?...done.
Creating adsp?...done.
Creating amidi?...done.
Creating admmidi?...done.
rm: cannot remove `/dev/snd': Is a directory
Creating snd/control?...done.
Creating snd/seq...done.
Creating snd/timer...done.
Creating snd/hw??...done.
Creating snd/midi??...done.
Creating snd/pcm??p...done.
Creating snd/pcm??c...done.
Creating aload?...done.
Creating aloadSEQ...done.
Remove old alsa library
Compile ALSA Library.....
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Compile ALSA Utility......
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Remove Folder.....
install: line 102: alsaconf: command not found

```

---

