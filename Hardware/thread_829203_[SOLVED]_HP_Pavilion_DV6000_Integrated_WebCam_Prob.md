---
title: "[SOLVED] HP Pavilion DV6000 Integrated WebCam Problems"
date: 2008-06-14
forum: Hardware
---

### Post by KemKev on 2008-06-14
I'm having some difficulty getting my integrated webcam working on my DV6000 with Hardy Heron 8.04.

When I run "lsusb", I get the info below

[COLOR="Blue"]Bus 002 Device 002: ID 050d:0845 Belkin Components
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 05ca:1810 Ricoh Co., Ltd
Bus 001 Device 001: ID 0000:0000[/COLOR]

When I run lsmod | grep videodev, I get:

[COLOR="Blue"]videodev 30720 1 uvcvideo
v4l1_compat 15492 2 uvcvideo,videodev
v4l2_common 21888 3 uvcvideo,compat_ioctl32,videodev[/COLOR]

Then, I then got the "r5u870-0.10.0.tgz" and after unpacking and running the "make" command, I get the following:

[COLOR="Blue"]make -C /lib/modules/2.6.24-18-generic/build M=/home/colin/Desktop/r5u870-0.10.0 V=0 modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
CC [M] /home/colin/Desktop/r5u870-0.10.0/r5u870_md.o

In file included from /home/colin/Desktop/r5u870-0.10.0/r5u870_md.c:55:
/home/colin/Desktop/r5u870-0.10.0/usbcam.h:36:29: error: media/video-buf.h: No such file or directory

make[2]: *** [/home/colin/Desktop/r5u870-0.10.0/r5u870_md.o] Error 1

make[1]: *** [_module_/home/colin/Desktop/r5u870-0.10.0] Error 2

make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'

make: *** [all] Error 2[/COLOR]

I've downloaded the file form different sources, but all the packages contain the same files, so I'm not sure why I'm getting all the errors.

I've also tried to run Cheese and a few other apps to see if I could get the cam recognized, but no luck.

I came across a site that says the Linux headers changed names in Hardy, and so the compilation will only work on kernels up to 2.6.22. Hardy is 2.6.24 Is there a work around?

Any help would be greatly appreciated.  Thanks much.

---

### Post by KemKev on 2008-06-15
Help anyone? I'd really appreciate it. :neutral:

Thanks.

---

### Post by KemKev on 2008-06-16
Found an old thread with a suggestion I tried and got the webcam working.  For those still trying to get theirs working, you may want to try this:

Firstly:
* Verify that you have svn installed.
* Remove any instance of r5u870 or the ry5u870 modules you may already have from previous attempts.

Code: 

