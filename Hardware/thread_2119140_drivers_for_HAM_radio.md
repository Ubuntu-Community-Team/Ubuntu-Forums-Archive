---
title: "drivers for HAM radio"
date: 2013-02-23
forum: Hardware
---

### Post by wc5b on 2013-02-23
I am having a bit of an issue trying to get a radio interface installed correctly. Manufacture claims its been tested a ok on Ubuntu and other owners of interface claim its practically plug and play. (Running Linux Mint 14)

First let me explain the device. Its used for Ham Radio and has a built in sound card and and it allows the program to actually key the radio and then send audio into the radio. So there is two pieces to the puzzle. There is an audio side and what amounts to a USB to Serial side. The main issue I am having is the drivers do not seem to want to install. Manufacture drivers include a batch install.sh file for ubuntu but it appears to fail. When I try to compile, this is what I get:

```

tar -zxvf RIGblasterDrivers-20110524.tar.gz
cp210x.c
install.sh
Makefile
readme.txt
wc5b@wc5b-mint ~/Downloads $ gedit readme.txt
wc5b@wc5b-mint ~/Downloads $ make
make -C /lib/modules/3.5.0-17-generic/build SUBDIRS=/home/wc5b/Downloads modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
  CC [M]  /home/wc5b/Downloads/cp210x.o
/home/wc5b/Downloads/cp210x.c:147:12: error: &#8216;usb_serial_probe&#8217; undeclared here (not in a function)
/home/wc5b/Downloads/cp210x.c:148:16: error: &#8216;usb_serial_disconnect&#8217; undeclared here (not in a function)
/home/wc5b/Downloads/cp210x.c:165:2: warning: initialization from incompatible pointer type [enabled by default]
/home/wc5b/Downloads/cp210x.c:165:2: warning: (near initialization for &#8216;cp210x_device.tiocmget&#8217;) [enabled by default]
/home/wc5b/Downloads/cp210x.c:166:2: warning: initialization from incompatible pointer type [enabled by default]
/home/wc5b/Downloads/cp210x.c:166:2: warning: (near initialization for &#8216;cp210x_device.tiocmset&#8217;) [enabled by default]
/home/wc5b/Downloads/cp210x.c: In function &#8216;cp210x_init&#8217;:
/home/wc5b/Downloads/cp210x.c:840:2: error: implicit declaration of function &#8216;usb_serial_register&#8217; [-Werror=implicit-function-declaration]
/home/wc5b/Downloads/cp210x.c:847:3: error: implicit declaration of function &#8216;usb_serial_deregister&#8217; [-Werror=implicit-function-declaration]
/home/wc5b/Downloads/cp210x.c: In function &#8216;__check_debug&#8217;:
/home/wc5b/Downloads/cp210x.c:870:1: warning: return from incompatible pointer type [enabled by default]
cc1: some warnings being treated as errors
make[2]: *** [/home/wc5b/Downloads/cp210x.o] Error 1
make[1]: *** [_module_/home/wc5b/Downloads] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [default] Error 2
wc5b@wc5b-mint ~/Downloads $ 



```Once installed I should be getting a /dev/ttyUSB0 which I can then hypothetically find in a drop down serial tab of my program I am attempting to use, a well established program called fldigi.

**Readme with drivers:**

To use the RIGblaster Advantage's rig control interface, you will need to
build a custom driver.  We have provided a simple script which will
execute on Ubuntu.  Otherwise you can manually invoke the Makefile.


For Ubuntu:
1) Double click the install.sh script and run it.  You will see some
   files get generated and disappear.
2) You should now have a /dev/ttyUSB0 device.  This will be the serial
   device you'll use with HAM software.

The audio portion is usable out of the box.  No drivers should need to be modified
or loaded manually.


For Other Distributions:
1) Install gcc, make and kernel headers for the currently running kernel.
   Consult your distributions documentation on how to do this.
2) Open a terminal and change directory to where you extracted the files.
3) Type the following to build and install the driver:

    $ make
    $ sudo make install

4) You should now have a /dev/ttyUSB0 device.  This will be the serial
   device you'll use with HAM software.

The audio portion of the device uses the snd_usb_audio driver as provided
by ALSA.  This may need to be installed and loaded before the RIGblaster
can be used as an audio device.

________
So that is problem one. Problem two is the audio side of it. Manufacture claims that audio should work out of the box Plug and Play. As stated above, it has its own built in sound card. When using the program I go to PortAudio Audio settings and the device in question does very well show up. However, it does not appear to be receiving a signal. Easiest way to explain it is I can see a graphical representation of audio and their is none. If I go to PulseAudio I can see a signal, but that is only because its receiving it through my microphone near the radio itselfs external speaker via my PC's audio card.

