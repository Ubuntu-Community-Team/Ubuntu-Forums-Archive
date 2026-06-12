---
title: "poor quality video with M$ VX-1000 webcam+GSPCA driver"
date: 2008-05-08
forum: Hardware
---

### Post by deepclutch on 2008-05-08
Hi,
I got a M$ lifecam VX-1000 webcamera. :( now it is detected and working with cheese,camorama etc applications using **[HIS]("http://mxhaard.free.fr/")** drivers(Thank you Man! :D ).

The Problem is with this module any of these apps shows very poor quality video,FPS is around 23-24 on camorama and on Gnome's cheese,it is dragging :( 

reg,pic quality,it is like B/W with a orange,green and blue colors flickering  :confused:

I tried adjusting camora for hue,bright,contrast etc but all in vain :( 

Tried,modprobbing as :
```
modprobe gspca gamma=4  
```
to hopefully correct gamma.but still video seems **garbled** and unclear!

So,Please share your ideas and Help me solve this!

Thank You!


*PS:In windows XP,this webcam works really good with average quality video @ res 640x480*

---

### Post by deepclutch on 2008-05-08
Hey people! :| I am feeling sorry after getting this M$haft thingy :cry:

---

### Post by deepclutch on 2008-05-09
Will there be any chances of having this **SN9C1xx PC camera controller** getting right drivers? :(

I am very poor in Mathematics,hence in coding also(But I am very interested!).else,I'd have tried my bit with the support for this cams :oops:

So,guys,do reply! :D

Thanks!

---

### Post by hantms on 2008-06-29
Same problem.. 

Guess I will be doing my Skype-calls in Windows. :/

---

### Post by Goklagie on 2008-10-03
Same here. The image is perfect for horror movies.:)

---

### Post by jesterthejedi on 2008-12-24
Working after 6 months of waiting and searching forums. My cam is the dreaded Microsoft VX-1000.

Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file
extract and change directory
in terminal type "make" no quotes take about 5 mins
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue Hardy mess.
not working in Camorama, Camstream, errors in gqcam

installed xawtv, luvcview, and removed camserv.

I am so happy that I should pinch myself. I bought this webcam in June for my birthday and it was always a pain in the butt to solve. Success at last!

---

### Post by e_labranche on 2009-02-07
Hi,

I tried doing what jesterthejedi just posted to my 8.04..and now I have more problems than before. My apps crash when trying to load it.

My question is " how to I remove the driver from http://linuxtv.org/hg/~jfrancois/gspca/" ????

I tried sudo make uninstall with no luck. I do I get my old "working" install and remove the gspca??

Any help appreciated.

thanks

---

### Post by jesterthejedi on 2009-02-09
The fix I posted was for Intrepid Ibex. It worked out of the box in Hardy Heron. To remove that driver just delete the folder its located in. Any other cam related files can be removed or reinstalled with Synaptic. I would recommend to you to just search for "web cam" and "cam and install and play around with those programs.

---

### Post by Cauda_Draconis on 2009-03-01
Jesterthejedi, I tried your instructions and got this output upon issuing the "make" command. I'm using Linux Mint 6, which is Intrepid-based...
```
user@computer ~/gspca-332a4d374f56 $ make
make -C /home/user/gspca-332a4d374f56/v4l 
make[1]: Entering directory `/home/user/gspca-332a4d374f56/v4l'
creating symbolic links...
Kernel build directory is /lib/modules/2.6.27-7-generic/build
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/user/gspca-332a4d374f56/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/user/gspca-332a4d374f56/v4l/tvmixer.o
/home/user/gspca-332a4d374f56/v4l/tvmixer.c: In function 'tvmixer_ioctl':
/home/user/gspca-332a4d374f56/v4l/tvmixer.c:78: error: storage size of 'va' isn't known
/home/user/gspca-332a4d374f56/v4l/tvmixer.c:114: error: 'VIDIOCGAUDIO' undeclared (first use in this function)
/home/user/gspca-332a4d374f56/v4l/tvmixer.c:114: error: (Each undeclared identifier is reported only once
/home/user/gspca-332a4d374f56/v4l/tvmixer.c:114: error: for each function it appears in.)
/home/user/gspca-332a4d374f56/v4l/tvmixer.c:129: error: 'VIDEO_AUDIO_BASS' undeclared (first use in this function)
/home/user/gspca-332a4d374f56/v4l/tvmixer.c:131: error: 'VIDEO_AUDIO_TREBLE' undeclared (first use in this function)
/home/user/gspca-332a4d374f56/v4l/tvmixer.c:142: error: 'VIDEO_AUDIO_MUTE' undeclared (first use in this function)
/home/user/gspca-332a4d374f56/v4l/tvmixer.c:143: error: 'VIDIOCSAUDIO' undeclared (first use in this function)
/home/user/gspca-332a4d374f56/v4l/tvmixer.c:147: warning: type defaults to 'int' in declaration of '_min1'
/home/user/gspca-332a4d374f56/v4l/tvmixer.c:149: warning: type defaults to 'int' in declaration of '_min1'
/home/user/gspca-332a4d374f56/v4l/tvmixer.c:149: warning: comparison of distinct pointer types lacks a cast
/home/user/gspca-332a4d374f56/v4l/tvmixer.c:78: warning: unused variable 'va'
/home/user/gspca-332a4d374f56/v4l/tvmixer.c: In function 'tvmixer_clients':
/home/user/gspca-332a4d374f56/v4l/tvmixer.c:254: error: storage size of 'va' isn't known
/home/user/gspca-332a4d374f56/v4l/tvmixer.c:286: error: 'VIDIOCGAUDIO' undeclared (first use in this function)
/home/user/gspca-332a4d374f56/v4l/tvmixer.c:288: error: 'VIDEO_AUDIO_VOLUME' undeclared (first use in this function)
/home/user/gspca-332a4d374f56/v4l/tvmixer.c:254: warning: unused variable 'va'
make[3]: *** [/home/user/gspca-332a4d374f56/v4l/tvmixer.o] Error 1
make[2]: *** [_module_/home/user/gspca-332a4d374f56/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/user/gspca-332a4d374f56/v4l'
make: *** [all] Error 2
```

Any suggestions?

---

### Post by jesterthejedi on 2009-03-03
Check synaptic and look to see if "make" and "build-essential" are installed. Also try to download a fresh copy of the bz2 link and extract with default options, ie right click choose extract here. Make does not require sudo to run. I'm thinking its either a bad archive or your system can't compile.

---

### Post by Cauda_Draconis on 2009-03-09
I do have Make and Build-Essential installed. I grabbed the latest archive (gspca-b1c4c263338f) in bz2 format, and extracted in the manner you suggested, and it still won't let me compile. If I try using ./configure, it says there's no such directory or file. 
```
make -C /home/user/downloads/gspca-b1c4c263338f/v4l 
make[1]: Entering directory `/home/user/downloads/gspca-b1c4c263338f/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.28
File not found: /lib/modules/2.6.28-8-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/user/downloads/gspca-b1c4c263338f/v4l'
make: *** [all] Error 2
```
It says it can't find the file ./configure. Is that part of the problem?

---

### Post by jesterthejedi on 2009-03-16
NOoooooooo! Don´t use ¨./configure¨

use ¨make¨

wait for it to work its stuff, then

¨sudo make install¨

sudo will ask to confirm your password. 

Also be sure you are in the main ¨gspca-b1c4c263338f¨ folder and not the sub folder ¨v4l¨

This must be done in a terminal and not the ALT +F2 run box. Make is a command to compile the source code into an actual program. The make install is to get it all copied over and installed properly. If you still have trouble it may be a good idea to check on the download site for help or an email to write to ask for help.

---

### Post by nostradamnit on 2009-03-20
The above steps worked for me. Now my VX-1000 works with Ekiga but not Skype :(

---

### Post by jesterthejedi on 2009-03-20
I do know that when your linux headers update you will have to reinstall this setup. As for why some programs cant do cam I have no clues. That would be up to the individual programs written to use v4l1 or v4l2.

---

### Post by biker3 on 2009-03-30
> **nostradamnit said:**
> The above steps worked for me. Now my VX-1000 works with Ekiga but not Skype :(

Skype doesn't work correctly for me also:(
I see it so when I try to tune in a channel at TV:confused:

---

### Post by october1917 on 2009-05-03
Has anybody try to use in Skype? Does it work?

Thank you in advance.

---

### Post by jesterthejedi on 2009-05-03
You have to use the LD=preload trick

in terminal type:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

search the forum for more examples and also how to create shortcuts/launchers for your use.

---

### Post by kyleabaker on 2010-07-12
I've posted a patch to fix the Microsoft LifeCam VX-1000 where the microphone stops working or doesn't work at all.

Please test this patch and let me know if it fixes your webcam. It may also fix the Microsoft VX-3000 if it is having mic problems where the microphone stops working.

All the details are here:
[http://ubuntuforums.org/showthread.php?p=9581593#post9581593]("http://ubuntuforums.org/showthread.php?p=9581593#post9581593")

---

