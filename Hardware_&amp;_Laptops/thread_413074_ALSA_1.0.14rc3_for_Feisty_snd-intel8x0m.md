---
title: "ALSA 1.0.14rc3 for Feisty snd-intel8x0m"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by erothoff on 2007-04-18
Does anyone have the bin for snd-intel8x0m for the ALSA 1.0.14rc3 or explain better how to compile it? I tried and failed. (I am trying to get sound my my Fujitsu Lifebook B series 2610 and from all that I read, I need this newer driver. (In windows, the chipset is a SigmaTel STAC 9723) Feisty install doesn't find the sound card. I can manually add the snd-intel8x0m and then it is recognized using  aplay -l but it still doesn't work.
  Any help would be appreciated.

---

### Post by drpaul on 2007-04-18
Unless there is something strange about Feisty, there are lots of threads that address this.

The standard procedure is

d/l the source package from the Alsa site
install the kernel headers and things [like C compilers] you need to compile things
unpack the Alsa package; switch to the directory created
./configure
make
sudo make install

then you should modprobe with the module needed by your sound chips

That's about it, I think.

HTH

Paul

---

### Post by erothoff on 2007-04-18
Hi,
  Get this error when doing ./configure

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables

The config.log says:

configure:1684: checking for C compiler default output file name
configure:1687: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:1690: $? = 1


I looked and the problem is that it can not create files in /usr/bin/ld 
/usr/bin/ld is a file and not a directory. 

I don't know enough of gcc to figure out what the problem is. Thanks in advance for the help.

---

### Post by erothoff on 2007-04-19
Well, I got ALSA 1.0.14rc3 to install. (I didn't have all the components necessary to install.) I had to  

sudo apt-get install build-essential

and then I was able to compile. Unfortunately, it did not solve my sound problem. When I get intel-8x0m compiled and installed, it is recognized by aplay -l and I get just a bit of sound, but there is no way to change any settings. The XFCE sound option lets me select it, but I can not change anything.  And alsamixergui has errors when I try to run it. (It is looking for the default sound card. When I change it to card 1 the mixer works, but still no sound.) (But there is just a hint of should, so something is working... I just can't figure out what.

---

