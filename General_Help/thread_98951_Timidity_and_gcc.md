---
title: "Timidity and gcc"
date: 2005-12-04
forum: General Help
---

### Post by bluevoodoo1 on 2005-12-04
I'm having trouble installing Timidity++, here's what I get when I try to configure. 

brian@ubuntu:~$ cd TiMidity++-2.13.0
brian@ubuntu:~/TiMidity++-2.13.0$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether grep returns status... yes
checking if --enable-debug option specified... no
checking for emacs... no
checking for xemacs... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
brian@ubuntu:~/TiMidity++-2.13.0$

I checked the gcc and get..
brian@ubuntu:~$ gcc
gcc: no input files

EDIT: I got build-essentials, seems to progress, but now I get this...

brian@ubuntu:~$ touch /usr/local/share/timidity/timidity.cfg
touch: cannot touch `/usr/local/share/timidity/timidity.cfg': No such file or directory

I'm following [http://www.geocities.jp/midi_organ_net/timidity/](http://www.geocities.jp/midi_organ_net/timidity/)


Any ideas?

---

### Post by ranf on 2005-12-04
Is 'timidity++' something different to `timidity'?
Because timidity is available from the universe repository.

---

### Post by bluevoodoo1 on 2005-12-04
ah yes. I think it is the same... but after installing it from Synaptic, I can't find it anywhere on my system...

---

