---
title: "Hauppage HD PVR installation?"
date: 2010-09-15
forum: Hardware
---

### Post by iFritzL on 2010-09-15
Hey guys, well i have been running my HD PVR on windows for a while now and windows has really started to annoy me so i decided to switch to Ubuntu. I have run ubuntu before but im still completely clueless on how anything really works, all i need is web browsing, my music and to be able to record videos with my HD PVR.

So i was told to follow this guide to get the PVR to work on Ubuntu 10.04:

```

[Downloading]
$ sudo apt-get install build-essential mercurial linux-headers-`uname -r`
$ hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
$ cd v4l-dvb

[Compiling]
$ make

If that gives you an error, try this:
$ cd v4l
Open the file ".config" in your favourite text-editor, search for "CONFIG_DVB_FIREDTV", replace "m" with "n", save.
$ cd ..
$ make

[Installing]
$ sudo make install
$ sudo modprobe hdpvr
```

When i try to compile i get this error:

```

alex@alex-desktop:~/v4l-dvb$ make
make -C /home/alex/v4l-dvb/v4l 
make[1]: Entering directory `/home/alex/v4l-dvb/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.32

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at http://kernel.org.
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

LIRC: Requires at least kernel 2.6.36
IR_LIRC_CODEC: Requires at least kernel 2.6.36
IR_IMON: Requires at least kernel 2.6.36
IR_MCEUSB: Requires at least kernel 2.6.36
V4L2_MEM2MEM_DEV: Requires at least kernel 2.6.33
VIDEO_TVP7002: Requires at least kernel 2.6.34
VIDEO_AK881X: Requires at least kernel 2.6.33
File not found: ../linux/drivers/media/video/davinci/Kconfig at ./scripts/make_kconfig.pl line 283, <GEN7> line 541.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'. Stop.
make[1]: Leaving directory `/home/alex/v4l-dvb/v4l'
make: *** [all] Error 2

```

From what i understand something is wrong with my kernel? Now as i said im completely new so try not to go to hard on me and can someone provide a fix for my problem, thanks alot.

---

### Post by cgy on 2010-09-15
as you do not use davinci card just copy the missing file into that folder from some another one.
Some how someone has forgotten to place a corresponding file there :)

It worked for me well

---

### Post by cgy on 2010-09-15
and after doing make config
change m to and also for the davinci card

---

### Post by iFritzL on 2010-09-15
Im quite new to ubuntu, none of what you said just made sense to me.

---

### Post by cgy on 2010-09-16
File not found: ../linux/drivers/media/video/davinci/Kconfig at ./scripts/make_kconfig.pl line 283, <GEN7> line 541.



simply there is a missing  file called Kconfig in the subfolder linux/drivers/media/video/davinci/

if you look to other folders in the  linux/drivers/media/video/ you will notice that all of them have a file called Kconfig

so in order for the "make" script to stop complaining, just copy some file called Kconfig from any other similar folder to linux/drivers/media/video/davinci/

after that run  the command:

make config 

and when you get the first question do CTRL-C to exit

running make config shall create a hidden file .config in V4L subfolder

then you edit this file and find CONFIG_DVB_FIREDTV and change m to n on this line and also 
CONFIG_DVB_DAVINCI and change m to n

continue with the  proceture you have correctly metioned in your message

---

### Post by cgy on 2010-09-16
disregard this part (not needed):

"and also 
CONFIG_DVB_DAVINCI and change m to n"

---

