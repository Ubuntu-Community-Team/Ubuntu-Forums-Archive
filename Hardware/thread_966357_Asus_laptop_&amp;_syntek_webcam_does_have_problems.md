---
title: "Asus laptop &amp; syntek webcam does have problems under intrepid ibex 8.04"
date: 2008-11-01
forum: Hardware
---

### Post by kelenpe on 2008-11-01
Hi everyone,

Well, here is a description of my problem:

I have a laptop Asus F3jv with a built-in web-cam based on the syntek chipset. Yesterday I have updated my Ubuntu system from hardy_8.04 (kernel 2.6.20) to intrepid_8.10 (kernel 2.6.27).

In the previous version (hardy_8.04 (kernel 2.6.20)), I have compiled and installed the module supporting my web-cam which worked with every software (not flawlessly though, the picture was darker than under windows, but it worked).
Now (intrepid_8.10 (kernel 2.6.27)), the webcam works with every software except of camorama "Could not connect to video device /dev/video0". The web-cam works but I still have two issues which make it not usable.

1. The picture quality is very (too) bright:
When the web-cam is activated the brightness increases automatically, until reaching the maximum level, which make the picture very bad (noticed with ekiga, skype and cheese).

2. A power management issue:
When I close a software using the web-cam, the LED indicating the activity  of the web-cam remains on (I am afraid of an overheat). Even when I unload the implied module (modprobe -r stkwebcam) I do still have this issue.

I have googled about this module, and it seems that the gnu/linux kernel 2.6.27 included with intrepid has the module stkwebcam which was not working in the alpha release of intrepid with a kernel in rc6 state. [Link]("https://bugs.launchpad.net/ubuntu/ source/linux/ bug/269123")
It is embarrassing to have regressions between versions like that. Though, generally  I have a better support of my hardware with this new kernel. But I really need my webcam to work.

So If anyone has the same issue or a workaround thanks to let me know.
Thank you for your answers!

---

### Post by seeebek on 2008-11-01
Hi kelenpe,
I have just the same issue. I tried to instal the stk11xx module, but it did not compile:

make[2]: *** Keine Regel vorhanden, um das Target »kernel/bounds.c«,
  benötigt von »kernel/bounds.s«, zu erstellen.  Schluss.
make[1]: *** [prepare0] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.27-7-generic'
make: *** [driver] Fehler 2

I tried with the kernel source, but it didn't help. I would be also happy to know if there is any walkaround or a way to compile the stk11xx driver. The stkwebcam sucks... 
My kernel: 2.6.27-7.15

---

### Post by kelenpe on 2008-11-02
Hi seeebek,

I have managed to compile and use the stk11xx module for the kernel 2.6.27,
Use the svn source code!

I checked out the code with this command :
```
$ svn co https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver
```
Then look the README file for the compilation and so on...

it works for me. but the quality of the picture is really dark, I do not succeed to make it brighter even with the loading of the module with its options.

Any workarounds about the stkwebcam module?
Or how to set correctly the brightness of the stk11xx?

Thank you!

---

### Post by sgleo87 on 2008-11-02
How did you guys get the webcam to work??? I followed various how to's including the README for the compilation but I cannot seem to get it to work. The drivers install fine and seem to be running (I get insmod: error inserting '/home/sandra/.syntekdriver/trunk/driver/stk11xx.ko': -1 File exists when running sudo insmod stk11xx.ko) but Skype, Camorama, and Cheese all do not find the webcam! It used to work just fine in Hardy....please help!

---

### Post by kelenpe on 2008-11-02
Hi sgleo87.

first, Try to remove stkwebcam.

```
sudo modprobe -r stkwebcam
```

Go in the root directory of the driver, containing the compiled module
Then, load videodev
```
sudo modprobe videodev
```
and insert the stk11xx.ko module
```
sudo insmod stk11xx.ko
```

It works for me, but with this driver the picture is too dark... and so far, I did not find any ways to make it better even with the module options

