---
title: "Bison web cam working on ubuntu 8.10"
date: 2008-12-31
forum: Hardware
---

### Post by dadozgb on 2008-12-31
This is a short how-to configure a bison web cam on ubuntu intrepid (8.10). Before you begin check this short faq on [http://m560x-driver.wiki.sourceforge.net/m5602-FAQ](http://m560x-driver.wiki.sourceforge.net/m5602-FAQ). I have a msi ex700 with a bison web cam build in. There is a project which aim is to create ali 5620 and 5630 web cam drivers on  [http://m560x-driver.sourceforge.net/](http://m560x-driver.sourceforge.net/) . To download and compile driver one must have some programs installed like gcc, subversion and probably kernel headers of running kernel.
To download driver you have to open terminal and 
cd /usr/src
sudo svn co [https://m560x-driver.svn.sourceforge.net/svnroot/m560x-driver](https://m560x-driver.svn.sourceforge.net/svnroot/m560x-driver) m560x-driver 
When download complete you will have directory m560x-driver. Then you have to go to branches subdirectory and compile a module. Which module is right for you is hard to write in this document, but check for the branches file to give you a hint, so one will probably have to experiment a bit. For my msi ex700 the right module is in m5602-s5k4aa subdirectory. We compile module as sudo make, sudo make install. As I compiled modules I copied two files, C10H0121.bin and M1000CVd.inf,  found in firmware subdirectory to /lib/firmware/your_running_kernel (mine 2.6-27-9-generic). The only thing left to do is to turn my web camera on and launch cheese. And thing is working. I wrote this short post in hope it will be useful to others who had similar problems. But in my short experience with this driver, it works, but obviously the work on it isn't done yet. My laptop frozed on changing picture resolution and a picture is a bit dark. But I'm sure things will be much better. D

---

### Post by LINUX_ID10T on 2009-01-07
Thanks for this thread. It is the first one I found that could possible work for me. I downloaded the drivers, but I have a few questions though.

I found out that the version of the Bison webcam I have built into my laptop is a M5603c-mt9v011.

When I enter sudo mode and run make I get the following:

user@user-laptop:~$ cd /usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011

user@user-laptop:/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011$ make

make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011 modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'

  CC [M]  /usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.o

Assembler messages:

Fatal error: can't create /usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/.tmp_m5603c.o: Permission denied

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c: In function &#8216;usb_m5603c_probe&#8217;:

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c:209: error: &#8216;struct video_device&#8217; has no member named &#8216;owner&#8217;

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c:210: error: &#8216;struct video_device&#8217; has no member named &#8216;type&#8217;

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c:210: error: &#8216;VID_TYPE_CAPTURE&#8217; undeclared (first use in this function)

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c:210: error: (Each undeclared identifier is reported only once

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c:210: error: for each function it appears in.)

In file included from /usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c:287:

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c_v4l2.c: In function &#8216;v4l_m5603c_do_ioctl&#8217;:

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c_v4l2.c:700: warning: pointer targets in passing argument 1 of &#8216;strlcpy&#8217; differ in signedness

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c_v4l2.c:705: warning: pointer targets in passing argument 1 of &#8216;strlcpy&#8217; differ in signedness

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c_v4l2.c:707: warning: pointer targets in passing argument 2 of &#8216;usb_make_path&#8217; differ in signedness

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c_v4l2.c:708: warning: pointer targets in passing argument 1 of &#8216;strlcpy&#8217; differ in signedness

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c_v4l2.c:733: warning: pointer targets in passing argument 1 of &#8216;strcpy&#8217; differ in signedness

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c_v4l2.c:811: warning: pointer targets in passing argument 1 of &#8216;strlcpy&#8217; differ in signedness

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c: In function &#8216;__check_debug&#8217;:

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c:321: warning: pointer targets in return differ in signedness

make[2]: *** [/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.o] Error 2

make[1]: *** [_module_/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011] Error 2

make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'

make: *** [all] Error 2

user@user-laptop:/usr/mx560/m560x-driver/m560x/branchesuser@user-laptop:~$ cd /usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011

user@user-laptop:/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011$ make

make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011 modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'

  CC [M]  /usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.o

Assembler messages:

Fatal error: can't create /usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/.tmp_m5603c.o: Permission denied

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c: In function &#8216;usb_m5603c_probe&#8217;:

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c:209: error: &#8216;struct video_device&#8217; has no member named &#8216;owner&#8217;

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c:210: error: &#8216;struct video_device&#8217; has no member named &#8216;type&#8217;

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c:210: error: &#8216;VID_TYPE_CAPTURE&#8217; undeclared (first use in this function)

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c:210: error: (Each undeclared identifier is reported only once

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c:210: error: for each function it appears in.)

In file included from /usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c:287:

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c_v4l2.c: In function &#8216;v4l_m5603c_do_ioctl&#8217;:

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c_v4l2.c:700: warning: pointer targets in passing argument 1 of &#8216;strlcpy&#8217; differ in signedness

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c_v4l2.c:705: warning: pointer targets in passing argument 1 of &#8216;strlcpy&#8217; differ in signedness

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c_v4l2.c:707: warning: pointer targets in passing argument 2 of &#8216;usb_make_path&#8217; differ in signedness

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c_v4l2.c:708: warning: pointer targets in passing argument 1 of &#8216;strlcpy&#8217; differ in signedness

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c_v4l2.c:733: warning: pointer targets in passing argument 1 of &#8216;strcpy&#8217; differ in signedness

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c_v4l2.c:811: warning: pointer targets in passing argument 1 of &#8216;strlcpy&#8217; differ in signedness

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c: In function &#8216;__check_debug&#8217;:

/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.c:321: warning: pointer targets in return differ in signedness

make[2]: *** [/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011/m5603c.o] Error 2

make[1]: *** [_module_/usr/mx560/m560x-driver/m560x/branches/m5603c-mt9v011] Error 2

make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'

make: *** [all] Error 2


I honestly don't know how to compile software in linux. I think I have all the necessary software but could be wrong. Can you point me in the right direction? Not sure what I am doing, just trying to learn a new OS.

Thanks

A Linux_ID10T

---

### Post by dadozgb on 2009-01-07
No problem. You have to build it as root which means as sys admin 'cause this is an admin task. So you have to do it like sudo make, sudo make install. Anyway when I wrotte this I was really thrilled 'bout cam is finally working. There is a new version of the driver found here [http://m560x-driver.wiki.sourceforge.net/testing_m5602](http://m560x-driver.wiki.sourceforge.net/testing_m5602) and it should be much more stable than this one.There sholud be soon a far better howto on this web cam driver so if it doesn't work for you be a bit more patient.

---

### Post by sfleite on 2009-01-25
Thank you very much. =D>
Since I instaled my system I expect for this. I don't know nothing about the "Linux world", and because this I extract those bz2 to one folder and than "make" and "make install". I suspect this method is not a correct one. But work. My camera is running on Ekiga and Skype. :D
Quality is not very good. But enough for my calls.
Regards.
sfleite.

---

