---
title: "[SOLVED] Sound on Gateway MT3422"
date: 2008-03-08
forum: Hardware &amp; Laptops
---

### Post by maximusmmiv on 2008-03-08
I'm attempting to use the "quick" fix offered by antonywilliams.com (found [here]("http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html")) to get sound working on my Gateway MT3422 laptop with a fresh install of Ubuntu 7.10. Several comments on the article from MT3422 users report flawless success after the first try. I guess I'm not so lucky.

I'm a brand new Linux user, so please bear with my idiocy if the solution to my problem is blazingly obvious to you, because it's not to me.

I've created the two scripts (found on antonywilliams.com). I ran the first script as instructed, restarted, and ran the second script. The second script doesn't do anything and reports missing files or folders. I would assume that those are something the first script was supposed to create.

Here's the output from the first script:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ncurses-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.22-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
downloading alsa packages...
--23:06:22--  ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2
           => `alsa-driver-1.0.15.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/driver ... done.
==> PASV ... done.    ==> RETR alsa-driver-1.0.15.tar.bz2 ... done.
Length: 2,677,415 (2.6M) (unauthoritative)

100%[========================================================>] 2,677,415     52.24K/s    ETA 00:00

23:07:18 (49.38 KB/s) - `alsa-driver-1.0.15.tar.bz2' saved [2677415]

--23:07:18--  ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2
           => `alsa-lib-1.0.15.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/lib ... done.
==> PASV ... done.    ==> RETR alsa-lib-1.0.15.tar.bz2 ... done.
Length: 793,909 (775K) (unauthoritative)

100%[========================================================>] 793,909       48.33K/s    ETA 00:00

23:07:36 (48.45 KB/s) - `alsa-lib-1.0.15.tar.bz2' saved [793909]

--23:07:36--  ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2
           => `alsa-utils-1.0.15.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/utils ... done.
==> PASV ... done.    ==> RETR alsa-utils-1.0.15.tar.bz2 ... done.
Length: 1,014,199 (990K) (unauthoritative)

100%[========================================================>] 1,014,199     49.37K/s    ETA 00:00

23:07:57 (51.44 KB/s) - `alsa-utils-1.0.15.tar.bz2' saved [1014199]

extracting alsa packages...
setting up alsa for compilation
mv: cannot move `alsa-driver-1.0.15' to a subdirectory of itself, `/usr/src/alsa/alsa-driver-1.0.15'
mv: cannot move `alsa-lib-1.0.15' to a subdirectory of itself, `/usr/src/alsa/alsa-lib-1.0.15'
mv: cannot move `alsa-utils-1.0.15' to a subdirectory of itself, `/usr/src/alsa/alsa-utils-1.0.15'
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15'

Please, run the configure script as first...

if [ -L /include/sound ]; then \
                rm -f /include/sound; \
                ln -sf /usr/src/alsa/alsa-driver-1.0.15/include/sound /include/sound; \
        else \
                rm -rf /include/sound; \
                install -d -m 755 -g root -o root /include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /include/sound; \
                done \
        fi
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1
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
now reboot your machine, and run alsa_2

```

I then restart the machine and run the second script, which outputs this:
```
cp: cannot stat `/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver*/modules/*': No such file or directory

```

Any ideas?

---

### Post by Yellow Pasque on 2008-03-09
> E: Couldn't find package ncurses-dev
This is your problem.

Go to System -> Administration -> Software Sources and make sure everything is checked on the first tab. You need that package to configure/build ALSA properly.

I would also suggest modifying the first script to use ALSA 1.0.16 instead, as it is newer/updated.

---

### Post by maximusmmiv on 2008-03-09
Thank you very, very much. I knew it was something simple, but my untrained eyes couldn't find it. I appreciate your help.

---

