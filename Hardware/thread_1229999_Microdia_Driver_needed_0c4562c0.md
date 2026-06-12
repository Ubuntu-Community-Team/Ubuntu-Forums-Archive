---
title: "Microdia Driver needed: 0c45:62c0"
date: 2009-08-02
forum: Hardware
---

### Post by astarr on 2009-08-02
EDIT: Issue resolved

---

### Post by astarr on 2009-08-09
I'm running Ubuntu 9.04. The issue begins with my webcam not being detected in any program: Skype, Cheese, AMSN, etc. I receive this error message:

> /dev/video0 not found

the lsusb command returns that my webcam is a Microdia webcam 0c45:62c0 
[SIZE="2"]*(Sidenote: it is not appearing in the lsusb listings currently, however, it has appeared while using Ubuntu 8.10 and appeared after installing the drivers in Ubuntu 9.04 - referred to later)*[/SIZE]

The webcam had worked prior to upgrading to 9.04 through these instructions, found on multiple forums regarding this webcam specifically:

> svn co svn://svn.berlios.de/linux-uvc/linux-uvc/trunk linux-uvc
cd linux-uvc
sudo make
sudo make install
sudo modprobe -r uvcvideo
sudo mv /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko.original
sudo cp uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko
sudo modprobe uvcvideo 

On sudo make, I receive this:

