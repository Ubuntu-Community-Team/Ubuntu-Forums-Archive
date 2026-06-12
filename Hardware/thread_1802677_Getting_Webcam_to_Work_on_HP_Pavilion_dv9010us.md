---
title: "Getting Webcam to Work on HP Pavilion dv9010us"
date: 2011-07-12
forum: Hardware
---

### Post by dodle on 2011-07-12
I have been searching for hours on how to get this webcam to work. It's beginning to look like my only option would be to compile and older version of the linux kernel.

lsusb:
```
Bus 001 Device 002: ID 05ca:1870 Ricoh Co., Ltd Webcam 1000
```

The camera that I have requires the r5u870 driver. But the latest version that I can find was written for kernel version 2.6.30 and is found here: [http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html). And as the site says, the project is discontinued. I tried compiling it with my current kernel version 2.6.38. But support for video4linux has been removed. So I get an error that says "linux/videodev.h : no such file or directory". 

I also tried following the instructions [here](https://launchpad.net/~r5u87x-loader/+archive/ppa) to install the r5u87x driver but it does not support my camera. 

So I'm guessing that my only option is to downgrade to a kernel that supports video4linux. Can that be done? I am using Ubuntu 11.04. Has anyone else been able to get this same webcam to work?

This is a list of cameras that use the r5u870 driver:
05ca:1810 HP Pavilion Webcam &#8211; UVC
05ca:1830 Sony Visual Communication Camera VGP-VCC2 (VAIO SZ)
05ca:1832 Sony Visual Communication Camera VGP-VCC3 (VAIO UX)
05ca:1833 Sony Visual Communication Camera VGP-VCC2 (VAIO AR1)
05ca:1834 Sony Visual Communication Camera VGP-VCC2 (VAIO AR2)
05ca:1835 Sony Visual Communication Camera VGP-VCC5 (VAIO SZ)
05ca:1836 Sony Visual Communication Camera VGP-VCC4 (VAIO FE)
05ca:1870 HP Pavilion Webcam / HP Webcam 1000

Has anyone been able to get one of these to work?

---

### Post by dodle on 2011-07-14
I found a possible driver here: [http://code.google.com/p/r5u870/](http://code.google.com/p/r5u870/). But I can't get it to compile because of missing headers.

```
make -C /lib/modules/2.6.38-10-generic/build M=/home/jordan/Downloads/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-10-generic'
  CC [M]  /home/jordan/Downloads/r5u870/r5u870.o
In file included from /home/jordan/Downloads/r5u870/r5u870.c:59:0:
/home/jordan/Downloads/r5u870/usbcam/usbcam.h:38:28: fatal error: linux/videodev.h: No such file or directory
compilation terminated.
make[2]: *** [/home/jordan/Downloads/r5u870/r5u870.o] Error 1
make[1]: *** [_module_/home/jordan/Downloads/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-10-generic'
make: *** [all] Error 2
```

Does anyone know which package I need to install to get the linux/videodev.h header?

**----- Edit -----**
Okay, it looks like the package libv4l-dev has the header libv4l1-videodev.h which is supposed to replace linux/videodev.h. But now my compiler is complaining that it can't find libv4l1-videodev.h. I've checked to make sure that it is installed to /usr/include/libv4l1-videodev.h.

```
make -C /lib/modules/2.6.38-10-generic/build M=/home/jordan/Downloads/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-10-generic'
  CC [M]  /home/jordan/Downloads/r5u870/r5u870.o
In file included from /home/jordan/Downloads/r5u870/r5u870.c:59:0:
/home/jordan/Downloads/r5u870/usbcam/usbcam.h:39:30: fatal error: libv4l1-videodev.h: No such file or directory
compilation terminated.
make[2]: *** [/home/jordan/Downloads/r5u870/r5u870.o] Error 1
make[1]: *** [_module_/home/jordan/Downloads/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-10-generic'
make: *** [all] Error 2
```

---

### Post by iceguitar on 2011-07-15
Folks, I have the same issue with my VAIO CR series laptop that has the Ricoh camera as in-built, and I get a similar trouble with a "missing videodev.h" when trying to make the drivers. Considering I am a total newbie to Linux, this has caused significant pain for weeks now :'( and I am spending more time on this issue rather than move on and start using the OS to its fullest.

Some Ubuntu God out there... please respond to us!!

---

### Post by dodle on 2011-07-16
So here is what I have done so far:

1) I downloaded the source for the driver from here: [http://code.google.com/p/r5u870/downloads/detail?name=r5u870.tar.gz&can=2&q=](http://code.google.com/p/r5u870/downloads/detail?name=r5u870.tar.gz&can=2&q=)

2) I installed the kernel headers and video4linux development files:
```
sudo apt-get install linux-headers-<version>-generic libv4l-0 libv4l-dev
```

3) Created a symbolic link to the libv4l1-videodev.h file:
```
sudo ln -s /usr/include/libv4l1-videodev.h /usr/src/linux-headers-<version>-generic/include/linux/videodev.h
```

Now when I try to compile I get a new error:
```
make -C /lib/modules/2.6.38-10-generic/build M=/home/jordan/Downloads/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-10-generic'
  CC [M]  /home/jordan/Downloads/r5u870/r5u870.o
In file included from include/linux/videodev.h:6:0,
                 from /home/jordan/Downloads/r5u870/usbcam/usbcam.h:38,
                 from /home/jordan/Downloads/r5u870/r5u870.c:59:
/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/include/stdint.h:3:26: error: no include path in which to search for stdint.h
make[2]: *** [/home/jordan/Downloads/r5u870/r5u870.o] Error 1
make[1]: *** [_module_/home/jordan/Downloads/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-10-generic'
make: *** [all] Error 2
```

Any advice?

---

### Post by dodle on 2011-07-19
I've had no luck compiling the driver on newer linux distros. I have been able to do it with distros running an earlier kernel than 2.6.36. And I don't know if we will see new releases for newer systems.

I have not been able to get it to work with Skype at all, it does work with cheese and camorama.

If you are running a kernel older than 2.6.36 you can install it like this:

Make sure you have the linux-headers package for your installed for your current kernel. It's usually something like: linux-headers-<version>

Download the source from here: [http://code.google.com/p/r5u870/downloads/detail?name=r5u870.tar.gz&can=2&q=](http://code.google.com/p/r5u870/downloads/detail?name=r5u870.tar.gz&can=2&q=). You can do:

```
wget http://r5u870.googlecode.com/files/r5u870.tar.gz
```

Extract the contents:

```
tar -xzf r5u870.tar.gz
```

Edit the file r5u870/usbcam/usbcam_fops.c. There will be a line that says ".compat_ioctl	= v4l_compat_ioctl32,", it should be line 1199. Either comment it out with "//" at the beginning of the line or just delete it.

Now move into the r5u870 folder and compile and install:

```
cd r5u870
make
sudo make install
```

Now run the following command and your webcam should work:

```
sudo modprobe r5u870
```

---

