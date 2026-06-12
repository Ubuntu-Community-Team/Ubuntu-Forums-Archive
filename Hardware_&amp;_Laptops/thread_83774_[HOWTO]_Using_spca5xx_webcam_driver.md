---
title: "[HOWTO] Using spca5xx webcam driver"
date: 2005-10-29
forum: Hardware &amp; Laptops
---

### Post by mloskot on 2005-10-29
Hi,

4 weeks ago I reported that my Creative Notebook webcam does not work under Ubuntu with [spca5xx]("http://mxhaard.free.fr") drivers. Ubuntu freezed every time any application tried to access webcam. Here is my former thread - [Breezy hangs when using webcam]("http://www.ubuntuforums.org/showthread.php?t=70203")

The problem is solved.
Four days ago I got a message from Alvaro Arenas - big thanks - and he wrote step-by-step instructions how to use spca5xx drivers properly. It seems I used wrong, different than used to build Ubuntu kernel,  gcc version to build spca5xx. The kernel was build with gcc 3.4 but I used gcc 4.0.

Here is a screenshot presenting my webcam working with latest Ubuntu 5.10: [Finally, my webcam works with spca5xx drivers]("http://mateusz.loskot.net/gallery/ubuntu/spca5xx_1_1_1_works_on_ubuntu")

Alvaro asked me to forward his solution to Ubuntu Forums and because Breezy development forum is closed so I paste it here.

[QUOTE="Alvaro Arenas"]Hi
I had the same problem.
I installed the spca5xx module from [http://mxhaard.free.fr/spca50x/Download/spca5xx-20051001.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20051001.tar.gz)

you have to install the kernel headers 
aptitude install linux-headers-2.6.12-9-386

you have to delete the old spca5xx module
cd /lib/modules/2.6.12-9-386/kernel/drivers/usb/media
mv spca5xx spca5xx.bak

then you need the gcc version with which the kernel was compiled:
cat /proc/version
Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
gcc 3.4

aptitude install gcc-3.4
then untar and go to hte spca5xx directory
then

$ MAKEFLAGS="CC=gcc-3.4" make
$ make install
and at least you can re-do the modules list with:
depmod
depmod -ae

If you want to try the new module, be sure that you don't have loaded the old one with 
lsmod |grep spca5xx
if yes, you can do:
modprobe -r spca5xx

then plug you webcam and the module should be loaded automaticaly

I hope you could add this email to the forum thread. ([http://ubuntuforums.org/showthread.php?p=377397](http://ubuntuforums.org/showthread.php?p=377397)) I tried but I could do it. As you see some things are easy for some people and other not  :)[/QUOTE]

:KS BTW, is there any chance to include spca5xx + spcaview to Ubuntu repositories?

Best regards

---

### Post by dro0g on 2005-10-31
I just gave this a shot with an Intel CS110. The module appears to load correctly if I look at dmesg or lsmod after pluggin in the camera. However as soon as I bring up any application which accesses the camera (xawtv, gnomeMeeting) the computer still hangs. 

:(

---

### Post by mloskot on 2005-10-31
Are you sure you use same gcc versions?
If you are, sorry I can not help you in this case. I have no idea what is going wrong  ;-((

Cheers

---

### Post by tseliot on 2005-11-04
[QUOTE=dro0g]I just gave this a shot with an Intel CS110. The module appears to load correctly if I look at dmesg or lsmod after pluggin in the camera. However as soon as I bring up any application which accesses the camera (xawtv, gnomeMeeting) the computer still hangs. 

:([/QUOTE]
Try this:

[http://www.ubuntuforums.org/showthread.php?t=75284&highlight=webcam]("http://www.ubuntuforums.org/showthread.php?t=75284&highlight=webcam")

---

### Post by bennett on 2006-08-24
Thank you so much to Alvaro Arenas & to YOU mloskot for posting this!!!! Really, I have been trying to get my logitech notebook deluxe working with my Dell Inspiron 1300 for about 4 months (off & on) & finally you have posted some clear instructions that finally worked. I loaded the driver (sudo modprobe spca5xx) & the system seemed to hang a bit but when I rebooted, the little green light came on my webcam. A very pretty sight!
Thanks again.

---

### Post by mloskot on 2006-08-25
> **bennett said:**
> Thank you so much to Alvaro Arenas & to YOU mloskot for posting this!!!!

You're welcome! I'm glad it was helpful for you.
Cheers

---

