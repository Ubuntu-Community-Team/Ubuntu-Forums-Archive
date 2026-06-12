---
title: "Sony Vaio VGN-CR220E Webcam Issue"
date: 2009-11-10
forum: Hardware
---

### Post by Phoxly on 2009-11-10
I have googled all over, and checked every forum I could find, including this one. Yes there are tons of posts about this, but every link to all the drivers are broken. So I guess I'll create a new thread and get some fresh responses. 

I have a Sony Vaio VGN-CR220E with a built in webcam, when I partitioned my drive and installed Ubuntu 9.04 (now 9.10) the webcam has not worked.

I "lsusb'd" and got:

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:1839 Ricoh Co., Ltd Visual Communication Camera VGP-VCC6 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c024 Logitech, Inc. MX300 Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by rmp73 on 2009-11-12
Just to say I have the same problem.  Think there's currently no driver that's working under Ubuntu 9.10 Karmic from what I see.

My lsusb line reads:
Bus 001 Device 002: ID 05ca:1837 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]

Running on a Sony Vaio VGN-FZ11Z

Sincerely hope someone fixes this before too long, as I'm loathe to buy an external webcam when one's built in!

---

### Post by rrstelling on 2009-12-04
I got my Vaio cam working on Ubuntu 9.10, by building the kernel module from source. Not as hard as it sounds.
```

lsusb output:
Bus 001 Device 003: ID 05ca:1836 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]
```
[LIST=1]
[*]Install the packages required to build the module (I may have missed some):
[LIST]
[*]sudo apt-get install build-essential linux-headers-`uname -r`
[/LIST]
 
[*]Download and unzip the latest, although now unsupported, version of the r5u870 module.
[LIST]
[*]_[wget http://www.palmix.org/download/r5u870_k2.6.30_i386.tar.bz2]("http://www.palmix.org/download/r5u870_k2.6.30_i386.tar.bz2")_
[*]tar -xvf r5u870_k2.6.30_i386.tar.bz2
[*]cd ./r5u870
[/LIST]
 
[*]Build and install the module.
[LIST]
[*]make
[*]sudo make install
[*]sudo modprobe 5u870
[/LIST]
 
[/LIST]
Afterwards my webcam appeared as /dev/video0 and works as a v4l device. I've tested it with skype, VLC and motion.

---

### Post by Charles07 on 2011-01-07
Below is a link with the pertinent quote below that.  Worked like a charm.

[http://ubuntuforums.org/showthread.php?p=8930938](http://ubuntuforums.org/showthread.php?p=8930938)

> **JanHJT said:**
> To try this driver open a terminal and type

$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
$ hg clone [https://bitbucket.org/ahixon/r5u87x/]("http://bitbucket.org/ahixon/r5u87x/")      *[I changed the link to reflect SSL]
$ cd r5u87x
$ make
$ sudo make install
$ sudo r5u87x-loader --reload
    
The loader will automatically be run on boot when it detects your webcam.

My Logfile:```
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [    33.628213] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183a)
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640293] uvcvideo:  UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640543] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640603] uvcvideo: Failed to initialize the device (-5).
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640768] usbcore: registered new interface driver uvcvideo
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.641451] USB Video Class driver (v0.1.0)
```related bugfile: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460290](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460290)

* Sorry for editing the quote, it was necessary - Charles07

[ETA: Oh, and install both "webcam" and "cheese" {I did it under terminal with "sudo apt-get install XXX", XXX being the aforementioned packages}.  Cheese will then be found under "sound and video".]

---

### Post by Charles07 on 2011-01-07
Oh, and for anyone searching for this under a fresh install of Linux Mint 10/LinuxMint 10:

The line "hg clone [https://bitbucket.org/ahixon/r5u87x/]("http://bitbucket.org/ahixon/r5u87x/")" may be omitted.

The driver came installed.  Just follow the rest of the steps above to make the loader.

---

### Post by Fictitious1 on 2011-07-21
$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
$ hg clone [https://bitbucket.org/ahixon/r5u87x/]("http://bitbucket.org/ahixon/r5u87x/")      *[I changed the link to reflect SSL]
$ cd r5u87x
$ make
$ sudo make install
$ sudo r5u87x-loader --reload



HEY! Thanks - This worked perfectly on a Japanese Version Sony VGN-FE53B - Cheese first showed a black and white pic type only but camorama showed up fine.

---

### Post by dr_anirudh_shukla on 2011-10-02
> **Fictitious1 said:**
> $ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
$ hg clone [https://bitbucket.org/ahixon/r5u87x/]("http://bitbucket.org/ahixon/r5u87x/")      *[I changed the link to reflect SSL]
$ cd r5u87x
$ make
$ sudo make install
$ sudo r5u87x-loader --reload



HEY! Thanks - This worked perfectly on a Japanese Version Sony VGN-FE53B - Cheese first showed a black and white pic type only but camorama showed up fine.

Followed the instructions above and now my web-cam is working fine. Thanks everyone.

---

### Post by 00sanjeev on 2011-11-12
> **Fictitious1 said:**
> $ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
$ hg clone [https://bitbucket.org/ahixon/r5u87x/]("http://bitbucket.org/ahixon/r5u87x/")      *[I changed the link to reflect SSL]
$ cd r5u87x
$ make
$ sudo make install
$ sudo r5u87x-loader --reload



HEY! Thanks - This worked perfectly on a Japanese Version Sony VGN-FE53B - Cheese first showed a black and white pic type only but camorama showed up fine.


Worked for my VGN CR353
thanks a ton:KS

---

### Post by Anyone1982 on 2013-02-18
> **Fictitious1 said:**
> $ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
$ hg clone [https://bitbucket.org/ahixon/r5u87x/]("http://bitbucket.org/ahixon/r5u87x/")      *[I changed the link to reflect SSL]
$ cd r5u87x
$ make
$ sudo make install
$ sudo r5u87x-loader --reload



HEY! Thanks - This worked perfectly on a Japanese Version Sony VGN-FE53B - Cheese first showed a black and white pic type only but camorama showed up fine.


Worked for my vgn-tz290. Many thanks!

---

### Post by Dr._Daniel_James_White on 2013-08-31
i have a sony vaio vgn-fz19vn
lsusb gives
Bus 001 Device 002: ID 05ca:1837 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]
so its the same camera
so i installed this driver as above, but i gen in upside down image in camorama, and a black image in skype and cheese...
any clues? I can provide further diagnostic output... Best, D

---

