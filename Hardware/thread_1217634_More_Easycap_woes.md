---
title: "More Easycap woes"
date: 2009-07-19
forum: Hardware
---

### Post by cooper77z on 2009-07-19
Having read through the easycap discussions on this site and and the ebay forums I was able to download the following driver, syntekdriver.tar.gz for gnu

Now I don't know what to do to install it. Will you all please help me install the driver step by step? Because I don't know what to do with the file after I extract it and I never have any luck installing an extracted file or program because I don't know how to do it. Any help is appreciated.

The driver is quite large, it's 13.2 megabytes and it is still compressed.

P.S. I downloaded the driver from here [http://syntekdriver.svn.sourceforge.net/](http://syntekdriver.svn.sourceforge.net/)

---

### Post by HotShotDJ on 2009-07-19
I don't have any personal knowledge regarding the drivers for these webcams.  However, I did a search, and found the following: [http://ubuntuforums.org/showthread.php?t=1044175](http://ubuntuforums.org/showthread.php?t=1044175)
See especially comment #7 in that thread.

---

### Post by cooper77z on 2009-07-20
How do I install my easycap device to work in cinelerra? I am going to surf the net for a while but I'll check back periodically to see if anyone is chatting about my question, thanks

<snip>

Please help me install this usb easycap device in 8.04.2

---

### Post by ibuclaw on 2009-07-21
[COLOR="Red"]JAUNTY USERS ONLY[/COLOR]
As discussed in IRC, I have come up with this resolution. (to be confirmed whether or not it works).

1) First, you require some prerequesites:
```
sudo apt-get install build-essential linux-headers-$(uname -r) ctags
```

2) Follow these instructions carefully.

Download the patched source attached to this post [here]("http://ubuntuforums.org/attachment.php?attachmentid=121998&stc=1&d=1248273571"). It should save on your Desktop.
```
cd ~/Desktop
tar xf stk11xx-2.1.0a.tar.gz 
cd stk11xx-2.1.0a/

```

3) You can now build and install the driver
```
make -f Makefile.standalone
```

As far as the documentation is concerned, they are yet to write a script to install it. Which seems rather unfortunate.

4) To load the driver for testing/use, run the following:
```
sudo modprobe videodev
sudo insmod stk11xx.ko
```
And then open a video device recorder to test of the device.

5) If the device works, brilliant! The best way to have this autoload everytime you boot would be to do the following:
```
sudo cp stk11xx.ko /lib/modules/$(uname -r)/kernel/drivers/usb/misc/
sudo depmod
```
Then run:
```
gksudo gedit /etc/modules
```
And put at the bottom of the file:
```
stk11xx
```
Then save and close the file.

Now update the initrd file
```
sudo update-initramfs -u -k all
```

And Voila! you are done.

Give it a whirl, and hopefully all should work for you.

Regards
Iain

---

### Post by cooper77z on 2009-07-21
Hi iain_ and friends. I did go ahead and install Jaunty, so that I could try out this Tek and because everyone kept telling me to. I updated it. Then I followed the Tek. Camorama tells me that there isn't a device. So it is not working at the moment. I wonder if I messed up following the Tek or if there is something wrong that is keeping the driver from communicating with Camorama or something else entirely. iain_, did you actually try the Tek out with Camorama and an easycap device?

Thanks for all the work so far. I think we might be close to a solution.

P.S. Cinelerra can't see the device either. I finally did figure out how to tell Cinelerra what input to use, but there are no available inputs listed in the menu.

P.S.S. Oy, I tried to install SELinux under Jaunty from synaptic and my system totally crashed. Back on 8.04.2 now. I tried. I am pretty sure SELinux works under 8.04 so I'll try switching and installing the tek again.

---

### Post by cooper77z on 2009-07-23
I am going to consider the audio and video capture issue in ubuntu solved. If I wish to work with audio and video media in ubuntu, then for the time being, I must provide ubuntu with the media in digital form. That's fine. I can live with that.

---

### Post by atarisal on 2009-11-14
Hi all,

I am having troubles to install EASYCAP. I am using ubuntu 9.10.

When I tried using suggestion from tinivole, I got

cosi@cosi-computer:~/Escritorio/stk11xx-2.1.0a$ make -f Makefile.standalone
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/cosi/Escritorio/stk11xx-2.1.0a modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/cosi/Escritorio/stk11xx-2.1.0a/stk11xx-v4l.o
/home/cosi/Escritorio/stk11xx-2.1.0a/stk11xx-v4l.c: In function ‘v4l_stk11xx_ioctl’:
/home/cosi/Escritorio/stk11xx-2.1.0a/stk11xx-v4l.c:1662: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/cosi/Escritorio/stk11xx-2.1.0a/stk11xx-v4l.c:1662: warning: passing argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/cosi/Escritorio/stk11xx-2.1.0a/stk11xx-v4l.c:1662: warning: passing argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but argument is of type ‘long unsigned int’
/home/cosi/Escritorio/stk11xx-2.1.0a/stk11xx-v4l.c:1662: error: too many arguments to function ‘video_usercopy’
/home/cosi/Escritorio/stk11xx-2.1.0a/stk11xx-v4l.c: In function ‘v4l_stk11xx_register_video_device’:
/home/cosi/Escritorio/stk11xx-2.1.0a/stk11xx-v4l.c:1686: warning: assignment from incompatible pointer type
make[2]: *** [/home/cosi/Escritorio/stk11xx-2.1.0a/stk11xx-v4l.o] Error 1
make[1]: *** [_module_/home/cosi/Escritorio/stk11xx-2.1.0a] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [driver] Error 2

Then I fail to build the driver and I dont understand how to avoid the Error.

Please Help me!!!!

---

### Post by ctvbs on 2009-12-14
alby@ubuntu:~/Scaricati/stk11xx-2.1.0a$ sudo make -f Makefile.standalone
make -C /lib/modules/2.6.31-16-generic/build SUBDIRS= modules
make[1]: ingresso nella directory «/usr/src/linux-headers-2.6.31-16-generic»
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** Nessuna regola per creare l'obiettivo «kernel/bounds.c», necessario a «kernel/bounds.s».  Arresto.
make[1]: *** [prepare0] Errore 2
make[1]: uscita dalla directory «/usr/src/linux-headers-2.6.31-16-generic»
make: *** [driver] Errore 2

ubuntu 9.10 confirm don't work

solutions?

thanks

---