svn co [http://svn.mediati.org/svn/r5u870/trunk](http://svn.mediati.org/svn/r5u870/trunk) ~/r5u870
cd ~/r5u870
sudo make
sudo make install
sudo modprobe r5u870

Then try xawtv to see if the cam works (sudo apt-get install xawtv)

test is using code: xawtv /dev/video0

[COLOR="Blue"]I apologize for not remembering where the initial thread is located, and as such, for being unable to give credit to the person who posted this solution.  If s/he is reading this, thank you.
 [/COLOR]
Good Luck.

---

### Post by afdanistan on 2008-06-26
Brilliant!!! Your directions worked perfectly! Thanks so much!

---

### Post by aquamammal on 2008-06-28
Thank you. This some how solved my Skype problems. Web cam still doesn't work with Cheese, but I really wanted to web cam with other people.

---

### Post by ozzyprv on 2008-07-16
This workedwith my dc9005ca (Ricoh) too.

Thanks.

---

### Post by retro93292 on 2008-08-27
That was great , works good . Props for re-posting :popcorn:

---

### Post by ozzyprv on 2008-12-07
> **KemKev said:**
> 

Code: 

svn co [http://svn.mediati.org/svn/r5u870/trunk](http://svn.mediati.org/svn/r5u870/trunk) ~/r5u870
cd ~/r5u870
sudo make
sudo make install
sudo modprobe r5u870

Then try xawtv to see if the cam works (sudo apt-get install xawtv)

test is using code: xawtv /dev/video0

[COLOR="Blue"]I apologize for not remembering where the initial thread is located, and as such, for being unable to give credit to the person who posted this solution.  If s/he is reading this, thank you.
 [/COLOR]
Good Luck.

The http address does not work (at least today/right now.
Any idea of a different source?

---

### Post by bushd on 2008-12-17
This worked wonderfully but something I should mention incase someone else finds themselves in the same situation: chmod your /dev/video0.  It didn't dawn on me until I saw the original output of Xawtv telling me no permission (couldn't see the others) so I sudo xawtv and it worked.  Well, video0 is chmodded to allow access now (777) because I haven't figured out how to give me and my non-existant root access only.  I did find out that I hate cheese because even now it doesn't work when I can get Ekiga and Xawtv to work.

---

### Post by hmich176 on 2008-12-18
This DID NOT work for me.  I got this code: 
```
make -C /lib/modules/2.6.24-22-generic/build M=/home/harry/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-22-generic'
  CC [M]  /home/harry/r5u870/usbcam/usbcam_fops.o
/home/harry/r5u870/usbcam/usbcam_fops.c:24:30: error: media/v4l2-ioctl.h: No such file or directory
/home/harry/r5u870/usbcam/usbcam_fops.c: In function &#8216;usbcam_v4l_ioctl&#8217;:
/home/harry/r5u870/usbcam/usbcam_fops.c:1162: warning: unused variable &#8216;udp&#8217;
/home/harry/r5u870/usbcam/usbcam_fops.c: At top level:
/home/harry/r5u870/usbcam/usbcam_fops.c:1214: error: variable &#8216;this_cam_ops&#8217; has initializer but incomplete type
/home/harry/r5u870/usbcam/usbcam_fops.c:1215: error: unknown field &#8216;vidioc_querycap&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1215: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1215: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1216: error: unknown field &#8216;vidioc_enum_fmt_vid_cap&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1216: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1216: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1217: error: unknown field &#8216;vidioc_g_fmt_vid_cap&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1217: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1217: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1218: error: unknown field &#8216;vidioc_s_fmt_vid_cap&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1218: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1218: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1219: error: unknown field &#8216;vidioc_try_fmt_vid_cap&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1219: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1219: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1220: error: unknown field &#8216;vidioc_reqbufs&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1220: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1220: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1221: error: unknown field &#8216;vidioc_querybuf&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1221: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1221: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1222: error: unknown field &#8216;vidioc_qbuf&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1222: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1222: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1223: error: unknown field &#8216;vidioc_dqbuf&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1223: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1223: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1224: error: unknown field &#8216;vidiocgmbuf&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1224: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1224: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1225: error: unknown field &#8216;vidioc_enum_input&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1225: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1225: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1226: error: unknown field &#8216;vidioc_streamon&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1226: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1226: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1227: error: unknown field &#8216;vidioc_streamoff&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1227: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1227: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1228: error: unknown field &#8216;vidioc_g_input&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1228: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1228: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1229: error: unknown field &#8216;vidioc_s_input&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1229: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1229: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1230: error: unknown field &#8216;vidioc_queryctrl&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1230: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1230: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1231: error: unknown field &#8216;vidioc_g_ctrl&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1231: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1231: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1232: error: unknown field &#8216;vidioc_s_ctrl&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1232: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1232: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1233: error: unknown field &#8216;vidioc_querymenu&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1233: warning: excess elements in struct initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1233: warning: (near initialization for &#8216;this_cam_ops&#8217;)
/home/harry/r5u870/usbcam/usbcam_fops.c:1238: error: unknown field &#8216;vfl_type&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1240: error: unknown field &#8216;ioctl_ops&#8217; specified in initializer
/home/harry/r5u870/usbcam/usbcam_fops.c:1240: warning: initialization makes integer from pointer without a cast
make[3]: *** [/home/harry/r5u870/usbcam/usbcam_fops.o] Error 1
make[2]: *** [/home/harry/r5u870/usbcam] Error 2
make[1]: *** [_module_/home/harry/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
make: *** [all] Error 2
```

---

### Post by stefanadelbert on 2008-12-26
Chmodding /dev/video0 also did not work for me. I find it weird that my webcam is working in Skype, but not in Cheese. XSane is also complaining that it cannot open the webcam, with error:
```
Failed to open device 'v4l:/dev/video0': Invalid argument.
```
I'm on 8.10, running kernel 2.6.27-9, HP Pavilion dv6836TX with built-in webcam:
```
Bus 004 Device 002: ID 05c8:010c Cheng Uei Precision Industry Co., Ltd (Foxlink)
```

---

### Post by mkarnicki on 2009-03-29
> I find it weird that my webcam is working in Skype, but not in Cheese.
Same here ..

---

### Post by hmich176 on 2009-03-29
> **stefanadelbert said:**
> Chmodding /dev/video0 also did not work for me. I find it weird that my webcam is working in Skype, but not in Cheese. XSane is also complaining that it cannot open the webcam, with error:
```
Failed to open device 'v4l:/dev/video0': Invalid argument.
```
I'm on 8.10, running kernel 2.6.27-9, HP Pavilion dv6836TX with built-in webcam:
```
Bus 004 Device 002: ID 05c8:010c Cheng Uei Precision Industry Co., Ltd (Foxlink)
```

Actually, my webcam just quit working for me.  I'm not even sure why. Skype doesn't recognize it's there.  And of course, it doesn't work in Cheese.

---

### Post by stefanadelbert on 2009-03-29
I posted this a while ago and I'm pretty sure that the webcam on my laptop is working again. I don't use the webcam on my laptop at all really (have another machine in the lounge with external Logitec webcam that I use for Skype), but I'll go back and check it out. There have been a few kernel updates since the post, so maybe one of the fixed something...

Stef

---

### Post by urs4edal on 2009-04-06
I have a Sony Vaio VGN-CR240E with a built in webcam:

Bus 003 Device 002: ID 05ca:1839 Ricoh Co., Ltd 

I tried the solution 
svn co [http://svn.mediati.org/svn/r5u870/trunk](http://svn.mediati.org/svn/r5u870/trunk) ~/r5u870
cd ~/r5u870
sudo make
sudo make install
modprobe r5u870
then try xawtv to see if it works (sudo apt-get install xawtv)

test it using 
Code:
xawtv /dev/video0

and when I run the test I get the following:
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-11-generic)
xinerama 0: 1280x800+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

Does anyone know how to help me get this webcam working?

---

### Post by anjohnso on 2009-05-09
I tried this, seemed to work, but when I run the test all I get is a black screen.  The webcam lights up signaling it's on, but no display. End up having to restart the computer.   

It's a hp dv5 so I figured it was worth a try.  Any ideas?

---

### Post by jjmoreno23 on 2009-05-20
I have a HP Pavillion DV6220la with a microdia webcam. When i run xawtv the webcam works just fine, but ekiga doesn't recognize dev/video0.
Some ideas?
thanks a lot.

---

### Post by bradleyed on 2009-06-26
the webcam works with xawtv, but nothing else recognizes the camera. maybe the other programs call a different module?

---

### Post by micio8 on 2010-01-06
[SIZE=4][SIZE=2]Hi,
I have just tried your code but when i get to
sudo make
i get the following error:[/SIZE]
[/SIZE]                                        /home/fabio/r5u870/usbcam/usbcam_fops.c:1174: error: too many arguments to function ‘video_ioctl2’
    [LEFT]/home/fabio/r5u870/usbcam/usbcam_fops.c:1162: warning: unused variable ‘udp’[/LEFT]
    [LEFT]make[3]: *** [/home/fabio/r5u870/usbcam/usbcam_fops.o] Error 1[/LEFT]
    [LEFT]make[2]: *** [/home/fabio/r5u870/usbcam] Error 2[/LEFT]
    [LEFT]make[1]: *** [_module_/home/fabio/r5u870] Error 2[/LEFT]
    [LEFT]make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'[/LEFT]
    [LEFT]make: *** [all] Error 2[/LEFT]
    [LEFT]fabio@ubuntu01:~/r5u870$ 



can you help???




[/LEFT]
   
  
[SIZE=4]

[/SIZE]

---

### Post by bradleyed on 2010-01-07
i'm running on karmic now. 64 bit amd with nvidia chipset. here's what happens when i try sudo make.

brad@brad-laptop:~$ cd ~/r5u870
brad@brad-laptop:~/r5u870$ sudo make
make -C /lib/modules/2.6.31-16-generic/build M=/home/brad/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /home/brad/r5u870/r5u870.o
/home/brad/r5u870/r5u870.c:872:1: warning: "V4L2_CID_PRIVACY" redefined
In file included from include/linux/videodev.h:17,
                 from /home/brad/r5u870/usbcam/usbcam.h:38,
                 from /home/brad/r5u870/r5u870.c:59:
include/linux/videodev2.h:1148:1: warning: this is the location of the previous definition
/home/brad/r5u870/r5u870.c:874:1: warning: "V4L2_CID_LASTP1" redefined
include/linux/videodev2.h:904:1: warning: this is the location of the previous definition
  CC [M]  /home/brad/r5u870/usbcam/usbcam_dev.o
/home/brad/r5u870/usbcam/usbcam_dev.c: In function ‘usbcam_register_mod’:
/home/brad/r5u870/usbcam/usbcam_dev.c:535: warning: assignment from incompatible pointer type
  CC [M]  /home/brad/r5u870/usbcam/usbcam_fops.o
/home/brad/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_vidioc_querycap’:
/home/brad/r5u870/usbcam/usbcam_fops.c:522: error: ‘struct device’ has no member named ‘bus_id’
/home/brad/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_ioctl’:
/home/brad/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/brad/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/brad/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but argument is of type ‘long unsigned int’
/home/brad/r5u870/usbcam/usbcam_fops.c:1170: error: too many arguments to function ‘video_usercopy’
/home/brad/r5u870/usbcam/usbcam_fops.c:1174: warning: passing argument 1 of ‘video_ioctl2’ from incompatible pointer type
include/media/v4l2-ioctl.h:302: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/brad/r5u870/usbcam/usbcam_fops.c:1174: warning: passing argument 2 of ‘video_ioctl2’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:302: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/brad/r5u870/usbcam/usbcam_fops.c:1174: error: too many arguments to function ‘video_ioctl2’
/home/brad/r5u870/usbcam/usbcam_fops.c:1162: warning: unused variable ‘udp’
/home/brad/r5u870/usbcam/usbcam_fops.c: At top level:
/home/brad/r5u870/usbcam/usbcam_fops.c:1198: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
make[3]: *** [/home/brad/r5u870/usbcam/usbcam_fops.o] Error 1
make[2]: *** [/home/brad/r5u870/usbcam] Error 2
make[1]: *** [_module_/home/brad/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [all] Error 2

---

### Post by niteshreddy on 2010-08-13
> **bradleyed said:**
> i'm running on karmic now. 64 bit amd with nvidia chipset. here's what happens when i try sudo make.

brad@brad-laptop:~$ cd ~/r5u870
brad@brad-laptop:~/r5u870$ sudo make
make -C /lib/modules/2.6.31-16-generic/build M=/home/brad/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /home/brad/r5u870/r5u870.o
/home/brad/r5u870/r5u870.c:872:1: warning: "V4L2_CID_PRIVACY" redefined
In file included from include/linux/videodev.h:17,
                 from /home/brad/r5u870/usbcam/usbcam.h:38,
                 from /home/brad/r5u870/r5u870.c:59:
include/linux/videodev2.h:1148:1: warning: this is the location of the previous definition
/home/brad/r5u870/r5u870.c:874:1: warning: "V4L2_CID_LASTP1" redefined
include/linux/videodev2.h:904:1: warning: this is the location of the previous definition
  CC [M]  /home/brad/r5u870/usbcam/usbcam_dev.o
/home/brad/r5u870/usbcam/usbcam_dev.c: In function ‘usbcam_register_mod’:
/home/brad/r5u870/usbcam/usbcam_dev.c:535: warning: assignment from incompatible pointer type
  CC [M]  /home/brad/r5u870/usbcam/usbcam_fops.o
/home/brad/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_vidioc_querycap’:
/home/brad/r5u870/usbcam/usbcam_fops.c:522: error: ‘struct device’ has no member named ‘bus_id’
/home/brad/r5u870/usbcam/usbcam_fops.c: In function ‘usbcam_v4l_ioctl’:
/home/brad/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/brad/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/brad/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but argument is of type ‘long unsigned int’
/home/brad/r5u870/usbcam/usbcam_fops.c:1170: error: too many arguments to function ‘video_usercopy’
/home/brad/r5u870/usbcam/usbcam_fops.c:1174: warning: passing argument 1 of ‘video_ioctl2’ from incompatible pointer type
include/media/v4l2-ioctl.h:302: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/brad/r5u870/usbcam/usbcam_fops.c:1174: warning: passing argument 2 of ‘video_ioctl2’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:302: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/brad/r5u870/usbcam/usbcam_fops.c:1174: error: too many arguments to function ‘video_ioctl2’
/home/brad/r5u870/usbcam/usbcam_fops.c:1162: warning: unused variable ‘udp’
/home/brad/r5u870/usbcam/usbcam_fops.c: At top level:
/home/brad/r5u870/usbcam/usbcam_fops.c:1198: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
make[3]: *** [/home/brad/r5u870/usbcam/usbcam_fops.o] Error 1
make[2]: *** [/home/brad/r5u870/usbcam] Error 2
make[1]: *** [_module_/home/brad/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [all] Error 2


samer errors here... :(

---

### Post by tango_ninja on 2011-01-08
same errors as previous post

---

### Post by merimjunior on 2011-01-28
Me too, I have the same error from the previous posts. Please, anyone can solve it? Waiting for some answer. By the way, my ubuntu is 10.10.

---

### Post by jagallego on 2011-02-27
Hello,

I had the same problems as the other users (errors and so on). I found this updated version that worked fine for me in an HP Pavilion 9000:
[https://bitbucket.org/ahixon/r5u87x/src](https://bitbucket.org/ahixon/r5u87x/src)

Good luck

---

### Post by tango_ninja on 2011-02-28
> **jagallego said:**
> Hello,

I had the same problems as the other users (errors and so on). I found this updated version that worked fine for me in an HP Pavilion 9000:
[https://bitbucket.org/ahixon/r5u87x/src](https://bitbucket.org/ahixon/r5u87x/src)

Good luck

Hmm... unfortunately tried this just now and still not working for me on my dv6000.  Looks like I may have to reinstall a windows partition and ensure the hardware is functioning correctly.

---

### Post by Oldagodz on 2011-04-23
Thanks it worked on my HP G60!! Great post

---

