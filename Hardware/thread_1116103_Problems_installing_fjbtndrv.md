---
title: "Problems installing fjbtndrv"
date: 2009-04-04
forum: Hardware
---

### Post by M@s on 2009-04-04
Hi,

I have a Fujitsu-Siemens T4010D running Ubuntu 8.10, and I'm trying to get the tablet buttons and rotation working with fjbtndrv. I can't find an installation guide for it, and the Readme is empty. I got it working before when installing Ubuntu through Windows, but now I'm having a clean netboot installation. I can't remember how I got it working, but I think the procedure is as follows:

1. Download fjbtnrdv ([fjbtndrv_2.0.orig.tar.gz](https://launchpad.net/%7Ekhnz/+archive/ppa/+files/fjbtndrv_2.0.orig.tar.gz)) and unzip.
2. Run ./configure in terminal.
3. make
4. make install

Is this correct? On step 2 I get this error:

```
checking for XRANDR... configure: error: Package requirements (x11 xrandr) were not met:

No package 'x11' found
No package 'xrandr' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XRANDR_CFLAGS
and XRANDR_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Any ideas?

---

### Post by Favux on 2009-04-07
Hi M@s,

Have you considered PMing aussiedwarf.  We know he got it to work.  You could ask him for help.  I doubt he is aware of this thread.

Have you read any read.me's in the unpacked source code tar?  Usually they'll tell you if you need to do anything else.

---

### Post by sirajperson on 2010-04-20
Hey there M@t. Just type the following into the command line. It adds the fjbtndvr ppa repository and installs it.

```
sudo add-apt-repository ppa:khnz; sudo apt-get update; sudo apt-get -y install fjbtndrv
```

Then reboot. This adds auto rotation, and fixes the buttons... At least it did a great job on my Fujitsu t4420

Cheers!

---

### Post by GotDiesel on 2011-02-01
WOW that worked perfectly on my T900.  I've been trying to install the driver for weeks.  I know this post is old but thanks!!

---

### Post by limotux on 2011-03-26
> **sirajperson said:**
> Hey there M@t. Just type the following into the command line. It adds the fjbtndvr ppa repository and installs it.

```
sudo add-apt-repository ppa:khnz; sudo apt-get update; sudo apt-get -y install fjbtndrv
```Then reboot. 
....
Cheers!

I wonder why this is not working anymore?
I am getting the following error:
```
W: Failed to fetch http://ppa.launchpad.net/khnz/ppa/ubuntu/dists/isadora/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fjbtndrv
```Any suggestions?
What about the .deb packages on this link? [https://launchpad.net/~khnz/+archive/ppa/+buildjob/1996623]("https://launchpad.net/%7Ekhnz/+archive/ppa/+buildjob/1996623")

Would they work properly? which to install?
I don't want to take the risk of installing something that might mess up my system as I already have stylus and multitouch working, but no rotate.

Thanks for your help.

---

### Post by GotDiesel on 2011-12-07
I upgraded to 11.04 and I once again can't get the screen buttons and the auto rotate to work on my T900.  Although the above procedure worked with 10.10, I am having no luck with Natty.

---

### Post by Cobuntu on 2012-01-07
The PPA has been updated and I just tried as described in #3 on my T730. All five buttons worked immediately! Ubuntu 11.10.

---

### Post by SonikkuAmerica on 2013-02-08
Unfortunately, the fjbtndrv packages don't work in 12.04 (Precise) or 12.10 (Quantal) (T4220). Has the project been discontinued?

---

### Post by Favux on 2013-02-08
Hi SonikkuAmerica,

Welcome to Ubuntu forums!

> Has the project been discontinued? 
Yes.  Because the kernel maintainers finally accepted Robert Gerlach's fujitsu-tablet.ko into the 3.3 kernel.  But you'd want the one in the 3.4 kernel because Robert did some bug fixes.

You can get that version of fujitsu-tablet.ko as a dkms implementation for Precise or earlier in Magick Rotation.  See the MagickExtras folder:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

Should be working out of the box with Quantal's 3.5 kernel.  You just need a script to rotate would be my guess.  Or Magick Rotation.

---