btw about the stkwebcam module, for my first issue mentioned in the first post, I talked about the automatic increasing of the brightness until the max level, which make the picture really bad.
I gave another try today, and the increasing did not reach the maximum, at least it was not as strong as the first time. The only difference was that I have tried it in a lighter environment. Conclusion, I think that my first issue which is not really one any more is related to an auto exposure feature which adjust the brightness according to the environment. Well, an unknown feature, probably brought with the stkwebcam module. So far I would like to know if I am right and if I am, how to activate/deactivate or adjust this feature.

I still have a problem with the power management with stkwebcam, the webcam does not want to turn off.

Some Ideas ?
thx

---

### Post by ironpingwin on 2008-11-02
Hi!

I found nice tutorial - installation of stk11xx driver from svn: [http://doc.ubuntu-fr.org/syntek]("http://doc.ubuntu-fr.org/syntek")

**kelenpe**: there is explanation how to change brightness, maybe it would be helpful for you.

After installation, my web cam works in xawtv (xawtv -nodga), but it doesn't in Cheese or Skype. Cheese doesn't find any web cam, Skype does, but test screen is green while I am testing it. It's strange, web cam worked in hardy, and now (Intrepid) it works only with xawtv. Any ideas why?

---

### Post by Ev1L on 2008-11-02
> **kelenpe said:**
> 
Or how to set correctly the brightness of the stk11xx?

Thank you!

In hardy i had these settings that helped a bit with the darkness on skype (not good but acceptable).

options stk11xx brightness=0xBFFF
options stk11xx contrast=0xFFFF
#options stk11xx whitebalance=0xFFFF
options stk11xx colour=0xBFFF

I noticed the better support with Intrepid but i have an acceptable quality out of the box without any tweak, but the always on cam is annoying.

If some driver developer could fix it, we all would appreciate :p

---

### Post by kelenpe on 2008-11-02
Thx ironpingwin and Ev1l,

I have already been through the French documentation (by the way I posted the same topic in the French forum, but there is no answers...) the tutorial is very good but does not resolve my problem with stkwebcam.

The fact is that with stk11xx.ko I can adjust the brightness loading the module, but still it is not to dark.

ex :
```
$ sudo insmod stk11xx.ko vflip=1 brightness=0xBBBB
```

Actually I would like to do it with the stkwebcam as well(brought with intrepid 8.10), the parameters does not comply with stkwebcam (except of hflip/vflip). Is there a command to know the options we can used with a module ?

I would prefer to make it works with stkwebcam because:
Under hardy 8.04 I had no problems with stk11xx (worked with every softwares), but now under Intrepid 8.10 stk11xx works "only" with camorama.
and stkwebcam works with cheese and skype (Actually The one I need), but not camorama...:confused:

Conclusion, I must use the stkwebcam module. But I still have a power management issue and the brightness I would like to adjust (but as Ev1l I would say that I notice a better support for of the brightness).

Thx for your help

---

### Post by Ev1L on 2008-11-02
you could start trying v4l-info, maybe from there you can guess the parameters.
v4l-conf could do something too.
i remember in hardy i found something with the parameter list, but i forgot if i found it online or inside a file somewhere.

i am more interested in turning off the cam though, but i'll let you know if something works

---

### Post by Ev1L on 2008-11-02
take also a look into /etc/acpi, i am pretty sure i found clues inside there with the old release.
it was relate to v4l probably

---

### Post by kelenpe on 2008-11-02
Hi Ev1l and thx,

I will try to have a look in v4l. 
To turn off the webcam I have something but it is not clean.

I remove stkwebcam, and load the compiled stk11xx from the source svn ([http://syntekdriver.sourceforge.net/](http://syntekdriver.sourceforge.net/))

```

sudo modprobe -r stkwebcam &&
cd ~/.syntek/driver &&
sudo modprobe videodev &&
sudo insmod stk11xx.ko

```
It is awful but it is a temporary workaround for shutting off the webcam.

I come back tomorrow to see if I can figure out the paramaters/options following your advices.

Good night

---

### Post by seeebek on 2008-11-03
Hi guys,
I solved my problem. The file "bounds.h" was really missing. I reinstalled all "linux-headers-*" packages from synaptic and then I could compile the driver. 
Now I realized that I can access the webcam only if I start camorama or xawtv or anything else as root (sudo). If I try to do it as normal user, it is showing "could not open /dev/video0" or "permission deined". Beside that when I try to use it with Skype (unfortunatelly also only sudo) I see only green screen. 
Did anybody get it to work?

Little tip @kelenpe. I am always able to make the output brighter if I put whitebalance higher.

---

### Post by polig4e on 2008-11-04
Same problem here on ASUS F5V.

I can't compile syntek driver 1.3.1 because of bound.c problem.

I do managed to compile the SVN driver, but the driver is not working. I type

sudo modprobe videodev
sudo insmod stk11xx.ko

the camers flashes for a moment, but not working... 

anyone knows a solution? thank you!!

---

### Post by sgleo87 on 2008-11-04
> **kelenpe said:**
> Hi sgleo87.

first, Try to remove stkwebcam.

```
sudo modprobe -r stkwebcam
```

Go in the root directory of the driver, containing the compiled module
Then, load videodev
```
sudo modprobe videodev
```
and insert the stk11xx.ko module
```
sudo insmod stk11xx.ko
```


I get the following output:
```
sandra@sandra-laptop:~$ sudo modprobe -r stkwebcam
sandra@sandra-laptop:~$ cd ./.syntekdriver/trunk/driver/
sandra@sandra-laptop:~/.syntekdriver/trunk/driver$ sudo insmod stk11xx.ko
insmod: error inserting 'stk11xx.ko': -1 File exists
```

So same as before...and it is still not working with Skype...any ideas?

BTW when I go under System > Administration > Hardware Drivers the Syntek USB Video Camera drivers show up as active.

---

### Post by jonlowe on 2008-11-06
I have the same problems as everyone else.  Camera worked fine on my F3SV under 8.04, but doesn't under 8.10.  When I try to compile the dirver, I get:

jonlowe@ubuntu:~/syntek/driver$ make -f Makefile.standalone clean
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/jonlowe/syntek/driver clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CLEAN   /home/jonlowe/syntek/driver/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
jonlowe@ubuntu:~/syntek/driver$ make -f Makefile.standalone
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/jonlowe/syntek/driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/jonlowe/syntek/driver/stk11xx-usb.o
  CC [M]  /home/jonlowe/syntek/driver/stk11xx-v4l.o
/home/jonlowe/syntek/driver/stk11xx-v4l.c:1727: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
make[2]: *** [/home/jonlowe/syntek/driver/stk11xx-v4l.o] Error 1
make[1]: *** [_module_/home/jonlowe/syntek/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [driver] Error 2
jonlowe@ubuntu:~/syntek/driver$ 

Any ideas as to what is wrong?

Jon

---

### Post by seeebek on 2008-11-10
Hi guys,
I found my solution!
For everybody who get the camorama error like "cannot open /dev/video0" you should try to do:
```
$ useradd -G video username
```
I realized that intrepid isn't putting new user into "video" group, which camorama or skype are using. Now I can open camorama, xawtv and skype without almost any problem. Almost because: Kopete is still not seeing my webcam, and Skype is showing sometimes just a green screen.
List of all things I done:
1. Missing bound.c: Reinstalled linux-headers*
2. Compiling stk11xx from svn to prevent errors with the 2.6.27 kernel
3. Added myself to "video" group.
If somebody finds a solution for my Kopete and Skype problem, please drop me a line or answer here.

---

### Post by sgleo87 on 2008-11-10
> **seeebek said:**
> Hi guys,
I found my solution!
For everybody who get the camorama error like "cannot open /dev/video0" you should try to do:
```
$ useradd -G video username
```
I realized that intrepid isn't putting new user into "video" group, which camorama or skype are using. Now I can open camorama, xawtv and skype without almost any problem. Almost because: Kopete is still not seeing my webcam, and Skype is showing sometimes just a green screen.
List of all things I done:
1. Missing bound.c: Reinstalled linux-headers*
2. Compiling stk11xx from svn to prevent errors with the 2.6.27 kernel
3. Added myself to "video" group.
If somebody finds a solution for my Kopete and Skype problem, please drop me a line or answer here.

For that command I just get 
```
sandra@sandra-laptop:~$ useradd -G video sandra
useradd: user sandra exists

```
So it seems that is already taken care off. Under Administration>Hardware it shows that the drivers are running but Skype still does not recognized my webcam...help!

---

### Post by dentog on 2008-11-14
[QUOTE=seebek]1. Missing bound.c: Reinstalled linux-headers*
2. Compiling stk11xx from svn to prevent errors with the 2.6.27 kernel
3. Added myself to "video" group.[/QUOTE]

I'm noob in linux, can you please describe me more what should I do?

Tnx

---

### Post by berot3 on 2008-11-16
ok, so u i really tried everthing from the posts above. And i also have the problem that my syntek-webcam in my ASUS-V1S worked under hardy and now no more. :(
i dont understand how it is possible that something dont work in a newer version...
i also compiled from svn and deleted stkwebcam, which didint work

so i installed v4l-info, and how i understand this output it should work :confused: even the light from my webcam blinks 1 time, when executing v4l-info, like in hardy while it was booting
```

$ sudo v4l-info 

### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
	driver                  : "stk11xx"
	card                    : "Syntek USB Video Camera"
	bus_info                : "usb-0000:00:1a.7-3"
	version                 : 1.3.1
	capabilities            : 0x5000001 [VIDEO_CAPTURE,READWRITE,STREAMING]

standards
    VIDIOC_ENUMSTD(0)
	index                   : 0
	id                      : 0x0 []
	name                    : "webcam"
	frameperiod.numerator   : 0
	frameperiod.denominator : 0
	framelines              : 0

inputs
    VIDIOC_ENUMINPUT(0)
	index                   : 0
	name                    : "USB"
	type                    : CAMERA
	audioset                : 0
	tuner                   : 0
	std                     : 0x0 []
	status                  : 0x0 []

video capture
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
	index                   : 0
	type                    : VIDEO_CAPTURE
	flags                   : 0
	description             : "rgb24"
	pixelformat             : 0x33424752 [RGB3]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
	type                    : VIDEO_CAPTURE
	fmt.pix.width           : 640
	fmt.pix.height          : 480
	fmt.pix.pixelformat     : 0x33524742 [BGR3]
	fmt.pix.field           : NONE
	fmt.pix.bytesperline    : 1920
	fmt.pix.sizeimage       : 921600
	fmt.pix.colorspace      : SRGB
	fmt.pix.priv            : 0

controls
    VIDIOC_QUERYCTRL(BASE+0)
	id                      : 9963776
	type                    : INTEGER
	name                    : "Brightness"
	minimum                 : 0
	maximum                 : 65280
	step                    : 1
	default_value           : 32512
	flags                   : 0
    VIDIOC_QUERYCTRL(BASE+1)
	id                      : 9963777
	type                    : INTEGER
	name                    : "Contrast"
	minimum                 : 0
	maximum                 : 65280
	step                    : 1
	default_value           : 32512
	flags                   : 0
    VIDIOC_QUERYCTRL(BASE+2)
	id                      : 9963778
	type                    : INTEGER
	name                    : "Saturation"
	minimum                 : 0
	maximum                 : 65280
	step                    : 1
	default_value           : 32512
	flags                   : 0

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
	name                    : "stk11xx"
	type                    : 0x1 [CAPTURE]
	channels                : 1
	audios                  : 0
	maxwidth                : 640
	maxheight               : 480
	minwidth                : 80
	minheight               : 60

channels
    VIDIOCGCHAN(0)
	channel                 : 0
	name                    : "Webcam"
	tuners                  : 0
	flags                   : 0x0 []
	type                    : CAMERA
	norm                    : 0

tuner
ioctl VIDIOCGTUNER: Unknown error 515

audio
ioctl VIDIOCGAUDIO: Invalid argument

picture
    VIDIOCGPICT
	brightness              : 32767
	hue                     : 65535
	colour                  : 32767
	contrast                : 32767
	whiteness               : 32767
	depth                   : 24
	palette                 : RGB24

buffer
    VIDIOCGFBUF
	base                    : (nil)
	height                  : 0
	width                   : 0
	depth                   : 0
	bytesperline            : 0

window
    VIDIOCGWIN
	x                       : 0
	y                       : 0
	width                   : 640
	height                  : 480
	chromakey               : 0
	flags                   : 0

```

but still when i start camorama or any other app it says 
"could not connect to device /dev/video0"

---

### Post by noobi_agocs on 2008-11-16
Hello there!

Ive just finished installing the syntek driver as I read from this website: [http://doc.ubuntu-fr.org/syntek](http://doc.ubuntu-fr.org/syntek)

I followed every step, and its working. However only skype recognizes the webcam (thats the only one I need). As I said, only skype recognizes the camera (cheese, kopete did not, and i dont no if pidgin or other messengers would recognize it, i didnt checked it).

Peace!

---

### Post by noobi_agocs on 2008-11-16
Ive forgotten my laptops parameters:
Intel Duo T5250, ATI Radeon X2300, 2GB ram, 160 HDD

---

### Post by sgleo87 on 2008-11-16
> **noobi_agocs said:**
> Hello there!

Ive just finished installing the syntek driver as I read from this website: [http://doc.ubuntu-fr.org/syntek](http://doc.ubuntu-fr.org/syntek)

I followed every step, and its working. However only skype recognizes the webcam (thats the only one I need). As I said, only skype recognizes the camera (cheese, kopete did not, and i dont no if pidgin or other messengers would recognize it, i didnt checked it).

Peace!

I followed that guide but I still have the same probelm as before: installation runs fine but the webcam does not work. I get the following error from dmesg: [   51.308575] stk11xx: Check device return error (0x0201 = 0C) !. Here is my entire output from the installation:```
sandra@sandra-laptop:~$ sudo update-usbids
--2008-11-16 12:39:01--  http://linux-usb.sourceforge.net/usb.ids
Resolving linux-usb.sourceforge.net... 216.34.181.96
Connecting to linux-usb.sourceforge.net|216.34.181.96|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357258 (349K) [text/plain]
Saving to: `/var/lib/misc/usb.ids.new'

100%[======================================>] 357,258      473K/s   in 0.7s    

2008-11-16 12:39:02 (473 KB/s) - `/var/lib/misc/usb.ids.new' saved [357258/357258]

Done.
sandra@sandra-laptop:~$ lsusb
Bus 002 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 005: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 007 Device 004: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 007 Device 003: ID 0424:2507 Standard Microsystems Corp. 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
Bus 004 Device 003: ID 046d:c221 Logitech, Inc. G15 Keyboard / Keyboard
Bus 004 Device 002: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
sandra@sandra-laptop:~$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-8-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sandra@sandra-laptop:~$ sudo apt-get install build-essential subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
subversion is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sandra@sandra-laptop:~$ cd ./Desktop/
sandra@sandra-laptop:~/Desktop$ tar -xzvf stk11xx-1.3.1.tar.gz 
stk11xx-1.3.1/
stk11xx-1.3.1/stk11xx.txt
stk11xx-1.3.1/Makefile
stk11xx-1.3.1/Kbuild
stk11xx-1.3.1/README
stk11xx-1.3.1/Makefile.standalone
stk11xx-1.3.1/stk11xx.h
stk11xx-1.3.1/doxygen.cfg
stk11xx-1.3.1/stk11xx-buf.c
stk11xx-1.3.1/stk11xx-dev.c
stk11xx-1.3.1/stk11xx-dev.h
stk11xx-1.3.1/Kconfig
stk11xx-1.3.1/stk11xx-v4l.c
stk11xx-1.3.1/stk11xx-usb.c
stk11xx-1.3.1/stk11xx-dev-6a31.c
stk11xx-1.3.1/stk11xx-dev-6a33.c
stk11xx-1.3.1/stk11xx-dev-6a51.c
stk11xx-1.3.1/stk11xx-dev-6a54.c
stk11xx-1.3.1/stk11xx-sysfs.c
stk11xx-1.3.1/stk11xx-bayer.c
stk11xx-1.3.1/stk11xx-dev-a311.c
stk11xx-1.3.1/stk11xx-dev-a821.c
sandra@sandra-laptop:~/Desktop$ mkdir syntek
sandra@sandra-laptop:~/Desktop$ cd syntek/
sandra@sandra-laptop:~/Desktop/syntek$ svn co https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver
A    driver/Kconfig
A    driver/stk11xx-dev.c
A    driver/stk11xx-dev-a311.c
A    driver/stk11xx-dev.h
A    driver/stk11xx-dev-6a31.c
A    driver/stk11xx-dev-a821.c
A    driver/stk11xx-dev-6a33.c
A    driver/stk11xx-dev-6a51.c
A    driver/stk11xx-usb.c
A    driver/README
A    driver/stk11xx-dev-6a54.c
A    driver/stk11xx-dev-6d51.c
A    driver/stk11xx.txt
A    driver/Makefile.standalone
A    driver/stk11xx-bayer.c
A    driver/stk11xx-v4l.c
A    driver/stk11xx-sysfs.c
A    driver/stk11xx.h
A    driver/Kbuild
A    driver/doxygen.cfg
A    driver/Makefile
A    driver/stk11xx-buf.c
Checked out revision 81.
sandra@sandra-laptop:~/Desktop/syntek$ cd driver/
sandra@sandra-laptop:~/Desktop/syntek/driver$ wget http://bookeldor-net.info/merdier/Makefile-syntekdriver
--2008-11-16 12:44:40--  http://bookeldor-net.info/merdier/Makefile-syntekdriver
Resolving bookeldor-net.info... 213.186.33.48
Connecting to bookeldor-net.info|213.186.33.48|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 967 [text/plain]
Saving to: `Makefile-syntekdriver'

100%[======================================>] 967         --.-K/s   in 0s      

2008-11-16 12:44:40 (38.3 MB/s) - `Makefile-syntekdriver' saved [967/967]

sandra@sandra-laptop:~/Desktop/syntek/driver$ make -f Makefile-syntekdriver
make -C /lib/modules/2.6.27-8-generic/build SUBDIRS=/home/sandra/Desktop/syntek/driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-8-generic'
  CC [M]  /home/sandra/Desktop/syntek/driver/stk11xx-usb.o
  CC [M]  /home/sandra/Desktop/syntek/driver/stk11xx-v4l.o
  CC [M]  /home/sandra/Desktop/syntek/driver/stk11xx-sysfs.o
  CC [M]  /home/sandra/Desktop/syntek/driver/stk11xx-dev.o
  CC [M]  /home/sandra/Desktop/syntek/driver/stk11xx-buf.o
  CC [M]  /home/sandra/Desktop/syntek/driver/stk11xx-bayer.o
  CC [M]  /home/sandra/Desktop/syntek/driver/stk11xx-dev-a311.o
  CC [M]  /home/sandra/Desktop/syntek/driver/stk11xx-dev-a821.o
  CC [M]  /home/sandra/Desktop/syntek/driver/stk11xx-dev-6a31.o
  CC [M]  /home/sandra/Desktop/syntek/driver/stk11xx-dev-6a33.o
  CC [M]  /home/sandra/Desktop/syntek/driver/stk11xx-dev-6a51.o
  CC [M]  /home/sandra/Desktop/syntek/driver/stk11xx-dev-6a54.o
  CC [M]  /home/sandra/Desktop/syntek/driver/stk11xx-dev-6d51.o
  LD [M]  /home/sandra/Desktop/syntek/driver/stk11xx.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/sandra/Desktop/syntek/driver/stk11xx.mod.o
  LD [M]  /home/sandra/Desktop/syntek/driver/stk11xx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-8-generic'
sandra@sandra-laptop:~/Desktop/syntek/driver$ sudo make -f Makefile-syntekdriver install
mkdir -p /lib/modules/2.6.27-8-generic/kernel/drivers/usb/media
install -m 644 -o 0 -g 0 stk11xx.ko /lib/modules/2.6.27-8-generic/kernel/drivers/usb/media
depmod -a
sandra@sandra-laptop:~$ sudo modprobe stk11xx
sandra@sandra-laptop:~$ dmesg
[   51.189427] stk11xx: Syntek USB2.0 webcam driver startup
[   51.189479] stk11xx: Syntek USB2.0 - STK-1135 based webcam found.
[   51.189484] stk11xx: Syntek AVStream USB2.0 1.3M WebCam - Product ID 0x6A31.
[   51.189491] stk11xx: Release: 0005
[   51.189495] stk11xx: Number of interfaces : 1
[   51.192244] stk11xx: Initialize USB2.0 Syntek Camera
**[   51.308575] stk11xx: Check device return error (0x0201 = 0C) !**
[   51.380773] stk11xx: Syntek USB2.0 Camera is ready
[   51.380867] stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0
[   51.380903] usbcore: registered new interface driver usb_stk11xx_driver
[   51.380906] stk11xx: v1.3.1 : Syntek USB Video Camera
sandra@sandra-laptop:~$ sudo lsusb -v|grep -A 8 Syntek
Bus 003 Device 003: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x174f Syntek
  idProduct          0x6a31 Web Cam - Asus A8J, F3S, F5R, VX2S, V1S
  bcdDevice            0.05
  iManufacturer           1 
  iProduct                2 
  iSerial                10 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9

```
Does anyone know what the solution to this is?

---

### Post by berot3 on 2008-11-18
Hello again. i just posted 2 posts ago and simply tried > sudo camorama and to my surprice IT WORKED!!!
So the question is now how can i use the webcam as normal user...

---

### Post by prezeus on 2008-11-20
Ok, I did it! the problem is that i don't know what driver i have installed, because a i tried diferents drivers, the 1.3.1, the 1.2.3, and the trunk (one of the three worked haha). The problem that camorama only can be executed as root, can be solved changing the permissions of /dev/video0.

Sorry for my english, i need to practise a little bit more...

---

### Post by razvanescu on 2009-01-06
i have an asus vx2s laptop, and a syntek webcam integrated ; had the same problem, i've followed instructions from [http://doc.ubuntu-fr.org/syntek](http://doc.ubuntu-fr.org/syntek) and the results are: ```
razvan@ubuntu:~$ lsusb
Bus 005 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
razvan@ubuntu:~$ sudo lsusb -v|grep -A 8 Syntek
Bus 003 Device 003: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x174f Syntek
  idProduct          0x6a31 Web Cam - Asus A8J, F3S, F5R, VX2S, V1S
  bcdDevice            0.05
  iManufacturer           1 
  iProduct                2 
  iSerial                10 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
razvan@ubuntu:~$ sudo gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
```
.... a little tweak...et voila:[ATTACH]98961[/ATTACH]

in cheese doesn't work neither when running "sudo cheese"; skype is seing my webcam only if I run it as ```
sudo skype
```

good luck!

---

### Post by nikola.borisof on 2009-01-24
I still can not get the webcam working. It shows a black box in skype options. When is view the webcam with camorama it looks fine. ;(
Please help.

---

### Post by audunmb on 2009-02-09
How do I go back to using the stkwebcam-driver? I installed the stk11xx-driver, but would like to have the stkwebcam-driver instead?

---

### Post by berot3 on 2009-02-10
did any1 try this?: [http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html]("http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html")

---

### Post by gnimsh on 2009-03-15
I just wanted to add my experience to this.  I also was having the error 2, which was solved for me by reinstalling all the linux-headers-* files that were already installed.  After I did that the makefile was created just fine.  

Then I ran into another problem, as Prezeus mentioned, about having to change the permissions on video0.  It was set to root, I believe because the driver is installed as root.  So to reset the permissions, fire up nautilus as root: alt+f2 (for the run application menu) then type gksu nautilus, or in a terminal type sudo nautilus and enter your password.  Then browse to filesystem, and the dev folder.  Start typing video until you find video0 and right click it, go to the permissions tab, and change from root to your username.  Restart.  
Now the only thing that doesn't work for me is cheese, but I'm working on that too. Will post in a bit.

---

### Post by jose1711 on 2009-12-08
> **kelenpe said:**
> 

I remove stkwebcam, and load the compiled stk11xx from the source svn ([http://syntekdriver.sourceforge.net/](http://syntekdriver.sourceforge.net/))

```

sudo modprobe -r stkwebcam &&
cd ~/.syntek/driver &&
sudo modprobe videodev &&
sudo insmod stk11xx.ko

```
It is awful but it is a temporary workaround for shutting off the webcam.

Thank you Kelenpe. It might be a dirty solution to turn this annoying led off but it works!

Many thanks, Jose & his wife

---

