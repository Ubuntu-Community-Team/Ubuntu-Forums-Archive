---
title: "[SOLVED] A window Fan Said my webcam cant work.. help me proof him wrong"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by bigbrovar on 2007-12-27
Thanks for coming to my aid.. ever since i got my lappy i have never been able to get my webcam to work.. now in an arguement  Ubuntu vs Vista .. a window fan dissed me saying that webcams dont work on linux and i would never get to use a webcam on my system.. please i need help to proof him wrong...

---

### Post by bigbrovar on 2007-12-27
when i tried using this driver [http://avilella.googlepages.com/r5u870-0.10.0.tgz](http://avilella.googlepages.com/r5u870-0.10.0.tgz)  i got an error  [PHP]/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1241: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1241: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1241: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1241: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1242: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1242: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1242: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1242: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1243: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1243: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1244: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1244: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
make[2]: *** [/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.o] Error 1
make[1]: *** [_module_/home/bigbrovar/Desktop/r5u870-0.10.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2
root@bigbrovar-laptop:/home/bigbrovar/Desktop/r5u870-0.10.0#[/PHP] 
   pls what can i do

---

### Post by bigbrovar on 2007-12-27
Finally I got it to work  ... MEHN AM I SO HAPPY ......... YEEEEEEEEEEEEEEEEEEEEEEEEEY I FINALLY GOT MY WEBCAM TO WORK .. U CANT BELIEVE IT .. APPREARANTLY THE PROBLEM WAS CAUSED BY THIS > "
I have my webcam (05ca:183a) working on the Sony Vaio SZ650 by using this patched version of the r5u870 source:
[http://ubuntuforums.org/attachment.p...0&d=1191746623](http://ubuntuforums.org/attachment.p...0&d=1191746623)

untar, make, sudo makeinstall, reboot.

However, this only works up to kernel 2.6.22 (Gutsy). Compilation fails on kernel 2.6.24 (Hardy) because the linux headers have changed name:

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-2-generic'
CC [M] /home/michael/drivers/r5u870-0.10.0-tz17/r5u870_md.o
In file included from /home/michael/drivers/r5u870-0.10.0-tz17/r5u870_md.c:55:
/home/michael/drivers/r5u870-0.10.0-tz17/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/michael/drivers/r5u870-0.10.0-tz17/r5u870_md.o] Error 1
make[1]: *** [_module_/home/michael/drivers/r5u870-0.10.0-tz17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-2-generic'
make: *** [all] Error 2
__________________"

---

### Post by bigbrovar on 2007-12-27
I Just Downgraded My Kernel And I Parched The Driver And Whala ... Linux Rules... I Cant Never Leave Ubuntu For Anything .. Not Even If I Need To Start Paying For It

---

