---
title: "Compiling alsa from CVS in Gutsy on thinkpad T61"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by k@zp3r on 2007-08-07
Hi there,

I am the happy owner of a Lenovo Thinkpad T61. It's a very nice machine, but since it's very new, it seems the Linux support is still a bit lacking.

In order to make the sound work, I need to compile the alsa drivers, namely the intel_hda driver, from alsa-cvs. I just haven't been able to figure that out. I cannot compile the drivers outside of the kernel source and if I merge them into the kernel source, I get an error about version mismatch if I use the make-kpkg command and compiler errors about missing config.h if i use 'make modules'.

Actually, if I get the kernel sources (apt-get install kernel-source) and try to install them unmodified with make-kpkg, I get the version mismatch errors.

I upgraded to Gutsy in hope that the newer drivers would be there quicker, so I do know that I'm running an unstable release and I do know that compiling stuff from a cvs tree is sometimes a bit cumbersome, but I really cannot figure out what is the right approach.

Anyone who could please be helpful with some guidelines?

Thanks a lot!

---

### Post by renzokuken on 2007-08-07
why not just download the sourec from alsa-project.org

install the build-essentials package so you can compile (build-essential is in synaptic or apt-get it)

then extract the alsa-driver tar.gz and run

```
cd alsa*
./configure
make
sudo make install

```

thats how i updated my alsa

---

### Post by k@zp3r on 2007-08-07
I need the CVS version of Alsa, since the bugfixes for the sound card in my laptop didn't make it to the latest Alsa release, so I cannot just download the files from the ftp mirrors at alsa-project.org.

Your input was very helpful though, since I figured out to download and compile the drivers with Mercurial (never heard of that before) and now my sound is working. Part of the problem seems to be that for some reason whatever I try to compile against my kernel seems to think I'm running 2.6.22.1 where I'm actually running 2.6.22-9.

The drivers load though, and I have sound, so I'm happy and I'm quite sure the issues will be fixed the closer Gutsy comes to being released.

Thanks once again!

---

### Post by serezha on 2007-08-10
I am having the same problem on the same laptop. Can  you tell how you compiled alsa?

serezha.

---

### Post by socrates.wei on 2007-08-11
You can vist this site
[http://alsa.opensrc.org/index.php/AlsaCVS](http://alsa.opensrc.org/index.php/AlsaCVS)

Notice that you should install these packages:
automake, autoconfig, libtool, python-dev, build-essential

If you have a problem about missing Python.h when you compile alsa-lib
you should do these

```

cd /usr/include
sudo ln -s python2.5 python

```

It works fine for my X61

---

### Post by zorkerz on 2007-08-11
which version of automake did you use? there are a number in the repos

I just started [this thread]("http://http://ubuntuforums.org/showthread.php?p=3171965#post3171965") for anyone with an X61 on Gutsy. It would be great if you could drop a line if anyone has solved  any other problems.

---

### Post by serezha on 2007-08-11
For some reason I could not compile alsa from CVS, but successfully compiled it using snapshots from here [ftp://ftp.suse.com/pub/projects/alsa/snapshot/]("ftp://ftp.suse.com/pub/projects/alsa/snapshot/")

Sound working.:guitar:

serezha.

---

### Post by turbage on 2007-08-14
Ok, I am having a LOT of trouble getting sound to work on my t61 using Gutsy

What ive done

**1) compiled using ALSACVS (thinkwiki's solution)**

```


#install requisite packages
 sudo apt-get install automake
 sudo apt-get install autoconf
 sudo apt-get install libtool
 sudo apt-get install python-dev
 sudo apt-get install build-essential
 sudo apt-get install gettext
 sudo apt-get install libncurses5-dev

#set up directory
 mkdir alsacvs
 cd alsacvs

#download the latest rysnc of the cvs to /home/brian/alsacvs

 rsync -avz --delete rsync://alsa.alsa-project.org/hg /home/brian/alsacvs

#set up alsa-driver

 cd alsa-driver
 autoconf
 ./cvscompile --with-cards=intel_hda
 sudo make install

#set up alsa-lib

 cd /usr/include
 sudo ln -s python2.5 python
 cd /home/brian/alsacvs/alsa-lib
 ./cvscompile
 sudo make install

#set up alsa-utils
 cd ../asla-utils
 ./cvscompile
 sudo make install
```

What this got me:

A totally non-functioning, non-recognizable sound card.


So, I moved on:
**2) Compiled it from snapshots (see above post) using ./hgcompile**

Now I can play with the sliders, and  $ aplay -l returns data.......but NO SOUND!!

Try, try again:
[B]
3) Used ciphermonk's method (patch_analog.c) recompilation[/B]

