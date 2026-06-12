---
title: "hda-intel alsa compilation scripts"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by Jeanpaul145 on 2007-11-13
Here is a collection of scripts I've developed to automate the compilation process of alsa 1.0.15 with hda-intel audio cards because I was getting fed up with doing the whole compilation-and-copy thing.
They're a bit stiff, but they just might work for you.
All you have to do to get started is read the README file in the archive.
Enjoy!

P.s. I don't know for a fact they will work for you; however there's a good chance they will.

---

### Post by Jeanpaul145 on 2007-11-21
Any help testing (and maybe even upgrading the functionality and usefulness) would be appreciated. If you download the script, please post your experience. Thank you in advance!

---

### Post by Remuzzz on 2008-02-05
Hi,

It doesn't work for me :( Apparently sudo doesn't have the rights to create directories. This are the errors that I'm getting:

```

Reading package lists... Done
Building dependency tree... 50%

Building dependency tree       
Reading state information... Done


libncurses5 is already the newest version.
Note, selecting libncurses5-dev instead of ncurses-dev
gettext is already the newest version.
gettext set to manual installed.

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
  libncurses5-dev: Depends: libc-dev

E: Broken packages
mkdir: cannot create directory `/usr/src/alsa': File exists
mv: cannot move `./alsa-driver-1.0.15' to a subdirectory of itself, `/usr/src/alsa/alsa-driver-1.0.15'
mv: cannot move `./alsa-lib-1.0.15' to a subdirectory of itself, `/usr/src/alsa/alsa-lib-1.0.15'
mv: cannot stat `./alsa-util-1.0.15': No such file or directory
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
cd: 40: can't cd to /usr/src/alsa/alsa-utils-1.0.15
sudo: ./configure: command not found
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.


```

I'm fed up with my sound not working properly :( Can somebody please help me how I can delete all my ALSA Drivers and re-install them again? I really want it to work!

PS: I have a Dell XPS M1330 laptop, with a Sigmatel onboard soundcard (HDA-Intel i think?)

When I go to settings and test settings I get the following errors. I suspect that there's something seriously wrong with the drivers. :(

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
```

I'm a Ubuntu newbe, can somebody help me? :D

Thx in advance.

---

### Post by Jeanpaul145 on 2008-02-05
Heya,
I built these scripts before I found out about the info on [the Gutsy Intel HD Audio Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") website. You could check there.
Alternatively (it is mentioned as an option for some audio chipsets, maybe even yours) you could try installing linux-backports-modules (you may need to enable the universe repo, I'm not sure).

Thing no. 2 I wanted to mention: these scripts are (already...sigh :popcorn: ) hopelessly outdated because ALSA 1.0.16rc2 is out already.

I Hope this info will help you!

---

### Post by Activist on 2008-03-30
how to undo any operations by the script? (makealsa step 1)

i did and i have no sound :S
previously i was ~ok (dont ask me why i run the script :P)

---

### Post by Activist on 2008-03-30
> **Activist said:**
> how to undo any operations by the script? (makealsa step 1)

i did and i have no sound :S
previously i was ~ok (dont ask me why i run the script :P)
well i found it...
for anyone (whos is as dump as me)  who wants to un-do the script and return to the default ubuntu audio (alsa drivers)
```
download ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2
open terminal and:

cd (whre the file u downloaded is)
tar -xvjf alsa-driver-1.0.15.tar.bz2
./configure
make
make install
```

---

