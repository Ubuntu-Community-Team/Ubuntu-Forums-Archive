---
title: "gspca driver will not compile in intrepid"
date: 2008-11-01
forum: Hardware
---

### Post by lamer1 on 2008-11-01
Hi everybody,

This question has been asked couple of times on the forums:

[http://ubuntuforums.org/showthread.php?t=952718](http://ubuntuforums.org/showthread.php?t=952718)

I was having the same problem and I starting browsing through the code investigating the compile errors one by one. I managed to fix the compile problem and managed to compile and load the gspca driver.
It seems that there are some interface incompatibilities between the gspcav1-20071224 driver and the current kernel.
Just to let you know that I have no knowledge of the v4l and how it works. All I did is just found the incompatible parts of the gspca code and updated them to comply with the new changes from the kernel. 
After some time I managed to fix all compile errors and compiled the driver.
Perhaps someone with better gspca+v4l knowledge can make use of this...

In case there is anyone out there that needs to compile the driver I am attaching a patch for gspcav1-20071224 (note the patch contains QuickCam E2500 from [http://forums.quickcamteam.net/showthread.php?tid=310](http://forums.quickcamteam.net/showthread.php?tid=310)).

I own an E2500 cam and it does not seem to work properly. Most of the time the picture is dark (I don't know how to change the settings, anyone knows?). Sometimes I can see the video, but after I change settings using gqcam the picture goes dark again.

Hope this helps,

---

### Post by durilka on 2008-11-01
[http://v4l2ucp.sourceforge.net/](http://v4l2ucp.sourceforge.net/) helps with the image brightness

---

### Post by loell on 2008-11-01
this is a widespread glitch on  webcam apps since libv4l migration, i think this can only be address on application to application basis, that if the particular webcam app uses the libv4l api.

---

### Post by nagolchi on 2008-11-14
did you try adding this to the end of your /etc/modprobe.d/options file?

options gspca gamma=1 autoexpo=0

taken from [http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/)

Thanks for that patch!

---

### Post by lamer1 on 2008-11-14
nagolchi,

Thnx that worked... 

I still have to test the CPU load mentioned in the given link.

---

### Post by actionshrimp on 2008-11-14
thanks a lot for this patch, can finally get video on skype again. Hopefully they'll include support for this camera soon, but until then at least I can get something working! This patch works on the source in the gspca-source package in the repos too, as well as the gspcav1-20071224 off the website.

---

### Post by knedlyk on 2008-11-17
> **nagolchi said:**
> did you try adding this to the end of your /etc/modprobe.d/options file?

options gspca gamma=1 autoexpo=0

taken from [http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/)


I don't understand how this option can work under Intrepid???
There is no driver gspca alone, but gspca_main and the corresponding to the camera driver (gspca_spca651 for example). It can be useful under hardy, but not under ubuntu 8.10!

---

### Post by nagolchi on 2008-11-18
this will work if you compile gspca from the source mentioned above instead of using gspca_main included in the kernel in 8.10

---

### Post by knedlyk on 2008-11-18
> **nagolchi said:**
> this will work if you compile gspca from the source mentioned above instead of using gspca_main included in the kernel in 8.10

Yes, I agree, it can work in this case, but gspcav1-20071224 driver is very old and you have to patch it for the new camera models. Moreover, there is a problem to make the developer version of the driver from linux-dvb work under new ubuntu kernel. You can easily compile it, but it gives errors when you load driver into the memory.

---

### Post by Jumbalaspi on 2008-11-18
i cannot compile, it gives me some errors:



make -C /lib/modules/`uname -r`/build SUBDIRS=/home/jumbalaya/sources/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /home/jumbalaya/sources/gspcav1-20071224/gspca_core.o
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:54:29: error: linux/semaphore.h: No such file or directory
In file included from /home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:64:
/home/jumbalaya/sources/gspcav1-20071224/gspca.h:17:30: error: media/v4l2-ioctl.h: No such file or directory
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:2615: error: unknown field &#8216;vfl_type&#8217; specified in initializer
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c: In function &#8216;spca50x_create_sysfs&#8217;:
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:2773: warning: passing argument 1 of &#8216;device_create_file&#8217; from incompatible pointer type
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:2776: warning: passing argument 1 of &#8216;device_create_file&#8217; from incompatible pointer type
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:2779: warning: passing argument 1 of &#8216;device_create_file&#8217; from incompatible pointer type
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:2784: warning: passing argument 1 of &#8216;device_remove_file&#8217; from incompatible pointer type
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:2786: warning: passing argument 1 of &#8216;device_remove_file&#8217; from incompatible pointer type
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:2788: warning: passing argument 1 of &#8216;device_remove_file&#8217; from incompatible pointer type
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_probe&#8217;:
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:4315: error: incompatible types in assignment
make[2]: *** [/home/jumbalaya/sources/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/jumbalaya/sources/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [default] Error 2


i'm using kubuntu 8.04, kernel 2.6.24-21-generic, gspcav1-20071224 patched drivers

---

### Post by luddite666 on 2008-11-18
> **lamer1 said:**
> Hi everybody,

This question has been asked couple of times on the forums:

[http://ubuntuforums.org/showthread.php?t=952718](http://ubuntuforums.org/showthread.php?t=952718)

I was having the same problem and I starting browsing through the code investigating the compile errors one by one. I managed to fix the compile problem and managed to compile and load the gspca driver.
It seems that there are some interface incompatibilities between the gspcav1-20071224 driver and the current kernel.
Just to let you know that I have no knowledge of the v4l and how it works. All I did is just found the incompatible parts of the gspca code and updated them to comply with the new changes from the kernel. 
After some time I managed to fix all compile errors and compiled the driver.
Perhaps someone with better gspca+v4l knowledge can make use of this...

In case there is anyone out there that needs to compile the driver I am attaching a patch for gspcav1-20071224 (note the patch contains QuickCam E2500 from [http://forums.quickcamteam.net/showthread.php?tid=310](http://forums.quickcamteam.net/showthread.php?tid=310)).

I own an E2500 cam and it does not seem to work properly. Most of the time the picture is dark (I don't know how to change the settings, anyone knows?). Sometimes I can see the video, but after I change settings using gqcam the picture goes dark again.

Hope this helps,

Thanks so much for the post. I used your patch with the details here(see sweepers comment which uses your patch) here [http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype) and now it works beautifully in skype.

Cheers and appreciated very much so.
luddite

---

### Post by nagolchi on 2008-11-19
> **Jumbalaspi said:**
> i cannot compile, it gives me some errors:



make -C /lib/modules/`uname -r`/build SUBDIRS=/home/jumbalaya/sources/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /home/jumbalaya/sources/gspcav1-20071224/gspca_core.o
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:54:29: error: linux/semaphore.h: No such file or directory
In file included from /home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:64:
/home/jumbalaya/sources/gspcav1-20071224/gspca.h:17:30: error: media/v4l2-ioctl.h: No such file or directory
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:2615: error: unknown field &#8216;vfl_type&#8217; specified in initializer
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c: In function &#8216;spca50x_create_sysfs&#8217;:
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:2773: warning: passing argument 1 of &#8216;device_create_file&#8217; from incompatible pointer type
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:2776: warning: passing argument 1 of &#8216;device_create_file&#8217; from incompatible pointer type
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:2779: warning: passing argument 1 of &#8216;device_create_file&#8217; from incompatible pointer type
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:2784: warning: passing argument 1 of &#8216;device_remove_file&#8217; from incompatible pointer type
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:2786: warning: passing argument 1 of &#8216;device_remove_file&#8217; from incompatible pointer type
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:2788: warning: passing argument 1 of &#8216;device_remove_file&#8217; from incompatible pointer type
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_probe&#8217;:
/home/jumbalaya/sources/gspcav1-20071224/gspca_core.c:4315: error: incompatible types in assignment
make[2]: *** [/home/jumbalaya/sources/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/jumbalaya/sources/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [default] Error 2


i'm using kubuntu 8.04, kernel 2.6.24-21-generic, gspcav1-20071224 patched drivers
jumbala - you're trying to compile for the older kernel.  this thread is for people who are using the most recent kernel in 8.10.  Try following the instructions listed here:
[http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/)

---

### Post by Ictinike on 2008-11-19
Not working for me. I'm getting errors across the board. Using fully updated Ubuntu 8.10

---

### Post by yauhen on 2008-11-29
I got my Logitech E2500 to work in cheese and skype on Intrepid (Xubuntu).
The best way is to :
A) install skype from medibuntu depositories

B)And follow the code I got  from here [http://admiral0.wordpress.com/2008/11/03/logitech-e2500-su-kubuntu-intrepid/](http://admiral0.wordpress.com/2008/11/03/logitech-e2500-su-kubuntu-intrepid/)

cd ~
mkdir webcam_driver
cd webcam_driver
mkdir v4l
cd v4l

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

cd v4l-dvb

cp /boot/config-`uname -r` v4l/.config



gedit linux/drivers/media/video/gspca/zc3xx.c

              #Insert the following line around 7587 and save the file
{USB_DEVICE(0x046d, 0x089d), .driver_info = SENSOR_MC501CB},


make

sudo make install
------------------------------------------------------------------------

That's it! Reboot and see if cheese works. If it doesn't work, try

sudo modprobe gspca_zc3xx



Works great in cheese with 640x480 resolution, but a little bit dark with 320x240. It's also a bit dark in skype.
Playing around with "options gspca gamma=1 autoexpo=0" doesn't do anything.
Anybody has any idea how to make it lighter in skype?

---

### Post by Matt Savage on 2009-01-09
> **yauhen said:**
> I got my Logitech E2500 to work in cheese and skype on Intrepid (Xubuntu).

gedit linux/drivers/media/video/gspca/zc3xx.c

              #Insert the following line around 7587 and save the file
{USB_DEVICE(0x046d, 0x089d), .driver_info = SENSOR_MC501CB},


make

sudo make install
------------------------------------------------------------------------

That's it! Reboot and see if cheese works. If it doesn't work, try

sudo modprobe gspca_zc3xx
?

Not having any joy with this :( 

My problems started with inserting the line around 7587 as this didn't look like the right place so I added it to the bottom of the list of other similar lines just above it.

Then when I did the "make" bit I would get some error messages (I forgot to copy them down but they were something like "unknown symbol")

I carried on anyway and rebooted but camorama gave me a dev/video01 error and Cheese can't find the camera.

So trying the modprobe bit I get this

FATAL: Error inserting gspca_zc3xx (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/gspca/gspca_zc3xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)

and the dmesg gives this (and lots more)...

[   19.239577] Linux video capture interface: v2.00                                     
[   19.294471] gspca: disagrees about version of symbol video_devdata                   
[   19.294482] gspca: Unknown symbol video_devdata                                      
[   19.295126] gspca: disagrees about version of symbol video_unregister_device         
[   19.295130] gspca: Unknown symbol video_unregister_device                            
[   19.295360] gspca: disagrees about version of symbol video_device_alloc              
[   19.295364] gspca: Unknown symbol video_device_alloc                                 
[   19.295457] gspca: disagrees about version of symbol video_register_device           
[   19.295461] gspca: Unknown symbol video_register_device                              
[   19.295903] gspca: disagrees about version of symbol video_usercopy                  
[   19.295907] gspca: Unknown symbol video_usercopy                                     
[   19.296012] gspca: disagrees about version of symbol video_device_release            
[   19.296016] gspca: Unknown symbol video_device_release                               
[   19.303839] gspca: disagrees about version of symbol video_devdata                   
[   19.303848] gspca: Unknown symbol video_devdata                                      

and so on.

I am really at a loss and out of my depth here. Frustratingly it worked OK before on Heron.

Any help greatly appreciated (or suggestion of a webcam that works out-of-the-box with 8.10)

Thanks Matt

---

### Post by sangandongo on 2009-01-09
Using the patch provided at the beginning of this thread I was able to get the gspca.ko module to compile. I installed it and it appeared to load properly. dmesg showed good info, etc. etc.

I tested the camera with camE, camorama, Ekiga, Skype and none seem to like it. BUT, I tested with Youtube and Youtube was able to capture video from it just fine. 

Any thoughts? I know I've not said much, but I can't see why the Adobe plugin on Youtube would be able to see video through the camera and no native apps would. 

--
j.k

---

### Post by martin.malos@gmail.com on 2009-01-18
Unfortunatelly, this still does not work for me with Ubuntu 8.10 64bit kernel 2.6.27-9-generic :(

It works ok with older kernel 2.6.24x where I was able to patch and compile the gspca driver, but unfortunatelly I can not make my nvidia card work with that.


I could compile the patched driver, but modprobe:

sudo modprobe gspca

FATAL: Error inserting gspca (/lib/modules/2.6.27-9-generic/kernel/drivers/usb/media/gspca.ko): Unknown symbol in module, or unknown parameter (see dmesg)

dmesg:

~/gspcav1-20071224$ dmesg | grep gspca

[15621.457128] gspca: disagrees about version of symbol video_devdata
[15621.457139] gspca: Unknown symbol video_devdata
[15621.457520] gspca: disagrees about version of symbol video_unregister_device
[15621.457522] gspca: Unknown symbol video_unregister_device
[15621.457666] gspca: disagrees about version of symbol video_device_alloc
[15621.457668] gspca: Unknown symbol video_device_alloc
[15621.457725] gspca: disagrees about version of symbol video_register_device
[15621.457726] gspca: Unknown symbol video_register_device
[15621.457993] gspca: disagrees about version of symbol video_usercopy
[15621.457994] gspca: Unknown symbol video_usercopy
[15621.458050] gspca: disagrees about version of symbol video_device_release
[15621.458052] gspca: Unknown symbol video_device_release

and so no progress in lsusb:

~/gspcav1-20071224$ lsusb

Bus 001 Device 008: ID 046d:089d Logitech, Inc.

Anyone made it work with this linux kernel? 

Thanks for help!

---

### Post by acoaco2 on 2009-01-28
Hello everybody! I followed all your tips and I finally was able to compile the module but webcam is still not working.
I have a Intel Create & Share with CS330 chipset.

Is the patch good for that also?

---

### Post by martin.malos@gmail.com on 2009-02-02
Resolved with the new kernel release 2.6.27-11-generic
Now the driver can be compiled without errors and installed
E2500 works for me fine with patched gspca on Ubuntu 8.10 64bit now.

---

### Post by mªrty on 2009-02-24
I agree with martin.malos above me - It compiled and everything. DMESG shows that gspca driver 01.00.20 registered, however when I plug in camera no program seems to recognize that a camera has been connected. any ideas?

EDIT: got it to work, just needed to "sudo modprobe -r gspca" then "sudo modprobe gspca" once or twice. ps my camera is an Intel CS630.

---

### Post by wingnux on 2009-03-02
I'm sorry for the completely noob question but how can I use this patch? Thanks in advance.

---

### Post by cseberino on 2009-04-06
I got E2500 to work in Ubuntu Jaunty beta.

Message #14 (yauhen's) above was the life saver....

You don't need to add a line to the source code because the latest code you get with hg already has e2500 ready to go.

It did *not* work with camorama for me.....camorama complained about not being able to grab a picture or something....However, XawTV *did* work great!
 
cd ~
mkdir webcam_driver
cd webcam_driver
mkdir v4l
cd v4l

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

cd v4l-dvb

cp /boot/config-`uname -r` v4l/.config


make

sudo make install
------------------------------------------------------------------------

That's it! Reboot and see if cheese works. If it doesn't work, try

sudo modprobe gspca_zc3xx

---

### Post by rodrigoD666 on 2009-04-19
[QUOTE=yauhen;6273516]I got my Logitech E2500 to work in cheese and skype on Intrepid (Xubuntu).
The best way is to :
A) install skype from medibuntu depositories

B)And follow the code I got  from here [http://admiral0.wordpress.com/2008/11/03/logitech-e2500-su-kubuntu-intrepid/](http://admiral0.wordpress.com/2008/11/03/logitech-e2500-su-kubuntu-intrepid/)

cd ~
mkdir webcam_driver
cd webcam_driver
mkdir v4l
cd v4l

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

cd v4l-dvb

cp /boot/config-`uname -r` v4l/.config



gedit linux/drivers/media/video/gspca/zc3xx.c

              #Insert the following line around 7587 and save the file
{USB_DEVICE(0x046d, 0x089d), .driver_info = SENSOR_MC501CB},


----> Hey use line 7657!!! <----

---

### Post by anystupidname on 2009-07-02
I putzed around with it for a while and got the patch applied and driver compiled and loaded as far as I can tell but jaunty doesn't create /dev/video0 

I may be missing something obvious, could somebody offer some suggestions please?

[http://ubuntuforums.org/showthread.php?t=1201803](http://ubuntuforums.org/showthread.php?t=1201803)

---

### Post by nishanthmenon on 2009-10-17
For 9.10 based systems using 2.6.31 kernel ->
in addition to the patch here:
[http://ubuntuforums.org/attachment.php?attachmentid=90642&d=1225570823](http://ubuntuforums.org/attachment.php?attachmentid=90642&d=1225570823)

Apply the second patch as attached. it seems to build, but looks like my camera 0x041E, 0x4038 is not supported..

---