If any hams are reading it and know exactly what I am working with, it is a Rigblaster Advantage.

Any hints on this one too would be a great help. Thank in advance.

---

### Post by BicyclerBoy on 2013-02-23
Are you sure that USB serial adapter is not just a FTDI or Parallax device..
Both have kernel support.
The adapter on West Mountain Radio site looks like a generic Parallax device..

Plug it in & then check in terminal:
dmesg

any USB device activity?

---

### Post by wc5b on 2013-02-23
Forgive me, as I am a novice for the most part with Linux. Hopefully not for long. I get a LONG and quick waterfall of this over and over:

```

[ 7720.734856] usb 5-2.2: >Not enough bandwidth for altsetting 1
[ 7720.734857] 4:1:1: usb_set_interface failed (-22)
[ 7720.735195] xhci_hcd 0000:06:00.0: >ERROR: unexpected command completion code 0x11.

and then

[ 7957.205551] type=1701 audit(1361613755.852:167): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=26648 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8304936b0 code=0x50000

```

---

### Post by BicyclerBoy on 2013-02-23
Maybe it does need a alt driver..or the old simpler driver..

Plug the device into a USB2.0 directly on the computer..no hubs etc.
In a terminal:
lsusb


Back to your source code..
Un-tarball the source into its own folder anywhere in your home folder..

Are you meant to run ./autogen.sh or ./configure before make or just use ./install.sh ?

Do you have "linux-headers-generic" package installed?
sudo apt-get -install linux-headers-generic

---

### Post by wc5b on 2013-02-23
It did seem to install some packages with generic headers. They may have just been updates. I am still getting lots of errors when I try it again. I also tried ./configure and ./autogen.sh. It did not like either one. I also get same results running make.

```
wc5b@wc5b-mint ~/Downloads $ ./install.sh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libasprintf0c2:i386 libgomp1:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
make -C /lib/modules/3.5.0-17-generic/build SUBDIRS=/home/wc5b/Downloads modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
  CC [M]  /home/wc5b/Downloads/cp210x.o
/home/wc5b/Downloads/cp210x.c:147:12: error: ‘usb_serial_probe’ undeclared here (not in a function)
/home/wc5b/Downloads/cp210x.c:148:16: error: ‘usb_serial_disconnect’ undeclared here (not in a function)
/home/wc5b/Downloads/cp210x.c:165:2: warning: initialization from incompatible pointer type [enabled by default]
/home/wc5b/Downloads/cp210x.c:165:2: warning: (near initialization for ‘cp210x_device.tiocmget’) [enabled by default]
/home/wc5b/Downloads/cp210x.c:166:2: warning: initialization from incompatible pointer type [enabled by default]
/home/wc5b/Downloads/cp210x.c:166:2: warning: (near initialization for ‘cp210x_device.tiocmset’) [enabled by default]
/home/wc5b/Downloads/cp210x.c: In function ‘cp210x_init’:
/home/wc5b/Downloads/cp210x.c:840:2: error: implicit declaration of function ‘usb_serial_register’ [-Werror=implicit-function-declaration]
/home/wc5b/Downloads/cp210x.c:847:3: error: implicit declaration of function ‘usb_serial_deregister’ [-Werror=implicit-function-declaration]
/home/wc5b/Downloads/cp210x.c: In function ‘__check_debug’:
/home/wc5b/Downloads/cp210x.c:870:1: warning: return from incompatible pointer type [enabled by default]
cc1: some warnings being treated as errors
make[2]: *** [/home/wc5b/Downloads/cp210x.o] Error 1
make[1]: *** [_module_/home/wc5b/Downloads] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [default] Error 2
cp cp210x.ko /lib/modules/3.5.0-17-generic/kernel/drivers/usb/serial/
make -C /lib/modules/3.5.0-17-generic/build SUBDIRS=/home/wc5b/Downloads clean
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
  CLEAN   /home/wc5b/Downloads/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'

```

---

### Post by d_in_Conduct on 2013-02-23
I don't use RIGBlaster but I do use a USB-serial adapter to send commands to my radio.  Every time I reboot I have to change permissions on /dev/ttyUSB0, so that might be your problem also.  (sudo chown [you]:[you] /dev/ttyUSB0)

I don't have to worry about sound on my system but sound can be tricky with virtual soundcards like you're dealing with.  Check whatever mixer(s) you have in your system and make sure the soundcard is detected there and the volumn is up.  Look for more than one mixer.

Good luck with it.

---

### Post by wc5b on 2013-02-24
Ya, I can understand that. I can't even get that far. It should be making the /dev/ttyUSB* folder but it errors out before it gets that far.

---

### Post by wc5b on 2013-03-03
Still looking on help with this one.

---

