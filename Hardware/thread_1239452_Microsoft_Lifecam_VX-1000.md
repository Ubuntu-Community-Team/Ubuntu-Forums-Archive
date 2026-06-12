---
title: "Microsoft Lifecam VX-1000"
date: 2009-08-13
forum: Hardware
---

### Post by Nate Shoffner on 2009-08-13
First off, I am sorry for posting this, but I have idea what else to do.  I have been looking around for days trying to find the answer.  I cannnot get my Microsoft Lifecam VX-1000 webcam working at all.  I am using Ubuntu Jaunty.  I have tried using Cheese, Skype, Camorama, you name it.  I've read this post [http://www.uluga.ubuntuforums.org/showthread.php?t=1034988](http://www.uluga.ubuntuforums.org/showthread.php?t=1034988) over and over again.  It stated that I should do the following:

```

# wget [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz)
# tar zxvf tip.tar.gz
# cd v4l... (whatever the newly created directory name is)
# make all
# sudo make install

edit /etc/modprobe.d/blacklist-custom and add:
blacklist sn9c102

# reboot                      

``````

sudo gstreamer-properties

```I've tried this but the only problem is that I can't find the blacklist-custom file for my life.  This is one of the few the things that is just keeping me from moving from Windows completely.  I would really appreciate it if somebody, anybody at all could help me with this.

---

### Post by Nate Shoffner on 2009-08-15
Bump.  Please, can anybody give me an idea as to what I should do?  I've tried everything.  How come some people are able to get it working.  I even just tried upgrading the kernel....still no luck.

---

### Post by Kemmerich on 2009-08-20
bumpity-bump

---

### Post by ichundu on 2009-08-20
some people have had success with vx-1000 and vx-3000 cams [here]("http://ubuntuforums.org/showthread.php?t=885795").
hope it works for you too

---

### Post by Richardarkless on 2009-08-30
Hey all just to tell you, I installed the latest kernel and amazingly enough my lifecam vx1000 worked after I rebooted (except the mic)

this is the website

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I installed v2.6.30.5

before I installed the kernel I tried this 

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) 

and all that come up what a static image where all there was, was just a green image so I dunno if you need to install the drivers before as well to get it to work

oh and my belkin fd5070 wireless (wireless g USB adaptor) has improved greatly from random slow downs to it working constantly

gonna try my netgear wg111v3 next because it would cut off after connecting to a WPA connection, will let you guys know soon

EDIT WOOP it worked but half the speed of my belkin though so not amazing but hey better than nothing

I love kernel updates :D

---

### Post by jesterthejedi on 2009-09-13
I have this cam. It took me a long time, 6 months to get the right driver up and working. Here is what I recommend:

Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file - located on the left bar
extract and change directory
in terminal type "make" no quotes, takes a few mins
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue Hardy mess.
not working in Camorama, Camstream, errors in gqcam

installed xawtv, luvcview, and removed camserv.

UPDATE! if you have errors on the MAKE step, you can use "make distclean" "make clean" then "make menuconfig" and deselect the other drivers included, I had errors trying this on my upgrade to karmic alpha 4 & 5. After the last step run a normal "make" and "sudo make install"

---

### Post by roussain on 2009-09-27
This sounds like a good solution.  Just want to confirm that a new kernel isn't required for this solution, correct?  I am a Ubuntu newbie and don't want to try something I can't undo or support...thanks for your help... 

I have the Microsoft VX-1000 webcam...trying to enable video calls in Skype.

David

---

### Post by jesterthejedi on 2009-09-29
> **roussain said:**
> This sounds like a good solution.  Just want to confirm that a new kernel isn't required for this solution, correct?  I am a Ubuntu newbie and don't want to try something I can't undo or support...thanks for your help... 

I have the Microsoft VX-1000 webcam...trying to enable video calls in Skype.

David

Rebuilding the kernel takes 2+ hours, installing from source 5 minutes, your choice.

---

### Post by stanca on 2009-10-07
With the newest kernel updates for 9.04 my webcam works again too,with this command:
```
sudo apt-get install subversion build-essential linux-headers-$(uname -r) && wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 && tar xf tip.tar.bz2 && cd gspca-* && make && sudo make install && sudo depmod -ae $(uname -r)
```.:P

---

### Post by kyleabaker on 2009-10-27
> **jesterthejedi said:**
> I have this cam. It took me a long time, 6 months to get the right driver up and working. Here is what I recommend:

Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file - located on the left bar
extract and change directory
in terminal type "make" no quotes, takes a few mins
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue Hardy mess.
not working in Camorama, Camstream, errors in gqcam

installed xawtv, luvcview, and removed camserv.

UPDATE! if you have errors on the MAKE step, you can use "make distclean" "make clean" then "make menuconfig" and deselect the other drivers included, I had errors trying this on my upgrade to karmic alpha 4 & 5. After the last step run a normal "make" and "sudo make install"

Has this been tested in Ubuntu 9.10 (Karmic) 64-bit? I'm trying to get my LifeCam VX-1000 working in Karmic 64-bit with no luck.

I was hoping to get the preload trick to work since most other people seem to be having luck with that (Jaunty users mostly it seems), but I've not had any luck with v4l1/v4l2 in the lib/lib32/lib64 folders. I've tried all of the combinations to make sure. Including gstreamer-properties set to v4l/v4l2 both ways.