> -------------------------------- WARNING ---------------------------------------
 The USB Video Class driver has moved to [http://linuxtv.org/](http://linuxtv.org/).
 Using the Berlios SVN repository is now deprecated.
 Please check [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) for download instructions.
 If you really want to compile this historical version, run 'make uvcvideo'.
--------------------------------------------------------------------------------


on command make uvcvideo I receive this:

> astarr@astarr-laptop:~/trunk$ make uvcvideo
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/astarr/trunk/uvc_driver.o
  CC [M]  /home/astarr/trunk/uvc_v4l2.o
/home/astarr/trunk/uvc_v4l2.c: In function ‘uvc_v4l2_do_ioctl’:
/home/astarr/trunk/uvc_v4l2.c:986: warning: passing argument 1 of ‘v4l_compat_translate_ioctl’ from incompatible pointer type
/home/astarr/trunk/uvc_v4l2.c:986: warning: passing argument 2 of ‘v4l_compat_translate_ioctl’ makes integer from pointer without a cast
/home/astarr/trunk/uvc_v4l2.c:986: warning: passing argument 3 of ‘v4l_compat_translate_ioctl’ makes pointer from integer without a cast
/home/astarr/trunk/uvc_v4l2.c:986: error: too many arguments to function ‘v4l_compat_translate_ioctl’
make[2]: *** [/home/astarr/trunk/uvc_v4l2.o] Error 1
make[1]: *** [_module_/home/astarr/trunk] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [uvcvideo] Error 2


There is no help for this error on the website, or through searching google and other forums.

I've found an alternative route, described here:

[https://groups.google.com/group/microdia/web/testing-microdia-driver-draft]("https://groups.google.com/group/microdia/web/testing-microdia-driver-draft")

Summary:

> [SIZE="2"]1. Download the source code

From a command-line prompt, cd to a directory where you want to download it, then run the command: 

$ git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)

This will create a folder named "microdia" which contains all the source code.

 

Sometimes the above command doesn't work. In such cases please try this one:

$ git clone [http://repo.or.cz/microdia.git](http://repo.or.cz/microdia.git)
2. Install bare minimum packages

To be able to compile the driver, you must have kernel sources and the necessary tools to compile it. For most applications you will also need libv4l.

    *
      Debian/Ubuntu
      # apt-get install kernel-package linux-headers build-essential ctags libv4l

      Note: linux-source is not necessary, rather linux-headers with the same version of your kernel will install /lib/modules/<kernel_version>/build.

      for details refer to here. if you use the latest kernel of ubuntu, linux-headers depends on it. libv4l package may not be available in the stable distribution so I'm attacheing a version that installs on debian lenny.

    *
      Gentoo
      # emerge -av gentoo-sources libv4l

    *
      Fedora
      # yum install git kernel-devel gcc make libv4l
    *
      openSUSE
      # have a Repository /drivers:/webcam (OpenSUSE 11 updated) with a microdia Kernel Driver (kmp)
    *
      Arch Linux
      Driver lies in AUR, [http://aur.archlinux.org/packages.php?ID=17451](http://aur.archlinux.org/packages.php?ID=17451).
      If you have yaourt:
      # yaourt -S microdia-git
      Or to do it manually, create a folder, download the PKGBUILD to that folder, and use:
      $ makepkg
      # pacman -U microdia-git*.pkg.tar.gz

    *
      FIXME: Add your distro here

3. Setting up the compilation environment

The linux kernel needs to be locally compiled in order to compile the microdia driver.

If the kernel is not compiled, "make" will complain of "modpost" missing.

The Makefile expects the source of linux to be located in /lib/modules/$(KVER)/build, if this is not the case edit the Makefile to set KSRC to point to the linux source location.
4. Building Microdia driver from source

After installing Git, you need to download microdia kernel driver source. After installing Kernel packages and necessary tools to compile it, you will be able to compile it by typing:
$ cd microdia
$ make

Attention: Do _NOT_ under any circumstances use "$ sudo make" or "# make". There are no root privileges necessary at this point and using them causes a never ending chain of different problems later on. 

Troubleshooting MAKE errors

If you get the following error:
make: *** [driver] Error 127
Error 127 simply means that the module is not in the proper location. This is not a major error.
5. Loading the driver

Now comes el gran finale. Using root user (su), load the driver module by typing:

# insmod ./sn9c20x.ko

If everything works fine you won't see any message on stdout, but your dmesg will have lines like the following:

sn9c20x: SN9C20X USB 2.0 webcam driver loaded
sn9c20x: SN9C20X USB 2.0 Webcam - 0C45:624E plugged-in.
sn9c20x: Detected SOI968 Sensor
sn9c20x: SN9C20X USB 2.0 Webcam is now controlling video device /dev/video0
usbcore: registered new interface driver usb_sn9c20x_driver
sn9c20x: v2008.10 : SN9C20X USB 2.0 Webcam Driver

So, congratulations! Your webcam is ready for action now. If not:
Troubleshooting insmod errors

# insmod sn9c20x.ko
insmod: error inserting 'sn9c20x.ko': -1 Unknown symbol in module

See the output of #dmesg

The last few lines would be complaints about missing symbols, depending upon whats missing you may not have loaded the modules that module depends on,
So it failed with those error messages. You would need to modprobe for that module's dependencies

Try:
# sudo modprobe videodev
# modprobe compat-ioctl32

then
# insmod sn9c20x.ko

If still you get errors on #insmod, perhaps you have had a recent kernel update.

Update a the lists the dependencies for every module.
# depmod -a
# m-a update,prepare

You may also need to regenerate kernel initrd image (really).

 

insmod: error inserting './sn9c20x.ko': -1 Invalid module format

 

Possible Reason

"The gcc which compiled the kernel and 

the gcc which compiled the module are incompatible." 

Possible Solution

Install an older gcc side-by-side, and change cc environment variable to use older version. 

 

Possible Solution

Reinstall the kernel image using

#apt-get install --reinstall linux-image-`uname -r`

Possible Reason 2

This happened to me(may be more people) when ubuntu Jaunty was upgdated with a 2.6.28-14-generic

kernel.

If your dmesg says something like:

microdia: Unknown symbol video_devdata

The videodev module needs to be loaded.


Possible Solution

modprobe videodev

insmod sn9c20.ko  (from the directory where you have this file, i.e, where you compiled it)


FIXME: more possibilities
6. Test it using mplayer
Please note that the test requires libv4l for video decoding. mplayer does not support JPEG compression on its own.

$ LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so mplayer tv:// \
    -tv driver=v4l2:width=640:height=480:fps=25:device=/dev/video0 -vo x11
7. Installing the Microdia Driver

This step is optional. If you don't do it though you will have to insmod sn9c20x.ko everytime you reboot.


# strip -g sn9c20x.ko
# mkdir -p /lib/modules/`uname -r`/kernel/drivers/media/video/usbvideo/
# cp sn9c20x.ko /lib/modules/`uname -r`/kernel/drivers/media/video/usbvideo/
# depmod -a [/SIZE]

Now, on step 4 I receive this error:
> make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/home/astarr/microdia modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
mkdir: cannot create directory `/home/astarr/microdia/.tmp_versions': Permission denied
  CC [M]  /home/astarr/microdia/sn9c20x-usb.o
Assembler messages:
Fatal error: can't create /home/astarr/microdia/.tmp_sn9c20x-usb.o: Permission denied
make[2]: *** [/home/astarr/microdia/sn9c20x-usb.o] Error 2
make[1]: *** [_module_/home/astarr/microdia] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [driver] Error 2


Again, no help for Error 2.

I have also thoroughly followed the instructions for this installation in Ubuntu 9.04, but I won't go through the work of copying and pasting, as there were no errors and it was not successful:
[http://ubuntuforums.org/showthread.php?t=838210]("http://ubuntuforums.org/showthread.php?t=838210")


Any help would be greatly appreciated!

---

### Post by astarr on 2009-08-09
Update:

Error 2 with the microdia file is solved, I received this message on the Google group:

> It looks like you do not have write permissions for the microdia directory.
try the following

# cd
# sudo chmod u+rwx microdia
# sudo chown -R astarr microdia

This should make sure you have the correct permissions


now the make works, as well I followed through the rest of the steps.

However, after restarting the webcam device (dev/video0) is still not detected by any programs.

Thoughts?

---

### Post by ddmitriy on 2009-08-24
Hi there! I have almost the same problem.
Lsusb command detects my camera as:

Bus 001 Device 003: ID 0c45:624f Microdia PC Camera (SN9C201)

I did all the actions described above without any significant problems and therefore /dev/video0 appeared in a tree list. My dmesg output says this about the camera:

[   11.094611] sn9c20x: SN9C20X USB 2.0 Webcam - 0C45:624F plugged-in.
[   11.238218] sn9c20x: Detected OV9650 Sensor.
[   11.238344] sn9c20x: Webcam device 0C45:624F is now controlling video device /dev/video0
[   11.242271] psmouse serio1: ID: 10 00 64<3>sn9c20x: No ack from I2C slave 0x30 for write to address 0x17
[   11.275366] sn9c20x: Using yuv420 output format
[   11.275441] usbcore: registered new interface driver sn9c20x
[   11.275450] sn9c20x: SN9C20x USB 2.0 Webcam Driver v2009.04 loaded
[   25.219722] sn9c20x: Using yuv420 output format

However, it still doesnt work. The camera itself became selectable in different software like Skype, Cheese, Ekiga etc but i cant get any image from it. All test screens there are just plain black.
When i try $ xawtv /dev/video0/ to test my camera, the screen is also black and this is what it throws into a console:

ioctl: VIDIOC_S_FMT(type=VIDEO_CAPTURE;fmt.pix.width=320;fmt.pix.height=240;fmt.pix.pixelformat=0x30323953 [S920];fmt.pix.field=ANY;fmt.pix.bytesperline=480;fmt.pix.sizeimage=115200;fmt.pix.colorspace=SRGB;fmt.pix.priv=0): Device or resource busy

PS. This camera worked fine under Win platforms and its integrity is not an issue here.
Any help will be greatly appreciated, thanks for advance.

---

### Post by ddmitriy on 2009-08-28
So far, no good...
The funny thing is the camera really DOES work in xawtv and mplayer (still no good in web pagers), but only under root privileges and only until the next reboot before driver initial install procedure described above. This means that right after the reboot the /dev/video0 becomes unavailable to use even under root login - every and each camera-using software says that device is busy. Looking through active processes in Administration -> System Monitor brought nothing - no programs were using /dev/video0. Ive browsed through module dependencies in /lib/modules/2.6.28.15-generic/modules.dep and looks like this driver is working like sn9c20x.ko -> videodev.ko -> v4l1-compat.ko trio. Notice that rmmod or modprobe -r wont work on any single of them or all of them alltogether while system in graphics mode (says module/modules in use). The only way to deinstall them is to rmmod/modprobe 'em in recovery console under root login. Numerous reinstallations of v4l1 / v4l2 video software didnt help either. Im total noob in Linux OSes an really hope somebody would answer this post, cuz im already out of ideas where to look/how to get that driver to work :(

---

### Post by ddmitriy on 2009-09-07
The issue was solved by installing Intrepid, thanks for everybody's attention.

---

### Post by alfovic on 2009-11-02
i have exactly this problem but under ubuntu 9.10 netbook remix
do anyone know how to solve it?

---

### Post by astarr on 2009-11-02
alfovic, what problem is it exactly?

I have yet to upgrade from 9.04 to 9.10, so when I do I know I'll have to go through these motions again. I'll try to update this thread as I go along with a thorough walkthrough.

ddmitriy,
I'm also trying to work through the problems as they arise. However, I'm not even close to being a programmer (I actually do research as a student, so I'm good at that!).
What I'd suggest is starting where I did by seeking out the Microdia Google Group and following their instructions. When you hit a snag, follow the troubleshooting they provide - or that I've provided.

Hope that helps!

---

### Post by rrorro on 2010-03-02
hi,
i am new in ubuntu and i am having trouble with my webcam. it used to work perfectly well with skype but suddenly it stopped working. i have tryed reinstalling it but it still won't work. there are no problems with cheese so i guess something is unconfigured for skype(?)... can someone help me? please =S

---

### Post by astarr on 2010-03-02
> **rrorro said:**
> hi,
i am new in ubuntu and i am having trouble with my webcam. it used to work perfectly well with skype but suddenly it stopped working. i have tryed reinstalling it but it still won't work. there are no problems with cheese so i guess something is unconfigured for skype(?)... can someone help me? please =S

rrorro, and everyone else who responded, you can get more help if you are specific.

What version of Ubuntu?
What is your webcam? (command 'lsusb' in the terminal)
Where are you stuck along the instructions in the first post?
What are the arguments that are returned to you?

Anything else would help. However, I'm new to Ubuntu, and what I get is usually from people with more experience than me.

Good luck.

---