Patched fine, installed OK......fixed the /etc/modprobe.d/alsa-base file..............

Computer boots, but gnome does not load.   (I booted into recovery and nano /etc/modprobe.d/alsa-base and removed the options snd-intel-hda(...) and there were no changes)



I need help!

Let me know what information you need to help me out, I'll try my best. Sound is a relatively low priority feature, but I switched from feisty to Gutsy so I can use compizfusion......and to sacrafice sound for eyecandy would be a pity.

Thanks!

---

### Post by checkup on 2007-08-18
maybe it's the same problem as with the 60s... you must not turn off the modem in the bios, this disables sound too.

---

### Post by czheng on 2007-08-18
I did this:

[http://skinetwork.org/mediawiki/index.php/Fedora-T61#Sound](http://skinetwork.org/mediawiki/index.php/Fedora-T61#Sound)

Except instead of modifying /etc/modprobe.conf (I don't have one) I added the relevant line at the end of /etc/modprobe.d/alsa-base

All set.

---

### Post by era86 on 2007-08-21
> **czheng said:**
> I did this:

[http://skinetwork.org/mediawiki/index.php/Fedora-T61#Sound](http://skinetwork.org/mediawiki/index.php/Fedora-T61#Sound)

Except instead of modifying /etc/modprobe.conf (I don't have one) I added the relevant line at the end of /etc/modprobe.d/alsa-base

All set.

Has anyone figured out how to get this working?  I still can't seem to get it to work.  Do I use hda_intel?  DOes that vary?  I'm lost...

---

### Post by zorkerz on 2007-08-23
I got my sound working for a number of days but not it has stopped again. I do not know what caused this but i have suspicions that it was the new kernal in gutsy. Anyone else having problems.
Has anyone filed a bug report because this will not be fixed unless the developers know about it.

update: Im having a really odd sound problem [http://ubuntuforums.org/showthread.php?p=3246495#post3246495](http://ubuntuforums.org/showthread.php?p=3246495#post3246495)

this [thread]("http://ubuntuforums.org/showthread.php?t=503233") has a good post on getting sound to work
also other x61 stuff at this [thread]("http://ubuntuforums.org/showthread.php?t=523022")

---

### Post by sancho panza on 2007-08-25
> **era86 said:**
> Has anyone figured out how to get this working?  I still can't seem to get it to work.  Do I use hda_intel?  DOes that vary?  I'm lost...

I tried and got stuck at ```
./configure && make
``` with the error (last few lines of output:```

config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
make dep
make[1]: Entering directory `/home/prash/alsa-driver-1.0.14'
make[2]: Entering directory `/home/prash/alsa-driver-1.0.14/acore'
copying file alsa-kernel/core/pcm.c
/home/prash/alsa-driver-1.0.14/utils/patch-alsa: 24: patch: not found
make[2]: *** [pcm.c] Error 1
make[2]: Leaving directory `/home/prash/alsa-driver-1.0.14/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/prash/alsa-driver-1.0.14'
make: *** [include/sndversions.h] Error 2
```

Any ideas?

---

### Post by sancho panza on 2007-08-26
Got sound working in Gutsy on Thinkpad T61. The details are here:
[http://ubuntuforums.org/showthread.php?t=535476](http://ubuntuforums.org/showthread.php?t=535476)

Cheers!

---

### Post by wsuetholz on 2007-11-06
> **sancho panza said:**
> I tried and got stuck at ```
./configure && make
``` with the error (last few lines of output:```

config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
make dep
make[1]: Entering directory `/home/prash/alsa-driver-1.0.14'
make[2]: Entering directory `/home/prash/alsa-driver-1.0.14/acore'
copying file alsa-kernel/core/pcm.c
/home/prash/alsa-driver-1.0.14/utils/patch-alsa: 24: patch: not found
make[2]: *** [pcm.c] Error 1
make[2]: Leaving directory `/home/prash/alsa-driver-1.0.14/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/prash/alsa-driver-1.0.14'
make: *** [include/sndversions.h] Error 2
```

Any ideas?

Either you need to run apt-get install build-essential or apt-get install patch

---

### Post by mightysween on 2007-11-27
For the record, 

apt-get install build-essential

worked to solve this problem for me on a Dell Inspiron 8200.

Thanks, wsuetholz. :)

---

### Post by Hoppiesbox on 2007-12-29
yeah, add 
apt-get install build-essentials 
to the method described here: [http://alsa.opensrc.org/index.php/Quick_Install](http://alsa.opensrc.org/index.php/Quick_Install)

---

### Post by syxbit on 2008-01-21
try this
[http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

---