So, anyone know if this GSPCA install is working (mic and video) in Karmic 64-bit? Thanks.

---

### Post by stanca on 2009-11-07
I tried and no.

---

### Post by kyleabaker on 2009-11-17
I've been trying to get the Microsoft Lifecam VX-1000 webcam working in Ubuntu 9.10 x86_64 for weeks with no luck. Does anyone have any suggestions at all? I'm tired of booting into Windows to video chat in Skype.

---

### Post by kyleabaker on 2010-07-12
I've posted a patch to fix the Microsoft LifeCam VX-1000 where the microphone stops working or doesn't work at all.

Please test this patch and let me know if it fixes your webcam. It may also fix the Microsoft VX-3000 if it is having mic problems where the microphone stops working.

All the details are here:
[http://ubuntuforums.org/showthread.php?p=9581593#post9581593]("http://ubuntuforums.org/showthread.php?p=9581593#post9581593")

---

### Post by RavAngell on 2011-02-12
Hello, guys.
I've this "amazing camera" - lifecam vx-1000 under ubuntu 10.10 x64 (russian). 
So I've installed skype. The sound and build-in microphone on camera is working (when calling to skype bot - I hear myself). But when I turning on video - the voice dies down. So, after googling the internet, i found some solving of this problem.
So I do:
mkdir tmp
cd /tmp
wget [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)
tar xvfj tip.tar.bz2
cd v4l*
make all

And an error appear:
make all
```

make -C /home/kevin/tmp/v4l-dvb-abd3aac6644e/v4l all
make[1]: Entering directory `/home/kevin/tmp/v4l-dvb-abd3aac6644e/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/kevin/tmp/v4l-dvb-abd3aac6644e/v4l/firmware'
make[2]: Leaving directory `/home/kevin/tmp/v4l-dvb-abd3aac6644e/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/kevin/tmp/v4l-dvb-abd3aac6644e/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/kevin/tmp/v4l-dvb-abd3aac6644e/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-25-generic/build
make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/kevin/tmp/v4l-dvb-abd3aac6644e/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  Building modules, stage 2.
  MODPOST 417 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
./scripts/rmmod.pl check
found 417 modules
make[1]: Leaving directory `/home/kevin/tmp/v4l-dvb-abd3aac6644e/v4l'

```

What I do wrong? linux-headers installed.

---

### Post by kyleabaker on 2011-02-12
> **RavAngell said:**
> Hello, guys.
I've this "amazing camera" - lifecam vx-1000 under ubuntu 10.10 x64 (russian). 
So I've installed skype. The sound and build-in microphone on camera is working (when calling to skype bot - I hear myself). But when I turning on video - the voice dies down. So, after googling the internet, i found some solving of this problem.
So I do:
mkdir tmp
cd /tmp
wget [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)
tar xvfj tip.tar.bz2
cd v4l*
make all

And an error appear:
make all
```

make -C /home/kevin/tmp/v4l-dvb-abd3aac6644e/v4l all
make[1]: &#1042;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; `/home/kevin/tmp/v4l-dvb-abd3aac6644e/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/kevin/tmp/v4l-dvb-abd3aac6644e/v4l/firmware'
make[2]: Leaving directory `/home/kevin/tmp/v4l-dvb-abd3aac6644e/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/kevin/tmp/v4l-dvb-abd3aac6644e/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/kevin/tmp/v4l-dvb-abd3aac6644e/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-25-generic/build
make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/kevin/tmp/v4l-dvb-abd3aac6644e/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  Building modules, stage 2.
  MODPOST 417 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
./scripts/rmmod.pl check
found 417 modules
make[1]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/home/kevin/tmp/v4l-dvb-abd3aac6644e/v4l'

```

What I do wrong?

If you read my post right above yours then you would see that I wrote a patch to fix this a while back. You can find instructions how to fix this here:

[http://ubuntuforums.org/showthread.php?t=1516541&page=3&p=9643477](http://ubuntuforums.org/showthread.php?t=1516541&page=3&p=9643477)

Cheers :D

---

### Post by RavAngell on 2011-02-12
> **kyleabaker said:**
> If you read my post right above yours then you would see that I wrote a patch to fix this a while back. You can find instructions how to fix this here:

[http://ubuntuforums.org/showthread.php?t=1516541&page=3&p=9643477](http://ubuntuforums.org/showthread.php?t=1516541&page=3&p=9643477)

Cheers :D

So, we have:

1. Download my patched GSPCA: gspca-2.9.51-vx1000-patch-20100712.zip
2. Extract the zip file on your Desktop (so you have the folder &#8220;gspca-2.9.51-vx1000-patch-20100712&#8243;).
3. Open a terminal window and enter the following commands:
cd Desktop/gspca-2.9.51-vx1000-patch-20100712/
make

Error [?]: 

```
 
make -C /lib/modules/2.6.35-25-generic/build M=/home/kevin/tmp/1/build modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
........................................................
 CC      /home/kevin/tmp/1/build/gspca_vc032x.mod.o
  LD [M]  /home/kevin/tmp/1/build/gspca_vc032x.ko
  CC      /home/kevin/tmp/1/build/gspca_zc3xx.mod.o
  LD [M]  /home/kevin/tmp/1/build/gspca_zc3xx.ko
make[1]: Leaving directory`/usr/src/linux-headers-2.6.35-25-generic'
```

When I try to start skype:
```
 
kevin@kevin:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```

---

