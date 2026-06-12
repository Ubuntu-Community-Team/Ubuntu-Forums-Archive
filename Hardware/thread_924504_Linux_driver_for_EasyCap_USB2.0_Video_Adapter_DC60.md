---
title: "Linux driver for EasyCap USB2.0 Video Adapter DC60"
date: 2008-09-19
forum: Hardware
---

### Post by digitalfiz on 2008-09-19
Ok I am posting a new thread because this thread was archived here:

[http://ubuntuforums.org/showthread.php?t=662531](http://ubuntuforums.org/showthread.php?t=662531)

And the solutions provided didnt work for me. I;ve tried each method with no results. I will say the audio part of the capture device seems to be working just not the video part. Here is the part of the dmesg that shows the stk driver starting:

```

[  644.067462] stk11xx: Syntek USB2.0 webcam driver startup
[  644.067506] usbcore: registered new interface driver usb_stk11xx_driver
[  644.067510] stk11xx: v1.3.1 : Syntek USB Video Camera

```

and here is the results from lsusb

```

Bus 002 Device 002: ID 046d:c043 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 059b:007e Iomega Corp. 
Bus 001 Device 003: ID 05e1:0408 Syntek Semiconductor Co., Ltd 
Bus 001 Device 001: ID 0000:0000

```

Like I said it seems like the audio part of the device is working just not the video. there is no /dev/video* at all and it seems programs like camorama look for cameras there. I am not a super ubuntu/linux guru so if I'm not providing something just ask I'll get it.

I am using ubuntu 8.04

---

### Post by digitalfiz on 2008-09-21
No body? I was hoping someone could give some help even if they didnt have the answer, maybe things I should try or places I should look anything really :(

---

### Post by nzjrs on 2008-09-29
> **digitalfiz said:**
> No body? I was hoping someone could give some help even if they didnt have the answer, maybe things I should try or places I should look anything really :(

I have one of these to, and I think we are screwed. The original guide at [http://doc.ubuntu-fr.org/em28xx_generique](http://doc.ubuntu-fr.org/em28xx_generique) indicated the EasyCap in that photo had an em2861 USB video bridge, however as the lsusb output and our experience has shown, EasyCAP devices with usb identifiers 05e1:0408 actually use the stk1160 usb bridge IC.

In both cases, the capture is handled by a SAA7113 video encoder chip. 

Now, the stk11xx driver is a webcam driver, and while being able to communicate with the stkxx bridge chips, on those webcams the image capture is handled by omnivision OVxxx sesors.

So AFAICT the em28xx-new driver has no chance of working because it does not include support for the stk1160, and the stk11xx driver has no chance of capturing video because it does not know anything about the SAA711X series of video capture devices.

A working driver would therefor need to use (I presume the communcation protocol for all stk11xx chips is similar) the usb setup routines from the stk11xx driver, and steal the SAA711x interface code from either em28xx, linux-uvc driver, or one of the other drivers that knows how to speak SAA711x

John

---

### Post by shanet on 2008-10-24
Yeah, the DC60 is the model we have, the DC60**+** (which is more expensive as it is advertised as having mac drivers) is the model that works with the above driver. It's a shame because these are very affordable and good for experimentation.

---

### Post by digitalfiz on 2008-10-25
shanet, are you confirming that the DC60+ works? I can't seem to find one in the US but they are on amazon.co.uk if it works ill be buying one because I need it.

---

### Post by digitalfiz on 2008-12-07
Still no luck and I am using ubuntu 8.10 :( Could anybody be arsed to login to my machine and work on it? I don't have much linux skills but I am a web developer maybe we can trade services?

---

### Post by Skerit on 2009-01-07
Well, if what nzjrs said is true, the only way to fix it is to create some kind of hybrid driver...

So I guess that means we should get a developper one, they're quite cheap on eBay :P

---

### Post by ivor on 2009-01-08
Just FYI - on this thread STK1160 support is being worked on and guinea pigs will be required soon! :)
[http://sourceforge.net/forum/forum.php?thread_id=2803299&forum_id=616182](http://sourceforge.net/forum/forum.php?thread_id=2803299&forum_id=616182)

---

### Post by johnaaronrose on 2009-03-13
Does the stk11xx 1.4 driver work for DC60+adapter?  If so, how do I obtain the v4l2-ioctl.h module since it does seem to be in Hardy's /lib>

---

### Post by johnaaronrose on 2009-03-16
I've tried Hugh Mulqueen's instructions in thread 662531 to get DC60+ working. I had to upgrade from Hardy to Intrepid to get stk11xx compiled without v4l2 problems. I differed from Hugh's instructions in that I followed stk11xx 1.4.0 README's instructions i.e. $ make -f Makefile.standalone clean and $ make -f Makefile.standalone (rather than sudo ./configure && make which gave problem). I used lsmod to check that stk11xx,videodev, v4l1_compat, em28xx, compat_ioctl32 all loaded OK. However, neither tvtime nor camorama show picture or give sound. xawtv & zapping both give black screen and have to Ctrl+Alt+Backspace & login in again.

---

### Post by johnaaronrose on 2009-05-15
Any news on DC60+ driver?

What make & model of video grabber have others used successfully for vhs tapes copying?

---

### Post by paraplegicpanda on 2009-06-06
Shameless bump because I would love to get this guy working... Borrowed it from a friend and since the USB port on my JVC hard drive video camera went out but the AV cable still works, so I want to be able to record straight to my laptop. Anybody having any luck with it?

---

### Post by sirjask on 2009-06-30
I installed the synteck driver on Ubuntu 8.10 but they works only with a single input, while I need o work with all the 4 inputs.

Using zone minder or example, if I switch on a new camera, the previous camera is automatically switched off...

The problem is that the drivers do not switch between the diffrent inputs...

Any suggestions?
Did someone solved this problem?

Thanks a lot.

JK

---

### Post by toineurlings on 2009-07-01
I also have a DC60 but ubuntu tells me nothing when I connect the device. Still nobody solved it?](*,)

---

### Post by toineurlings on 2009-07-01
I am not good at trying new things but I found this site: 
[http://www.torrentreactor.net/find/easycap-linux-driver](http://www.torrentreactor.net/find/easycap-linux-driver)
maybe someone can say how you manage to make it work with this.

---

### Post by toineurlings on 2009-07-01
I want to try the sollution given in the older topic but it won't do this stap:

sudo ./configure && make
(After this command the file stk11xx.ko is created in the stk11xx-1.3.1 folder)


it says:

toine@pc-onder:~$ cd '/home/toine/Bureaublad/stk11xx-2.1.0' sudo ./configure && make
make: *** Geen doelen.  Gestopt.
toine@pc-onder:~/Bureaublad/stk11xx-2.1.0$ sudo ./configure && make
[sudo] password for toine: 
sudo: ./configure: command not found
toine@pc-onder:~/Bureaublad/stk11xx-2.1.0$

---

### Post by cooper77z on 2009-07-19
toin, that website crashed my computer!

---

### Post by busman.guru on 2009-07-23
For me, the easycap USB2.0 works fine (kernel 2.6.23)... just use:

Syntex DC-1125 (1.4.0 not the last version)
[http://sourceforge.net/projects/syntekdriver/files/](http://sourceforge.net/projects/syntekdriver/files/)

Then apply two patch's:
(add support for the easycap, more specifically using lsusb: ID 05e1:0408 Syntek Semiconductor Co., Ltd)
[http://www.ivor.org/stk0408-1.patch](http://www.ivor.org/stk0408-1.patch)
(ntsc compability)
[http://www.bentrask.com/NTSC.diff](http://www.bentrask.com/NTSC.diff)

Then compile using the syntex instructions, if all goes normally you should create a kernel extension (.ko), to load it do:
sudo insmod kernelextension.ko

plug your camera and check dmesg, normally you camera is in /dev/vide0 or /dev/video1, I got 30fps, it doesn't work very nice with opencv but with mplayer the image is very nice...
enjoy!, Busman

---

### Post by johnaaronrose on 2009-07-23
Any luck anybode with DC60+?
lsusb shows:
Bus 001 Device 042: ID eb1a:2861 eMPIA Technology, Inc.

---

### Post by cooper77z on 2009-07-23
busman.guru, when I click on the very first download link my dl manager flashes and nothing happens. I can't even complete the first step. I am trying to decide whether to spend my money on a digital video camera that records to sd card or a stand alone dvd burner instead of fighting with easycap. I think I am going to unplug and permanently cap easycap.

---

### Post by url00 on 2009-08-04
> **busman.guru said:**
> For me, the easycap USB2.0 works fine (kernel 2.6.23)... just use:

Syntex DC-1125 (1.4.0 not the last version)
[http://sourceforge.net/projects/syntekdriver/files/](http://sourceforge.net/projects/syntekdriver/files/)

Then apply two patch's:
(add support for the easycap, more specifically using lsusb: ID 05e1:0408 Syntek Semiconductor Co., Ltd)
[http://www.ivor.org/stk0408-1.patch](http://www.ivor.org/stk0408-1.patch)
(ntsc compability)
[http://www.bentrask.com/NTSC.diff](http://www.bentrask.com/NTSC.diff)

Then compile using the syntex instructions, if all goes normally you should create a kernel extension (.ko), to load it do:
sudo insmod kernelextension.ko

plug your camera and check dmesg, normally you camera is in /dev/vide0 or /dev/video1, I got 30fps, it doesn't work very nice with opencv but with mplayer the image is very nice...
enjoy!, Busman

What file do I patch with the NTSC.diff file?

---

### Post by romeshj on 2009-09-25
I was having a real hard time trying to view video off a DC60 from a PC running Ubuntu 9.04 Desktop, and the post by Busman was extremely useful. Busman gives 2 patches that should be applied. My problem was that i applied only the patch at [http://www.ivor.org/stk0408-1.patch](http://www.ivor.org/stk0408-1.patch) 
and not the patch at [http://www.bentrask.com/NTSC.diff](http://www.bentrask.com/NTSC.diff)

After applying both patches i could view NTSC video  at 25 and 30 fps  without any problem with mplayer. really smooth!! Thanks, Busman.  

Environment used was as follows:
- the latest stk driver v2.2 obtained from 
-r 82 svn co https: / / syntekdriver.svn.sourceforge.net / svnroot / syntekdriver / trunk / driver syntekdriver
with the above two patches applied. 
- The video source used was a DVD player (NTSC format) - Composite video output.
- mplayer was invoked with following syntax:

mplayer tv:// -tv driver=v4l2:width=320:height=240:fps=25:outfmt=rgb24:device=/dev/video0

Only 640*480 resolution worked despite the resolution specified in the syntax. Also, when i tried to quit mplayer, the application got frozen. You can issue a "Ctrl-Z" followed by "exit" to exit the shell and re-launch mplayer.

I tried xawtv as well. It displays garbled screen with default invoke. Some websites mention that the xawtv output is de-interlaced with DC60. However, the application closes smoothly on user's command.

The audio capturing for DC 60, however, didnt seem to work under Windows XP or Ubuntu. There seems to be no audio support in the stk driver. 

url00, it seems the NTSC patch should be applied to the file "stk11xx-dev-0408.c".

Overall, great quality for a cheap capture device!!

---

### Post by bgiannes on 2009-09-28
i'd like to get my EasyCap working but i need a little more help.

[https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver](https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver) already has the patchs, i just need to add the ntsc stuff?

and thus to install just :-

make -f Makefile.standalone clean
make -f Makefile.standalone
modprobe videodev
sudo insmod stk11xx.ko or sudo insmod kernelextension.ko??

all as sudo??   (this doesn't work for me)

thank you...

---

### Post by esurfer11 on 2009-11-10
Hi romeshj
I followed your instructions to compile but received the following errors: my kernel is 2.6.28-15. any help is appreciated. thanks.


make -f Makefile.standalone
make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/home/lchan/easycap/syntekdriver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/lchan/easycap/syntekdriver/stk11xx-usb.o
  CC [M]  /home/lchan/easycap/syntekdriver/stk11xx-v4l.o
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c: In function ‘v4l_stk11xx_ioctl’:
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1744: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1744: warning: passing argument 2 of ‘video_usercopy’ makes pointer from integer without a cast
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1744: warning: passing argument 4 of ‘video_usercopy’ makes integer from pointer without a cast
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1744: error: too few arguments to function ‘video_usercopy’
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c: In function ‘v4l_stk11xx_register_video_device’:
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1768: warning: assignment from incompatible pointer type
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c: At top level:
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1810: error: variable ‘v4l_stk11xx_fops’ has initializer but incomplete type
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1811: error: unknown field ‘owner’ specified in initializer
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1811: warning: excess elements in struct initializer
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1811: warning: (near initialization for ‘v4l_stk11xx_fops’)
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1812: error: unknown field ‘open’ specified in initializer
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1812: warning: excess elements in struct initializer
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1812: warning: (near initialization for ‘v4l_stk11xx_fops’)
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1813: error: unknown field ‘release’ specified in initializer
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1813: warning: excess elements in struct initializer
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1813: warning: (near initialization for ‘v4l_stk11xx_fops’)
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1814: error: unknown field ‘read’ specified in initializer
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1814: warning: excess elements in struct initializer
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1814: warning: (near initialization for ‘v4l_stk11xx_fops’)
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1815: error: unknown field ‘poll’ specified in initializer
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1815: warning: excess elements in struct initializer
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1815: warning: (near initialization for ‘v4l_stk11xx_fops’)
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1816: error: unknown field ‘mmap’ specified in initializer
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1816: warning: excess elements in struct initializer
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1816: warning: (near initialization for ‘v4l_stk11xx_fops’)
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1817: error: unknown field ‘ioctl’ specified in initializer
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1817: warning: excess elements in struct initializer
/home/lchan/easycap/syntekdriver/stk11xx-v4l.c:1817: warning: (near initialization for ‘v4l_stk11xx_fops’)
make[2]: *** [/home/lchan/easycap/syntekdriver/stk11xx-v4l.o] Error 1
make[1]: *** [_module_/home/lchan/easycap/syntekdriver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'

---

### Post by bgiannes on 2009-11-11
i just upgrade to 9.10 and the system see the easycap correctly i havn't tryed recording anything, but it looks good.

EDIT: well it see's it as a device but it don't work.

---

### Post by SuperMau on 2009-11-12
Followed all instructions, it seems it compiles right but when I do the "sudo insmod stk11xx.ko I get the following error:

**insmod: error inserting 'stk11xx.ko': -1 Unknown symbol in module**

That happens with all versions of the driver, the dmesg relevant output is:

[ 4452.772560] stk11xx: disagrees about version of symbol video_devdata
[ 4452.772574] stk11xx: Unknown symbol video_devdata
[ 4452.774593] stk11xx: disagrees about version of symbol video_unregister_device
[ 4452.774602] stk11xx: Unknown symbol video_unregister_device
[ 4452.775278] stk11xx: disagrees about version of symbol video_device_alloc
[ 4452.775286] stk11xx: Unknown symbol video_device_alloc
[ 4452.775675] stk11xx: disagrees about version of symbol video_register_device
[ 4452.775683] stk11xx: Unknown symbol video_register_device
[ 4452.780282] stk11xx: disagrees about version of symbol video_device_release
[ 4452.780286] stk11xx: Unknown symbol video_device_release

Any ideas?

I am using karmic by the way!

---

### Post by P@ran0ic on 2009-11-13
[SuperMau]("http://ubuntuforums.org/member.php?u=135588"),
If you have installed v4l-dvb from mercurial sources, a problem is in bad Modules.symvers in kernel headers - it was described here:
[http://lists.berlios.de/pipermail/linux-uvc-devel/2008-February/003112.html](http://lists.berlios.de/pipermail/linux-uvc-devel/2008-February/003112.html)

Simply copy Module.symvers from compiled v4l-dvb to patched syntekdriver directory:
```
cp <path-to-v4l-dvb-sources>/v4l/Module.symvers .

```and then 
```
make
make install
```then
```
install -m 644 -c stk11xx.ko /lib/modules/`uname -r`/kernel/drivers/media/video/
/sbin/depmod -a
```you can force PAL tv standard adding norm=1 option (without it I can't get color image on PAL camera) and correct colours
```
echo 'options stk11xx norm=1 colour=24000' > /etc/modprobe.d/syntek.conf
```and reboot.
If v4l-dvb compilation is required for each new kernel, you have to make distclean before v4l-dvb compilation.

---

### Post by Skerit on 2009-11-15
I'm also getting the same compilation error as esurfer11:

```
root@barabas:/usr/local/src/syntekdriver/trunk/driver# make -f Makefile.standalone 
make -C /lib/modules/2.6.28-16-generic/build SUBDIRS=/usr/local/src/syntekdriver/trunk/driver modules
make[1]: Map '/usr/src/linux-headers-2.6.28-16-generic' wordt binnengegaan
  CC [M]  /usr/local/src/syntekdriver/trunk/driver/stk11xx-usb.o
  CC [M]  /usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.o
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c: In functie &#8216;v4l_stk11xx_ioctl&#8217;:
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1744: let op: passing argument 1 of &#8216;video_usercopy&#8217; from incompatible pointer type
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1744: let op: passing argument 2 of &#8216;video_usercopy&#8217; makes pointer from integer without a cast
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1744: let op: passing argument 4 of &#8216;video_usercopy&#8217; makes integer from pointer without a cast
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1744: fout: te weinig argumenten voor functie &#8216;video_usercopy&#8217;
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c: In functie &#8216;v4l_stk11xx_register_video_device&#8217;:
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1768: let op: assignment from incompatible pointer type
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c: Op bovenste niveau:
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1810: fout: variabele &#8216;v4l_stk11xx_fops&#8217; heeft beginwaarde, maar een onvolledig type
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1811: fout: unknown field &#8216;owner&#8217; specified in initializer
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1811: let op: overtollige elementen in beginwaarde van struct
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1811: let op: (near initialization for &#8216;v4l_stk11xx_fops&#8217;)
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1812: fout: unknown field &#8216;open&#8217; specified in initializer
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1812: let op: overtollige elementen in beginwaarde van struct
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1812: let op: (near initialization for &#8216;v4l_stk11xx_fops&#8217;)
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1813: fout: unknown field &#8216;release&#8217; specified in initializer
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1813: let op: overtollige elementen in beginwaarde van struct
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1813: let op: (near initialization for &#8216;v4l_stk11xx_fops&#8217;)
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1814: fout: unknown field &#8216;read&#8217; specified in initializer
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1814: let op: overtollige elementen in beginwaarde van struct
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1814: let op: (near initialization for &#8216;v4l_stk11xx_fops&#8217;)
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1815: fout: unknown field &#8216;poll&#8217; specified in initializer
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1815: let op: overtollige elementen in beginwaarde van struct
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1815: let op: (near initialization for &#8216;v4l_stk11xx_fops&#8217;)
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1816: fout: unknown field &#8216;mmap&#8217; specified in initializer
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1816: let op: overtollige elementen in beginwaarde van struct
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1816: let op: (near initialization for &#8216;v4l_stk11xx_fops&#8217;)
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1817: fout: unknown field &#8216;ioctl&#8217; specified in initializer
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1817: let op: overtollige elementen in beginwaarde van struct
/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.c:1817: let op: (near initialization for &#8216;v4l_stk11xx_fops&#8217;)
make[2]: *** [/usr/local/src/syntekdriver/trunk/driver/stk11xx-v4l.o] Fout 1
make[1]: *** [_module_/usr/local/src/syntekdriver/trunk/driver] Fout 2
make[1]: Map '/usr/src/linux-headers-2.6.28-16-generic' wordt verlaten
make: *** [driver] Fout 2

```

using gcc 4.3.3 on ubuntu 9.04 (kernel 2.6.28-16-generic)

---

### Post by Skerit on 2009-11-15
Double post

---

### Post by beyonlo on 2009-11-16
Hello,

I install ubuntu 9.10 and did just this:
# svn co [https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver](https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver) syntekdriver
# cd syntekdriver
# make -f Makefile.standalone clean
# make -f Makefile.standalone
# modprobe videodev
# insmod stk11xx.ko

All this above works fine, without error. The /dev/video0 was created with sucess after  insmod stk11xx.ko. Well, after I used xawtv to see image, image is show but image are wrong (wrong norm) because I'm using a NTSC camera. And xawtv option don't show  NTSC norm option. Just only show for me norm "webcam". I try mplayer too but not works too because NTSC is not recognized. 

How is possible to do for works in analogue NTSC camera?

Thank you!

---

### Post by beyonlo on 2009-11-17
Anyone?

---

### Post by spkm on 2009-12-05
Hi ! 
 I've managed to compile and install the stk11xx module and it is working almost fine, but the image is slightly cropped on top and right sides. 
 I'm initializing the drivers with norm=1 and fps=25 flags. 

 To get the image I'm using the following command : 

 ```
mplayer tv:// -tv driver=v4l2:width=640:height=480:fps=25:outfmt=rgb24:device=/dev/video0 
```I've tried different withs and heights, but nothing changed.... Any ideas ?





Edit: Nevermind, it was an aspect ratio problem. Everything is fine now :D

---

### Post by littlej on 2009-12-08
hy, i have a question, i managed to install the drivers they load ok, but it aint creating only /dev/video0 shouldnt be video0 - video3 ? or something like that cose it has 4 chanels? thanks

---

### Post by GolemdX on 2009-12-14
...or you can use GNOME System Monitor to kill the process.

The compiling seems to have gone well, but after installing I'm not sure what to do to display video.

---

### Post by beyonlo on 2009-12-17
Hello,

I install ubuntu 9.10 and did just this:
# svn co [https://syntekdriver.svn.sourceforge...r/trunk/driver]("https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver") syntekdriver
# cd syntekdriver
# make -f Makefile.standalone clean
# make -f Makefile.standalone
# modprobe videodev
# insmod stk11xx.ko

All this above works fine, without error. The /dev/video0 was created with sucess after insmod stk11xx.ko. Well, after I used xawtv to see image, image is show but image are wrong (wrong norm) because I'm using a NTSC camera. And xawtv option don't show NTSC norm option. Just only show for me norm "webcam". I try mplayer too but not works too because NTSC is not recognized. 

How is possible to do for works in analogue NTSC camera?

Thank you!

---

### Post by Robbyx on 2009-12-20
> **beyonlo said:**
> Hello,

I install ubuntu 9.10 and did just this:
# svn co [https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver](https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver) syntekdriver
# cd syntekdriver
# make -f Makefile.standalone clean
# make -f Makefile.standalone
# modprobe videodev
# insmod stk11xx.ko



Could you please indicate the new link because the one above is not working.

Robin

---

### Post by bgiannes on 2009-12-21
```
https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver/
```

the links is connect, but the post concatenated it

---

### Post by bgiannes on 2009-12-21
> **beyonlo said:**
> Hello,

I install ubuntu 9.10 and did just this:
# svn co [https://syntekdriver.svn.sourceforge...r/trunk/driver]("https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver") syntekdriver
# cd syntekdriver
# make -f Makefile.standalone clean
# make -f Makefile.standalone
# modprobe videodev
# insmod stk11xx.ko

All this above works fine, without error. The /dev/video0 was created with sucess after insmod stk11xx.ko. Well, after I used xawtv to see image, image is show but image are wrong (wrong norm) because I'm using a NTSC camera. And xawtv option don't show NTSC norm option. Just only show for me norm "webcam". I try mplayer too but not works too because NTSC is not recognized. 

How is possible to do for works in analogue NTSC camera?

Thank you!



in post #22 there are changes for NTSC (don't work for me)...
but maybe you can fix it?  

PS i have a another webcam on /dev/video0 , how should i deal with this?

---

### Post by VectorS on 2009-12-26
Dear all,

I have an EasyCap (DC60? composite video, and S-video), and am trying to get it to work on Mint Gloria, kernel 2.6.28-11-generic. 
I downloaded the drivers version 1.4.0, and applied the patch from igor.org. Didn't use the other patch as I need PAL input. 
The compilation (make -f Makefile.standalone) works, but complains that ctags needs another input string. Since the stk11xx.ko is created I decided to 'insmod' it anyway.
Compilation log:
```
 make -f Makefile.standalone 
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/victor/Drivers/stk11xx-1.4.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/victor/Drivers/stk11xx-1.4.0/stk11xx-usb.o
  CC [M]  /home/victor/Drivers/stk11xx-1.4.0/stk11xx-v4l.o
  CC [M]  /home/victor/Drivers/stk11xx-1.4.0/stk11xx-sysfs.o
  CC [M]  /home/victor/Drivers/stk11xx-1.4.0/stk11xx-dev.o
  CC [M]  /home/victor/Drivers/stk11xx-1.4.0/stk11xx-buf.o
  CC [M]  /home/victor/Drivers/stk11xx-1.4.0/stk11xx-bayer.o
  CC [M]  /home/victor/Drivers/stk11xx-1.4.0/stk11xx-dev-0408.o
/home/victor/Drivers/stk11xx-1.4.0/stk11xx-dev-0408.c: In function ‘stk11xx_copy_rgb’:
/home/victor/Drivers/stk11xx-1.4.0/stk11xx-dev-0408.c:1005: warning: ISO C90 forbids mixed declarations and code
/home/victor/Drivers/stk11xx-1.4.0/stk11xx-dev-0408.c: In function ‘stk11xx_copy_uvyv’:
/home/victor/Drivers/stk11xx-1.4.0/stk11xx-dev-0408.c:870: warning: ‘line2’ may be used uninitialized in this function
/home/victor/Drivers/stk11xx-1.4.0/stk11xx-dev-0408.c: In function ‘stk11xx_copy_rgb’:
/home/victor/Drivers/stk11xx-1.4.0/stk11xx-dev-0408.c:971: warning: ‘line2’ may be used uninitialized in this function
  CC [M]  /home/victor/Drivers/stk11xx-1.4.0/stk11xx-dev-a311.o
  CC [M]  /home/victor/Drivers/stk11xx-1.4.0/stk11xx-dev-a821.o
  CC [M]  /home/victor/Drivers/stk11xx-1.4.0/stk11xx-dev-6a31.o
  CC [M]  /home/victor/Drivers/stk11xx-1.4.0/stk11xx-dev-6a33.o
  CC [M]  /home/victor/Drivers/stk11xx-1.4.0/stk11xx-dev-6a51.o
  CC [M]  /home/victor/Drivers/stk11xx-1.4.0/stk11xx-dev-6a54.o
  CC [M]  /home/victor/Drivers/stk11xx-1.4.0/stk11xx-dev-6d51.o
  LD [M]  /home/victor/Drivers/stk11xx-1.4.0/stk11xx.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/victor/Drivers/stk11xx-1.4.0/stk11xx.mod.o
  LD [M]  /home/victor/Drivers/stk11xx-1.4.0/stk11xx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
ctags: no input files specified.
	Try `ctags --help' for a complete list of options.
make: *** [driver] Error 1

```
after modprobe videodev and insmod stk11xx.ko I insert my EasyCap. Log from dmesg:
```
[  427.852135] usb 2-2: new high speed USB device using ehci_hcd and address 4
[  427.985031] usb 2-2: configuration #1 chosen from 1 choice
[  427.985209] stk11xx: Probe function called with VendorID=05E1, ProductID=0408 and InterfaceNumber=0
[  427.985215] stk11xx: Syntek USB2.0 - STK-1160 based device found.
[  427.985220] stk11xx: Syntek AVStream USB2.0 Video Capture - Product ID 0x0408.
[  427.985226] stk11xx: Release: 0005
[  427.985230] stk11xx: Number of interfaces : 3
[  427.985851] stk11xx: Initialize USB2.0 Syntek Capture device
[  428.128945] stk11xx: SET FEATURE
[  428.128952] stk11xx: Syntek USB2.0 Capture device is ready
[  428.129071] stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0

```

When I try to play /dev/video0 (which is now created) I get error messages from either mplayer or vlc that they failed to open /dev/video0. 

Any suggestions?

---

### Post by Borg on 2009-12-27
> **beyonlo said:**
> 


# cd syntekdriver



when i use this command i get

```
syntekdriver: No such file or directory
```

---

### Post by nickcloy on 2010-01-03
> **busman.guru said:**
> For me, the easycap USB2.0 works fine (kernel 2.6.23)... just use:

Syntex DC-1125 (1.4.0 not the last version)
[http://sourceforge.net/projects/syntekdriver/files/](http://sourceforge.net/projects/syntekdriver/files/)

Then apply two patch's:
(add support for the easycap, more specifically using lsusb: ID 05e1:0408 Syntek Semiconductor Co., Ltd)
[http://www.ivor.org/stk0408-1.patch](http://www.ivor.org/stk0408-1.patch)


Im new to linux have have not needed to patch anything yet, what command do i use to apply this patch?

---

### Post by anewguy on 2010-01-05
OOOOPPPPSSSS - sorry I was copying things from here to post to a reply in another thread, but replied back here instead of the other thread!

Just ignore this!

---

### Post by adxvd on 2010-01-11
I tried this and after hours I finally seemed to compile it until the very last step...

$ sudo insmod stk11xx.ko
insmod: error inserting 'stk11xx.ko': -1 Unknown symbol in module

edit: ok so reinstalled without my v4l-dvb install this time and everything went fine. I could play my x360 through the yellow component in mplayer (but black and white..), but got a load of error messages in vlc (not correct frame size). 

Anyway, I want to play svideo, not component, but I can't figure out how to switch it to svideo...Anyone know?

---

### Post by dashxdr on 2010-01-14
I just received an easycap DC60 and have been trying to get it to work. Even under windows XP it only worked one time, and I could never repeat it. I'm 100% certain it is driver / software issues.

When I do lsusb -v under linux I get this:
```
Bus 003 Device 003: ID 05e1:0408 Syntek Semiconductor Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x05e1 Syntek Semiconductor Co., Ltd
  idProduct          0x0408 
  bcdDevice            0.05
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          182
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval              16
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              16
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0300  1x 768 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              16
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03fc  1x 1020 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0 
      iInterface             11 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength           38
        bInCollection           1
        baInterfaceNr( 0)       2
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Microphone
        bAssocTerminal          0
        bNrChannels             1
        wChannelConfig     0x0000
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               3
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 8
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                 3
        bSourceID               1
        bControlSize            1
        bmaControls( 0)      0x01
          Mute
        iFeature                0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface             11 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface             11 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           2
        bDelay                  1 frames
        wFormatTag              2 PCM8
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           1
        bBitResolution          8
        bSamFreqType            1 Discrete
        tSamFreq[ 0]         8000
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined

```Now I've been trying to get the latest svn syntek driver working, checked out with this command:

*svn co [https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver](https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver) syntekdriver*

I get tons of kernel error messages like these:

```

Jan 14 17:48:40 dash-desktop kernel: [  502.202552] usb 3-2: selecting invalid altsetting 5
Jan 14 17:48:41 dash-desktop kernel: [  502.946174] usb 3-2: selecting invalid altsetting 5
Jan 14 17:48:44 dash-desktop kernel: [  505.645826] usb 3-2: selecting invalid altsetting 5
Jan 14 17:48:45 dash-desktop kernel: [  506.389452] usb 3-2: selecting invalid altsetting 5
Jan 14 17:49:49 dash-desktop kernel: [  570.466867] usb 3-2: selecting invalid altsetting 5
Jan 14 17:49:49 dash-desktop kernel: [  571.210858] usb 3-2: selecting invalid altsetting 5
Jan 14 17:49:52 dash-desktop kernel: [  573.873864] usb 3-2: selecting invalid altsetting 5
Jan 14 17:49:53 dash-desktop kernel: [  574.617854] usb 3-2: selecting invalid altsetting 5
Jan 14 17:49:55 dash-desktop kernel: [  577.224863] usb 3-2: selecting invalid altsetting 5
Jan 14 17:49:56 dash-desktop kernel: [  577.968866] usb 3-2: selecting invalid altsetting 5

```In stk11xx-dev.c there is the function dev_stk11xx_camera_on which selects alternate interface '5':
 * In fact, we choose the alternate interface '5'.
    ret = usb_set_interface(udev, 0, 5);

According to the lsusb -v dump above for interface 0 there is no alternate setting '5'. The alternate settings only go up to 2 for interface 0. So this doesn't make sense.

Are there different versions of the hardware that share the same 05e1:0408 USB ID?

Here's a complete kernel dmesg output just now when I tried to insmod the stk11xx.ko module. See the submit_urb failures with EMSGSIZE. 

```

[ 2057.325830] stk11xx: Syntek USB2.0 webcam driver startup
[ 2057.325839] stk11xx: Copyright(c) 2006-2009 Nicolas VIVIEN
[ 2057.325878] stk11xx: Syntek USB2.0 - STK-1160 based device found.
[ 2057.325882] stk11xx: Syntek AVStream USB2.0 Video Capture - Product ID 0x0408.
[ 2057.325889] stk11xx: Release: 0005
[ 2057.325893] stk11xx: Number of interfaces : 3
[ 2057.325899] usb 3-2: selecting invalid altsetting 5
[ 2057.325903] stk11xx: usb_set_interface failed !
[ 2057.327744] stk11xx: Initialize USB2.0 Syntek Capture device
[ 2059.883731] stk11xx: Syntek USB2.0 Capture device is ready
[ 2059.883860] stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0
[ 2059.883923] usbcore: registered new interface driver usb_stk11xx_driver
[ 2059.883931] stk11xx: v2.2.0 : Syntek USB Video Camera
[ 2061.748736] usb 3-2: selecting invalid altsetting 5
[ 2061.748743] stk11xx: usb_set_interface failed !
[ 2062.505735] usb 3-2: selecting invalid altsetting 5
[ 2062.505742] stk11xx: usb_set_interface failed !
[ 2063.115753] stk11xx: isoc_init() submit_urb 0 failed with error -90
[ 2063.115761] stk11xx: EMSGSIZE
[ 2063.115766] stk11xx: isoc_init() submit_urb 1 failed with error -90
[ 2063.115770] stk11xx: EMSGSIZE
[ 2063.115774] stk11xx: isoc_init() submit_urb 2 failed with error -90
[ 2063.115777] stk11xx: EMSGSIZE
[ 2063.115781] stk11xx: isoc_init() submit_urb 3 failed with error -90
[ 2063.115784] stk11xx: EMSGSIZE
[ 2063.115788] stk11xx: isoc_init() submit_urb 4 failed with error -90
[ 2063.115791] stk11xx: EMSGSIZE
[ 2063.115794] stk11xx: isoc_init() submit_urb 5 failed with error -90
[ 2063.115798] stk11xx: EMSGSIZE
[ 2063.115801] stk11xx: isoc_init() submit_urb 6 failed with error -90
[ 2063.115804] stk11xx: EMSGSIZE
[ 2063.115808] stk11xx: isoc_init() submit_urb 7 failed with error -90
[ 2063.115812] stk11xx: EMSGSIZE
[ 2063.115815] stk11xx: isoc_init() submit_urb 8 failed with error -90
[ 2063.115818] stk11xx: EMSGSIZE
[ 2063.115822] stk11xx: isoc_init() submit_urb 9 failed with error -90
[ 2063.115825] stk11xx: EMSGSIZE
[ 2063.115829] stk11xx: isoc_init() submit_urb 10 failed with error -90
[ 2063.115832] stk11xx: EMSGSIZE
[ 2063.115836] stk11xx: isoc_init() submit_urb 11 failed with error -90
[ 2063.115840] stk11xx: EMSGSIZE
[ 2063.115843] stk11xx: isoc_init() submit_urb 12 failed with error -90
[ 2063.115847] stk11xx: EMSGSIZE
[ 2063.115850] stk11xx: isoc_init() submit_urb 13 failed with error -90
[ 2063.115853] stk11xx: EMSGSIZE
[ 2063.115857] stk11xx: isoc_init() submit_urb 14 failed with error -90
[ 2063.115860] stk11xx: EMSGSIZE
[ 2063.115864] stk11xx: isoc_init() submit_urb 15 failed with error -90
[ 2063.115867] stk11xx: EMSGSIZE
[ 2065.179737] usb 3-2: selecting invalid altsetting 5
[ 2065.179744] stk11xx: usb_set_interface failed !
[ 2065.923744] usb 3-2: selecting invalid altsetting 5
[ 2065.923751] stk11xx: usb_set_interface failed !
[ 2066.533745] stk11xx: isoc_init() submit_urb 0 failed with error -90
[ 2066.533753] stk11xx: EMSGSIZE
[ 2066.533758] stk11xx: isoc_init() submit_urb 1 failed with error -90
[ 2066.533762] stk11xx: EMSGSIZE
[ 2066.533766] stk11xx: isoc_init() submit_urb 2 failed with error -90
[ 2066.533769] stk11xx: EMSGSIZE
[ 2066.533773] stk11xx: isoc_init() submit_urb 3 failed with error -90
[ 2066.533776] stk11xx: EMSGSIZE
[ 2066.533779] stk11xx: isoc_init() submit_urb 4 failed with error -90
[ 2066.533783] stk11xx: EMSGSIZE
[ 2066.533786] stk11xx: isoc_init() submit_urb 5 failed with error -90
[ 2066.533790] stk11xx: EMSGSIZE
[ 2066.533793] stk11xx: isoc_init() submit_urb 6 failed with error -90
[ 2066.533797] stk11xx: EMSGSIZE
[ 2066.533800] stk11xx: isoc_init() submit_urb 7 failed with error -90
[ 2066.533803] stk11xx: EMSGSIZE
[ 2066.533807] stk11xx: isoc_init() submit_urb 8 failed with error -90
[ 2066.533810] stk11xx: EMSGSIZE
[ 2066.533813] stk11xx: isoc_init() submit_urb 9 failed with error -90
[ 2066.533817] stk11xx: EMSGSIZE
[ 2066.533820] stk11xx: isoc_init() submit_urb 10 failed with error -90
[ 2066.533824] stk11xx: EMSGSIZE
[ 2066.533828] stk11xx: isoc_init() submit_urb 11 failed with error -90
[ 2066.533831] stk11xx: EMSGSIZE
[ 2066.533834] stk11xx: isoc_init() submit_urb 12 failed with error -90
[ 2066.533838] stk11xx: EMSGSIZE
[ 2066.533841] stk11xx: isoc_init() submit_urb 13 failed with error -90
[ 2066.533845] stk11xx: EMSGSIZE
[ 2066.533848] stk11xx: isoc_init() submit_urb 14 failed with error -90
[ 2066.533852] stk11xx: EMSGSIZE
[ 2066.533855] stk11xx: isoc_init() submit_urb 15 failed with error -90
[ 2066.533859] stk11xx: EMSGSIZE

```Here is a new dmesg output log with DEBUG=1 when the module was installed (module recompiled with DEBUG=1)

```

[ 2221.978864] stk11xx: Syntek USB2.0 webcam driver startup
[ 2221.978872] stk11xx: Copyright(c) 2006-2009 Nicolas VIVIEN
[ 2221.978912] stk11xx: Probe function called with VendorID=05E1, ProductID=0408 and InterfaceNumber=0
[ 2221.978918] stk11xx: Syntek USB2.0 - STK-1160 based device found.
[ 2221.978922] stk11xx: Syntek AVStream USB2.0 Video Capture - Product ID 0x0408.
[ 2221.978929] stk11xx: Release: 0005
[ 2221.978932] stk11xx: Number of interfaces : 3
[ 2221.978939] usb 3-2: selecting invalid altsetting 5
[ 2221.978942] stk11xx: usb_set_interface failed !
[ 2221.980750] stk11xx: Initialize USB2.0 Syntek Capture device
[ 2223.020735] stk11xx: SET FEATURE
[ 2223.020743] stk11xx: Syntek USB2.0 Capture device is ready
[ 2223.020867] stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0
[ 2223.020932] usbcore: registered new interface driver usb_stk11xx_driver
[ 2223.020939] stk11xx: v2.2.0 : Syntek USB Video Camera
[ 2223.025685] stk11xx: Allocate video buffers
[ 2223.025722] stk11xx: Allocated iso buffer at ffff88004f100000
[ 2223.025751] stk11xx: Allocated iso buffer at ffff88004b5a0000
[ 2223.025781] stk11xx: Allocated iso buffer at ffff88004b3e8000
[ 2223.025812] stk11xx: Allocated iso buffer at ffff88004f168000
[ 2223.025842] stk11xx: Allocated iso buffer at ffff88004bca0000
[ 2223.025872] stk11xx: Allocated iso buffer at ffff88004bcb8000
[ 2223.025902] stk11xx: Allocated iso buffer at ffff88004c1a0000
[ 2223.025932] stk11xx: Allocated iso buffer at ffff88004c1a8000
[ 2223.025962] stk11xx: Allocated iso buffer at ffff88004b5b0000
[ 2223.025989] stk11xx: Allocated iso buffer at ffff88004b5b8000
[ 2223.026019] stk11xx: Allocated iso buffer at ffff88004c4a0000
[ 2223.026048] stk11xx: Allocated iso buffer at ffff88004c4a8000
[ 2223.026075] stk11xx: Allocated iso buffer at ffff88004b3f0000
[ 2223.026102] stk11xx: Allocated iso buffer at ffff88004b3f8000
[ 2223.026130] stk11xx: Allocated iso buffer at ffff88004f170000
[ 2223.026157] stk11xx: Allocated iso buffer at ffff88004f178000
[ 2223.026162] stk11xx: Allocated frame buffer structure at ffff880078564f60
[ 2223.026981] stk11xx: Allocated frame buffer 0 at ffffc9001628e000.
[ 2223.031744] stk11xx: Allocated frame buffer 1 at ffffc90016790000.
[ 2223.036197] stk11xx: Allocated frame buffer 2 at ffffc90016c92000.
[ 2223.051591] stk11xx: Allocated image buffer at ffffc90017194000
[ 2223.051601] stk11xx: Reset all buffers
[ 2223.051608] stk11xx: Set mode 5 [640x480]
[ 2224.849733] stk11xx: Set colour : 32767
[ 2224.849740] stk11xx: Set contrast : 32767
[ 2224.849743] stk11xx: Set hue : 65535
[ 2224.849747] stk11xx: Set brightness : 32767
[ 2224.849755] usb 3-2: selecting invalid altsetting 5
[ 2224.849759] stk11xx: usb_set_interface failed !
[ 2225.422732] stk11xx: Set colour : 32767
[ 2225.422738] stk11xx: Set contrast : 32767
[ 2225.422742] stk11xx: Set hue : 65535
[ 2225.422745] stk11xx: Set brightness : 32767
[ 2225.593737] usb 3-2: selecting invalid altsetting 5
[ 2225.593811] stk11xx: usb_set_interface failed !
[ 2225.944732] stk11xx: Set colour : 32767
[ 2225.944738] stk11xx: Set contrast : 32767
[ 2225.944742] stk11xx: Set hue : 65535
[ 2225.944746] stk11xx: Set brightness : 32767
[ 2226.202745] stk11xx: Set colour : 32767
[ 2226.202752] stk11xx: Set contrast : 32767
[ 2226.202756] stk11xx: Set hue : 65535
[ 2226.202760] stk11xx: Set brightness : 32767
[ 2226.202764] stk11xx: usb_stk11xx_isoc_init()
[ 2226.202782] stk11xx: dev->isoc_in_size = 0
[ 2226.202785] stk11xx: dev->isoc_in_endpointAddr = 2
[ 2226.202790] stk11xx: isoc_init() submit_urb 0 failed with error -90
[ 2226.202795] stk11xx: EMSGSIZE
[ 2226.202799] stk11xx: isoc_init() submit_urb 1 failed with error -90
[ 2226.202803] stk11xx: EMSGSIZE
[ 2226.202807] stk11xx: isoc_init() submit_urb 2 failed with error -90
[ 2226.202810] stk11xx: EMSGSIZE
[ 2226.202814] stk11xx: isoc_init() submit_urb 3 failed with error -90
[ 2226.202818] stk11xx: EMSGSIZE
[ 2226.202821] stk11xx: isoc_init() submit_urb 4 failed with error -90
[ 2226.202825] stk11xx: EMSGSIZE
[ 2226.202828] stk11xx: isoc_init() submit_urb 5 failed with error -90
[ 2226.202832] stk11xx: EMSGSIZE
[ 2226.202835] stk11xx: isoc_init() submit_urb 6 failed with error -90
[ 2226.202839] stk11xx: EMSGSIZE
[ 2226.202842] stk11xx: isoc_init() submit_urb 7 failed with error -90
[ 2226.202846] stk11xx: EMSGSIZE
[ 2226.202849] stk11xx: isoc_init() submit_urb 8 failed with error -90
[ 2226.202852] stk11xx: EMSGSIZE
[ 2226.202856] stk11xx: isoc_init() submit_urb 9 failed with error -90
[ 2226.202859] stk11xx: EMSGSIZE
[ 2226.202863] stk11xx: isoc_init() submit_urb 10 failed with error -90
[ 2226.202867] stk11xx: EMSGSIZE
[ 2226.202870] stk11xx: isoc_init() submit_urb 11 failed with error -90
[ 2226.202874] stk11xx: EMSGSIZE
[ 2226.202877] stk11xx: isoc_init() submit_urb 12 failed with error -90
[ 2226.202881] stk11xx: EMSGSIZE
[ 2226.202884] stk11xx: isoc_init() submit_urb 13 failed with error -90
[ 2226.202888] stk11xx: EMSGSIZE
[ 2226.202891] stk11xx: isoc_init() submit_urb 14 failed with error -90
[ 2226.202896] stk11xx: EMSGSIZE
[ 2226.202899] stk11xx: isoc_init() submit_urb 15 failed with error -90
[ 2226.202903] stk11xx: EMSGSIZE
[ 2226.316738] stk11xx: Set colour : 32767
[ 2226.316745] stk11xx: Set contrast : 32767
[ 2226.316748] stk11xx: Set hue : 65535
[ 2226.316752] stk11xx: Set brightness : 32767
[ 2226.316780] stk11xx: v4l_stk11xx_ioctl 00
[ 2226.316785] VIDIOC_QUERYCAP
[ 2226.316789] stk11xx: VIDIOC_QUERYCAP
[ 2226.340023] stk11xx: Isoc cleanup
[ 2226.340043] stk11xx: Free buffers
[ 2226.398956] stk11xx: Allocate video buffers
[ 2226.398997] stk11xx: Allocated iso buffer at ffff88004b898000
[ 2226.399025] stk11xx: Allocated iso buffer at ffff88004b880000
[ 2226.399055] stk11xx: Allocated iso buffer at ffff88004c088000
[ 2226.399086] stk11xx: Allocated iso buffer at ffff88004bcb8000
[ 2226.399116] stk11xx: Allocated iso buffer at ffff88004bca0000
[ 2226.399146] stk11xx: Allocated iso buffer at ffff88004f168000
[ 2226.399175] stk11xx: Allocated iso buffer at ffff88004b5a0000
[ 2226.399204] stk11xx: Allocated iso buffer at ffff88004f100000
[ 2226.399234] stk11xx: Allocated iso buffer at ffff88004b190000
[ 2226.399262] stk11xx: Allocated iso buffer at ffff88004b198000
[ 2226.399292] stk11xx: Allocated iso buffer at ffff88004c090000
[ 2226.399321] stk11xx: Allocated iso buffer at ffff88004c098000
[ 2226.399350] stk11xx: Allocated iso buffer at ffff88004f170000
[ 2226.399378] stk11xx: Allocated iso buffer at ffff88004f178000
[ 2226.399404] stk11xx: Allocated iso buffer at ffff88004c4a0000
[ 2226.399432] stk11xx: Allocated iso buffer at ffff88004c4a8000
[ 2226.399437] stk11xx: Allocated frame buffer structure at ffff880078564f60
[ 2226.400297] stk11xx: Allocated frame buffer 0 at ffffc90010c48000.
[ 2226.404950] stk11xx: Allocated frame buffer 1 at ffffc9001114a000.
[ 2226.430819] stk11xx: Allocated frame buffer 2 at ffffc90013a82000.
[ 2226.444141] stk11xx: Allocated image buffer at ffffc90013f84000
[ 2226.444149] stk11xx: Reset all buffers
[ 2226.444156] stk11xx: Set mode 5 [640x480]
[ 2228.431729] stk11xx: Set colour : 32767
[ 2228.431736] stk11xx: Set contrast : 32767
[ 2228.431740] stk11xx: Set hue : 65535
[ 2228.431744] stk11xx: Set brightness : 32767
[ 2228.431752] usb 3-2: selecting invalid altsetting 5
[ 2228.431756] stk11xx: usb_set_interface failed !
[ 2229.057733] stk11xx: Set colour : 32767
[ 2229.057740] stk11xx: Set contrast : 32767
[ 2229.057744] stk11xx: Set hue : 65535
[ 2229.057747] stk11xx: Set brightness : 32767
[ 2229.291463] usb 3-2: selecting invalid altsetting 5
[ 2229.291470] stk11xx: usb_set_interface failed !
[ 2229.663745] stk11xx: Set colour : 32767
[ 2229.663752] stk11xx: Set contrast : 32767
[ 2229.663756] stk11xx: Set hue : 65535
[ 2229.663760] stk11xx: Set brightness : 32767
[ 2229.922266] stk11xx: Set colour : 32767
[ 2229.922273] stk11xx: Set contrast : 32767
[ 2229.922277] stk11xx: Set hue : 65535
[ 2229.922280] stk11xx: Set brightness : 32767
[ 2229.922285] stk11xx: usb_stk11xx_isoc_init()
[ 2229.922301] stk11xx: dev->isoc_in_size = 0
[ 2229.922305] stk11xx: dev->isoc_in_endpointAddr = 2
[ 2229.922309] stk11xx: isoc_init() submit_urb 0 failed with error -90
[ 2229.922315] stk11xx: EMSGSIZE
[ 2229.922319] stk11xx: isoc_init() submit_urb 1 failed with error -90
[ 2229.922322] stk11xx: EMSGSIZE
[ 2229.922326] stk11xx: isoc_init() submit_urb 2 failed with error -90
[ 2229.922329] stk11xx: EMSGSIZE
[ 2229.922332] stk11xx: isoc_init() submit_urb 3 failed with error -90
[ 2229.922336] stk11xx: EMSGSIZE
[ 2229.922339] stk11xx: isoc_init() submit_urb 4 failed with error -90
[ 2229.922343] stk11xx: EMSGSIZE
[ 2229.922346] stk11xx: isoc_init() submit_urb 5 failed with error -90
[ 2229.922350] stk11xx: EMSGSIZE
[ 2229.922353] stk11xx: isoc_init() submit_urb 6 failed with error -90
[ 2229.922357] stk11xx: EMSGSIZE
[ 2229.922360] stk11xx: isoc_init() submit_urb 7 failed with error -90
[ 2229.922364] stk11xx: EMSGSIZE
[ 2229.922367] stk11xx: isoc_init() submit_urb 8 failed with error -90
[ 2229.922371] stk11xx: EMSGSIZE
[ 2229.922374] stk11xx: isoc_init() submit_urb 9 failed with error -90
[ 2229.922378] stk11xx: EMSGSIZE
[ 2229.922381] stk11xx: isoc_init() submit_urb 10 failed with error -90
[ 2229.922385] stk11xx: EMSGSIZE
[ 2229.922388] stk11xx: isoc_init() submit_urb 11 failed with error -90
[ 2229.922392] stk11xx: EMSGSIZE
[ 2229.922395] stk11xx: isoc_init() submit_urb 12 failed with error -90
[ 2229.922399] stk11xx: EMSGSIZE
[ 2229.922402] stk11xx: isoc_init() submit_urb 13 failed with error -90
[ 2229.922406] stk11xx: EMSGSIZE
[ 2229.922409] stk11xx: isoc_init() submit_urb 14 failed with error -90
[ 2229.922412] stk11xx: EMSGSIZE
[ 2229.922416] stk11xx: isoc_init() submit_urb 15 failed with error -90
[ 2229.922420] stk11xx: EMSGSIZE
[ 2230.032764] stk11xx: Set colour : 32767
[ 2230.032770] stk11xx: Set contrast : 32767
[ 2230.032775] stk11xx: Set hue : 65535
[ 2230.032778] stk11xx: Set brightness : 32767
[ 2230.032804] stk11xx: v4l_stk11xx_ioctl 00
[ 2230.032810] VIDIOC_QUERYCAP
[ 2230.032814] stk11xx: VIDIOC_QUERYCAP
[ 2230.061280] stk11xx: Isoc cleanup
[ 2230.061299] stk11xx: Free buffers

```I'm not sure where to start, or what to try. And advice or suggestions would be welcome. I am a programmer, I've done lots of linux work in the past (kernel + userspace). So I can try code changes + whatnot if necessary.

Thanks in advance!
-Dave
ETA:


[LIST]
[*] I'm running ubuntu 9.10 on x86_64 (amd64).
[*] I'm in North America, trying to feed in an NTSC signal to the device.
[*] When I say it doesn't work, xawtv only shows up black and the cpu is bogged down and sluggish. If I try launching xawtv too many times the kernel module crashes with a page fault, unable to handle kernel paging request inside function stk11xx_copy_uvyv
[*] When I was first trying it I could get horribly corrupt video out of xawtv, like the display was skewed (number of bytes in display memory per scan line did not match what was being displayed).
[*] Under windows XP it comes up with green + pink everywhere and it looks like the resolution is on the order of 40x30 pixels blown up to the viewing window. Just Plain Awful.
[*] The one time it worked 100% under XP I could select capture resolutions, the colors were perfect, and it seemed excellent. Now it's like the wrong driver takes control of it under XP.
[*]The feeling I get is that this hardware is different from what the linux Syntek and XP drivers are expecting.
[/LIST]

---

### Post by rmt1947 on 2010-01-16
Hi Dave,

There are indeed (at least) two different physical devices called "EasyCAP DC60" which share the same USB ID 05e1:0408.  One of them has four video input cables, whereas the other has input cables labelled AUDIO(L), AUDIO(R), CVBS, S-VIDEO.  (To add to the confusion there also exists an "EasyCAP DC60+", which is a completely different piece of hardware with a different USB ID.)

Your lsusb output does not seem to correspond to either of the two 05e1:0408 devices described above, both of which have six altsettings for interface 0 (the video interface).  Your EasyCAP seems to be missing half the video altsettings, if the lsusb output is to be believed.  Assuming there is no hardware problem, you would appear to have identified a third member of the 05e1:0408 family.  Hmm.  What is the purpose of a USB ID if it is not unique to a particular hardware configuration?

Mike Thomas

---

### Post by RichardTowyn on 2010-01-16
Hi Dave, 

I think I have the same device as my lsusb matched yours exactly!

I also can not get it to work with the stk11xx driver with Ivor's patch. I get similar dmesg to you.

The device did work in Windows Vista but it was reported as being a STK1150 chip not STK1160. Not sure if there are any differences.

If anybody has any ideas please let us know!

Thanks

Rich

---

### Post by dashxdr on 2010-01-16
My DC60 Eascap has Red, White, Yellow and S-video cables. Red + White are audio, Yellow is composite video input.

It may be the stk1150 vs stk1160 thing, I recall both numbers coming up under windows XP.

Still hoping for constructive suggestions!

-Dave

---

### Post by RichardTowyn on 2010-01-17
Hi, 

I've just checked, the numbers on the chips of my EasyCAP DC60 as follows:

STK1160DLQG 
BF916-0947

Silan
SC?113
HV0HUEE

VIA
VT1612A
0516CD TAIWAN
2H4424094


I've got pictures of the board if it's of any help.

Just to recap, I cant get the STK11xx driver (with patch) to work, the output of my lsusb -v is the same as Dave's above.

Thanks

Rich

---

### Post by dashxdr on 2010-01-17
> **RichardTowyn said:**
> VIA
VT1612A
0516CD TAIWAN
2H4424094

I've got pictures of the board if it's of any help.


I'd like to see the picture(s). That VT1612A chip doesn't make any sense. The datasheet says it is an AC97 codec... such chips are normally used for audio output.

Well, I guess it could make sense. The chips have an ADC inside so it could be an easy way to get analog input for audio. VIA chips are usually very inexpensive. Seems like overkill though...

The "SC?113" is probably the SAA7113H chip which converts analog video signals into a digital stream.

-Dave

---

### Post by usbeasycap on 2010-01-18
As far as I know now, this Easycap USB Video Capture Card can't support Linux system now. Waiting for development now!

---

### Post by axelmasok on 2010-01-19
Hi everyone, I'm interested in using the audio leads on the D60 for "line in" to my laptop. The snd-usb-audio alsa driver picks it up but I have failed to hear or record anything from the device. Anyone found this to work? Video doesn't faze me.

---

### Post by bgiannes on 2010-01-19
> **usbeasycap said:**
> As far as I know now, this Easycap USB Video Capture Card can't support Linux system now. Waiting for development now!


Some people do clam to have the easycap d60 working under 9.10?  There are some long threads on other forums talking about it.  But they maybe rebuilding the kernel?

NOTE:- I just got it working under xp, the install when less then smoothly, it was my 5th try...  Even when it was working it defauls to pal, and it took he 1/2hr to get to the properties screen to change it, as it looked like it was locking-up.  At least i can use the device now...  The driver that works is the XP STK1150.

there is this, [http://doc.ubuntu-fr.org/em28xx_generique](http://doc.ubuntu-fr.org/em28xx_generique) but i cant see which kernel it's good for? and my france is rusty.

fyi: [http://www.szforwardvideo.com/product/Pro_7_6.html](http://www.szforwardvideo.com/product/Pro_7_6.html)  They talk about there being a large amount of "copyed" hardware in the market place.  So maybe there are a number of different chip-sets out there?

---

### Post by rmt1947 on 2010-01-21
> **RichardTowyn said:**
> 

VIA
VT1612A
0516CD TAIWAN
2H4424094



This is a very useful piece of information - I haven't seen it posted before.  Glancing at the datasheet for the ICE1232 chip, which I believe is a (near?) equivalent of the VT1612A, I notice that its registers for volume control correspond to data passed through register 0x504 on the STK1160. Things are a lot clearer now. If video capture is done by the SAA7113H and audio capture is done by the VT1612A, for both of which datasheets are available, the only remaining mysterious component in the EasyCAP DC60 is the STK1160.  And for guidance on that we can turn to Ivor Hewitt's patch from January 2009.

Mike

---

### Post by manco on 2010-02-01
Hi everyone

I've been looking online today for a way to use my laptop as a TV/monitor and EasyCAP looks like the best bet.

I haven't purchased one yet, but looking at [DealExtreme]("http://www.dealextreme.com/products.dx/category.313~search.easycap") there are 3 different products:

#1 [DC60]("http://www.dealextreme.com/details.dx/sku.5707")

#2 [DC60]("http://www.dealextreme.com/details.dx/sku.11267") (why it's a different product I don't know)

#3 [DC60++]("http://www.dealextreme.com/details.dx/sku.26319") ([this image]("http://www1.dealextreme.com/productimages/sku_26319_4.jpg") confirms it's the DC60++)

I've seen the [DC60 working under OSX]("http://www.youtube.com/watch?v=H2lBSbM3LeA"), as well as the [DC60++ working under Linux]("http://www.youtube.com/user/BaJIeHTuHbi4#p/u/3/xsZuSDwtnnQ").

If they were all the same price, I'd go with the DC60++ (since I know it works in Linux).  But seeing as the DC60 works with a Mac (and isn't advertised as such) I'm beginning to think the DC60 will work with Linux as well.

In the DC60++ video, it works with a Linux program called "TVTime".  Under OSX, it works with a program called "EasyCAP Viewer" (which apparently is a reverse-engineered version of an EasyCAP Linux driver)

Which version should I get?  They are pretty cheap on eBay too.

---

### Post by bobthebastard3 on 2010-03-05
Hiya,

Steps I had to do to get an easycap DC60 working under Fedora Core 9 (Sulfur)

1. Download latest Easycap tarball from sourceforge.

[http://sourceforge.net/projects/easycapdc60/files/easycap_dc60.0.7.tar.gz/download]("http://sourceforge.net/projects/easycapdc60/files/easycap_dc60.0.7.tar.gz/download")

2. Extract Tarball, read instructions, modified the makefile for correct kernel header location. In this case copied the appropriate command from astroeasycap driver makefile (Sure its a cheat, but works) 
(So, replaced //easycapdir//src/makefile KERNELDIR line with "KERNELDIR ?= /lib/modules/`uname -r`/build"

3. sudo or su root in shell, type sh install.sh

Script should build easycap.ko, load it, and do a depmod to rebuild modules list.

4. Check module is loaded using lsmod

5. Plugin Easy cap module.

6. Check /dev/ directory not for video0 but as per instructions, easycap0 and easysnd0.

The latest module is patched for NTSC and PAL, 

7. Changed permissions on the two dev files 
   chmod ugo+rw /dev/easycap0
   chmod ugo+rw /dev/easysnd0

This is as I used VLC which can't be run as root

8. Pick your appropriate media player, I had problems with sound, you may not, but opened capture device using vlc and vl42 device /dev/easycap0.

Works great! Thanks to Mike and BFC ex sourceforge. Painless. Well almost. ;)

The Easy cap DC60 is the S-video + CVBS + Audio L & R with A Syntek stk1160 Chipset and no VIA chipset. Presumably the VIA is only in the 4 channel model? But still carries the  ID 05e1:0408 via LSusb.

Hope it helps someone out. Also the garbled green image, you may get, appears to be related to a) using adapter on less than USB2.0 b) format negotiation error.

---

### Post by autogarsas on 2010-03-15
And when it will have any *.deb installation or somethink way easier? As this wont help me anythink.

---

### Post by andlinux on 2010-03-18
> **bobthebastard3 said:**
> Hiya,

Steps I had to do to get an easycap DC60 working under Fedora Core 9 (Sulfur)

1. Download latest Easycap tarball from sourceforge.

[http://sourceforge.net/projects/easycapdc60/files/easycap_dc60.0.7.tar.gz/download]("http://sourceforge.net/projects/easycapdc60/files/easycap_dc60.0.7.tar.gz/download")

2. Extract Tarball, read instructions, modified the makefile for correct kernel header location. In this case copied the appropriate command from astroeasycap driver makefile (Sure its a cheat, but works) 
(So, replaced //easycapdir//src/makefile KERNELDIR line with "KERNELDIR ?= /lib/modules/`uname -r`/build"

3. sudo or su root in shell, type sh install.sh

Script should build easycap.ko, load it, and do a depmod to rebuild modules list.

4. Check module is loaded using lsmod

5. Plugin Easy cap module.

6. Check /dev/ directory not for video0 but as per instructions, easycap0 and easysnd0.

The latest module is patched for NTSC and PAL, 

7. Changed permissions on the two dev files 
   chmod ugo+rw /dev/easycap0
   chmod ugo+rw /dev/easysnd0

This is as I used VLC which can't be run as root

8. Pick your appropriate media player, I had problems with sound, you may not, but opened capture device using vlc and vl42 device /dev/easycap0.

Works great! Thanks to Mike and BFC ex sourceforge. Painless. Well almost. ;)

The Easy cap DC60 is the S-video + CVBS + Audio L & R with A Syntek stk1160 Chipset and no VIA chipset. Presumably the VIA is only in the 4 channel model? But still carries the  ID 05e1:0408 via LSusb.

Hope it helps someone out. Also the garbled green image, you may get, appears to be related to a) using adapter on less than USB2.0 b) format negotiation error.
I have this device a week now and I used it on a win7 system to record old vhs tapes. Now I'm trying to make it work on my ubuntu laptop.

The module is loaded but I see no image. I have a cctv camera hooked up on this device. My first try with VLC gave an error so I searched further and saw that you did: 

chmod ugo+rw /dev/easycap0
chmod ugo+rw /dev/easysnd0

So I did that and know I have no error message in VLC but I have no image. (see image)

So I have no idea what I can do now.

EDIT: I just used the mplayer command that's standing in the readme file and executed that as su. I have a picture now but it has a big delay on it.

EDIT2: If I do:

mplayer tv:// -tv driver=v4l2:width=640:height=480:fps=25:outfmt=rgb24:device=/dev/easycap0

Then I have a picture and there's no delay. But I want to record it and I have no idea how I must do that ?

---

### Post by adxvd on 2010-03-19
> **bobthebastard3 said:**
> Hiya,

Steps I had to do to get an easycap DC60 working under Fedora Core 9 (Sulfur)

1. Download latest Easycap tarball from sourceforge.

[http://sourceforge.net/projects/easycapdc60/files/easycap_dc60.0.7.tar.gz/download]("http://sourceforge.net/projects/easycapdc60/files/easycap_dc60.0.7.tar.gz/download")

2. Extract Tarball, read instructions, modified the makefile for correct kernel header location. In this case copied the appropriate command from astroeasycap driver makefile (Sure its a cheat, but works) 
(So, replaced //easycapdir//src/makefile KERNELDIR line with "KERNELDIR ?= /lib/modules/`uname -r`/build"

3. sudo or su root in shell, type sh install.sh

Script should build easycap.ko, load it, and do a depmod to rebuild modules list.

4. Check module is loaded using lsmod

5. Plugin Easy cap module.

6. Check /dev/ directory not for video0 but as per instructions, easycap0 and easysnd0.

The latest module is patched for NTSC and PAL, 

7. Changed permissions on the two dev files 
   chmod ugo+rw /dev/easycap0
   chmod ugo+rw /dev/easysnd0

This is as I used VLC which can't be run as root

8. Pick your appropriate media player, I had problems with sound, you may not, but opened capture device using vlc and vl42 device /dev/easycap0.

Works great! Thanks to Mike and BFC ex sourceforge. Painless. Well almost. ;)

The Easy cap DC60 is the S-video + CVBS + Audio L & R with A Syntek stk1160 Chipset and no VIA chipset. Presumably the VIA is only in the 4 channel model? But still carries the  ID 05e1:0408 via LSusb.

Hope it helps someone out. Also the garbled green image, you may get, appears to be related to a) using adapter on less than USB2.0 b) format negotiation error.

Thanks for this, but I have a problem on the install. I get to step 3, but when it is installing I get this error:

root@ubuntu:/home/xxxxxx/easycap/easycap_dc60.0.7# ./install.sh
depmod OK
make clean OK
ERROR:  step failed:  make
/home/xxxxxxx/easycap/easycap_dc60.0.7/src/easycap_ioctl.c: In function ‘easycap_ioctl’:
/home/xxxxxxxx/easycap/easycap_dc60.0.7/src/easycap_ioctl.c:1824: warning: the frame size of 1060 bytes is larger than 1024 bytes
root@ubuntu:/home/xxxxxxxxx/easycap/easycap_dc60.0.7# 

Any ideas? I'm on ubuntu 9.10 32bit.

Also could you confirm that you can use s-video in using this method, thanks!

---

### Post by bobthebastard3 on 2010-03-20
> **andlinux said:**
> I have this device a week now and I used it on a win7 system to record old vhs tapes. Now I'm trying to make it work on my ubuntu laptop.

The module is loaded but I see no image. I have a cctv camera hooked up on this device. My first try with VLC gave an error so I searched further and saw that you did: 

chmod ugo+rw /dev/easycap0
chmod ugo+rw /dev/easysnd0

So I did that and know I have no error message in VLC but I have no image. (see image)

So I have no idea what I can do now.

EDIT: I just used the mplayer command that's standing in the readme file and executed that as su. I have a picture now but it has a big delay on it.

EDIT2: If I do:

mplayer tv:// -tv driver=v4l2:width=640:height=480:fps=25:outfmt=rgb24:device=/dev/easycap0

Then I have a picture and there's no delay. But I want to record it and I have no idea how I must do that ?


Hi andlinux, what I have found with vlc 0.9.9 9 the version I am using, later builds may differ, 
Is that it is fairly picky about using devices through the v4l2 subsystem.

can you open a console, type "ls /dev" and check your listings for devices named /video# where # is a number.

The structure of the easycap driver at this time is that it registers as a usb device instead of a proper v4l2 device driver, I have been in touch with the author of the driver to try and figure out how to modify the code to enable it to register properly.

If you follow the steps and modify the easycap_main.c file and change the '.name' to 'usb/video%. run the uninstall.sh as root, if you cant unload the module, unplug the easycap reboot and try again, then re-run install.sh, provided you dont have a webcam or a another device that registers as /dev/video0, when you plug the easycap in, it should register as /dev/video0.

VLC without any extra parameters should be able to open the device as a capture device at /dev/video0. 

There is an initial lag in opening the video stream, due to the structure of the driver, in that it auto negotiates the format for the picture without any additional options. 

I had problems setting the window size manually, I suspect once the driver conforms properly to the v4l2 standard the lag and the size options should work a bit better.

I will install mplayer later today to see how that works out compared to vlc.... I suspect there is a bug in my version of vlc, as it seems to only allow recording from video0 not video1, but at least its a workaround.

If you can get a picture in vlc after the above steps, you should be able to then click file, convert/save, then select the capture device again, and pick your output format.

Let me know how it works out for you...

---

### Post by bobthebastard3 on 2010-03-20
> **adxvd said:**
> Thanks for this, but I have a problem on the install. I get to step 3, but when it is installing I get this error:

root@ubuntu:/home/xxxxxx/easycap/easycap_dc60.0.7# ./install.sh
depmod OK
make clean OK
ERROR:  step failed:  make
/home/xxxxxxx/easycap/easycap_dc60.0.7/src/easycap_ioctl.c: In function ‘easycap_ioctl’:
/home/xxxxxxxx/easycap/easycap_dc60.0.7/src/easycap_ioctl.c:1824: warning: the frame size of 1060 bytes is larger than 1024 bytes
root@ubuntu:/home/xxxxxxxxx/easycap/easycap_dc60.0.7# 

Any ideas? I'm on ubuntu 9.10 32bit.

Also could you confirm that you can use s-video in using this method, thanks!
Hiya, it looks like your build is failing with specific reference to a v4l2 function, at line 1824 in the easycap_ioctl.c file. Can you check that you have the v4l2 packages installed, including the devel packages, make sure your running the latest kernel which has v4l2 support enabled, and the kernel headers are installed. 

Can you open a console as a regular user, and type gstreamer-properties, if thats installed, it should open a window with sound and video sources, and confirm that v4l2 or v4l1 is a valid source in the video tab under inputs for video. If it doesnt then its likely you may not have all the required dependecies installed for the package to compile properly.

Thats all I can think of at this time.

Regards

Angus...

---

### Post by bobthebastard3 on 2010-03-20
> **adxvd said:**
> Thanks for this, but I have a problem on the install. I get to step 3, but when it is installing I get this error:

root@ubuntu:/home/xxxxxx/easycap/easycap_dc60.0.7# ./install.sh
depmod OK
make clean OK
ERROR:  step failed:  make
/home/xxxxxxx/easycap/easycap_dc60.0.7/src/easycap_ioctl.c: In function ‘easycap_ioctl’:
/home/xxxxxxxx/easycap/easycap_dc60.0.7/src/easycap_ioctl.c:1824: warning: the frame size of 1060 bytes is larger than 1024 bytes
root@ubuntu:/home/xxxxxxxxx/easycap/easycap_dc60.0.7# 

Any ideas? I'm on ubuntu 9.10 32bit.

Also could you confirm that you can use s-video in using this method, thanks!

God Im and egg. just re-read the readme file.


KNOWN INSTALLATION PROBLEMS
---------------------------

(1) If the installation fails with a message similar to:

     warning: the frame size of .... bytes is larger than 1024 bytes

then you need to edit the file src/Makefile by removing the # character
at the beginning of the line:

     #EXTRA_CFLAGS += -Wframe-larger-than=8192

(This should not be necessary from version 0.7 onwards.  It's mentioned here
only as a precaution against possible regressions.)

Nice easy one afterall.... :D

---

### Post by andlinux on 2010-03-21
I forgot to mention it here, but it's working perfect now.
I went to sourceforge where the driver is located and asked it there on the open forum. 
It was simple what I had to do. If I start vlc and want to record then I have to give **/dev/easycap0:width=720:height=576** in by the video device name and not **/dev/easycap0**.

At first you have to give other rights to /dev/easycap0 or you're not able to let it work, I do it with this command: 
**sudo chmod ugo+rw /dev/easycap0**
But you can also use the **permit.sh ** script in the driver folder, it's the same. That's the only "problem" you have to live with. ;)

---

### Post by bobthebastard3 on 2010-03-21
Sweet! The way to resolve the rights issue, is to alter your udev rules to automatically assign 0664 or 0666 (equivalent to the chmod command)

From memory....In fedora sudo vi /etc/udev/rules.d/50-udev-default.rules from the console and add the following to the file under #video4linux heading,
KERNEL=="easycap0",            MODE="0666"
KERNEL=="easysnd1",            MODE="0666"

Save and sudo udevcontrol --reload_rules

Should assign access to standard. for read write and execute.

:D Glad you got it solved!

---

### Post by andlinux on 2010-03-21
> **bobthebastard3 said:**
> Sweet! The way to resolve the rights issue, is to alter your udev rules to automatically assign 0664 or 0666 (equivalent to the chmod command)

From memory....In fedora sudo vi /etc/udev/rules.d/50-udev-default.rules from the console and add the following to the file under #video4linux heading,
KERNEL=="easycap0",            MODE="0666"
KERNEL=="easysnd1",            MODE="0666"

Save and sudo udevcontrol --reload_rules

Should assign access to standard. for read write and execute.

:D Glad you got it solved!
I don't see 50-udev-default.rules in Ubuntu ;)

---

### Post by bobthebastard3 on 2010-03-21
[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

bout a third of the way down, this link is instructions for creating your own rules file. 

I have included link on the off chance that you get stuck, but 50-udev-default for example is read into udev control based upon the number 50, so 51 or 99 or, 10 at the start of the name of the file determines the load order when udev assumes control of the bus.

Ie you plug in a usb device, based upon the device table it maps to? I think udev then scans the rules-sets to determine what to do nect.

So either find the best matching one for your device, and add the lines from previous post, or just create a new file with 10-myrulset.rules and add the two items under any heading. Save, reload using udevcontrol ;)

---

### Post by adxvd on 2010-03-22
> **bobthebastard3 said:**
> God Im and egg. just re-read the readme file.


KNOWN INSTALLATION PROBLEMS
---------------------------

(1) If the installation fails with a message similar to:

     warning: the frame size of .... bytes is larger than 1024 bytes

then you need to edit the file src/Makefile by removing the # character
at the beginning of the line:

     #EXTRA_CFLAGS += -Wframe-larger-than=8192

(This should not be necessary from version 0.7 onwards.  It's mentioned here
only as a precaution against possible regressions.)

Nice easy one afterall.... :D

hehe thanks, can't believe I missed that!

So I have now got it installed and got a nice picture on mplayer and VLC but no sound. Is there an easy way to play microphone-in on VLC ubuntu like in windows?


EDIT: Nevermind, had a play around and managed to get it working well with s-video and line-in audio using 

/dev/easycap0:width=720:height=576:input=1

and the sound automagically came with it :)

Thanks again to the developers and this helpful thread :D

---

### Post by eikaf on 2010-03-26
Has someone managed to make it work with zoneminder?

---

### Post by bobthebastard3 on 2010-04-02
Yup, sorry for the delay, but yes. Lots of success with the latest zoneminder build that has v4l2 support built in, you will need to fully read the ZM documentation, first. I struck a problem with contant alrams, on the monitors, but deleted the initial monitor in favor of a post read, and it now foes a nice 25fps on modetect.

So It can be done, works well, only issue appears to be resizing the display window with firefox. :D Thanks again to the hard work of the developers that made the original drivers, and people that helped put Zoneminder together. its a high class product well written....

Feel free to post any issues that we can try to help you sort out.... ;)

---

### Post by nickc78 on 2010-04-09
I am getting an insmod error on the easycap.ko module. 

ERROR:  step failed:  insmod
insmod: error inserting '/lib/modules/linux-headers-2.6.32-19-generic/kernel/drivers/media/video/easycap.ko': -1 Invalid module format

 Any ideas on how I can get around this?  General insmod errors imply  that a local recompile from source will resolve most issues but I don't  think the tarball download includes the source to enable me to do this.

I had to edit the install.sh and makefile in /src to point to my specific kernel (2.6.32-19) as uname -r was returning a different version (not sure why I do not have linux headers for this kernel).  I have just upgraded to Lucid.

The error seems odd as it has actually inserted the easycap.ko file into /lib/modules/... folder.  When I plug my card in I do not get the video and sound devices appear in /usr/dev/ so I presume the install has not worked.

---

### Post by rmt1947 on 2010-04-09
The tarball does include the full source code of the driver in subdirectory ./src, and the script ./install.sh always performs a complete recompilation prior to the insmod step.  In the case of Ubuntu it should never be necessary to modify the script ./install.sh or the Makefile provided the kernel headers are consistent with the installed kernel.  If the headers are not the right ones I would fully expect the insmod step to fail with the "invalid module format" message.

I would recommend installing the kernel headers which match the Lucid kernel and then running the (original, unmodified) ./install.sh again.

Mike

---

### Post by bobthebastard3 on 2010-04-09
Interesting, running uname -r from the console should just return the current kernel version. uname, just Linux.


For the devices to be created, the module needs to be loaded via modprobe. 

Inserting the module via insmod is part of this process and I may be wrong, but I think it checks for dependancies via depmod, then runs insmod which should copy the file to the kernel modules directory, then modprobes it to load it actively into the running config.

I think the package should be kernel-devel with your specific kernel name in it somewhere, via apt-get. 

Id check and see via apt-get or synaptic or similiar (whichever package manager you use) and you may have more than one kernel installed, and the older one may be selected by default in your boot-loader config.?

Manually adding the sources for a kernel into the makefile that isnt the current working kernel will probably give way to those errors. Either that or you could try rebuilding your package databases. They may be corrupt and not showing your current config. Happens sometimes during an upgrade. God only knows why ;)

Either way once you get it built, /sbin/lsmod should show the currently loaded kernel modules. rmmod to remove them by name. If you mess about, run depmod -a to rebuild the module tables/database.

---

### Post by nickc78 on 2010-04-13
Thanks for your help.

If I run uname -r I get - 2.6.32-02063202-generic

If I run install.sh without mods I get the following error:

ERROR:  step failed:  make
make: *** /usr/src/linux-headers-2.6.32-02063202-generic: No such file or directory. Stop.

If I mod the makefile to point explicitly to 2.6.32-19 then I get the insmod error detailed in my first post.

If I look in /usr/src/ I have the following headers:

linux-headers-2.6.32-19  
linux-headers-2.6.32-19-generic

So why does uname -r return a kernel that does not exist in usr/src/ - I looked in synaptics and could see that the above kernels were installed but the one at the top of the post was not listed at all.

I have done some searching on your other suggestions but I am a bit of noob so really haven't a clue how to carry these out.  

Thanks

---

### Post by andlinux on 2010-04-13
> **nickc78 said:**
> Thanks for your help.

If I run uname -r I get - 2.6.32-02063202-generic

If I run install.sh without mods I get the following error:

ERROR:  step failed:  make
make: *** /usr/src/linux-headers-2.6.32-02063202-generic: No such file or directory. Stop.

If I mod the makefile to point explicitly to 2.6.32-19 then I get the insmod error detailed in my first post.

If I look in /usr/src/ I have the following headers:

linux-headers-2.6.32-19  
linux-headers-2.6.32-19-generic

So why does uname -r return a kernel that does not exist in usr/src/ - I looked in synaptics and could see that the above kernels were installed but the one at the top of the post was not listed at all.

I have done some searching on your other suggestions but I am a bit of noob so really haven't a clue how to carry these out.  

Thanks
What happens when you use linux-headers-2.6.32-19-generic ?

---

### Post by rmt1947 on 2010-04-13
I googled for

2.6.32-02063202-generic  headers

and uncovered a tale of woe.  An typical example of the problems people are having is:

[http://www.phoronix.com/forums/showthread.php?p=120563](http://www.phoronix.com/forums/showthread.php?p=120563)

So my suggestion a few days ago about "installing the kernel headers which match the Lucid kernel" was too glib.  Sorry to have been less than helpful on this.

Mike

---

### Post by nickc78 on 2010-04-13
> **andlinux said:**
> What happens when you use linux-headers-2.6.32-19-generic ?

When I use that I get the insmod error from my earlier post (on page 7).  I did just try 2.6.32-19 (without generic) and it came back with pages and pages of errors!

@rmt1947 - Is it likely that an update for Lucid at the end of the month may resolve my issue with the missing kernel at least - if not the issue with installing the easycap driver?

---

### Post by rmt1947 on 2010-04-13
I'm not an expert on installing modules, but as I understand it there will almost always be problems unless the version of the kernel headers exactly matches the version of the kernel you are running, and I wrote the installation script ./install.sh in a way which enforces this.

I suppose the most efficient strategy might be to wait for the next Lucid kernel.  As I recall, installation of a new kernel should be accompanied by automatic installation of matching kernel headers in /usr/src (provided the package manager thinks you have the kernel header package already installed).  It's a mystery to me why this synchronization hasn't happened with your present kernel 2.6.32-02063202-generic.

If the headers in /usr/src are not matched to the upcoming Lucid kernel you install at the end of month something is definitely wrong and it will have to be investigated at the time.

Once the header problem is resolved the easycapdc60 driver should install okay.  I hope.

Mike

---

### Post by bobthebastard3 on 2010-04-14
Sorry to sound like the spare prick at the wedding, if uname -r thinks the kernel is 
2.6.32-02063202-generic what does gnome or kde system properties think? 

If you build it against headers that arent generic, you may see the probs that you are describing when you are running a generic kernel. there will be all sorts of device and driver headers missing from the non generic sources, as generic caters for many different types of platforms.....

Its possible that your upgrade went south, check your /boot filesystem and see what kernels you actually have installed. It kinda sounds like you are on the old kernel with new headers installed and trying to build it from those new headers which would give you the error about invalid module format up on insertion.

From memory, ubuntu has a nice splash screen and boot loader so you never see the kernel version.

Either that or your upgrade is well and truly borked.

---

### Post by nickc78 on 2010-04-14
Bob/RMT - thanks again this is all great stuff

>  Once the header problem is resolved the easycapdc60 driver should  install okay.  I hope. That makes sense

> **bobthebastard3 said:**
>  if uname -r thinks the kernel is 
2.6.32-02063202-generic what does gnome or kde system properties think? 

In the System properties within Gnome System Monitor it thinks it is 2.6.32-02063202-generic

> **bobthebastard3 said:**
>  Its possible that your upgrade went south, check your /boot filesystem and see what kernels you actually have installed. 

In the /boot I have the following files for both 32-19-generic and 32-02063202-generic:

abi-
config-
initrd.img-
System.map-
vmlinuz-

I also have a file called vmcoreinfo- for 32-19-generic only

EDIT *** 

Just noticed that there are new generic headers available via update manager so I am going to download the updates and try again after that.

---

### Post by nickc78 on 2010-04-14
Ok that has not made any difference!  The update has installed kernel 2.6.32-20 but uname is still returning the long one!  I think I will put this on the back burner until the official Lucid release when I may reinstall the OS from scratch.

---

### Post by bobthebastard3 on 2010-04-15
> **nickc78 said:**
> Ok that has not made any difference!  The update has installed kernel 2.6.32-20 but uname is still returning the long one!  I think I will put this on the back burner until the official Lucid release when I may reinstall the OS from scratch.
If you have a menu item in gnome for bootloader, you should run that as root, and make sure that its set to boot from the latest kernel. Sorry I dont run ubuntu, but if you read up on modifying /etc/grub.conf if thats the boot loader that your distro uses, to make sure that its booting the latest one, pick an entry that you have the headers for, once thats sorted out, it should make more sense to the system. And until gnome and uname see that latest kernel as the one you have booted from, you'll be **** out of luck trying to get something to build properly with regards to kernel mods.

i think the source of the prob for you is that you still have the old kernel installed. but not the headers in a roundabout way. 

With fedora and grub, when you install the new kernel through an upgrade, it sometimes doesnt alter the bootloader config, so you end up with a new kernel installed, and a few old ones, and an out of date conf.

Best of luck, your teaching me a few things along the way too :)

---

### Post by bobthebastard3 on 2010-04-15
> **nickc78 said:**
> Ok that has not made any difference!  The update has installed kernel 2.6.32-20 but uname is still returning the long one!  I think I will put this on the back burner until the official Lucid release when I may reinstall the OS from scratch.
Oh and for future reference, I think generic refers to the architecture of the build. like i386 i586 i686. If thats the case you will end up with a **** load of other drivers and sources for other platforms as part of the upgrade, and you'll possibly be tied to using generic everytime when you install a package. kinda like the no-arch tag you sometimes see on packages. If you can spare the time, try and figure out what architecture you are running, and pick the closest matching one. You may see better performance as a result, and save a bit of disk space in the future. JMTCW ;)

---

### Post by nickc78 on 2010-04-17
> **bobthebastard3 said:**
>  your teaching me a few things along the way too :)

I echo that sentiment.

I have found my grub config - I am guessing the offending bit is the following:

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-02063202-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a438a18e-d6d0-47d7-b87a-38a04a1fa763
    linux    /boot/vmlinuz-2.6.32-02063202-generic root=UUID=a438a18e-d6d0-47d7-b87a-38a04a1fa763 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-02063202-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-02063202-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a438a18e-d6d0-47d7-b87a-38a04a1fa763
    echo    'Loading Linux 2.6.32-02063202-generic ...'
    linux    /boot/vmlinuz-2.6.32-02063202-generic root=UUID=a438a18e-d6d0-47d7-b87a-38a04a1fa763 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-02063202-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a438a18e-d6d0-47d7-b87a-38a04a1fa763
    linux    /boot/vmlinuz-2.6.32-20-generic root=UUID=a438a18e-d6d0-47d7-b87a-38a04a1fa763 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a438a18e-d6d0-47d7-b87a-38a04a1fa763
    echo    'Loading Linux 2.6.32-20-generic ...'
    linux    /boot/vmlinuz-2.6.32-20-generic root=UUID=a438a18e-d6d0-47d7-b87a-38a04a1fa763 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a438a18e-d6d0-47d7-b87a-38a04a1fa763
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=a438a18e-d6d0-47d7-b87a-38a04a1fa763 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a438a18e-d6d0-47d7-b87a-38a04a1fa763
    echo    'Loading Linux 2.6.32-19-generic ...'
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=a438a18e-d6d0-47d7-b87a-38a04a1fa763 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-19-generic
}
### END /etc/grub.d/10_linux ###

I have checked the 10_linux logic and it is the following that is building the above section in the grub config but I cannot work out what is controlling the loop to cause all the entries to be built in the config:

linux_entry ()
{
  os="$1"
  version="$2"
  recovery="$3"
  args="$4"
  if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s, with Linux %s")"
  fi
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
    recordfail
EOF
  save_default_entry | sed -e "s/^/\t/"

  if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
      cat << EOF
    set gfxpayload=$GRUB_GFXPAYLOAD_LINUX
EOF
  fi

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
    echo    '$(printf "$(gettext_quoted "Loading Linux %s ...")" ${version})'
EOF
  fi
  cat << EOF
    linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
    echo    '$(gettext_quoted "Loading initial ramdisk ...")'
EOF
  fi
  if test -n "${initrd}" ; then
    cat << EOF
    initrd    ${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

---

### Post by bobthebastard3 on 2010-04-17
> **nickc78 said:**
> I echo that sentiment.

I have found my grub config - I am guessing the offending bit is the following:

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-02063202-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a438a18e-d6d0-47d7-b87a-38a04a1fa763
    linux    /boot/vmlinuz-2.6.32-02063202-generic root=UUID=a438a18e-d6d0-47d7-b87a-38a04a1fa763 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-02063202-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-02063202-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a438a18e-d6d0-47d7-b87a-38a04a1fa763
    echo    'Loading Linux 2.6.32-02063202-generic ...'
    linux    /boot/vmlinuz-2.6.32-02063202-generic root=UUID=a438a18e-d6d0-47d7-b87a-38a04a1fa763 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-02063202-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a438a18e-d6d0-47d7-b87a-38a04a1fa763
    linux    /boot/vmlinuz-2.6.32-20-generic root=UUID=a438a18e-d6d0-47d7-b87a-38a04a1fa763 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a438a18e-d6d0-47d7-b87a-38a04a1fa763
    echo    'Loading Linux 2.6.32-20-generic ...'
    linux    /boot/vmlinuz-2.6.32-20-generic root=UUID=a438a18e-d6d0-47d7-b87a-38a04a1fa763 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a438a18e-d6d0-47d7-b87a-38a04a1fa763
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=a438a18e-d6d0-47d7-b87a-38a04a1fa763 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a438a18e-d6d0-47d7-b87a-38a04a1fa763
    echo    'Loading Linux 2.6.32-19-generic ...'
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=a438a18e-d6d0-47d7-b87a-38a04a1fa763 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-19-generic
}
### END /etc/grub.d/10_linux ###

I have checked the 10_linux logic and it is the following that is building the above section in the grub config but I cannot work out what is controlling the loop to cause all the entries to be built in the config:

linux_entry ()
{
  os="$1"
  version="$2"
  recovery="$3"
  args="$4"
  if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s, with Linux %s")"
  fi
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
    recordfail
EOF
  save_default_entry | sed -e "s/^/\t/"

  if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
      cat << EOF
    set gfxpayload=$GRUB_GFXPAYLOAD_LINUX
EOF
  fi

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
    echo    '$(printf "$(gettext_quoted "Loading Linux %s ...")" ${version})'
EOF
  fi
  cat << EOF
    linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
    echo    '$(gettext_quoted "Loading initial ramdisk ...")'
EOF
  fi
  if test -n "${initrd}" ; then
    cat << EOF
    initrd    ${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}
Simple, that is doing as it should, listing all the kernels you have installed, the step you are missing is to use that boot menu to select the kernel you want.

Not sure how you do it in Ubuntu, proably at the startup of your box, hit ESC or maybe a F1-F12 key. 

As for the default menu entry, that can propbably be set in gnome, read up on how to tweak the bootloader settings. [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Once you get the later kernel booting up properly, then the pesky errors your getting should hopefully vanish. :)

---

### Post by nickc78 on 2010-04-18
Bob - give yourself a gold star!!!

I followed the instructions for getting the grub2 menu to reappear at boot time and selected the version 20 kernel - upon rebooting I installed the driver with no complaints.  Just need to test that I can capture ok now.

Thanks

---

### Post by bobthebastard3 on 2010-04-19
> **nickc78 said:**
> Bob - give yourself a gold star!!!

I followed the instructions for getting the grub2 menu to reappear at boot time and selected the version 20 kernel - upon rebooting I installed the driver with no complaints.  Just need to test that I can capture ok now.

Thanks

No Probs Mate! :) Hopefully they will roll it out as a supported kernel mod once other bugs are ironed out. Glad you got it sorted.... :)

---

### Post by CJNZ on 2010-04-25
Hi,

Any new developments with the 4 port version of EasyCap?

I have been using the forum post:
[http://sourceforge.net/projects/syntekdriver/forums/forum/616182/topic/2803299/index/page/2](http://sourceforge.net/projects/syntekdriver/forums/forum/616182/topic/2803299/index/page/2)

It is working which is great, just trying to figure out how to work with more than one camera at a time.

Any ideas or has anyone achieved this?

Thanks,
CJ

---

### Post by wasntthisme on 2010-05-02
I'm having audio trouble using Lucid and the DC60.  My when using tvtime, my syslog gives entries like:

easycap: submit_audio_urbs: ERROR: usb_submit_urb() failed for urb with rc:
easycap: easycap_complete: ERROR: out-of-order urbs 13,0 ... continuing
easycap: easycap_ioctl: easycap driver shutting down on condition blue
easycap: check_stk: STK register 0x110 has 0x00, expected 0x14
easycap: check_stk: STK register 0x114 has 0xA0, expected 0x514

I haven't seen anything like this in the forums or searching google.  Please help. :D

Try to keep replies in newb language

---

### Post by rmt1947 on 2010-05-03
Re: "condition blue":  this can sometimes happen with poor-quality videotapes.  See the last paragraph of post no. 9 of the thread on the project's Open Discussion forum at:

[http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/3534088](http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/3534088)

I hope this helps.

Mike

---

### Post by nickc78 on 2010-05-03
in the end I rebuilt my machine with the latest version of 10.04 - the install was flawless with none of the previous kernel issues. running the scripts provided with the tarball gives mixed results - with vlc I get sound only, mplayer is just a bit better but with tvtime it is perfect both picture and sound - so the card works fine 
on linux.  what I now need is a simple capture software so that I can record my streams.  vlc seems the most logical but as have yet to see a picture I am not sure how I can get this to work. it seems whilst tvtime does not natively support recording I have seen mentioned that mencoder can be incorporated to achieve this but I have not managed to find any simple instructions on how to do this. does anyone have any suggestions of a GUI app that would meet my needs?

---

### Post by rmt1947 on 2010-05-03
I haven't tried it myself, but a method of recording using a GUI is mentioned here:

[http://easycap.blogspot.com/p/recording.html](http://easycap.blogspot.com/p/recording.html)

Mike

---

### Post by nickc78 on 2010-05-03
> **rmt1947 said:**
> I haven't tried it myself, but a method of recording using a GUI is mentioned here:

[http://easycap.blogspot.com/p/recording.html](http://easycap.blogspot.com/p/recording.html)

Mike

BINGO!!!

Thanks Mike - the easyrecord script works perfectly and is exactly what I have been looking for.

---

### Post by TimGS on 2010-05-13
I've tried the driver from [http://sourceforge.net/projects/easycapdc60/](http://sourceforge.net/projects/easycapdc60/), but install.sh fails with:

```

tim@dylan:~/Documents/WebBuild/Cams/easycap_dc60.0.7$ sudo ./install.sh
[sudo] password for tim: 
depmod OK
make clean OK
ERROR:  step failed:  make
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c: In function &#8216;explain_cid&#8217;:
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2103: error: &#8216;V4L2_CID_POWER_LINE_FREQUENCY&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2103: error: (Each undeclared identifier is reported only once
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2103: error: for each function it appears in.)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2104: error: &#8216;V4L2_CID_HUE_AUTO&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2105: error: &#8216;V4L2_CID_WHITE_BALANCE_TEMPERATURE&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2106: error: &#8216;V4L2_CID_SHARPNESS&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2107: error: &#8216;V4L2_CID_BACKLIGHT_COMPENSATION&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2108: error: &#8216;V4L2_CID_CHROMA_AGC&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2109: error: &#8216;V4L2_CID_COLOR_KILLER&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2111: error: &#8216;V4L2_CID_CAMERA_CLASS&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2112: error: &#8216;V4L2_CID_EXPOSURE_AUTO&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2113: error: &#8216;V4L2_CID_EXPOSURE_ABSOLUTE&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2114: error: &#8216;V4L2_CID_EXPOSURE_AUTO_PRIORITY&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2115: error: &#8216;V4L2_CID_PAN_RELATIVE&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2116: error: &#8216;V4L2_CID_TILT_RELATIVE&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2117: error: &#8216;V4L2_CID_PAN_RESET&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2118: error: &#8216;V4L2_CID_TILT_RESET&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2119: error: &#8216;V4L2_CID_PAN_ABSOLUTE&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2120: error: &#8216;V4L2_CID_TILT_ABSOLUTE&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2121: error: &#8216;V4L2_CID_FOCUS_ABSOLUTE&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2122: error: &#8216;V4L2_CID_FOCUS_RELATIVE&#8217; undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2123: error: &#8216;V4L2_CID_FOCUS_AUTO&#8217; undeclared (first use in this function)
make[3]: *** [/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.o] Error 1
make[2]: *** [_module_/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src] Error 2
make[1]: *** [all] Error 2
make: *** [build] Error 2

```

Can anyone give me any help with getting further?

My Easycap fits the description on sourceforge i.e. 
> Linux device driver for the EasyCAP USB 2.0 Video Adapter with Audio, Model No. DC60, having four input cables labelled respectively AUDIO(L), AUDIO(R), CVBS, S-VIDEO. The USB ID is 05e1:0408 and the manufacturer is Syntek Semiconductor Co., Ltd.

thanks in advance!
Tim.

PS. I'm running Hardy Heron on a Thinkpad T42. Kernel 2.6.24-27-generic.

---

### Post by andlinux on 2010-05-13
> **TimGS said:**
> I've tried the driver from [http://sourceforge.net/projects/easycapdc60/](http://sourceforge.net/projects/easycapdc60/), but install.sh fails with:

```

tim@dylan:~/Documents/WebBuild/Cams/easycap_dc60.0.7$ sudo ./install.sh
[sudo] password for tim: 
depmod OK
make clean OK
ERROR:  step failed:  make
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c: In function ‘explain_cid’:
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2103: error: ‘V4L2_CID_POWER_LINE_FREQUENCY’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2103: error: (Each undeclared identifier is reported only once
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2103: error: for each function it appears in.)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2104: error: ‘V4L2_CID_HUE_AUTO’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2105: error: ‘V4L2_CID_WHITE_BALANCE_TEMPERATURE’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2106: error: ‘V4L2_CID_SHARPNESS’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2107: error: ‘V4L2_CID_BACKLIGHT_COMPENSATION’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2108: error: ‘V4L2_CID_CHROMA_AGC’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2109: error: ‘V4L2_CID_COLOR_KILLER’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2111: error: ‘V4L2_CID_CAMERA_CLASS’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2112: error: ‘V4L2_CID_EXPOSURE_AUTO’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2113: error: ‘V4L2_CID_EXPOSURE_ABSOLUTE’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2114: error: ‘V4L2_CID_EXPOSURE_AUTO_PRIORITY’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2115: error: ‘V4L2_CID_PAN_RELATIVE’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2116: error: ‘V4L2_CID_TILT_RELATIVE’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2117: error: ‘V4L2_CID_PAN_RESET’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2118: error: ‘V4L2_CID_TILT_RESET’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2119: error: ‘V4L2_CID_PAN_ABSOLUTE’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2120: error: ‘V4L2_CID_TILT_ABSOLUTE’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2121: error: ‘V4L2_CID_FOCUS_ABSOLUTE’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2122: error: ‘V4L2_CID_FOCUS_RELATIVE’ undeclared (first use in this function)
/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.c:2123: error: ‘V4L2_CID_FOCUS_AUTO’ undeclared (first use in this function)
make[3]: *** [/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src/easycap_ioctl.o] Error 1
make[2]: *** [_module_/home/tim/Documents/WebBuild/Cams/easycap_dc60.0.7/src] Error 2
make[1]: *** [all] Error 2
make: *** [build] Error 2

```

Can anyone give me any help with getting further?

My Easycap fits the description on sourceforge i.e. 


thanks in advance!
Tim.

PS. I'm running Hardy Heron on a Thinkpad T42. Kernel 2.6.24-27-generic.
It's a guess but did you install the build-essential package ?

sudo  apt-get install build-essential

---

### Post by TimGS on 2010-05-13
Thanks for the suggestion - but yes, I have build-essential installed.

I have also tried the driver at [http://sourceforge.net/projects/syntekdriver/files/syntekdriver/stk11xx-1.4.0/stk11xx-1.4.0.tar.gz/download](http://sourceforge.net/projects/syntekdriver/files/syntekdriver/stk11xx-1.4.0/stk11xx-1.4.0.tar.gz/download), as mentioned elsewhere, but to no success either.

I have found out that media/v4l2-ioctl.h doesn't exist for my kernel so perhaps I simply need to upgrade to Lucid (with reluctance due to known issues with ipw2200 wireless - but I guess I can't put this off forever).

-- Tim.

*Edit: I am upgrading the machine in question to Lucid. I will be sure to report back with a report of success or failure - and most likely more questions!*

---

### Post by rmt1947 on 2010-05-13
Hi Tim,

The installation problem you are having is known, and is indeed related to the Hardy Heron distribution:

[http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/3682786](http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/3682786)

Upgrading to Lucid will fix it, though that's a rather drastic solution  :-)

I shall remove this bug in the next version of the driver, but that is a month or two in the future.

Mike

---

### Post by TimGS on 2010-05-14
Success!

Upgraded to Lucid. The only minor hiccup was the 1024 byte issue mentioned in the readme file, which also mentions the straightfoward fix.

Thanks Mike for providing the driver! Much appreciated.

-- Tim.

*PS: I* think* this is the D60, not the D60+.*

---

### Post by SuperMaxxio on 2010-05-16
I was worrying if anyone would go to full extent to make a step by step tutorial on how to do this because i have no idea what to do im sure if you posted it on youtube it would be a huge help to everyone, so if anyone could go to full extent please do so to help others who don't get it like me!!!:KS

---

### Post by mikefreeman on 2010-05-28
I just read through this thread and successfully got the EasyCap DC60 drive installed. Now, I was able to get it working once through VLC for about 20 seconds or so, then it froze. No other program will recognize the device. It also doesn't seem to work in Windows 7 with the "official" drivers off the CD. Any suggestions?

I'm running Linux Mint 9 (same as Ubuntu 10.04).

Thanks!

---

### Post by rmt1947 on 2010-05-28
Hi,

When the output freezes within a minute of startup it is usually for the reason mentioned in the README file as item (2) of the "Known Runtime Issues".  Sometimes an old, worn videotape will cause this.  You might like to try another videotape or a camera and see whether you get better results.

I hope this helps.

Mike

---

### Post by korifey13 on 2010-05-29
> **bobthebastard3 said:**
> [URL="http://ubuntuforums.org/showpost.php?p=8920422&postcount=56"][U]Hiya,

Steps I had to do to get an easycap DC60 working under Fedora Core 9 (Sulfur)...[/U][/URL]
EasyCAP OTP-128 (ID 05e1:0408, [produced by _mobiledata_]("http://www.mobiledata.ru/shop/UID_216.html")) works in Ubuntu Netbook Edition 10.04 at Eee PC 901. HOWTO:

1. Download latest EasyCAP DC60 tarball from [_http://sourceforge.net/projects/easycapdc60/_]("http://sourceforge.net/projects/easycapdc60/") and extract it into your home directory.

2. You'll need a build-essential package to build driver and a mplayer to test it's work, so install 'em if you didn't yet:
```
user@pc:~$ sudo apt-get install build-essential mplayer
```
3. Make a driver and if everyfing OK, you'll get the folowing output with no errors:
```
user@pc:~$ cd ~/easycap*
user@pc:~/easycap$ sudo ./install.sh
depmod OK
make clean OK
make OK
copied OK
depmod OK
insmod OK
```
In my case there was a make error showing that no such file "linux/bounds.h". So I've found this file at the Live session of the Ubuntu Startup Disk and added it into my /lib/modules/2.6.32-22-generic/build/include/linux:
```
user@pc:~$ sudo gedit /lib/modules/$(uname -r)/build/include/linux/bounds.h
```
Here are the contents of my bounds.h:
> #ifndef __LINUX_BOUNDS_H__
#define __LINUX_BOUNDS_H__
/*
 * DO NOT MODIFY.
 *
 * This file was generated by Kbuild
 *
 */

#define NR_PAGEFLAGS 25 /* __NR_PAGEFLAGS       # */
#define MAX_NR_ZONES 4 /* __MAX_NR_ZONES        # */

#endif
4. Plug in your EasyCAP DC60 and you'll see two new devices:
```
user@pc:~$ ls /dev/easy*
**[COLOR="Navy"]/dev/easycap0 /dev/easysnd1[/COLOR]**
```
Now you can plug an analog video input and test your device with mplayer:
```
user@pc:~$ sudo ./easycap/test.sh
```
To work as user without sudo, add permitions every time, you plug in the device:
```
user@pc:~$ sudo ./easycap/permit.sh
```
5. [Say thanks to _Mike Thomas - mighty developer_]("http://sourceforge.net/projects/easycapdc60/reviews/").

PS: I've tested video and audio input from all connectors. [_It worked_]("http://farm5.static.flickr.com/4022/4650234687_292c567500_b.jpg"). Good luck.

---

### Post by imafatmess on 2010-06-09
korifey13, this worked perfectly for me thanks. Problem is, its very jolty and thus unplayable (I'm trying to play gamecube through it). Anyone got any ideas on how to make it work?

---

### Post by imafatmess on 2010-06-09
Right, I now have it working but there is a delay between when it is processed on the gamecube to when it is shown. So, what I mean is, it takes about half a second for a button press to be shown. Anyone got any ideas?

---

### Post by andlinux on 2010-06-09
> **imafatmess said:**
> Right, I now have it working but there is a delay between when it is processed on the gamecube to when it is shown. So, what I mean is, it takes about half a second for a button press to be shown. Anyone got any ideas?

Maybe changing a buffer size ?

---

### Post by imafatmess on 2010-06-10
Unfortunately I have no idea how to do that. But that would make sense

---

### Post by Zittergie on 2010-06-16
Hi,

I have an EasyCap with ID 05e1:0408
I have installed the revision 99 driver and the easycap is detected.

Now the problem is I get only Black&White images

I am using the yellow (composite) input and have tried the following commands:

mplayer tv:// -tv driver=v4l2:width=720:height=576:fps=25: outfmt=rgb24:device=/dev/video1
mplayer tv:// -tv driver=v4l2:width=720:height=576:fps=25: outfmt=rgb24:device=/dev/video1:input=3
mplayer tv:// -tv driver=v4l2:width=720:height=576:fps=25: outfmt=rgb24:device=/dev/video1:input=2
mplayer tv:// -tv driver=v4l2:width=720:height=576:fps=25: outfmt=rgb24:device=/dev/video1:input=1
mplayer tv:// -tv driver=v4l2:width=720:height=576:fps=25: outfmt=rgb24:device=/dev/video1:input=0

The : and the outfmt contain no space

The image is not centered as it should be too.  It a bit to low.

Any ideas?

OK:  FOUND THE SOLUTION.  The module loaded worked in NTSC and not in PAL. SO I loaded the module using: norm=1 colour=24000

Still 1 Problems left:

2. No sound


OK, Everything solved. I was using the syntek driver, not the easycap driver.
Using the Easycap driver everything works

---

### Post by YogiPaolo on 2010-06-18
I am looking to build a budget CCTV system and easycap looks like the product i'm looking for. Also, I have a wifi spycam that runs on a 9v battery that I will eventually attach to a kite and take areal video (LOL). 

In any case, I want an inexpensive capture device that takes composite video. 

I'm looking around on amazon and there seem to be several products that carry the easycap name. One reviewer claims that he got a bootleg easycap with some bogus software. 

Can someone send a reliable link to a specific easycap product that works with these instructions?

Thanks

---

### Post by Kooster on 2010-06-25
Running lucid I get great video but can not seem to get any audio working. When I plug the dongle in it picks up usb audio but nothing is captured. I'm stuck, windows will never be a option again and I need to copy a whole lot of videos to dvd. PLEASE HELP!!!!

---

### Post by rmt1947 on 2010-06-25
Hi Kooster,

In order to help, we need to know what type of EasyCAP you have.  To find out, plug in the EasyCAP and then in a terminal window type the command

lsusb

You will get several lines of output, one of which will describe your EasyCAP.  Either this line will say

Bus XXX Device XXX: ID 05e1:0408 Syntek Semiconductor Co., Ltd

or it will say

Bus XXX Device XXX: ID eb1a:2861 eMPIA Technology, Inc.

If you have an EasyCAP of the Syntek type, there is a Linux driver available at

[http://sourceforge.net/projects/easycapdc60/](http://sourceforge.net/projects/easycapdc60/)

which should deliver both video and audio if things are set up correctly.

If you have an EasyCAP of the Empia type, the driver is already present in recent Linux kernels, which means that on distributions such as Ubuntu 10.04 LTS the EasyCAP should work out of the box without the need to install a driver manually.  For the Empia type of EasyCAP, video (at least) definitely works on Linux.

The Empia EasyCAPs are often marketed as DC60+ to distinguish them from the Syntek EasyCAPs branded DC60.  But there is some confusion about this and it's safer to use the lsusb command to be sure of what you've got.

Mike

---

### Post by fongoo on 2010-06-27
Guys iv had a good idea, if im correct you could install a thing called VMware i think you get it on linux, but anyway, then install windows vista/7/xp but i think vista works best, and then install easycap from there and when recording save the files to the hardrive some where you can find them, i havent tried this yet, but will get back to you guys when i can.
and i know this is a long annoying prosess but i relly want some video footage of my gaming so i think its worth it. best of luck to you all and please with me luck :L

---

### Post by Blue-K on 2010-07-02
Edit: Nevermind. Was a typo :P. Instead of PAL_60 I typed PAL-60. Stupid me...

Thanks for the help though!

---

### Post by rmt1947 on 2010-07-02
I'm the very last person on earth who should be attempting a comment on this, because I've never played a video game in my life (seriously), but here goes.

If you are in the US you need to run

./test.sh 5

to get NTSC (at 640x480).  If you are in Europe I believe you may need PAL_60:

[http://support.microsoft.com/kb/917304](http://support.microsoft.com/kb/917304)

If PAL_60 is what you want you will need to adapt the commands in the script ./test.sh by replacing the parts which say "norm=PAL" by "norm=PAL_60".

I've already sufficiently revealed my ignorance, so I'll say nothing about Nintendo Wii   :-)

Mike

---

### Post by the dammed one on 2010-07-10
running ubuntu 10.04 as of today all updates are installed. have a epson v300 scanner installed and working. (oem drivers)

Tried to install the drivers for the synaptic dc60 drivers.

the chipsets are the same. 

downloaded the easycap_dc60.0.8.2

unzipped into /home/user3 subdirectory

rebuilt the mplayer as described in step 2

did step 3 did not complete due to errors. no file in /etc/ subdirectory. 

help would like to use this dongle without loading windoz.

---

### Post by the dammed one on 2010-07-10
no vmware wont work as the root sytem called linux does not recognize the device. good thought though. hey even a newbie might know something.

---

### Post by madsmaddad on 2010-08-02
I bought an unbranded device from e-bay and it looks like teh easycap one, has the same ID, and works following these instructions. Now to find out how to duplicate the driver for each channel, link them, and drive it via zoneminder....

Thank You, and Mike Thomas

---

### Post by rmt1947 on 2010-08-03
The current version 0.8.2 of the easycapdc60 driver does not play properly with zoneminder when multiple video sources are in use.  I'm working to rectify this as a matter of urgency, but progress is rather slow because an unrelated project is taking up almost all my time at the moment.  I hope to be able to upload a zoneminder-capable version 0.8.3 of the driver in a week or so, but can't promise - there are a couple of outstanding problems with the low-level register programming which I don't yet know the answer to.

Mike

---

### Post by madsmaddad on 2010-08-10
Thanks Mike. 

As a quicky, the videocams that I am using are ancient, and work best using your test.sh with the device fixed as NTSC-M (7). Any quick help how to get the command line (198 ) there to display in colour and not B&W? 

](*,)

---

### Post by rmt1947 on 2010-08-10
Running ./test.sh 7 specifies S-VIDEO as the input and NTSC_M as the standard.  Are your cameras really NTSC with S-VIDEO output only?  If so, this is the first feedback I've had on the part of the driver which processes S-VIDEO.  I have been unable to test this myself because I do not possess any equipment which delivers S-VIDEO output.  If you are not seeing any colour it may mean that there is a programming error in the driver which I must attend to.  You should not need to change the mplayer command line to get colour - it should be there by default.

There's good news on ZoneMinder.  I've fixed the problem with the register programming and I'm now getting two video inputs working well together in ZoneMinder at just over 1 frame-per-second.  I'm at the stage of tidying up the source code (removing things I tried but didn't work), and will then move on to running my usual panel of tests to check that I haven't impaired any existing functionality in introducing the ZoneMinder capability.  I'll then upload version 0.8.3, probably sometime next week.

Mike

---

### Post by rmt1947 on 2010-08-10
Hmm, just realised you meant ./test4.sh 7 and not ./test.sh 7.  So all my ramblings about S-VIDEO are off target.  The question then remains:  are your cameras really NTSC?  And does ./test4.sh 6 (NTSC_443) not give any colour either?

Mike

---

### Post by qpmz123 on 2010-08-11
> **rmt1947 said:**
> I've fixed the problem with the register programming and I'm now getting two video inputs working well together in ZoneMinder at just over 1 frame-per-second.

Is that the sort of framerate to expect long-term or is it likely to improve? What sort of framerate does the EasyCap offer in zoneminder with a single active input?

FYI: I'm planning to setup a cheap zoneminder arrangement to watch what the cat gets up to while I'm not around, initially with one camera but adding a second or third later if it works out well, and 1 frame a second might not be enough. I'm trying to decide between a cheap EasyCap and the more expensive BT878-based PCI card that the zoneminder site refers to.

---

### Post by unknows on 2010-08-11
Thanks for this driver Mike !

> **qpmz123 said:**
> Is that the sort of framerate to expect long-term or is it likely to improve? What sort of framerate does the EasyCap offer in zoneminder with a single active input?

Use motion like me, im waiting the zoneminder support and motion works fine.

---

### Post by rmt1947 on 2010-08-11
With only one camera ZoneMinder gives a full 25 fps (PAL) at 320x240.

If I then define a second video input, each input is displayed at just over 1 fps.  This is because ZoneMinder asks the first camera for a few frames, then switches input and asks the second camera for a few frames, then switches input and asks the first camera for a few frames, ... and so on.  So the EasyCAP hardware spends almost all its time in an input-switching state (which involves repeatedly achieving frame/line lock).

I suspect (without any real reason) that some streamlining of the way in which inputs are switched could give maybe a two-fold improvement in framerate.  I can't say at the moment whether it is possible to do any better than that.  I got ZoneMinder working properly with multiple EasyCAP inputs for the first time only last Monday evening.

I'm not a ZoneMinder expert and haven't used motion at all.  My plan is to upload ZoneMinder-capable version 0.8.3 of the driver and await assessments from those who are experts.

Mike

---

### Post by qpmz123 on 2010-08-12
Hi Mike, thanks for the quick reply.

That sounds to me that is is as likely to be a limitation of the device as it is a limitation of your driver, so I'll probably get myself the more expensive PCI card (assuming there is a usable PCI slot in the machine I intend to use, I've not checked that yet!). I'll keep an eye on this thread though as other people are waiting on the success/failure of my little plan before trying something similar themselves so they may find your code useful.

Thanks again,
Dave.

---

### Post by rmt1947 on 2010-08-25
I uploaded version 0.8.3 of the driver to the site

[http://sourceforge.net/projects/easycapdc60/](http://sourceforge.net/projects/easycapdc60/)

last weekend.  ZoneMinder works with this new version (for me, at least), giving about one frame per second when tested with two inputs from a single four-CVBS EasyCAP.

Mike

---

### Post by m3how on 2010-09-11
I've followed the instructions in the post couple pages ago. I using Ubuntu 10.4 and this is what I get when I try to install:
```
kernel directory is /lib/modules/2.6.32-24-generic/build
not overwriting top level Makefile
not overwriting src/Makefile
not overwriting tools/Makefile
make clean OK
make OK
ERROR: Module snd_usb_audio is in use
ERROR:  snd_usb_audio module cannot be removed
```

Can anyone shed some light on what could be the problem ?

---

### Post by rmt1947 on 2010-09-11
Hi,

I imagine there is already a program running on the computer which is processing sound using the snd-usb-audio module.  You will need to close this program, whatever it is, before running ./install.sh.

When the driver is in use it requires OSS, not Alsa, and (as far as I know) OSS will take control of the sound card, so I think you will not be able to run more than one audio program at a time in these circumstances.  I am not an expert on the Linux audio permutations, so I may be wrong.

Mike

---

### Post by hellocatfood on 2010-09-22
Thanks all for making this work!

I just have one problem. Can something be done to make the device appear as a video device?

Programs like Cheese,Kdenlive and kino aren't picking up the device

---

### Post by rmt1947 on 2010-09-22
Hi,

In upcoming version 0.8.4 of the driver it will be possible to opt to have /dev/video0 instead of /dev/easycap0.  The timescale for the release of version 0.8.4, given my workload on other things, is probably the end of October 2010.

In fact, you can already get /dev/video0 by building current version 0.8.3 of the driver after modifying the file ./install.sh so that the line

CLIENT=0

becomes

CLIENT=1

I wouldn't recommend it, however.  In version 0.8.3 the routines relating to the creation of /dev/video0 are not quite right.  I'm doing a complete rewrite of these for version 0.8.4.

Mike

---

### Post by hellocatfood on 2010-09-22
Thanks! That actually solved my problem. You're right in that it doesn't work perfectly. In Kdenlive I only get black and white output with a lot of latency and it doesn't work at all in Cheese, but it works in [Graffiti Analysis](http://graffitianalysis.com/), which is actually what I wanted it for

---

### Post by rmt1947 on 2010-09-22
Ok, that's useful.  I'll test version 0.8.4 against Kdenlive and Cheese and see what happens.  I've had a lot of trouble with Cheese and gstreamer in the past.

Thanks for reporting back on that.

Mike

---

### Post by Silix on 2010-09-28
I tried to use this driver on a very old notebook (Compaq M300) and the video playback is fast enough.Unfortunately audio doesn't work at all, neither with VLC nor with Mplayer.
I read somewhere that there are some "slow" easycap devices with this problem,but I didn't understand if it can be fixed and how.

Thank you in advance for any help on the matter.

---

### Post by rmt1947 on 2010-09-28
Hi,

For the easycapdc60 driver at Sourceforge the "slow audio USB" problem was solved back in June:

[http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/3731294](http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/3731294)

The current version 0.8.3 of the driver is capable of delivering sound as well as video for all EasyCAPs which have USB ID 05e1:0408, provided the Linux distribution includes an OSS package or a means of emulating OSS.  Ubuntu 10.04 LTS meets this criterion, but as far as I know Ubuntu 10.10 does not:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/631885](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/631885)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300)

If you cannot see /dev/dsp on your system, the easycapdc60 driver and its test scripts will not deliver audio.

I should mention in passing that the Syntek EasyCAP with USB ID 05e1:0408 is not the only type of EasyCAP.  There also exists the Empia type, which has USB ID eb1a:2861 and is supported by the em28xx driver included in recent kernels.  The Empia EasyCAPs have been known to be silent, but (although I haven't tried it myself) I believe there is a simple cure:

[http://permalink.gmane.org/gmane.linux.drivers.video-input-infrastructure/21179](http://permalink.gmane.org/gmane.linux.drivers.video-input-infrastructure/21179)

Mike

---

### Post by Silix on 2010-09-29
> **rmt1947 said:**
> 

....

The current version 0.8.3 of the driver is capable of delivering sound as well as video for all EasyCAPs which have USB ID 05e1:0408, provided the Linux distribution includes an OSS package or a means of emulating OSS.  Ubuntu 10.04 LTS meets this criterion, but as far as I know Ubuntu 10.10 does not

....
 
Mike

Hi Mike, thank you for your prompt reply.

I can confirm that my device id is 05e1:0408. I'm running Xubuntu 10.04 and I tried to install OSS following some guides, but then I realized that my onboard audio is not supported,so I reinstalled ALSA.
Is there any way to use ALSA instead of OSS? What do you mean with "emulating OSS"?

> **rmt1947 said:**
> 
....

If you cannot see /dev/dsp on your system, the easycapdc60 driver and its test scripts will not deliver audio.

....
Mike

/dev/dsp is present. Any other thing to check?

---

### Post by rmt1947 on 2010-09-29
Hi,

I'm rather vague about Linux audio, so any advice I venture on this should be regarded as very tentative.

I have no experience of Xubuntu, so if this is an xfce-vs-Gnome issue I wouldn't have encountered it myself.

I have run Ubuntu 10.04 on several different machines here and (if I remember correctly) the driver gives problem-free audio on all of them, with various EasyCAPs, without the need for any special effort.  In fact, the output of the command `aptitude search oss` reveals that I have no extra OSS-related packages installed except for one associated with sox, which is not required for most uses of the driver:

```
p   alsa-oss                        - ALSA wrapper for OSS applications
p   alsaplayer-oss                  - PCM player designed for ALSA (OSS output m
p   audiooss                        - transparent OSS emulation over NAS
i   libsox-fmt-oss                  - SoX OSS format I/O library
p   oss-compat                      - OSS compatibility package
p   oss-preserve                    - Program to save/restore OSS mixer settings
p   oss4-base                       - Open Sound System - base package
p   oss4-dev                        - Open Sound System - development files
p   oss4-dkms                       - Open Sound System - DKMS module sources
p   oss4-gtk                        - Open Sound System - simple GTK2-based mixe
p   oss4-source                     - Open Sound System - drivers sources
p   python-oss                      - Open Sound System (OSS) interface for Pyth
p   solfege-oss                     - OSS sound module for GNU Solfege
p   tuxguitar-oss                   - tuxguitar plugin for sound playback using
p   xmms2-plugin-oss                - XMMS2 - OSS output
```

I conclude (again possibly wrongly) that on Ubuntu 10.04 the ALSA modules are, by default, willing and able to "emulate" OSS in some sense, or more specifically in the sense that a command line like

mplayer tv:// -tv driver=v4l2:norm=PAL_BGHIN:width=720:height=576:outfmt=uyvy:device=/dev/easycap0:input=0:fps=25:adevice=/dev/easysnd0:forceaudio:immediatemode=0 -hardframedrop -vo xv -ao oss -msglevel all=9

generates sound as well as video (note the "-ao oss").  (As I understand it, it is this generous behaviour of ALSA which is deliberately turned off in Ubuntu 10.10.)

So, as is often the case where audio is concerned, I'm mystified.  I cannot think of anything plausible which would cause muting on your machine.  When I run `alsamixer` I see that the "Master", "PCM", "Surround" and "Center" sliders are pushed way up, and the others are on zero, but I don't know what all this means.  Why is audio so complicated?

Mike

---

### Post by Culito on 2010-09-30
So I just bought an EasyCap.

Lsusb: 1c88:003c Somagic, Inc.

In Windows (I dual-boot) it is identified as a SM-USB 007.  In the device manager under audio/video devices it comes up as SMI-Grabber Device.
I have the windows 7 / vista disk for it but I had to go through the web service to find Xp drivers.  It comes up with video and audio but I have yet to actually record anything.

Anyone have any info on this (evidently new) version?

Thanks,
-C

---

### Post by anewguy on 2010-10-01
I have the Easycap that is listed as 05e1:0408 Syntek Semiconductor Co., Ltd .  I installed the driver from sourceforge and it works great with the test scripts included - mplayer, ntsc output.

Can anyone tell me the way to capture the video/audio stream to disk - does mplayer have such an option?

I want to capture my old VCR tapes and burn them to DVD.

Thanks in advance!
Dave ;)

---

### Post by rmt1947 on 2010-10-01
Hi Culito,

For the situation regarding SM-USB 007, please see:

[http://forum.easycap.co.uk/index.php/topic,495.0.html](http://forum.easycap.co.uk/index.php/topic,495.0.html)

As far as I know, there is no Linux driver for these EasyCAPs.

Mike

---

### Post by rmt1947 on 2010-10-01
Hi Dave,

There's a useful guide to recording with the 05e1:0408 EasyCAP on Linux here:

[http://easycap.blogspot.com/p/recording.html](http://easycap.blogspot.com/p/recording.html)


Mike

---

### Post by anewguy on 2010-10-01
> **rmt1947 said:**
> Hi Dave,

There's a useful guide to recording with the 05e1:0408 EasyCAP on Linux here:

[http://easycap.blogspot.com/p/recording.html](http://easycap.blogspot.com/p/recording.html)


Mike

Thanks!  I'm going over to check it out now!

Dave ;)

---

### Post by anewguy on 2010-10-01
Went to the link for recording - the download for the easyview-n-cap script does nothing.  I tried the first mencoder suggestion by copying and pasting the text into a terminal window (as all 1 chunk) and it fails as follows:

```

dave@dave-desktop:~$ mencoder tv:// -tv driver=v4l2:width=720:height=576:outfmt=uyvy:device=/dev/easycap0:input=0:fps=25:adevice=/dev/easysnd1:audiorate=48000:amode=1:forceaudio:immediatemode=0 -msglevel all=9
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team

Exiting... (No output file specified, please see the -o option.)
dave@dave-desktop:~$ -ffourcc DX50
-ffourcc: command not found
dave@dave-desktop:~$ -ovc lavc
-ovc: command not found
dave@dave-desktop:~$ -lavcopts vcodec=mpeg4:mbd=2:turbo:vbitrate=1200:keyint=15
-lavcopts: command not found
dave@dave-desktop:~$ -vf pp=lb,scale=640:480
-vf: command not found
dave@dave-desktop:~$ -oac mp3lame
-oac: command not found
dave@dave-desktop:~$ -o test.avi

```

Please note that while the output makes it look like I pasted in several independent lines I actually just did 1 paste of the entire thing.

Tried VLC as suggested and it never seems to start recording as my PC never hits the hard disk.  In addition, when I press "Play" it gives a message about the playlist being empty.


Dave

---

### Post by anewguy on 2010-10-02
Well, made the mencoder line a shell script so I wouldn't have to keep messing with it.  Also realized that after a reboot the kernel module wasn't getting reloaded, so will be adding that to modules file.

When I run the mencode shell script it goes through the initialization and then starts skipping frames - apparently ALL frames.  I don't know how to stop the thing so I did a cntrl-z.  Saw output file length was 0.  Killed the process - output file length still 0.

So:

(1) Is there some setting I need to adjust so it quits skipping frames?

(2) How do you terminate this when the video stream is finished playing?

Thanks again,

Dave ;)

---

### Post by rmt1947 on 2010-10-02
Hi Dave,

I haven't attempted any recording for some months, but I'll test that mencoder command with driver version 0.8.3 and report back here later today.

At present I don't know how to get the easycap module to load satisfactorily at boot time.  The problem is that if the snd_usb_audio module is registered (?) at boot time before (or with higher priority than?) the easycap module, you may find that when the EasyCAP is plugged in the snd_usb_audio has usurped the EasyCAP's audio channel and /dev/easysnd1 is not created.  This may not seem a big deal, but if you then try to run mplayer or mencoder with a command line which requests audio streaming from /dev/easysnd1 you will get no video as well as no audio.  I may have a fix for this in the next version of the driver, but I'm not sure yet.

The question about terminating mencoder cleanly has been asked on a couple of other forums before, but I don't remember seeing a good answer.  If the driver and mencoder get into a deadlock there may be no way out other than a `kill -9 ...` from another window.

Mike

---

### Post by rmt1947 on 2010-10-02
Hi Dave,

It seems necessary to add the "norm=..." parameter to the command line, because mencoder hangs otherwise, and the "fps=..." parameter needs to be adapted too.  It's probably also advisable to omit the "audiorate=48000" parameter because this isn't appropriate to those EasyCAPs which do not have a dedicated audio chip.  With these edits the result is:

```
mencoder tv:// -tv driver=v4l2:norm=NTSC_M:width=640:height=480:outfmt=uyvy:device=/dev/easycap0:input=0:fps=30:adevice=/dev/easysnd1:amode=1:forceaudio:immediatemode=0 -msglevel all=9 -ffourcc DX50 -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:turbo:vbitrate=1200:keyint=15 -vf pp=lb,scale=640:480 -oac mp3lame -o test.avi
```

Mike

---

### Post by anewguy on 2010-10-02
Hey, thanks for all the quick info!  I'll remember what you said about the module and just manually load it rather than put it in modules and then have it get out of sync.

I'll be trying the mencoder line in a little while, but I wanted to post a thank you first.

Thanks again!
Dave ;)

---

### Post by anewguy on 2010-10-04
Thanks again, Mike.

Tried the mencoder line (just copied it from your post and pasted in the .sh file).  Still getting frame drops - I copied what I could of the screen and will paste it here - a bunch of stuff rolled off the top of the buffer.

```

==========================================================================
Forcing output FourCC to 30355844 [DX50].
Building audio filter chain for 32000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 32000Hz/2ch/s16le
[libaf] Adding filter format 
[format] Changing sample format from little-endian 16-bit signed int to big-endian 8-bit signed int
[dummy] Was reinitialized: 32000Hz/2ch/s16le
[format] Changing sample format from little-endian 16-bit signed int to big-endian 8-bit signed int
LAME 3.98.2 32bits (http://www.mp3dev.org/)
CPU features: MMX (ASM used), 3DNow! (ASM used), SSE, SSE2
Using polyphase lowpass filter, transition band: 15613 Hz - 16000 Hz

misc:

	scaling: 1
	ch0 (left) scaling: 0
	ch1 (right) scaling: 0
	huffman search: normal
	experimental Y=0
	...

stream format:

	MPEG-1 Layer 3
	2 channel - joint stereo
	padding: all
	variable bitrate - VBR mtrh (default)
	...

psychoacoustic:

	using short blocks: channel coupled
	subblock gain: 1
	adjust masking: -7 dB
	adjust masking short: -4 dB
	quantization comparison: 9
	 ^ comparison short blocks: 9
	noise shaping: 1
	 ^ amplification: 0
	 ^ stopping: 0
	ATH: using
	 ^ type: 4
	 ^ shape: 1 (only for type 4)
	 ^ level adjustement: -0.75
	 ^ adjust type: 3
	 ^ adjust sensitivity power: 1.000000
	 ^ adapt threshold type: 2
	experimental psy tunings by Naoki Shibata
	   adjust masking bass=0 dB, alto=0 dB, treble=0 dB, sfb21=6.5 dB
	using temporal masking effect: no
	interchannel masking ratio: 0
	...

MP3 audio selected.
Building audio filter chain for 32000Hz/2ch/s16le -> 32000Hz/2ch/s16le...
[dummy] Was reinitialized: 32000Hz/2ch/s16le
[format] Changing sample format from little-endian 16-bit signed int to big-endian 8-bit signed int
[libaf] Removing filter format 
[dummy] Was reinitialized: 32000Hz/2ch/s16le
======= WAVE Format =======
Format Tag: 85 (0x55)
Channels: 2
Samplerate: 32000
avg byte/sec: 24000
Block align: 1152
bits/sample: 0
cbSize: 12
mp3.wID=1
mp3.fdwFlags=0x2
mp3.nBlockSize=1152
mp3.nFramesPerBlock=1
mp3.nCodecDelay=0
==========================================================================
Forcing audio preload to 0, max pts correction to 0.
ds_fill_buffer(d_video) called
v4l2: going to capture
DEMUX: Append packet to d_video, len=829440  pts=0.000  pos=0  [packs: A=0 V=1]
DEMUX: Append packet to d_video, len=829440  pts=0.000  pos=0  [packs: A=0 V=1]
*** [scale] Exporting mp_image_t, 720x576x16bpp YUV packed, 829440 bytes
(imgfmt: 59565955, planes: (nil),(nil),(nil) strides: 0,0,0, chroma: 0x0, shift: h:0,v:0)

Skipping frame!
ds_fill_buffer(d_video) calledps Trem:   0min   0mb  A-V:0.000 [0:0] A/Vms 0/0 D/B/S 0/1/1 
DEMUX: Append packet to d_video, len=829440  pts=0.000  pos=0  [packs: A=0 V=1]

Skipping frame!
ds_fill_buffer(d_video) calledps Trem:   0min   0mb  A-V:0.000 [0:0] A/Vms 0/0 D/B/S 0/2/2 
DEMUX: Append packet to d_video, len=829440  pts=0.000  pos=0  [packs: A=0 V=1]

Skipping frame!
ds_fill_buffer(d_video) calledps Trem:   0min   0mb  A-V:0.000 [0:0] A/Vms 0/0 D/B/S 0/3/3 
DEMUX: Append packet to d_video, len=829440  pts=0.000  pos=0  [packs: A=0 V=1]

Skipping frame!
ds_fill_buffer(d_video) calledps Trem:   0min   0mb  A-V:0.000 [0:0] A/Vms 0/0 D/B/S 0/4/4 
DEMUX: Append packet to d_video, len=829440  pts=0.000  pos=0  [packs: A=0 V=1]

Skipping frame!
ds_fill_buffer(d_video) calledps Trem:   0min   0mb  A-V:0.000 [0:0] A/Vms 0/0 D/B/S 0/5/5 
DEMUX: Append packet to d_video, len=829440  pts=0.000  pos=0  [packs: A=0 V=1]

Skipping frame!
ds_fill_buffer(d_video) calledps Trem:   0min   0mb  A-V:0.000 [0:0] A/Vms 0/0 D/B/S 0/6/6 
^Z
[3]+  Stopped                 ./mencoder_cap.sh
dave@dave-desktop:~/Downloads/easycap_dc60.0.8.3$ 

```

Thanks!

Dave ;)

BTW - if we get this working, I'd like to go over with you afterwards what all the options mean, why you selected them, etc., so I can try to get an understanding of this.  It's all new to me!

---

### Post by rmt1947 on 2010-10-04
Hi Dave,

That's strange - the mencoder command works fine on my Ubuntu 10.04.  If I understand the situation correctly, you are getting satisfactory video and sound when you run

./test.sh 5

but no output from mencoder.  That's puzzling, because in many respects mencoder is almost the same as mplayer - it differs only in that it sends the output to file rather than the screen.  If you have not already done so, it would be a good idea to check that `./test.sh 5` is successful for the actual videotape you are using for the mencoder tests - there might be something wrong with the tape itself.

The mencoder messages tell me incidentally that your EasyCAP has no dedicated audio chip (because the sound is 32000Hz, not 48000Hz), but they don't explain why frames are being skipped.  To capture all mencoder's messages to file, you can prepend "1>mc.out 2>mc.err" to the mencoder command, like this (all on one line):

```
1>mc.out 2>mc.err mencoder tv:// -tv driver=v4l2:norm=NTSC_M:width=640:height=480:outfmt=uyvy:device=/dev/easycap0:input=0:fps=30:adevice=/dev/easysnd1:amode=1:forceaudio:immediatemode=0 -msglevel all=9 -ffourcc DX50 -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:turbo:vbitrate=1200:keyint=15 -vf pp=lb,scale=640:480 -oac mp3lame -o test.avi
```

The messages will then appear in files mc.out and mc.err and can be perused at leisure after the run has finished.  I suspect, however, that the mencoder messages will not give a clear indication of what is going wrong, and it will probably be necessary to look instead at the messages written by the driver in file /var/log/kern.log.  You can open this file in your editor of choice and look for lines suggesting that the driver is in distress.  If you are comfortable with the vi editor, you can alternatively run ./tail.sh from the directory where the other easycap scripts are kept:  this will automatically extract the lines from /var/log/kern.log which are written by the driver and display them neatly within the editor.

Mike

---

### Post by anewguy on 2010-10-04
Thanks again, Mike.  I'll look at things later today when I'm at home again.  I'd sure like to get this to work, because indeed running ./test.sh 5 works fine - in fact, the video wasn't all jittery as it is in Windows (looks like it's dropping a lot of frames there as well so the video is jumpy), so I was hoping I'd be able to capture that "not-jittery" video and audio using ubuntu and burn to dvd.

About the audio - is it still going to be captured and play ok?  It plays fine with the test, so I assumed it would.

Audio/video files are something I have never known squat about, so I really appreciate the help!

Dave ;)

---

### Post by anewguy on 2010-10-05
Well, I have no idea what I did before, but I copied the latest mencoder line you provided, where you redirect the messages from mencoder to the 2 files, and it runs fine!  I replaced the line in the shell script with the line and the shell script runs fine also!

So, THANK YOU VERY MUCH!!!

Now, I've just got to figure out how to know when I'm at the end of the movie that's being recorded, but I know that will just be a matter of knowing the elapsed time.

It's interesting - running this through Ubuntu and mencoder, using the same VCR, the same tape and the same Easycap plugged into the same USB port, the output in Ubuntu doesn't look all choppy - just nice and smooth!  Doing this in Windows with the software supplied with the Easycap results in really choppy video, like it's dropping a lot of frames.  Maybe it's because it's playing it back on screen at the same time it is recording it, whereas with mencoder there is no video being played while recording (which is fine with me!).

So, could you perhaps explain the pieces of the mencoder line you provided that worked?  I'm sure this stuff is probably tucked away in some user guide somewhere, but giving that info with this example will help me understand, and perhaps help some others also.

Thanks again, Mike!!!

Dave ;)

---

### Post by rmt1947 on 2010-10-05
Hi Dave,

I'm relieved that it's working now - I wasn't at all confident about what to suggest next  :-)

You may be right about the MS-Windows driver overloading the hardware by displaying the video on screen at the same time as recording, although I must say a lot of people like this feature because the on-screen video gives reassurance that the recording is actually taking place.  Redirecting the mencoder messages to file with the "1>mc.out 2>mc.err" option also takes some load off the CPU:  in the default arrangement where the messages are written to screen the video subsystem has to do an appreciable amount of work to render the characters, fit them in the output window, etc.

I'm really not the person to advise on the optimization of the command line parameters for mencoder, because I very rarely do any recording nowadays either with mencoder or ffmpeg.  One of my objectives when deciding to write the driver was to allow the EasyCAP DC60 to generate good recordings, but when I actually came to experiment with recording earlier this year the results were rather disappointing.  I found that mencoder begins to drop frames after a while because its buffers get filled up.  One might expect ffmpeg to do better in this respect, but the disadvantage of ffmpeg is that there is an unacceptable loss of audio/video synchronisation.  My personal opinion is that recording with the EasyCAP on Linux is an unsolved problem, but I suppose it depends on the duration of the material to be recorded and what is regarded as acceptable quality.  Maybe I just didn't try hard enough to find the right recording parameters.

The command `man mencoder` brings up a very lengthy guide to the mencoder options which is intimidating at first, but spending 15 or 20 minutes looking through it is definitely worth the effort.  For example, you'll see that if you know in advance the duration of the recording, you can include a command-line parameter to tell mencoder when to stop: 

```

 -endpos <[[hh:]mm:]ss[.ms]|size[b|kb|mb]> (also see -ss and -sb)
              Stop at given time or byte position.
              NOTE: Byte position is enabled only for MEncoder and will not be
              accurate, as it can only stop at a frame boundary.  When used in
              conjunction with -ss option, -endpos time will shift forward  by
              seconds specified with -ss.

              EXAMPLE:
                 -endpos 56
                      Stop at 56 seconds.
                 -endpos 01:10:00
                      Stop at 1 hour 10 minutes.
                 -ss 10 -endpos 56
                      Stop at 1 minute 6 seconds.
                 -endpos 100mb
                      Encode only 100 MB.
```


Of course, knowing the syntax for setting the more sophisticated parameters isn't enough - you also need to know what values to give them, and here I guess you just have to do a bit of googling to see what is claimed to work.  There's some information in the Sourceforge thread

[http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/3534088](http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/3534088)

but you'll certainly want to look elsewhere too in order to get a balanced view.

Mike

---

### Post by anewguy on 2010-10-06
Well, I put in a ending position of 01:25:00 for 1 hour and 25 minutes, and indeed it seems to have stopped then.  The file on disk is under a gigabyte, yet when I try to open it in any of the media creators it says the file is almost 3 hours long.  The only program I've gotten to open it (besides mplayer of course) is devede, which still said it was huge (1.98 times the size of a 4.7 gb DVD).  I did the "adjust size" option in devede which immediately changed it to 99% and am trying the conversion now.  My past experience with devede is not good, and I really don't expect this to be any better (sound way out of sync with video), but we'll see.

I looked at the man pages for mencoder/mplayer and was wondering if there is a way to create a file that Windows Media Player can handle - my previous AVI outputs from mencoder cause WMP to choke.

Thanks!
Dave ;)

---

### Post by SteveDee on 2010-11-20
I'm having problems with this 'ere EasyCrap device, so I just want to check that its not a known driver issue before I send it back.

When I first plug it in and run using a command line like this:-
```

mplayer tv:// -tv device=/dev/video0:input=1:norm=PAL

```
it runs for 60-70s OK, and then the picture starts to break up, just like it has lost sync. After a short time, the video stops updating and the green light then goes off.

If I unplug it, then plug it back in and run the command again, it typically runs for 10-20s before stopping.

It appears that if I "let it cool down" then try again, it will run for 60-70s (so the cycle repeats).

Details:-
Tested on Lubuntu & Ubuntu 10.10
EzCap DC+ from Climax Digital (via Amazon)
ID eb1a:2861 eMPIA Technology, Inc.
From:-
```

dmesg | grep em28

```
I see this...em28xx #0: Board detected as EM2860/SAA711X Reference Design

Any clues (or a glimmer of hope) may save me postage!

---

### Post by rmt1947 on 2010-11-20
Hi,

We haven't heard much about the model DC60+/++ (USB eb1a:2861) on this forum - usually it's the cheaper model DC60 (USB ID 05e1:0408 ) which is discussed.

Three-quarters of an hour ago I plugged an EasyCAP DC60+ into a machine running kernel 2.6.36 on Ubuntu 10.04 and set it running with a videotape on the CVBS input, using the same command line as yours.  It's still working perfectly, and the EasyCAP itself is barely perceptibly warm.  I conclude that the Linux em28xx driver works fine. 

I'm inclined to suspect a hardware problem.  Does the EasyCAP misbehave on Microsoft Windows as well?

Mike

---

### Post by SteveDee on 2010-11-21
> **rmt1947 said:**
> ...and the EasyCAP itself is barely perceptibly warm.  I conclude that the Linux em28xx driver works fine....

Hi Mike, I understand you are a developer for the dc60 driver (not "+") so thanks for taking the time to do this test.

I did briefly try it on an old Windows XP test box (that is rarely used), and it crashed several times when I ran the "ShowBiz" software provided. On the one attempt when I managed to get into the capture view menu, it seemed to show video for a short time before crashing, but I couldn't be sure if the device stopped or the software crashed the system. So, not a brilliant test.

My unit does not feel very hot, but it is noticeably warm within a few seconds of starting capture. So I think an internal component may be over-heating and shutting down.

I'll try to contact Climax on Monday, but it looks like it is going back! Thanks once again.
Steve


-------
Update: I'm now sure its a hardware problem. If I suspend the module in front of a 12" desk fan running at full speed, it works fine.

---

### Post by nc101 on 2010-12-06
Hi,

We've been having problems with a similar easycap device. Again lsusb gives

```
ID eb1a:2861 eMPIA Technology, Inc.
```dmesg gives

```
[ 2187.340076] usb 1-6.7: new high speed USB device using ehci_hcd and address 14
[ 2187.432449] usb 1-6.7: configuration #1 chosen from 1 choice
[ 2187.432635] em28xx: New device @ 480 Mbps (eb1a:2861, interface 0, class 0)
[ 2187.432712] em28xx #0: chip ID is em2860
[ 2187.530083] em28xx #0: board has no eeprom
[ 2187.544458] em28xx #0: Identified as Unknown EM2750/28xx video grabber (card=1)
[ 2187.558709] em28xx #0: found i2c device @ 0x4a [saa7113h]
[ 2187.592336] em28xx #0: Your board has no unique USB ID.
[ 2187.592339] em28xx #0: A hint were successfully done, based on i2c devicelist hash.
[ 2187.592342] em28xx #0: This method is not 100% failproof.
[ 2187.592344] em28xx #0: If the board were missdetected, please email this log to:
[ 2187.592347] em28xx #0:     V4L Mailing List  <linux-media@vger.kernel.org>
[ 2187.592350] em28xx #0: Board detected as EM2860/SAA711X Reference Design
[ 2187.592353] em28xx #0: Registering snapshot button...
[ 2187.592484] input: em28xx snapshot button as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6.7/input/input21
[ 2187.956499] saa7115 3-0025: saa7113 found (1f7113d0e100000) @ 0x4a (em28xx #0)
[ 2188.664178] em28xx #0: Config register raw data: 0x10
[ 2188.689180] em28xx #0: AC97 vendor ID = 0x83847652
[ 2188.700058] em28xx #0: AC97 features = 0x6a90
[ 2188.700061] em28xx #0: Sigmatel audio processor detected(stac 9752)
[ 2189.160021] em28xx #0: v4l2 driver version 0.1.2
[ 2190.088136] em28xx #0: V4L2 video device registered as /dev/video0
[ 2190.088139] em28xx #0: V4L2 VBI device registered as /dev/vbi0
[ 2190.088206] em28xx audio device (eb1a:2861): interface 1, class 1

```which all looks the same as the SteveDees.

Works fine on windows. On Linux (Ubuntu 10.04) we get a couple of flickering pixels in the top right and that's all we get. I've got a couple of the devices and they're both the same (from [www.ezcap.tv]("http://www.ezcap.tv")). They do get a bit hot after a while, but even while cold the image is the same.

Any ideas of things I could try? I tried various card=xx settings using cards with EM2861 in em28xx.h, but no effect (do I have to replug USB after I do modprobe? and should I always do modprobe -r first or not?)

TBH we've had a nightmare with USB based capture devices, and are still trying to find one that's reliable. We started out with an easycap with the STK  1160 chip, but that died after a week's use. We then ordered a handful of what we thought were the same, but they turned out to have somagic chips which don't work at all. We were hoping that these empia ones would be pain-free, but I guess not.

It gets worse too as we really want to use these things on ARM boards with the 2.6.31 kernel, and we experience a lot of crashes in the driver. We're told it'd be better with an updated kernel, but the board manufacturers don't support anything more recent (yet).

---

### Post by nc101 on 2010-12-06
ah, modprobe em28xx card=35 makes it works

a bit bizarre, that's the same card number we had to use for the STK 1160 chips to work. I went through all the EM2861_* cards, but nothing worked with those. At least it's going now I guess...

---

### Post by Crazy K on 2010-12-06
I just got the EasyCap in the mail today and I'm trying to get it to work on my computer; Ubuntu 10.04 Lucid Lynx. I made a thread here: [http://ubuntuforums.org/showthread.php?p=10207371#post10207371](http://ubuntuforums.org/showthread.php?p=10207371#post10207371) 

Here's the lsusb output for mine: 

```
Bus 001 Device 008: ID 05e1:0408 Syntek Semiconductor Co., Ltd STK1160 Video Capture Device
Bus 001 Device 005: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 004: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 001 Device 003: ID 04b3:3025 IBM Corp. 
Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Says it's there. 

I already extracted the drivers into my home folder as well.

---

### Post by SteveDee on 2010-12-08
> **nc101 said:**
> ah, modprobe em28xx card=35 makes it works

a bit bizarre, that's the same card number we had to use for the STK 1160 chips to work. I went through all the EM2861_* cards, but nothing worked with those. At least it's going now I guess...

Having read your comments, I've just tried my EzCap on a system running Ubuntu 10.04 with kernel 2.6.32-24 and I can view video via terminal command:-
```

steve@steve-laptop:~$ mplayer tv:// -tv device=/dev/video0:driver=v4l2:input=1:norm=PAL

```
It also works on 10.10 (2.6.32-25), again without using modprobe. So I guess your earlier kernel is causing problems.

I have yet to find a way to capture sound.

Here are a couple of packages you may find useful (install from Synaptic):-
v4l-conf
v4l2ucp

From a terminal type:-
```

v4l-info > EasyCap

```

This will create a text file (EasyCap) in your home folder which provides information on supported analogue encodings, inputs modes & so on.

The 2nd package will install the Video4Linux Control Panel, is useful for testing (you can launch by right clicking on /dev/video*).

---

### Post by zonemikel on 2010-12-13
Hello everyone, been reading this thread all day and still no luck. Basically I got the driver and run the mplayer command but I just get a green screen. I have the dc60 with the four plugs for video. I'm using ubuntu 10.04

here is my basic info
```
Bus 001 Device 005: ID 05e1:0408 Syntek Semiconductor Co., Ltd
```

I downloaded the syntek driver and installed it as a bunch of other people have on this thread by using svn and then running make and finally insmod stk11, i already have it running see. 
```
zonemikel@michael-PC:~/syntekdriver$ sudo insmod stk11xx.ko
insmod: error inserting 'stk11xx.ko': -1 File exists
```

then i run the mplayer command and I just get a green screen. It always says i'm using input 4 and that pal and ntsc are "bogus" see here
```
zonemikel@michael-PC:~/syntekdriver$ mplayer tv:// -tv device=/dev/video0:driver=v4l2:input=4:norm=NSTC
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Syntek USB Video Camera
 Capabilites:  video capture  read/write  streaming
 supported norms: 0 = webcam;
 inputs: 0 = Input1; 1 = Input2; 2 = Input3; 3 = Input4;
 Current input: 4
 Current format: BGR24
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl enum input failed: Invalid argument
tv.c: norm_from_string(NSTC): Bogus norm parameter, setting default.
Selected input hasn't got a tuner!
v4l2: Cannot get fps
v4l2: ioctl set mute failed: Invalid argument
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Packed UYVY)
VDec: using Packed UYVY as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Packed UYVY 
Selected video codec: [rawuyvy] vfm: raw (RAW UYVY)
==========================================================================
Audio: no sound
Starting playback...
v4l2: select timeout
V:   0.0   2/  2 ??% ??% ??,?% 0 0 

```

I've tried VLC also to no avail. Any help would be great because i'm lost ... spent two days on this already!

---

### Post by rmt1947 on 2010-12-13
Hi,

There is an alternative Linux driver for the EasyCAP DC60 with USB ID 05e1:0408 at:

[http://sourceforge.net/projects/easycapdc60/](http://sourceforge.net/projects/easycapdc60/)

In my experience, this works well on Ubuntu 10.04 LTS.  There is no sound on Ubuntu 10.10 yet (I'm working on it).

Mike

---

### Post by Crazy K on 2010-12-13
> **rmt1947 said:**
> Hi,

There is an alternative Linux driver for the EasyCAP DC60 with USB ID 05e1:0408 at:

[http://sourceforge.net/projects/easycapdc60/](http://sourceforge.net/projects/easycapdc60/)

In my experience, this works well on Ubuntu 10.04 LTS.  There is no sound on Ubuntu 10.10 yet (I'm working on it).

How do you install a tar.gz file and use it? I could never get them to work properly.

---

### Post by SteveDee on 2010-12-13
> **zonemikel said:**
> ...then i run the mplayer command and I just get a green screen. It always says i'm using input 4 and that pal and ntsc are "bogus" ...

Open Synaptic and install:-
v4l-conf

With your DC60 connected, open a terminal and enter:-
```

v4l-info > myDetails

```

This should create a "myDetails" file in your home folder.

Now post the "myDetails" text file on this thread.

---

### Post by zonemikel on 2010-12-13
> **SteveDee said:**
> Open Synaptic and install:-
v4l-conf

With your DC60 connected, open a terminal and enter:-
```

v4l-info > myDetails

```This should create a "myDetails" file in your home folder.

Now post the "myDetails" text file on this thread.

I installed the "alternate driver" as suggested above, everything went ok but when i run the test scripts I still get a green screen and no output. I plug my video into all the different channels and get nothing. With the vlc test scripts nothing ever comes up on the screen. 

Here is the info from v4l ... belive it or not I actually have been studying video for a while for another project, i know all about the encryption and how this stuff works. If we can figure this out and get a consensus maybe I could write up a guide on how to do this on my blog. 
```
### v4l2 device info [/dev/easycap0] ###
general info
    VIDIOC_QUERYCAP
    driver                  : "easycap"
    card                    : "EasyCAP DC60"
    bus_info                : "usb-0000:00:1f.2-1.3.1"
    version                 : 0.8.5
    capabilities            : 0x5020001 [VIDEO_CAPTURE,AUDIO,READWRITE,STREAMING]

standards
    VIDIOC_ENUMSTD(0)
    index                   : 0
    id                      : 0x21d [PAL_B,PAL_G,PAL_H,PAL_I,PAL_N]
    name                    : "PAL_BGHIN"
    frameperiod.numerator   : 1
    frameperiod.denominator : 25
    framelines              : 625
    VIDIOC_ENUMSTD(1)
    index                   : 1
    id                      : 0x1000000000 [(null)]
    name                    : "NTSC_N_443"
    frameperiod.numerator   : 1
    frameperiod.denominator : 25
    framelines              : 480
    VIDIOC_ENUMSTD(2)
    index                   : 2
    id                      : 0x400 [PAL_Nc]
    name                    : "PAL_Nc"
    frameperiod.numerator   : 1
    frameperiod.denominator : 25
    framelines              : 625
    VIDIOC_ENUMSTD(3)
    index                   : 3
    id                      : 0x2000000000 [(null)]
    name                    : "NTSC_N"
    frameperiod.numerator   : 1
    frameperiod.denominator : 25
    framelines              : 525
    VIDIOC_ENUMSTD(4)
    index                   : 4
    id                      : 0xff0000 [SECAM_B,SECAM_D,SECAM_G,SECAM_H,SECAM_K,SECAM_K1,SECAM_L,?ATSC_8_VSB]
    name                    : "SECAM"
    frameperiod.numerator   : 1
    frameperiod.denominator : 25
    framelines              : 625
    VIDIOC_ENUMSTD(5)
    index                   : 5
    id                      : 0x1000 [NTSC_M]
    name                    : "NTSC_M"
    frameperiod.numerator   : 1
    frameperiod.denominator : 30
    framelines              : 525
    VIDIOC_ENUMSTD(6)
    index                   : 6
    id                      : 0x2000 [NTSC_M_JP]
    name                    : "NTSC_M_JP"
    frameperiod.numerator   : 1
    frameperiod.denominator : 30
    framelines              : 525
    VIDIOC_ENUMSTD(7)
    index                   : 7
    id                      : 0x800 [PAL_60]
    name                    : "PAL_60"
    frameperiod.numerator   : 1
    frameperiod.denominator : 30
    framelines              : 525
    VIDIOC_ENUMSTD(8)
    index                   : 8
    id                      : 0x4000 [?]
    name                    : "NTSC_443"
    frameperiod.numerator   : 1
    frameperiod.denominator : 30
    framelines              : 525
    VIDIOC_ENUMSTD(9)
    index                   : 9
    id                      : 0x100 [PAL_M]
    name                    : "PAL_M"
    frameperiod.numerator   : 1
    frameperiod.denominator : 30
    framelines              : 525
    VIDIOC_ENUMSTD(10)
    index                   : 10
    id                      : 0x10000021d [PAL_B,PAL_G,PAL_H,PAL_I,PAL_N,(null)]
    name                    : "PAL_BGHIN_SLOW"
    frameperiod.numerator   : 1
    frameperiod.denominator : 5
    framelines              : 625
    VIDIOC_ENUMSTD(11)
    index                   : 11
    id                      : 0x1100000000 [(null),(null)]
    name                    : "NTSC_N_443_SLOW"
    frameperiod.numerator   : 1
    frameperiod.denominator : 5
    framelines              : 480
    VIDIOC_ENUMSTD(12)
    index                   : 12
    id                      : 0x100000400 [PAL_Nc,(null)]
    name                    : "PAL_Nc_SLOW"
    frameperiod.numerator   : 1
    frameperiod.denominator : 5
    framelines              : 625
    VIDIOC_ENUMSTD(13)
    index                   : 13
    id                      : 0x2100000000 [(null),(null)]
    name                    : "NTSC_N_SLOW"
    frameperiod.numerator   : 1
    frameperiod.denominator : 5
    framelines              : 525
    VIDIOC_ENUMSTD(14)
    index                   : 14
    id                      : 0x100ff0000 [SECAM_B,SECAM_D,SECAM_G,SECAM_H,SECAM_K,SECAM_K1,SECAM_L,?ATSC_8_VSB,(null)]
    name                    : "SECAM_SLOW"
    frameperiod.numerator   : 1
    frameperiod.denominator : 5
    framelines              : 625
    VIDIOC_ENUMSTD(15)
    index                   : 15
    id                      : 0x100001000 [NTSC_M,(null)]
    name                    : "NTSC_M_SLOW"
    frameperiod.numerator   : 1
    frameperiod.denominator : 6
    framelines              : 525
    VIDIOC_ENUMSTD(16)
    index                   : 16
    id                      : 0x100002000 [NTSC_M_JP,(null)]
    name                    : "NTSC_M_JP_SLOW"
    frameperiod.numerator   : 1
    frameperiod.denominator : 6
    framelines              : 525
    VIDIOC_ENUMSTD(17)
    index                   : 17
    id                      : 0x100000800 [PAL_60,(null)]
    name                    : "PAL_60_SLOW"
    frameperiod.numerator   : 1
    frameperiod.denominator : 6
    framelines              : 525
    VIDIOC_ENUMSTD(18)
    index                   : 18
    id                      : 0x100004000 [?,(null)]
    name                    : "NTSC_443_SLOW"
    frameperiod.numerator   : 1
    frameperiod.denominator : 6
    framelines              : 525
    VIDIOC_ENUMSTD(19)
    index                   : 19
    id                      : 0x100000100 [PAL_M,(null)]
    name                    : "PAL_M_SLOW"
    frameperiod.numerator   : 1
    frameperiod.denominator : 6
    framelines              : 525

inputs
    VIDIOC_ENUMINPUT(0)
    index                   : 0
    name                    : "CVBS0"
    type                    : CAMERA
    audioset                : 1
    tuner                   : 0
    std                     : 0xffb0ff [PAL_B,PAL_B1,PAL_G,PAL_H,PAL_I,PAL_D,PAL_D1,PAL_K,NTSC_M,NTSC_M_JP,?,SECAM_B,SECAM_D,SECAM_G,SECAM_H,SECAM_K,SECAM_K1,SECAM_L,?ATSC_8_VSB]
    status                  : 0x0 []
    VIDIOC_ENUMINPUT(1)
    index                   : 1
    name                    : "CVBS1"
    type                    : CAMERA
    audioset                : 1
    tuner                   : 0
    std                     : 0xffb0ff [PAL_B,PAL_B1,PAL_G,PAL_H,PAL_I,PAL_D,PAL_D1,PAL_K,NTSC_M,NTSC_M_JP,?,SECAM_B,SECAM_D,SECAM_G,SECAM_H,SECAM_K,SECAM_K1,SECAM_L,?ATSC_8_VSB]
    status                  : 0x0 []
    VIDIOC_ENUMINPUT(2)
    index                   : 2
    name                    : "CVBS2"
    type                    : CAMERA
    audioset                : 1
    tuner                   : 0
    std                     : 0xffb0ff [PAL_B,PAL_B1,PAL_G,PAL_H,PAL_I,PAL_D,PAL_D1,PAL_K,NTSC_M,NTSC_M_JP,?,SECAM_B,SECAM_D,SECAM_G,SECAM_H,SECAM_K,SECAM_K1,SECAM_L,?ATSC_8_VSB]
    status                  : 0x0 []
    VIDIOC_ENUMINPUT(3)
    index                   : 3
    name                    : "CVBS3"
    type                    : CAMERA
    audioset                : 1
    tuner                   : 0
    std                     : 0xffb0ff [PAL_B,PAL_B1,PAL_G,PAL_H,PAL_I,PAL_D,PAL_D1,PAL_K,NTSC_M,NTSC_M_JP,?,SECAM_B,SECAM_D,SECAM_G,SECAM_H,SECAM_K,SECAM_K1,SECAM_L,?ATSC_8_VSB]
    status                  : 0x0 []
    VIDIOC_ENUMINPUT(4)
    index                   : 4
    name                    : "CVBS4"
    type                    : CAMERA
    audioset                : 1
    tuner                   : 0
    std                     : 0xffb0ff [PAL_B,PAL_B1,PAL_G,PAL_H,PAL_I,PAL_D,PAL_D1,PAL_K,NTSC_M,NTSC_M_JP,?,SECAM_B,SECAM_D,SECAM_G,SECAM_H,SECAM_K,SECAM_K1,SECAM_L,?ATSC_8_VSB]
    status                  : 0x0 []
    VIDIOC_ENUMINPUT(5)
    index                   : 5
    name                    : "S-VIDEO"
    type                    : CAMERA
    audioset                : 1
    tuner                   : 0
    std                     : 0xffb0ff [PAL_B,PAL_B1,PAL_G,PAL_H,PAL_I,PAL_D,PAL_D1,PAL_K,NTSC_M,NTSC_M_JP,?,SECAM_B,SECAM_D,SECAM_G,SECAM_H,SECAM_K,SECAM_K1,SECAM_L,?ATSC_8_VSB]
    status                  : 0x0 []

video capture
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
    index                   : 0
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "uyvy"
    pixelformat             : 0x59565955 [UYVY]
    VIDIOC_ENUM_FMT(1,VIDEO_CAPTURE)
    index                   : 1
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "yuy2"
    pixelformat             : 0x56595559 [YUYV]
    VIDIOC_ENUM_FMT(2,VIDEO_CAPTURE)
    index                   : 2
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "rgb24"
    pixelformat             : 0x33424752 [RGB3]
    VIDIOC_ENUM_FMT(3,VIDEO_CAPTURE)
    index                   : 3
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "rgb32"
    pixelformat             : 0x34424752 [RGB4]
    VIDIOC_ENUM_FMT(4,VIDEO_CAPTURE)
    index                   : 4
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "bgr24"
    pixelformat             : 0x33524742 [BGR3]
    VIDIOC_ENUM_FMT(5,VIDEO_CAPTURE)
    index                   : 5
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "bgr32"
    pixelformat             : 0x34524742 [BGR4]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
    type                    : VIDEO_CAPTURE
    fmt.pix.width           : 720
    fmt.pix.height          : 576
    fmt.pix.pixelformat     : 0x56595559 [YUYV]
    fmt.pix.field           : NONE
    fmt.pix.bytesperline    : 2880
    fmt.pix.sizeimage       : 1658880
    fmt.pix.colorspace      : 470_SYSTEM_BG
    fmt.pix.priv            : 0

controls
    VIDIOC_QUERYCTRL(BASE+0)
    id                      : 9963776
    type                    : INTEGER
    name                    : "Brightness"
    minimum                 : 0
    maximum                 : 255
    step                    : 1
    default_value           : 127
    flags                   : 0
    VIDIOC_QUERYCTRL(BASE+1)
    id                      : 9963777
    type                    : INTEGER
    name                    : "Contrast"
    minimum                 : 0
    maximum                 : 255
    step                    : 1
    default_value           : 191
    flags                   : 0
    VIDIOC_QUERYCTRL(BASE+2)
    id                      : 9963778
    type                    : INTEGER
    name                    : "Saturation"
    minimum                 : 0
    maximum                 : 255
    step                    : 1
    default_value           : 175
    flags                   : 0
    VIDIOC_QUERYCTRL(BASE+3)
    id                      : 9963779
    type                    : INTEGER
    name                    : "Hue"
    minimum                 : 0
    maximum                 : 255
    step                    : 1
    default_value           : 128
    flags                   : 0

```here is the log from running the test script. it seems like everything is ok maybe i just have a crappy video card or something that does not let me see whats going through the media player. I am going to try it on another pc with ubuntu installed and see if that has any difference 

```
install.sh        Makefile           README.ZM          src                 testNTSC.sh       tvtime_NTSC.xml  vlcPAL.sh
zonemikel@michael-PC:~/easycap/easycap_dc60.0.8.5$ cat testeasycap0.log 
Config pushed level is now 2
Config pushed level is now 3
Setting tv=driver=v4l2:norm=NTSC_M:width=640:height=480:outfmt=uyvy:device=/dev/easycap0:input=1:fps=30:adevice=/dev/easysnd1:forceaudio:immediatemode=0
Setting hardframedrop=-vo
Setting vo=xv
Setting ao=oss
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 2
CPU:  (Family: 6, Model: 8, Stepping: 6)
Detected cache-line size is 32 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 0 SSSE3: 0
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/zonemikel/.mplayer/codecs.conf'
Reading /home/zonemikel/.mplayer/codecs.conf: Can't open '/home/zonemikel/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --target=i586-linux --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
CommandLine: 'tv://' '-tv' 'driver=v4l2:norm=NTSC_M:width=640:height=480:outfmt=uyvy:device=/dev/easycap0:input=1:fps=30:adevice=/dev/easysnd1:forceaudio:immediatemode=0' '-hardframedrop' '-vo' 'xv' '-ao' 'oss' '-msglevel' 'all=9'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/zonemikel/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/zonemikel/.mplayer/input.conf'
Can't open input config file /home/zonemikel/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('.conf') -> '/home/zonemikel/.mplayer/.conf'

[[[init getch2]]]

Playing tv://.
get_path('sub/') -> '/home/zonemikel/.mplayer/sub/'
STREAM: [tv] tv://
STREAM: Description: TV Input
STREAM: Author: Benjamin Zores, Albeu
STREAM: Comment: 
seek to 0x0
s->pos=0  newpos=0  new_bufpos=0  buflen=0  
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: video fd: /dev/easycap0: 3
Selected device: EasyCAP DC60
 Capabilites:  video capture  audio  read/write  streaming
 supported norms: 0 = PAL_BGHIN; 1 = NTSC_N_443; 2 = PAL_Nc; 3 = NTSC_N; 4 = SECAM; 5 = NTSC_M; 6 = NTSC_M_JP; 7 = PAL_60; 8 = NTSC_443; 9 = PAL_M; 10 = PAL_BGHIN_SLOW; 11 = NTSC_N_443_SLOW; 12 = PAL_Nc_SLOW; 13 = NTSC_N_SLOW; 14 = SECAM_SLOW; 15 = NTSC_M_SLOW; 16 = NTSC_M_JP_SLOW; 17 = PAL_60_SLOW; 18 = NTSC_443_SLOW; 19 = PAL_M_SLOW;
 inputs: 0 = CVBS0; 1 = CVBS1; 2 = CVBS2; 3 = CVBS3; 4 = CVBS4; 5 = S-VIDEO;
 Current input: 0
 Format UYVY   (16 bits, uyvy): Packed UYVY
 Format YUYV   (16 bits, yuy2): Packed YUY2
 Format RGB24  (24 bits, rgb24): RGB 24-bit
 Format RGB32  (32 bits, rgb32): RGBA
 Format BGR24  (24 bits, bgr24): BGR 24-bit
 Format BGR32  (32 bits, bgr32): BGRA
 Current format: UYVY
v4l2: set format: UYVY
v4l2: set input: 1
Selected norm : NTSC_M
v4l2: set norm: NTSC_M
v4l2: set width: 640
v4l2: set height: 480
Selected input hasn't got a tuner!
==> Found video stream: 0
v4l2: get format: UYVY
v4l2: get fps: 30.000000
v4l2: get width: 640
v4l2: get height: 480
ioctl dsp getfmt: 0
Supported formats: 10
ioctl dsp setfmt: 0
ioctl dsp stereo: 0 (req: 1)
ioctl dsp speed: 0
ioctl dsp trigger: 0
trigger: 1
ioctl dsp trigger: 0
ioctl dsp getblocksize: 0
blocksize: 16384
v4l2: set audio samplerate: 44100
v4l2: get audio format: 9
==> Found audio stream: 0
v4l2: get audio samplerate: 32000
v4l2: get audio samplesize: 2
v4l2: get audio channels: 2
  TV audio: 2 channels, 16 bits, 32000 Hz
Audio capture - buffer 256 blocks of 16384 bytes, skew average from 16 meas.
Using a ring buffer for maximum 211 frames, 123 MB total size.
v4l2: set Brightness: 127 [0, 255]
v4l2: set Hue: 128 [0, 255]
v4l2: set Saturation: 175 [0, 255]
v4l2: set Contrast: 191 [0, 255]
[V] filefmt:9  fourcc:0x59565955  size:640x480  fps:30.000  ftime:=0.0333
get_path('sub/') -> '/home/zonemikel/.mplayer/sub/'
X11 opening display: :0.0
vo: X11 color mask:  FFFF  (R:F800 G:7E0 B:1F)
vo: X11 running at 1024x768 with depth 16 and 16 bpp (":0.0" => local display)
[x11] Detected wm supports layers.
[x11] Detected wm supports NetWM.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports STAYS_ON_TOP state.
[x11] Current fstype setting honours LAYER FULLSCREEN STAYS_ON_TOP ABOVE BELOW X atoms
[VO_XV] Using Xv Adapter #0 (I810 Video Overlay)
[xv common] Drawing colorkey manually.
[xv common] Using colorkey from Xv (0x00083e).
[xv common] Maximum source image dimensions: 1440x1080
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Packed UYVY)
Trying filter chain: vo
vo_debug: query(Packed UYVY) returned 0x437 (i=0) 
VDec: using Packed UYVY as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO Config (640x480->640x480,flags=0,'MPlayer',0x59565955)
VO: [xv] 640x480 => 640x480 Packed UYVY 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x35315652 (RV15) packed
Xvideo image format: 0x36315652 (RV16) packed
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
using Xvideo port 63 for hw scaling
Selected video codec: [rawuyvy] vfm: raw (RAW UYVY)
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
dec_audio: Allocating 2048 + 65536 = 67584 bytes for output buffer.
AUDIO: 32000 Hz, 2 ch, s16le, 1024.0 kbit/100.00% (ratio: 128000->128000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
Building audio filter chain for 32000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 32000Hz/2ch/s16le
[dummy] Was reinitialized: 32000Hz/2ch/s16le
Trying preferred audio driver 'oss', options '[none]'
ao2: 32000 Hz  2 chans  s16le
audio_setup: using '/dev/dsp' dsp device
audio_setup: using '/dev/mixer' mixer device
audio_setup: using 'pcm' mixer device
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
Failed to initialize audio driver 'oss'
Could not open/initialize audio device -> no sound.

*** uninit(0x400)
Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: pcm
Audio: no sound
Freeing 0 unused audio chunks.
Starting playback...
ds_fill_buffer(d_video) called
v4l2: going to capture
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
*** [vo] Exporting mp_image_t, 640x480x16bpp YUV packed, 614400 bytes
(imgfmt: 59565955, planes: (nil),(nil),(nil) strides: 0,0,0, chroma: 0x0, shift: h:0,v:0)
Unicode font: 5025 glyphs.
Unicode font: 5025 glyphs.
OSD chg: 6  V: no  pb:-1  
OSD chg: 3  V: no  pb:-1  
OSD chg: 2  V: no  pb:-1  
*** ftime=0.000 ***
Warping cursor to disable gnome-screensaver.
ds_fill_buffer(d_video) called 0 0 
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
ds_fill_buffer(d_video) called 0 0 
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
ds_fill_buffer(d_video) called 0 0 
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
ds_fill_buffer(d_video) called 0 0 
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
ds_fill_buffer(d_video) called 0 0 
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
ds_fill_buffer(d_video) called 0 0 
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
ds_fill_buffer(d_video) called 0 0 
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
ds_fill_buffer(d_video) called 0 0 
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
ds_fill_buffer(d_video) called 0 0 
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
ds_fill_buffer(d_video) called 0 0 
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
ds_fill_buffer(d_video) called 0 0 
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
ds_fill_buffer(d_video) called 0 0 
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
ds_fill_buffer(d_video) called 0 0 
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
ds_fill_buffer(d_video) called 0 0 
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
ds_fill_buffer(d_video) called 0 0 
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
ds_fill_buffer(d_video) called 0 0 
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
ds_fill_buffer(d_video) called 0 0 


MPlayer interrupted by signal 2 in module: video_read_frame
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
OSD chg: 6  V: no  pb:-1  
*** ftime=0.000 ***
V:   0.0  18/ 18 ??% ??% ??,?% 0 0 
*** uninit(0xAC9)
Uninit video: raw
DEMUXER: freeing demuxer at 0x8f3e528


MPlayer interrupted by signal 2 in module: free_demuxer[
```thanks for the help so far ... :popcorn:

// on my other pc this is what I did 
```

michael@uspc:~/Desktop/easycap_dc60.0.8.5$ sudo ./install.sh
kernel directory is /lib/modules/2.6.32-26-generic/build
not overwriting top level Makefile
unlocked_ioctl not required
not overwriting src/Makefile
not overwriting tools/Makefile
make clean OK
make OK
depmod OK
copied OK
depmod OK
unlocked_ioctl required
creating /etc/modprobe.d/easycap.conf
modprobe OK
creating /etc/udev/rules.d/57-easycap.rules
michael@uspc:~/Desktop/easycap_dc60.0.8.5$ lsmod | grep easycap
easycap              1246874  0 
michael@uspc:~/Desktop/easycap_dc60.0.8.5$ ls /dev/easy*
/dev/easycap0  /dev/easysnd1
michael@uspc:~/Desktop/easycap_dc60.0.8.5$ 
michael@uspc:~/Desktop/easycap_dc60.0.8.5$ ./test4NTSC.sh 1
Devices are:  /dev/easycap0  /dev/easysnd1
Log file is:  ./testeasycap0.log

```And it works fine ... ??!!! i see the video just fine.

The only difference between the two pc's is one is runing ubuntu desktop the other (non working one) is running ubuntu server. They are both running 10.04 LTS but the one where the video shows green is running fvwm-crystal. 

I guess I should install gnome desktop on the one downstairs and try again to see if that works.

.................

also has anyone gotten this to work with zoneminder, do you know what settings to use. Even on the pc where it works with mplayer it does not show up in zoneminder i was using yuyv and 320x240 but it just shows a broken image when i try to view it in zoneminder.

---

### Post by rmt1947 on 2010-12-14
Hi zonemikel,

Thanks for the detailed report, it's interesting.  Before uploading any new version of the driver I test it on machines running the desktop distributions of Debian Lenny, Ubuntu 10.04 and 10.10 and OpenSUSE 11.2.  I've never tried the driver on Ubuntu Server, because it did not occur to me that the server version of Ubuntu might be significantly different from the desktop version.

The mplayer output obtained with your Ubuntu Server shows failure of the audio stream because /dev/dsp is missing:

```
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
Failed to initialize audio driver 'oss'
Could not open/initialize audio device -> no sound.
```

In these circumstances (the same problem arises on Ubuntu 10.10 desktop until I fix it) scripts such as ./test4NTSC.sh will not work as intended, and it is necessary to run mplayer manually with a simplified command line like this:

```
mplayer tv:// -tv driver=v4l2:norm=NTSC_M:width=640:height=480:outfmt=uyvy:device=/dev/easycap0:input=1:fps=30:noaudio -hardframedrop -vo xv
```

If with this command you still don't see any video on Ubuntu Server, further diagnosis probably involves looking in the file /var/log/kern.log or /var/log/messages for lines containing the string "easycap" which provide clues to driver distress.  The script ./tail.sh can be used, if you wish, to automatically extract easycap information from the logfile in a form suitable for posting on discussion forums (after deleting any confidential information in the logfile, of course).

I personally have succeeded in getting driver version 0.8.5 working with ZoneMinder using the settings mentioned in file README.ZM, but I must admit it was difficult, and the final result was not brilliant:  I could do no better than about 1 frame per second for each of two video cameras.  As far as I can tell, this is a hardware limitation which is difficult or impossible to overcome in software.  At least one other person has had success with ZoneMinder:

[http://www.zoneminder.com/forums/viewtopic.php?t=16639](http://www.zoneminder.com/forums/viewtopic.php?t=16639)

but otherwise I have not had much positive feedback on use of the driver with ZoneMinder.

I'd be interested in seeing a link to your blog if you decide to comment on your experiences.  You may find that the blog (it's not mine) at

[http://easycap.blogspot.com](http://easycap.blogspot.com)

provides a useful guide to some EasyCAP issues.

Mike

---

### Post by zonemikel on 2010-12-14
rmt1947, 
  Thanks for your help. You have clearly spent a lot of time on this. I've never written a driver, I should try it some time to see what it involves. 

  So on my upstairs computer with 10.04-ubuntu everything works as expected. But on my server that i use downstairs all i get is a green screen. I've tried whatching normal movies with mplayer and that works. I tried that last command you gave with nosound and i still get the same green screen. 

  I'm pretty sure its something to do with the hardware on this computer or the fact that its runniing ubuntu server. I did install ubuntu-desktop and that didnt seem to help anything. 

  I did find that there is a /dev/dsp1 .... i think it showed up after installing ubuntu-desktop. Also now when I plug in the easycap the /dev/easysnd is not created just he /dev/easycap0. 

  this same server is my web server so i installed another hdd just to put 10.04 server on it thinking i would solve my problems. Unfortunately i have to disable this hard drive and let it run as it was before because i have run out of time. I have several things going on and i've spent too much time on this already. Spent all morning looking for the readme.zm file ... i thought it came with zoneminder just now found i in the driver folder :(

  When/if I have more time i will install ubuntu desktop on this same machine and test it on that. But I cant say when I will be able too. Thanks for all your help so far ! I wish I had server installed on another machine to determine if its server or hardware causing the problems. 

here is the info from tail maybe it can help someone. 

```
 easycap_module_init: ========easycap=======
 easycap_module_init: version: 0.8.5
0easycap_usb_probe: allocated 0xD75A0000=peasycap
0adjust_standard: selected standard: PAL_BGHIN
0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x00=std mask
0adjust_format: sought:    V4L2_FIELD_NONE
0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
0adjust_brightness: adjusting brightness to  0x7F
0adjust_contrast: adjusting contrast to  0x3F
0adjust_saturation: adjusting saturation to  0x2F
0adjust_hue: adjusting hue to  0x00
0easycap_usb_probe: easycap attached to minor #192
Dec 14 10:06:58 michael-PC kernel: [ 1202.111403] usbcore: registered new interface driver snd-usb-audio
Dec 14 10:06:58 michael-PC kernel: [ 1202.116735] usbcore: registered new interface driver easycap
 easycap_open: ==========OPEN=========
0adjust_standard: selected standard: PAL_BGHIN
0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x00=std mask
0adjust_format: sought:    V4L2_FIELD_NONE
0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
0adjust_brightness: adjusting brightness to  0x7F
0adjust_contrast: adjusting contrast to  0x3F
0adjust_saturation: adjusting saturation to  0x2F
0adjust_hue: adjusting hue to  0x00
0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x00=std mask
0adjust_format: sought:    V4L2_FIELD_NONE
0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
0adjust_format: sought:    640x480,UYVY(0x59565955),0=field,0x00=std mask
0adjust_format: sought:    V4L2_FIELD_ANY 
0adjust_format: prefer:    V4L2_FIELD_NONE=field, was V4L2_FIELD_ANY
0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
0easycap_ioctl: user requests input 1
0adjust_standard: selected standard: NTSC_M
0adjust_format: sought:    640x480,UYVY(0x59565955),0=field,0x01=std mask
0adjust_format: sought:    V4L2_FIELD_ANY 
0adjust_format: prefer:    V4L2_FIELD_NONE=field, was V4L2_FIELD_ANY
0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x01=std mask
0adjust_format: sought:    V4L2_FIELD_NONE
0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
0adjust_format: sought:    640x480,UYVY(0x59565955),0=field,0x01=std mask
0adjust_format: sought:    V4L2_FIELD_ANY 
0adjust_format: prefer:    V4L2_FIELD_NONE=field, was V4L2_FIELD_ANY
0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
0adjust_mute: adjusting mute: 0=peasycap->audio_idle
0adjust_brightness: unchanged brightness at  0x7F
0adjust_hue: unchanged hue at  0x80
0adjust_saturation: unchanged saturation at  0xAF
0adjust_contrast: unchanged contrast at  0xBF
0easycap_dqbuf: aborted by signal ... returning -EIO
 easycap_open: ==========OPEN=========
0adjust_standard: selected standard: PAL_BGHIN
0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x00=std mask
0adjust_format: sought:    V4L2_FIELD_NONE
0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
0adjust_brightness: adjusting brightness to  0x7F
0adjust_contrast: adjusting contrast to  0x3F
0adjust_saturation: adjusting saturation to  0x2F
0adjust_hue: adjusting hue to  0x00
0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x00=std mask
0adjust_format: sought:    V4L2_FIELD_NONE
0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
0adjust_format: sought:    640x480,UYVY(0x59565955),0=field,0x00=std mask
0adjust_format: sought:    V4L2_FIELD_ANY 
0adjust_format: prefer:    V4L2_FIELD_NONE=field, was V4L2_FIELD_ANY
0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
0easycap_ioctl: user requests input 1
0adjust_standard: selected standard: NTSC_M
0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x01=std mask
0adjust_format: sought:    V4L2_FIELD_NONE
0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
0adjust_standard: selected standard: NTSC_M
0adjust_standard: selected standard already in effect
0adjust_format: sought:    640x480,UYVY(0x59565955),0=field,0x01=std mask
0adjust_format: sought:    V4L2_FIELD_ANY 
0adjust_format: prefer:    V4L2_FIELD_NONE=field, was V4L2_FIELD_ANY
0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x01=std mask
0adjust_format: sought:    V4L2_FIELD_NONE
0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
0adjust_format: sought:    640x480,UYVY(0x59565955),0=field,0x01=std mask
0adjust_format: sought:    V4L2_FIELD_ANY 
0adjust_format: prefer:    V4L2_FIELD_NONE=field, was V4L2_FIELD_ANY
0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
0adjust_mute: adjusting mute: 0=peasycap->audio_idle
0adjust_brightness: unchanged brightness at  0x7F
0adjust_hue: unchanged hue at  0x80
0adjust_saturation: unchanged saturation at  0xAF
0adjust_contrast: unchanged contrast at  0xBF
0adjust_mute: adjusting mute: 1=peasycap->audio_idle
 easycap_open: ==========OPEN=========
0adjust_standard: selected standard: PAL_BGHIN
0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x00=std mask
0adjust_format: sought:    V4L2_FIELD_NONE
0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
0adjust_brightness: adjusting brightness to  0x7F
0adjust_contrast: adjusting contrast to  0x3F
0adjust_saturation: adjusting saturation to  0x2F
0adjust_hue: adjusting hue to  0x00
0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x00=std mask
0adjust_format: sought:    V4L2_FIELD_NONE
0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
0adjust_format: sought:    640x480,UYVY(0x59565955),0=field,0x00=std mask
0adjust_format: sought:    V4L2_FIELD_ANY 
0adjust_format: prefer:    V4L2_FIELD_NONE=field, was V4L2_FIELD_ANY
0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
0easycap_ioctl: user requests input 1
0adjust_standard: selected standard: NTSC_M
0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x01=std mask
0adjust_format: sought:    V4L2_FIELD_NONE
0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
0adjust_standard: selected standard: NTSC_M
0adjust_standard: selected standard already in effect
0adjust_format: sought:    640x480,UYVY(0x59565955),0=field,0x01=std mask
0adjust_format: sought:    V4L2_FIELD_ANY 
0adjust_format: prefer:    V4L2_FIELD_NONE=field, was V4L2_FIELD_ANY
0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x01=std mask
0adjust_format: sought:    V4L2_FIELD_NONE
0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
0adjust_format: sought:    640x480,UYVY(0x59565955),0=field,0x01=std mask
0adjust_format: sought:    V4L2_FIELD_ANY 
0adjust_format: prefer:    V4L2_FIELD_NONE=field, was V4L2_FIELD_ANY
0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
0adjust_mute: adjusting mute: 0=peasycap->audio_idle
0adjust_brightness: unchanged brightness at  0x7F
0adjust_hue: unchanged hue at  0x80
0adjust_saturation: unchanged saturation at  0xAF
0adjust_contrast: unchanged contrast at  0xBF
0easycap_dqbuf: aborted by signal ... returning -EIO
Dec 14 10:14:00 michael-PC kernel: [ 1624.524199] kjournald starting.  Commit interval 5 seconds
Dec 14 10:14:00 michael-PC kernel: [ 1624.524251] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Dec 14 10:14:00 michael-PC kernel: [ 1624.525001] EXT3 FS on sdc4, internal journal
Dec 14 10:14:00 michael-PC kernel: [ 1624.525017] EXT3-fs: mounted filesystem with ordered data mode.
Dec 14 10:17:25 michael-PC kernel: [ 1829.168156] usb 1-2: USB disconnect, address 4
0easycap_usb_disconnect: easycap detached from minor #192
 easycap_delete:        0= video urbs     after all deletions
 easycap_delete:        0= video pages    after all deletions
 easycap_delete:        0= video structs  after all deletions
 easycap_delete:        0= video devices  after all deletions
 easycap_delete:        0= audio urbs     after all deletions
 easycap_delete:        0= audio pages    after all deletions
 easycap_delete:        0= audio structs  after all deletions
 easycap_delete:        0= audio devices  after all deletions
Dec 14 10:17:30 michael-PC kernel: [ 1834.348061] usb 1-2: new full speed USB device using uhci_hcd and address 5
Dec 14 10:17:30 michael-PC kernel: [ 1834.516351] usb 1-2: configuration #1 chosen from 1 choice
0easycap_usb_probe: allocated 0xC2780000=peasycap
0adjust_standard: selected standard: PAL_BGHIN
0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x00=std mask
0adjust_format: sought:    V4L2_FIELD_NONE
0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
0adjust_brightness: adjusting brightness to  0x7F
0adjust_contrast: adjusting contrast to  0x3F
0adjust_saturation: adjusting saturation to  0x2F
0adjust_hue: adjusting hue to  0x00
0easycap_usb_probe: easycap attached to minor #192
 easycap_open: ==========OPEN=========
0adjust_standard: selected standard: PAL_BGHIN
0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x00=std mask
0adjust_format: sought:    V4L2_FIELD_NONE
0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
0adjust_brightness: adjusting brightness to  0x7F
0adjust_contrast: adjusting contrast to  0x3F
0adjust_saturation: adjusting saturation to  0x2F
0adjust_hue: adjusting hue to  0x00
0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x00=std mask
0adjust_format: sought:    V4L2_FIELD_NONE
0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
0adjust_format: sought:    640x480,UYVY(0x59565955),0=field,0x00=std mask
0adjust_format: sought:    V4L2_FIELD_ANY 
0adjust_format: prefer:    V4L2_FIELD_NONE=field, was V4L2_FIELD_ANY
0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
0easycap_ioctl: user requests input 1
0adjust_standard: selected standard: NTSC_M
0adjust_format: sought:    640x480,UYVY(0x59565955),0=field,0x01=std mask
0adjust_format: sought:    V4L2_FIELD_ANY 
0adjust_format: prefer:    V4L2_FIELD_NONE=field, was V4L2_FIELD_ANY
0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x01=std mask
0adjust_format: sought:    V4L2_FIELD_NONE
0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
0adjust_format: sought:    640x480,UYVY(0x59565955),0=field,0x01=std mask
0adjust_format: sought:    V4L2_FIELD_ANY 
0adjust_format: prefer:    V4L2_FIELD_NONE=field, was V4L2_FIELD_ANY
0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
0adjust_mute: adjusting mute: 0=peasycap->audio_idle
0adjust_brightness: unchanged brightness at  0x7F
0adjust_hue: unchanged hue at  0x80
0adjust_saturation: unchanged saturation at  0xAF
0adjust_contrast: unchanged contrast at  0xBF
0easycap_dqbuf: aborted by signal ... returning -EIO
```

---

### Post by rmt1947 on 2010-12-14
Hi zonemikel,

Thanks for reporting back.  Sorry about the confusion over the file README.ZM - I should have been more specific that it was part of the driver distribution.

The diagnostic output from the machine running Ubuntu Server is puzzling.  As regards the video stream, neither the driver nor mplayer is producing any error messages.  Xvideo is enabled on the server, and if you can watch videos from other sources we must conclude that the video card on the server machine is good and that there are no hardware problems.  It seems that for some reason mplayer simply does not receive any video data from the driver.  Very strange.

The most efficient way forward on this is probably for me to install Ubuntu Server temporarily on a spare machine here and to investigate what is happening.  I can't do that immediately, as all my spare machines are set up at the moment for testing the ALSA extension which I am adding to the driver.  I'll try to have a look at Ubuntu Server towards the end of the month if you have not fixed the problem by then.

Mike

---

### Post by SteveDee on 2010-12-14
> **zonemikel said:**
> ... belive it or not I actually have been studying video for a while for another project, i know all about the encryption and how this stuff works....

...sorry, I didn't mean to sound patronising. It was just the "bogus norm" message in your earlier post that made me wonder what your options were. However, error messages from mPlayer/mEncoder can sometimes be rather confusing.

Have you checked the kernel versions you are using on desktop & server machines? I have problems ([http://ubuntuforums.org/showthread.php?t=1642985](http://ubuntuforums.org/showthread.php?t=1642985)) with newer kernels when running my DC60+.

Zoneminder: I tried using this almost 2 years ago without much success, and found the excellent "motion" application much easier to get running ([http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome)).

---

### Post by zonemikel on 2010-12-14
> **rmt1947 said:**
> Hi zonemikel,

Thanks for reporting back.  Sorry about the confusion over the file README.ZM - I should have been more specific that it was part of the driver distribution.

The diagnostic output from the machine running Ubuntu Server is puzzling.  As regards the video stream, neither the driver nor mplayer is producing any error messages.  Xvideo is enabled on the server, and if you can watch videos from other sources we must conclude that the video card on the server machine is good and that there are no hardware problems.  It seems that for some reason mplayer simply does not receive any video data from the driver.  Very strange.

The most efficient way forward on this is probably for me to install Ubuntu Server temporarily on a spare machine here and to investigate what is happening.  I can't do that immediately, as all my spare machines are set up at the moment for testing the ALSA extension which I am adding to the driver.  I'll try to have a look at Ubuntu Server towards the end of the month if you have not fixed the problem by then.

Mike

I had seen references to the readme.zm file all over the place it was not just your reference. I guess a easy way for me to resolve this would be for me to pop the hdd out of the server and put it into another machine and see if it works in the other machine. If I still see green then I can almost conclude its the server version of ubuntu thats causing it. This would be pretty easy, i might do it later on tonight just have to find a spare ... nevermind i have one in mind that will work. I'll try this later on this evening. 

> ...sorry, I didn't mean to sound patronising. It was just the "bogus  norm" message in your earlier post that made me wonder what your options  were. However, error messages from mPlayer/mEncoder can sometimes be  rather confusing.

Have you checked the kernel versions you are using on desktop & server machines? I have problems ([http://ubuntuforums.org/showthread.php?t=1642985](http://ubuntuforums.org/showthread.php?t=1642985)) with newer kernels when running my DC60+.

Zoneminder: I tried using this almost 2 years ago without much success,  and found the excellent "motion" application much easier to get running ([http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome)).     You didnt, thanks for the info i'll check out motion later tonight, for now I'm late ... gtg


UPDATE >>> !!!
I took the hdd with ubuntu server 10.04 and popped it into another computer, started up the other computer and then plugged in the usb easycap from there I ran the mplayer command (no sound) and it worked great. So whatever it is it has to do with the hardware on the pc NOT ubuntu server. I can kinda tell the machine has problems also because the panels never show up in ubuntu, and they did on the other computer. So i think there are some serious problems with the video card embedded in that computer. 

I will try a different video card in the machine if I ever find one, it only has pci slots and I dont have any pci video cards. I might just build another machine, I have enough parts laying around I should be able too ... but anyway dont waste any of your valuable time messing with ubuntu server that was not the culprit. 

Thanks for all your help, once I get time i'll write up a blog entry and post the link here.

---

### Post by rmt1947 on 2010-12-14
@zonemikel:  Thanks for the update - one thing less for me to worry about  :-)

---

### Post by Crazy K on 2010-12-14
Can one of you guys help me on this topic?: 
[http://ubuntuforums.org/showthread.php?p=10207371#post10207371](http://ubuntuforums.org/showthread.php?p=10207371#post10207371) 

It's about the same thing, but I can't go through this whole topic to figure out how to get it to work. Can't be bothered to read 17 pages.

---

### Post by Si_M on 2011-01-15
I am getting this error when attempting to install the driver

xxxx@Studio:~/EASYCAP/easycap_dc60.x.y$ sudo ./install.sh
kernel directory is /lib/modules/2.6.35-24-generic/build
snd_card_new() will not be used
snd_card_create() will be used
<media/v4l2-device.h> will be included
struct v4l2_file_operations OK
unlocked_ioctl required
v4l2_file_operations.unlocked_ioctl will be used
ERROR: script ./ioctlmess.sh running from wrong directory
ERROR:  script ./ioctlmess.sh failed


Any pointers?

---

### Post by Si_M on 2011-01-15
I am getting this error when attempting to install the driver

xxxx@Studio:~/EASYCAP/easycap_dc60.x.y$ sudo ./install.sh
kernel directory is /lib/modules/2.6.35-24-generic/build
snd_card_new() will not be used
snd_card_create() will be used
<media/v4l2-device.h> will be included
struct v4l2_file_operations OK
unlocked_ioctl required
v4l2_file_operations.unlocked_ioctl will be used
ERROR: script ./ioctlmess.sh running from wrong directory
ERROR:  script ./ioctlmess.sh failed


Any pointers?

---

### Post by Si_M on 2011-01-15
I am getting this error when attempting to install the driver

xxxx@Studio:~/EASYCAP/easycap_dc60.x.y$ sudo ./install.sh
kernel directory is /lib/modules/2.6.35-24-generic/build
snd_card_new() will not be used
snd_card_create() will be used
<media/v4l2-device.h> will be included
struct v4l2_file_operations OK
unlocked_ioctl required
v4l2_file_operations.unlocked_ioctl will be used
ERROR: script ./ioctlmess.sh running from wrong directory
ERROR:  script ./ioctlmess.sh failed


Any pointers?

---

### Post by Si_M on 2011-01-15
Sorry for the multi post but it hung than I can't work out how to delete my extra posts

---

### Post by rmt1947 on 2011-01-15
Hi,

For driver version 0.9, step 2 of the installation procedure is

```

Create a directory to work in:

mkdir ~/EASYCAP
cd ~/EASYCAP

Next, depending on where the file was downloaded to:

cp -p ~/Downloads/easycap_dc60.0.9.tar.gz .
tar zxf ./easycap_dc60.0.9.tar.gz
cd easycap_dc60.0.9

```

assuming you are using the Firefox browser on Ubuntu 10.10, which puts downloads into directory ~/Downloads by default.

The mention of things like  easycap_dc60.x.y  in the README file was intended to cover the general case of driver version x.y.  I'll change this in any future release because I can see now that the instructions are not very clear.  Sorry for the confusion.

Mike

---

### Post by 19Grumpah42 on 2011-01-15
I recently purchased 2 of these DC60 devices, for two reasons: (1) they have a terrible reputation for not working at all!, and (2) they cost me less than $4 each. I chose wisely: one of them was "dead on arrival", the other seems to work very well on both WinXP and Ubuntu Lucid. [I am most grateful to "the team" for having created the drivers etc.]. They are a good little device for webcaming and security cameras. So my recommendation would be BUY THREE at that price, and one of them will most probably work very well for you. --Grahame

---

### Post by celem on 2011-02-12
I just received my purchase of an EasyCap002 ( USB ID 05e1:0408 ). I loaded Mike Thomas' drivers from SourceForge. I am running Ubuntu 10.04. The install went without a problem. I tested the setup with Mike Thomas' test script - testNTSC.sh. I have not loaded any kernel modules. I get a good picture but the sound level is low and scratchy. I'll be looking into this a bit more over the next couple of weeks when time permits.Meanwhile, any ideas on the scratchy audio?

---

### Post by King Ryan on 2011-03-05
I have installed the latest version of this driver on Ubuntu 10.04 Lucid Lynx and it seemed to install no problem.  All the checks indicated in the README succeeded...easycap0 was there, the usb id was correct, and so forth.  

But when I try to view my webcam in VLC or cheese or anything, all I get are black&white vertical bars.  Has anyone come across this?

Ryan

---

### Post by rmt1947 on 2011-03-06
Hi Ryan,

The black and white bars mean that the EasyCAP cannot lock onto the analogue input signal.  Usually this is due to one of two things:

Either:

(1) there is literally no analogue signal being received by the EasyCAP, typically because of a hardware problem (bad connection or faulty wiring).

or:

(2) the driver expects an NTSC signal when in fact a PAL signal is being supplied (or vice versa), for example when running ./testPAL.sh on an NTSC signal or ./testNTSC.sh on a PAL signal.

Mike

---

### Post by Aisteru on 2011-03-10
> **m3how said:**
> I've followed the instructions in the post couple pages ago. I using Ubuntu 10.4 and this is what I get when I try to install:
```
kernel directory is /lib/modules/2.6.32-24-generic/build
not overwriting top level Makefile
not overwriting src/Makefile
not overwriting tools/Makefile
make clean OK
make OK
ERROR: Module snd_usb_audio is in use
ERROR:  snd_usb_audio module cannot be removed
```Can anyone shed some light on what could be the problem ?

I had the same problem. I got around it by rebooting to a command line, & running the install.sh script that way. The other way to do it would be to unload all the kernel models that depend on snd_usb_audio, then unload it, but that seemed to be more work. 
I hope this helps, I am having other troubles now that I am past that part.

---

### Post by LuizCB on 2011-03-11
Did anyone manage to have EasyCap working with Natty (11.04) kernel module 'kernel/drivers/staging/easycap/easycap.ko'?
If so, how, please.

Other question, btw. What are all EasyCap dependencies? Because I'm trying using it on a basic server installation.

Thanks in advance.

Luiz

---

### Post by celem on 2011-03-15
I have done a bit more with my EasyCap002 ( USB ID 05e1:0408 ) on 10.04. This time I used mtvcgui ([http://easycap.blogspot.com/p/mtvcgui.html]("http://easycap.blogspot.com/p/mtvcgui.html")). This GUI makes the process nice and easy. My audio and video are in sync but the ausio level remains low and thus a bit scratchy. I have not figured out how to boost the record audio level. Ideas?

---

### Post by celem on 2011-03-15
> **celem said:**
> I have done a bit more with my EasyCap002 ( USB ID 05e1:0408 ) on 10.04. ...but the audio level remains low and thus a bit scratchy...
The cure seems to be at the link below. I need to order this plug:
> Distortion-fix Guide:
[http://www.youtube.com/watch?v=AoWL2CoFnlM](http://www.youtube.com/watch?v=AoWL2CoFnlM)


---

### Post by rmt1947 on 2011-03-15
Hi,

I'm sorry to say there's no way of tweaking the driver in order to improve the audio signal from an EasyCAP002.  As you probably know, these EasyCAPs have no dedicated AC'97 audio chip, and I never managed to find out how their microphone audio channel is handled by the hardware.  In contrast, EasyCAP DC60s with CVBS, S-Video and two audio input leads do have an AC'97 audio chip if you're lucky (although in practice many don't), and for those with the AC'97 chip the driver can be configured to alter the gain within certain limits.

I've bought half a dozen EasyCAPs over the past couple of years.  I've noticed that the audio quality varies considerably, as regards both volume and noise level, but I've not found a satisfactory way to make the driver compensate for these variations.

Mike

---

### Post by celem on 2011-03-16
Success was found by connecting the audio outputs into the microphone jack and then selecting the audio source as “plughw.0,0”. The EasyCap audio source of “plughw.1,0” was scratchy and of low quality.

I used mtvcgui-0.31 to set things up. The command line produced is shown below.

mencoder tv:// -tv channel=0:driver=v4l2:device=/dev/easycap1:normid=6:input=0:chanlist=us-cable:width=720:height=576:brightness=0:contrast=0:hue=0:saturation=0:buffersize=16:alsa:amode=1:forcechan=2:audiorate=48000:adevice=plughw.0,0:forceaudio:immediatemode=0 -oac mp3lame -ovc lavc -quiet -lavcopts acodec=mp2:abitrate=128:vcodec=mpeg4:vbitrate=1072 -lameopts cbr:br=128 -o ./capture_0_20110316_133604.avi

With this setup the audio is strong and clear.

---

### Post by tttonyyy on 2011-03-22
> **zonemikel said:**
> 
UPDATE >>> !!!
I took the hdd with ubuntu server 10.04 and popped it into another computer, started up the other computer and then plugged in the usb easycap from there I ran the mplayer command (no sound) and it worked great. So whatever it is it has to do with the hardware on the pc NOT ubuntu server. I can kinda tell the machine has problems also because the panels never show up in ubuntu, and they did on the other computer. So i think there are some serious problems with the video card embedded in that computer. 

I will try a different video card in the machine if I ever find one, it only has pci slots and I dont have any pci video cards. I might just build another machine, I have enough parts laying around I should be able too ... but anyway dont waste any of your valuable time messing with ubuntu server that was not the culprit. 

Thanks for all your help, once I get time i'll write up a blog entry and post the link here.

I've also got the green output with a Ubuntu 10.4 LTS server edition - but I don't think it's video card related as I'm using X11 tunnel over ssh to a local X server.  And I know it's not this that's the problem because if I use mplayers -vo jpeg option to dump video to jpeg files and pop them on the webserver, they're all green too!

The only thing I can think of is that all the ports on this Linux server box are USB 1.1 only, perhaps the same on yours?

(I presumed this would just drop the capture framerate but it looks like it just stops it working altogether).

---

### Post by latinhawk on 2011-04-14
> **LuizCB said:**
> Did anyone manage to have EasyCap working with Natty (11.04) kernel module 'kernel/drivers/staging/easycap/easycap.ko'?
If so, how, please.

Other question, btw. What are all EasyCap dependencies? Because I'm trying using it on a basic server installation.

Thanks in advance.

Luiz

I'm having the same problem as Luiz on Natty.

Here is the error as shown in console:

~/EASYCAP/easycap_dc60.0.9$ sudo ./install_simple.sh
depmod OK
unlocked_ioctl not required
make clean OK
ERROR:  step ~/EASYCAP/easycap_dc60.0.9$ sudo ./install_simple.sh
depmod OK
unlocked_ioctl not required
make clean OK
ERROR:  step failed:  make
/home/backend/EASYCAP/easycap_dc60.0.9/src/easycap_main.c:76:2: error: unknown field ‘ioctl’ specified in initializer
/home/backend/EASYCAP/easycap_dc60.0.9/src/easycap_main.c:76:2: warning: initialization from incompatible pointer type
make[3]: *** [/home/backend/EASYCAP/easycap_dc60.0.9/src/easycap_main.o] Error 1
make[2]: *** [_module_/home/backend/EASYCAP/easycap_dc60.0.9/src] Error 2
make[1]: *** [all] Error 2
make: *** [build] Error 2
failed:  make
/home/backend/EASYCAP/easycap_dc60.0.9/src/easycap_main.c:76:2: error: unknown field ‘ioctl’ specified in initializer
/home/backend/EASYCAP/easycap_dc60.0.9/src/easycap_main.c:76:2: warning: initialization from incompatible pointer type
make[3]: *** [/home/backend/EASYCAP/easycap_dc60.0.9/src/easycap_main.o] Error 1
make[2]: *** [_module_/home/backend/EASYCAP/easycap_dc60.0.9/src] Error 2
make[1]: *** [all] Error 2
make: *** [build] Error 2

Any help will be greatly appreciated. Thanks.

latinhawk

---

### Post by rmt1947 on 2011-04-15
Hi latinhawk,

With a view to giving some advice I've just installed Ubuntu from

ubuntu-11.04-beta2-desktop-i386.iso

on a spare machine.  Unfortunately the entire installation is unworkable - the Gnome menus just don't function at all.  I guess I'll have to wait for the stable release.

Mike

---

### Post by danielvulrich on 2011-04-15
@ [rmt1947]("http://ubuntuforums.org/member.php?u=581850")
and there's noything to do with it? i mean, just wait?

---

### Post by rmt1947 on 2011-05-07
Hi,

The final release of Ubuntu 11.04 (Natty) is no better than the beta on my test machine, so I installed xubuntu-11.04-desktop-i386.iso instead.  This works well enough for me to install the driver.

On my test machine, version 0.9 of the driver from 

[http://sourceforge.net/projects/easycapdc60/](http://sourceforge.net/projects/easycapdc60/)

installs without any problems on Xubuntu 11.04, and mplayer gave perfect sound and vision from a PAL videotape.  I did not investigate anything else.

The version of the driver in Natty's kernel tree under drivers/staging/easycap can also be installed, but it should be realized that this is an old version of the driver which does not have any ALSA capability.  Since Natty supports only ALSA and not OSS audio, the driver under drivers/staging/easycap can provide only silent video output on Natty.  Anybody who really wishes to activate the drivers/staging/easycap driver in Natty can try the following procedure.

Open a terminal window (Ctrl-Alt-T for Unity users) and do:

sudo apt-get install linux-source-2.6.38
cd /usr/src/linux-source-2.6.38
sudo tar jxf linux-source-2.6.38.tar.bz2

Point a browser to

[http://sourceforge.net/projects/easycapdc60/](http://sourceforge.net/projects/easycapdc60/)

and download file easycap_dc60.0.9.tar.gz into directory ~/Downloads.  Then continue in the terminal window:

cd ~
mkdir EASYCAP
mv Downloads/easycap_dc60.0.9.tar.gz EASYCAP
cd EASYCAP
tar zxf easycap_dc60.0.9.tar.gz
cd easycap_dc60.0.9/src
pwd
# check that you are in directory ~/EASYCAP/easycap_dc60.0.9/src before issuing the next command!
rm *
cp -p /usr/src/linux-source-2.6.38/linux-source-2.6.38/drivers/staging/easycap/* .
cd ..
sudo ./install.sh
sudo apt-get install mplayer
mplayer tv:// -tv driver=v4l2:norm=PAL_BGHIN:width=640:height=480:outfmt=uyvy:device=/dev/video0:input=0:fps=25 -hardframedrop -msglevel all=9

For me, this succeeded in getting the staging driver working on Natty (that is: gave video with no sound).

Mike

---

### Post by mciverza on 2011-05-12
FYI, mine is working with Maverick 64-bit, video and sound are present using the test4PAL.sh and sound is present with test4NTSC.sh. I only have a PAL video source at the moment, so I haven't been able to verify that video works with NTSC, but I expect it will.

2.6.35-28-generic #50-Ubuntu SMP x86_64 GNU/Linux
USBID: 05e1:0408
[http://sourceforge.net/projects/easycapdc60/](http://sourceforge.net/projects/easycapdc60/)

A very special thank you to rmt1947 (Mike Thomas)

---

### Post by htcrwn148 on 2011-06-24
I need help... i know it works... but i dont know what i did wrong. im a noob to linux somewhat.  Im on Ubuntu 10.04 32bit? i think. some basic terminal knowledge. but i cant seem to get it working. i tried to install by 3 different instructions and nothing works... my best guess is that it isnt me


This what i got according to the read me intructions


tobe@Tobe:~/EASYCAP/easycap_dc60.0.9$ sudo ./install.sh
[sudo] password for tobe: 
kernel directory is /lib/modules/2.6.35-28-generic/build
snd_card_new() will not be used
snd_card_create() will be used
<media/v4l2-device.h> will be included
struct v4l2_file_operations OK
unlocked_ioctl required
v4l2_file_operations.unlocked_ioctl will be used
-> regenerating top level Makefile
---> generating src/Makefile
---> generating tools/Makefile
make clean OK
make OK
ERROR: Module snd_usb_audio is in use
ERROR:  snd_usb_audio module cannot be removed

Ok after trying to install this on my other pc at home (ubuntu 10.04) the install was succesfull and the lsmod | grep easycap.. shows what its supposed to show.

At work i have a webcam installed, wine installed. crossoever games. could one of these be causing th errors seen above if so how do i disable to try do i have to uninstall the webcam... (which by the way took hours to figure out) so i hope thats not it. 

Please help

---

### Post by rmt1947 on 2011-06-25
Hi,

No, it's not your fault.  Either there is some audio hardware on your computer which needs the module snd_usb_audio, or that module is being loaded indirectly by some action of wine or your games software.  My script ./install.sh tries to remove the snd_usb_module, but fails if the snd_usb_audio module is in use.  (In my experience it is necessary to remove the snd_usb_audio module temporarily during installation, because otherwise it will prevent my driver from taking control of the EasyCAP's sound channel later when the EasyCAP is plugged in.  I have never understood why this problem arises, and I feel sure there's a better way around it, but nobody has told me what the solution is.)

You could edit the script ./install.sh as follows.  Find line 587, which is

```
    echo "ERROR:  snd_usb_audio module cannot be removed" 

```

then change line 588 from

```
    exit 1
```

to

```
#    exit 1
```

and try reinstalling the driver.  If this succeeds, you may get the EasyCAP working for video, though I doubt that the audio will work properly.

Mike

---

### Post by htcrwn148 on 2011-06-25
Mike, 
thank you that worked to install it... now the only thing is i cannot get good video. Just lines and grainy video. I tried 2 different devices. same thing. I though it might be the device (security cam) maybe not. 
1 question: is the yellow rca cable (like for dvd) is that the same as the input wire on the easycap labeled "cvbs"?

DO i need to download video drivers for my ubuntu?  i can watch dvd on my pc, youtube, flash... do i need some other video support?

Thanks for the help.
Tobe

---

### Post by rmt1947 on 2011-06-25
Hi Tobe,

It's disappointing that you are getting poor video quality.  If you're sure the cables and connections are good, it is always possible that the EasyCAP itself has poor internal connections or some other hardware problem.  Does the EasyCAP give a good picture on machines using Microsoft Windows?

I have a PAL camera here.  The video output is on a lead with a yellow plug, and I connect this to the yellow CVBS plug on the EasyCAP.  So I think your connections are probably correct.

Drivers are associated with particular pieces of hardware.  If you can successfully play DVDs and view YouTube videos I expect you already have most of what you need.

Mike

---

### Post by htcrwn148 on 2011-06-25
Mike,
I was messing with the Iput configuration, and a few of those attempts gave me video. but it would immidietly go to bars (white, to gray to black) now i only get the bars. i dont know what input configuration. COuld this be because of what is described in the read me.

"---(1)---:  Intentionally, this driver will not stream material which is
unambiguously identified by the hardware as copy-protected.  Normal video
output will be present for about a minute but will then freeze."
 
Still poking around.. but i dont want to do anything to drastic and make it worse. I considered trying the s-video... but the adapter is 19.99... and well im cheap. 

is there a way to stop the copy protection thing to eliminate that as the problem. before i spend 19.99 on an adapter?

---

### Post by rmt1947 on 2011-06-26
Hi Tobe,

I have never tested the driver with S-Video because I don't own any equipment with S-Video output, but I doubt whether the adapter you mention will solve anything (I could be wrong, of course).

Mike

---

### Post by timgood on 2011-06-28
I am trying to use this adapter with 10.10 64bit. The driver installed OK with no errors, but when I run testPAL.sh I get a few seconds of video, then black and grey vertical lines. Sound is OK.

Earlier in this thread it was suggested that this may be due to NTSC signal being used when PAL was expected, but the VCR I am using is PAL only. The adapter works OK on Mac OS X (the sound is a bit iffy) but I would like to get it working with Maverick. Any clues?

---

### Post by rmt1947 on 2011-06-28
I'm seeing quite a few reports of this syndrome lately, but I remain clueless.  Version 0.9 of the driver works fine for me on 32-bit Ubuntu 10.10 with PAL VHS tapes, and I doubt whether this is a 64-bit vs 32-bit issue.  Does the EasyCAP have any problems on Microsoft Windows?

Mike

---

### Post by timgood on 2011-06-29
> **rmt1947 said:**
> I'm seeing quite a few reports of this syndrome lately, but I remain clueless.  Version 0.9 of the driver works fine for me on 32-bit Ubuntu 10.10 with PAL VHS tapes, and I doubt whether this is a 64-bit vs 32-bit issue.  Does the EasyCAP have any problems on Microsoft Windows?

Mike

Hmm - I don't have Windows anymore! :D However, I do have a test machine running 32bit Natty. I'll try it on that and see what happens. Weird thing: when I try the NTSC script, I do get a picture that stays (but it is very scrambled and B&W) and does not go to the 'test card' black and grey screen. Also, it is strange that I do get up to 5 seconds of stable video with the PAL script.

---

### Post by rmt1947 on 2011-06-29
Yes, it's odd.  I own several EasyCAPs, but my only hardware is x86 and x86_64 PCs, and I have a very limited range of input sources (PAL and NTSC video tapes, plus a PAL camera).  I've never encountered the symptoms "5 seconds of good video, then testcard bars".  Furthermore, I never get poor quality video - it's either good or entirely absent.  Crackly sound, yes - audio quality is notoriously variable from one EasyCAP to another - but video is always good for me, at least on CVBS (I don't have any S-Video equipment).

Mike

---

### Post by rizlmilk on 2011-06-30
I recently purchased an Easycap to see if I could get it to work in Linux. (It was less than $10)

I installed the drivers for it located on SourceForge. I had to go into recovery mode to get it installed because snd_usb_audio was being used and caused it to not install otherwise.

Now that the drivers are installed, I still can't seem to get it to work. For example, trying to record with mencoder results in an endless amount of skipped frames. Also, Cheese tries to do something with it, but it just shows the spinning "loading" image forever. Here is the terminal output for mencoder:

> ryan@ryan-desktop:~$ mencoder tv:// -tv device=/dev/video0:input=1:norm=1:width=640: height=480 -vf pp=md -o Recording -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=8000
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: EasyCAP DC60
 Capabilites:  video capture  audio  read/write  streaming
 supported norms: 0 = PAL_BGHIN; 1 = NTSC_N_443; 2 = PAL_Nc; 3 = NTSC_N; 4 = SECAM; 5 = NTSC_M; 6 = NTSC_M_JP; 7 = PAL_60; 8 = NTSC_443; 9 = PAL_M; 10 = PAL_BGHIN_SLOW; 11 = NTSC_N_443_SLOW; 12 = PAL_Nc_SLOW; 13 = NTSC_N_SLOW; 14 = SECAM_SLOW; 15 = NTSC_M_SLOW; 16 = NTSC_M_JP_SLOW; 17 = PAL_60_SLOW; 18 = NTSC_443_SLOW; 19 = PAL_M_SLOW;
 inputs: 0 = CVBS0; 1 = CVBS1; 2 = CVBS2; 3 = CVBS3; 4 = CVBS4; 5 = S-VIDEO;
 Current input: 0
 Current format: UYVY
tv.c: norm_from_string(1): Bogus norm parameter, setting default.
Selected input hasn't got a tuner!
[V] filefmt:9  fourcc:0x59565955  size:640x480  fps:25.000  ftime:=0.0400
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Packed UYVY)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Packed UYVY as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
    Last message repeated 1 times
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0xc79020]BICUBIC scaler, from uyvy422 to yuv420p using MMX2
[swscaler @ 0xc79020]using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0xc79020]using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0xc79020]using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0xc79020]640x480 -> 640x480
videocodec: libavcodec (640x480 fourcc=34504d46 [FMP4])
Selected video codec: [rawuyvy] vfm: raw (RAW UYVY)
==========================================================================
Forcing audio preload to 0, max pts correction to 0.

Skipping frame!
Pos:   0.0s      1f ( 0%)  0.95fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      2f ( 0%)  1.27fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      3f ( 0%)  1.43fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      4f ( 0%)  1.52fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      5f ( 0%)  1.59fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      6f ( 0%)  1.63fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      7f ( 0%)  1.67fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      8f ( 0%)  1.69fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s      9f ( 0%)  1.71fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s     10f ( 0%)  1.73fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s     11f ( 0%)  1.75fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s     12f ( 0%)  1.76fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s     13f ( 0%)  1.77fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s     14f ( 0%)  1.78fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s     15f ( 0%)  1.78fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s     16f ( 0%)  1.79fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
^Cs:   0.0s     17f ( 0%)  1.80fps Trem:   0min   0mb  A-V:0.000 [0:0]
Skipping frame!
Pos:   0.0s     18f ( 0%)  1.80fps Trem:   0min   0mb  A-V:0.000 [0:0]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:     -nan kbit/s  (-2147483648 B/s)  size: 0 bytes  0.000 secs  18 frames



Any help is greatly appreciated.

---

### Post by rmt1947 on 2011-06-30
Hi @rizlmilk,

I'll need some more information in order to comment sensibly.  Which version of Ubuntu are you using?  Is your video source PAL or NTSC or something exotic (for example PAL-60)?  What happens when you run the script ./testPAL.sh or ./testNTSC.sh (both of which invoke mplayer)?  Your mencoder message about "supported norms" proves that the video part of the easycap module is working properly, but do you have /proc/asound/EasyALSA# present?  (For mplayer and mencoder, I have found that absent audio can sometimes cause knock-on difficulties with the video processing.)  If /proc/asound/EasyALSA# is missing, you could try the command:


```
mplayer tv:// -tv driver=v4l2:norm=PAL_BGHIN:width=640:height=480:outfmt=uyvy:device=/dev/easycap0:input=0:fps=25:noaudio -hardframedrop
```


(replacing PAL_BGHIN by NTSC_M and fps=25 by fps=30 if appropriate).

Have you tried running the script ./tail.sh in order to extract error messages written by the driver to file /var/log/kern.log?  These will provide a clue to any distress experienced by the driver.  As a last resort, you can change the line "DEBUG=0" in the script ./install.sh to "DEBUG=9", reinstall the driver, perform a test run, and then finally run ./tail.sh.  This will generate a lot output, though, which is not very convenient for posting on discussion forums, so I recommend the DEBUG=9 option only if problems cannot be diagnosed by simpler means.

Mike

---

### Post by rizlmilk on 2011-06-30
My video source is NTSC. I'm using Ubuntu 10.04. Is there a more compatible version?

Running ./testNTSC.sh spits out: "ERROR: missing /proc/asound/EasyALSA0" so I am missing the file you listed. Is there any way for me to insert/restore it?

Running the mplayer command you provided resulted in a green screen being displayed by mplayer.

Running ./tail.sh spits out "ERROR:  missing executable: ./tailer"

---

### Post by rmt1947 on 2011-07-01
Driver version 0.9 (and version 0.8.5) should work fine on Ubuntu 10.04.

"ERROR: missing /proc/asound/EasyALSA0" does not imply a missing file.  It means (as I suspected) that the audio part of the driver is not active, presumably because of a run-time conflict with the competing module snd_usb_audio.

With mplayer, a green screen means that the EasyCAP has successfully locked onto the analogue video source, but the driver cannot process the video stream for some reason.  (A grey-bar testcard, on the other hand, would mean that the EasyCAP hardware cannot even lock onto the video source.)

"ERROR: missing executable: ./tailer" means that the script ./install.sh never completed the installation procedure, presumably because a premature error exit occurred.

To avoid having to install from "recovery mode" you could modify the script ./install.sh as suggested in my post #191 in the present thread:

[http://ubuntuforums.org/showthread.php?t=924504&page=20](http://ubuntuforums.org/showthread.php?t=924504&page=20)

and try installing the driver from the normal Ubuntu desktop.  Even if the modified script does not work, the manner of its failing will give useful information on what's going wrong.

The script ./tail.sh is convenient for obtaining diagnostics, but is not essential.  You can (as root) open the file /var/log/kern.log directly, look for messages containing the string "easycap" (especially any mentioning "ERROR" or "MISTAKE"), and cut-and-paste these into another file suitable for reporting here.

Mike

---

### Post by rizlmilk on 2011-07-04
I commented out the "exit 1" line just like that post you linked to. It continued with the installation after hitting the two audio/usb errors instead of quitting. I tried both testNTSC.sh and the command you provided, but both just show a green screen in mplayer.

Here is the applicable log after plugging the easycap in and running the command you provided.

> 
Jul  4 15:53:45 ryan-desktop kernel: [ 9568.354815] easycap:: easycap_delete:        0= video urbs     after all deletions
Jul  4 15:53:45 ryan-desktop kernel: [ 9568.354823] easycap:: easycap_delete:        0= video pages    after all deletions
Jul  4 15:53:45 ryan-desktop kernel: [ 9568.354829] easycap:: easycap_delete:        0= video structs  after all deletions
Jul  4 15:53:45 ryan-desktop kernel: [ 9568.354835] easycap:: easycap_delete:        0= video devices  after all deletions
Jul  4 15:53:45 ryan-desktop kernel: [ 9568.354840] easycap:: easycap_delete:        0= audio urbs     after all deletions
Jul  4 15:53:45 ryan-desktop kernel: [ 9568.354845] easycap:: easycap_delete:        0= audio pages    after all deletions
Jul  4 15:53:45 ryan-desktop kernel: [ 9568.354851] easycap:: easycap_delete:        0= audio structs  after all deletions
Jul  4 15:53:45 ryan-desktop kernel: [ 9568.354856] easycap:: easycap_delete:        0= audio devices  after all deletions
Jul  4 15:53:48 ryan-desktop kernel: [ 9571.330069] usb 2-4: new high speed USB device using ehci_hcd and address 4
Jul  4 15:53:48 ryan-desktop kernel: [ 9571.481150] hub 2-0:1.0: unable to enumerate USB device on port 4
Jul  4 15:53:49 ryan-desktop kernel: [ 9572.020083] usb 4-4: new full speed USB device using ohci_hcd and address 4
Jul  4 15:53:49 ryan-desktop kernel: [ 9572.234655] usb 4-4: not running at top speed; connect to a high speed hub
Jul  4 15:53:49 ryan-desktop kernel: [ 9572.249854] usb 4-4: configuration #1 chosen from 1 choice
Jul  4 15:53:49 ryan-desktop kernel: [ 9572.252877] easycap::0easycap_usb_probe: allocated 0xFFFF8800BF7C0000=peasycap
Jul  4 15:53:49 ryan-desktop kernel: [ 9572.252885] easycap::0easycap_usb_probe: where     0xFFFF8800BF7C0018=&peasycap->video_device
Jul  4 15:53:49 ryan-desktop kernel: [ 9572.252892] easycap::0easycap_usb_probe: and       0xFFFF8800BF7C0290=&peasycap->v4l2_device
Jul  4 15:53:54 ryan-desktop kernel: [ 9576.923967] easycap::0adjust_standard: selected standard: PAL_BGHIN
Jul  4 15:53:54 ryan-desktop kernel: [ 9577.202929] easycap::0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x00=std mask
Jul  4 15:53:54 ryan-desktop kernel: [ 9577.202938] easycap::0adjust_format: sought:    V4L2_FIELD_NONE
Jul  4 15:53:54 ryan-desktop kernel: [ 9577.202946] easycap::0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
Jul  4 15:53:54 ryan-desktop kernel: [ 9577.277909] easycap::0adjust_brightness: adjusting brightness to  0x7F
Jul  4 15:53:54 ryan-desktop kernel: [ 9577.304917] easycap::0adjust_contrast: adjusting contrast to  0x3F
Jul  4 15:53:54 ryan-desktop kernel: [ 9577.331910] easycap::0adjust_saturation: adjusting saturation to  0x2F
Jul  4 15:53:54 ryan-desktop kernel: [ 9577.358898] easycap::0adjust_hue: adjusting hue to  0x00
Jul  4 15:53:54 ryan-desktop kernel: [ 9577.400901] easycap 4-4:1.0: Non-NULL drvdata on register
Jul  4 15:53:54 ryan-desktop kernel: [ 9577.401052] easycap::0easycap_usb_probe: registered with videodev: 0=minor
Jul  4 15:53:54 ryan-desktop kernel: [ 9577.401059] easycap::0easycap_usb_probe: ends successfully for interface 0
Jul  4 15:53:54 ryan-desktop kernel: [ 9577.402844] easycap:: easycap_open: ==========OPEN=========
Jul  4 15:53:59 ryan-desktop kernel: [ 9581.798255] easycap::0adjust_standard: selected standard: PAL_BGHIN
Jul  4 15:53:59 ryan-desktop kernel: [ 9582.077188] easycap::0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x00=std mask
Jul  4 15:53:59 ryan-desktop kernel: [ 9582.077197] easycap::0adjust_format: sought:    V4L2_FIELD_NONE
Jul  4 15:53:59 ryan-desktop kernel: [ 9582.077206] easycap::0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
Jul  4 15:53:59 ryan-desktop kernel: [ 9582.152195] easycap::0adjust_brightness: adjusting brightness to  0x7F
Jul  4 15:53:59 ryan-desktop kernel: [ 9582.179162] easycap::0adjust_contrast: adjusting contrast to  0x3F
Jul  4 15:53:59 ryan-desktop kernel: [ 9582.206175] easycap::0adjust_saturation: adjusting saturation to  0x2F
Jul  4 15:53:59 ryan-desktop kernel: [ 9582.233187] easycap::0adjust_hue: adjusting hue to  0x00
Jul  4 15:53:59 ryan-desktop kernel: [ 9582.278018] easycap:: easycap_open: ==========OPEN=========
Jul  4 15:54:04 ryan-desktop kernel: [ 9586.644526] easycap::0adjust_standard: selected standard: PAL_BGHIN
Jul  4 15:54:04 ryan-desktop kernel: [ 9586.923491] easycap::0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x00=std mask
Jul  4 15:54:04 ryan-desktop kernel: [ 9586.923500] easycap::0adjust_format: sought:    V4L2_FIELD_NONE
Jul  4 15:54:04 ryan-desktop kernel: [ 9586.923509] easycap::0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
Jul  4 15:54:04 ryan-desktop kernel: [ 9586.998474] easycap::0adjust_brightness: adjusting brightness to  0x7F
Jul  4 15:54:04 ryan-desktop kernel: [ 9587.025469] easycap::0adjust_contrast: adjusting contrast to  0x3F
Jul  4 15:54:04 ryan-desktop kernel: [ 9587.052466] easycap::0adjust_saturation: adjusting saturation to  0x2F
Jul  4 15:54:04 ryan-desktop kernel: [ 9587.079461] easycap::0adjust_hue: adjusting hue to  0x00
Jul  4 15:55:02 ryan-desktop kernel: [ 9645.294949] easycap:: easycap_open: ==========OPEN=========
Jul  4 15:55:06 ryan-desktop kernel: [ 9649.083266] easycap::0adjust_standard: selected standard: PAL_BGHIN
Jul  4 15:55:06 ryan-desktop kernel: [ 9649.362227] easycap::0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x00=std mask
Jul  4 15:55:06 ryan-desktop kernel: [ 9649.362236] easycap::0adjust_format: sought:    V4L2_FIELD_NONE
Jul  4 15:55:06 ryan-desktop kernel: [ 9649.362244] easycap::0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
Jul  4 15:55:06 ryan-desktop kernel: [ 9649.437213] easycap::0adjust_brightness: adjusting brightness to  0x7F
Jul  4 15:55:06 ryan-desktop kernel: [ 9649.464203] easycap::0adjust_contrast: adjusting contrast to  0x3F
Jul  4 15:55:06 ryan-desktop kernel: [ 9649.491198] easycap::0adjust_saturation: adjusting saturation to  0x2F
Jul  4 15:55:06 ryan-desktop kernel: [ 9649.518195] easycap::0adjust_hue: adjusting hue to  0x00
Jul  4 15:55:06 ryan-desktop kernel: [ 9649.560602] easycap::0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x00=std mask
Jul  4 15:55:06 ryan-desktop kernel: [ 9649.560610] easycap::0adjust_format: sought:    V4L2_FIELD_NONE
Jul  4 15:55:06 ryan-desktop kernel: [ 9649.560617] easycap::0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
Jul  4 15:55:06 ryan-desktop kernel: [ 9649.608223] easycap::0adjust_format: sought:    640x480,UYVY(0x59565955),0=field,0x00=std mask
Jul  4 15:55:06 ryan-desktop kernel: [ 9649.608231] easycap::0adjust_format: sought:    V4L2_FIELD_ANY 
Jul  4 15:55:06 ryan-desktop kernel: [ 9649.608236] easycap::0adjust_format: prefer:    V4L2_FIELD_NONE=field, was V4L2_FIELD_ANY
Jul  4 15:55:06 ryan-desktop kernel: [ 9649.608244] easycap::0adjust_format: actioning: 640x480 PAL_BGHIN_AT_640x480_FMT_UYVY-n
Jul  4 15:55:07 ryan-desktop kernel: [ 9649.656193] easycap::0easycap_ioctl: requested input already in effect
Jul  4 15:55:07 ryan-desktop kernel: [ 9649.656214] easycap::0adjust_standard: selected standard: NTSC_M
Jul  4 15:55:07 ryan-desktop kernel: [ 9649.935165] easycap::0adjust_format: sought:    640x480,UYVY(0x59565955),0=field,0x01=std mask
Jul  4 15:55:07 ryan-desktop kernel: [ 9649.935173] easycap::0adjust_format: sought:    V4L2_FIELD_ANY 
Jul  4 15:55:07 ryan-desktop kernel: [ 9649.935178] easycap::0adjust_format: prefer:    V4L2_FIELD_NONE=field, was V4L2_FIELD_ANY
Jul  4 15:55:07 ryan-desktop kernel: [ 9649.935186] easycap::0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
Jul  4 15:55:07 ryan-desktop kernel: [ 9649.983148] easycap::0adjust_format: sought:    640x480,UYVY(0x59565955),1=field,0x01=std mask
Jul  4 15:55:07 ryan-desktop kernel: [ 9649.983155] easycap::0adjust_format: sought:    V4L2_FIELD_NONE
Jul  4 15:55:07 ryan-desktop kernel: [ 9649.983163] easycap::0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
Jul  4 15:55:07 ryan-desktop kernel: [ 9650.031143] easycap::0adjust_format: sought:    640x480,UYVY(0x59565955),0=field,0x01=std mask
Jul  4 15:55:07 ryan-desktop kernel: [ 9650.031151] easycap::0adjust_format: sought:    V4L2_FIELD_ANY 
Jul  4 15:55:07 ryan-desktop kernel: [ 9650.031156] easycap::0adjust_format: prefer:    V4L2_FIELD_NONE=field, was V4L2_FIELD_ANY
Jul  4 15:55:07 ryan-desktop kernel: [ 9650.031164] easycap::0adjust_format: actioning: 640x480 NTSC_M_AT_640x480_FMT_UYVY-n
Jul  4 15:55:07 ryan-desktop kernel: [ 9650.079309] easycap::0adjust_mute: adjusting mute: 0=peasycap->audio_idle
Jul  4 15:55:07 ryan-desktop kernel: [ 9650.079321] easycap::0adjust_brightness: unchanged brightness at  0x7F
Jul  4 15:55:07 ryan-desktop kernel: [ 9650.079329] easycap::0adjust_hue: unchanged hue at  0x80
Jul  4 15:55:07 ryan-desktop kernel: [ 9650.079336] easycap::0adjust_saturation: unchanged saturation at  0xAF
Jul  4 15:55:07 ryan-desktop kernel: [ 9650.079343] easycap::0adjust_contrast: unchanged contrast at  0xBF
Jul  4 15:55:25 ryan-desktop kernel: [ 9668.252179] easycap::0easycap_dqbuf: aborted by signal


Thanks for the help.

---

### Post by rmt1947 on 2011-07-05
Hi,

Thanks for the diagnostics.  The video part of the driver seems to be working correctly, but simply never receives any video input signal.  The audio part of the driver seems inactive, but that should not matter when you use the mplayer command given in my post #201 above.  There are some messages not written by the driver:

```

Jul 4 15:53:48 ryan-desktop kernel: [ 9571.330069] usb 2-4: new high speed USB device using ehci_hcd and address 4
Jul 4 15:53:48 ryan-desktop kernel: [ 9571.481150] hub 2-0:1.0: unable to enumerate USB device on port 4
Jul 4 15:53:49 ryan-desktop kernel: [ 9572.020083] usb 4-4: new full speed USB device using ohci_hcd and address 4
Jul 4 15:53:49 ryan-desktop kernel: [ 9572.234655] usb 4-4: not running at top speed; connect to a high speed hub

```

In the past I have seen similar messages when an EasyCAP is plugged into a USB1.1 port instead of a USB2.0 port.  The EasyCAP will certainly not work on USB1.1.  Are your sure that your USB port is USB2.0?  Have you tried using the EasyCAP with Microsoft Windows on the same computer, with the EasyCAP plugged into the same USB port as that which you use for Linux?  (Maybe the green screen problem has nothing to do with USB1.1, but logically we must exclude the possibility.)

Mike

---

### Post by rizlmilk on 2011-07-05
EDIT: I kept on trying to plug it into different ports and it finally worked on one of my usb ports. I guess I have a mixture of different versions of usb on this motherboard. So now the video works, do you know of any way to make the audio work?

---

### Post by rmt1947 on 2011-07-06
Hi @rizlmilk,

It's good news that at least the video is working.  I've heard that some machines (particularly laptops) do have a mixture of USB1.1 and USB2.0 ports.

I think it will be difficult to make use of the EasyCAP's sound capabilities while the conflict with the snd_usb_audio module remains unresolved.  It might be easier just to route the sound so that it bypasses the EasyCAP entirely, as explained in my post #4 in the thread at

[http://ubuntuforums.org/showthread.php?t=1673182](http://ubuntuforums.org/showthread.php?t=1673182)

The disadvantage of the bypass arrangement is that there may be poor audio-video synchronization, although you might be able to compensate for it with mencoder, for example.  Every computer is different in this respect, and the only way to find out what's possible is to do some experimentation.

Mike

---

### Post by andlinux on 2011-07-07
Well, in the past this driver worked for me, but now I have reinstalled my system with Ubuntu 11.04 64bit and I get an error message when I want to install it.

```
/easycap_dc60.0.9$ sudo ./install_simple.sh
depmod OK
unlocked_ioctl not required
make clean OK
ERROR:  step failed:  make
/home/****/Bureaublad/easycap_dc60.0.9/src/easycap_main.c:76:2: error: unknown field ‘ioctl’ specified in initializer
/home/****/Bureaublad/easycap_dc60.0.9/src/easycap_main.c:76:2: warning: initialization from incompatible pointer type
make[3]: *** [/home/****/Bureaublad/easycap_dc60.0.9/src/easycap_main.o] Fout 1
make[2]: *** [_module_/home/****/Bureaublad/easycap_dc60.0.9/src] Fout 2
make[1]: *** [all] Fout 2
make: *** [build] Fout 2

```

And when I do sudo ./install.sh then I get this:

```
/easycap_dc60.0.9$ sudo ./install.sh
kernel directory is /lib/modules/2.6.39-0-generic/build
snd_card_new() will not be used
snd_card_create() will be used
<media/v4l2-device.h> will be included
struct v4l2_file_operations OK
unlocked_ioctl required
v4l2_file_operations.unlocked_ioctl will be used
not overwriting top level Makefile
-> saving former src/Makefile as src/Makefile_1310055637
-> regenerating src/Makefile
not overwriting tools/Makefile
make clean OK
ERROR:  step failed:  make
/home/****/Bureaublad/easycap_dc60.0.9/src/easycap_ioctl.c:28:28: fatal error: linux/smp_lock.h: Bestand of map bestaat niet
compilation terminated.
make[3]: *** [/home/****/Bureaublad/easycap_dc60.0.9/src/easycap_ioctl.o] Fout 1
make[2]: *** [_module_/home/****/Bureaublad/easycap_dc60.0.9/src] Fout 2
make[1]: *** [all] Fout 2
make: *** [build] Fout 2

```

What can be the problem and how can i fix it ?

---

### Post by rmt1947 on 2011-07-08
Hi,

I've had reports of problems on Ubuntu 11.04 (Natty) before - see posts ##179 and 185 of the present thread.  But when I tested it myself, as described in my post #188, I had no difficulty in building and using the easycapdc60 driver from Sourceforge on a fresh installation of Ubuntu 11.04.

I repeated this test yesterday, just in case something in Natty had changed during the past two months.  I found that, as before, the driver builds without any errors following a fresh installation of Ubuntu 11.04 and application of the pending 115 updates.

However, this time I spotted something which I hadn't noticed before.  Out of the box Ubuntu 11.04 is configured with the easycap driver in the staging part of the kernel activated, and when plugging in the EasyCAP it is the staging module, not the newly installed Sourceforge module that obtains control of the EasyCAP.  This is not an ideal situation, because the staging version of the easycap driver is an old one which has only OSS audio and no ALSA capability, whereas the Ubuntu distribution itself has not supported OSS at all since 10.10 (Maverick).  It is possible to get video from the staging driver by means of a command such as

```
mplayer tv:// -tv driver=v4l2:norm=PAL_BGHIN:width=640:height=480:outfmt=uyvy:device=/dev/easycap0:input=0:fps=25:noaudio -hardframedrop
```

but there will be no sound.  The solution is to rename the staging module so that it can never be loaded:

```
cd /lib/modules/`uname -r`/kernel/drivers/staging/easycap
sudo mv easycap.ko easycap.ko-WOMBAT
```

After reinstallation of the Sourceforge driver the command

```
sudo find / -name easycap.ko -print
```

should then give (within a minute or two) a result similar to:

/lib/modules/2.6.38-8-generic/kernel/drivers/media/video/easycap.ko
/home/xxxxxxxx/easycap_dc60.0.9/src/easycap.ko

When I followed this procedure I got a good picture and sound on running the script ./testPAL.sh.

The tests described above were done using as installation image xubuntu-11.04-desktop-i386.iso.  (My test computer dates from 2006 and has a single-core Celeron processor.  It is definitely incapable of running the Unity GUI and I believe it to be unsuitable for a 64-bit operating system.)  I doubt very much that the differences 64/32-bit and ubuntu/xubuntu are relevant to the difficulties people are having with the EasyCAP on Ubuntu 11.04.  The most likely reason for failures during installation of the Sourceforge driver, I think, is that the some or all of the Video4Linux software stack has been manually updated beyond the level provided by the Ubuntu 11.04 repository, for example by downloading and compiling source code from

[http://linuxtv.org/downloads/](http://linuxtv.org/downloads/) 

or by backporting Video4Linux modules from Ubuntu 11.10 (Oneiric).  Of course, there may be other reasons which I have overlooked so far.

Mike

---

### Post by rmt1947 on 2011-07-08
Hi @timgood,

There's been some discussion recently of the syndrome "good video for a few seconds, then grey bars" on the forum at

[http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/4583233](http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/4583233)

It seems that a possible solution might be to edit line 31 of the script ./install.sh so that it becomes

BARS=0

and then run ./install.sh again.  Worth a try.

Mike

---

### Post by andlinux on 2011-07-08
> **rmt1947 said:**
>  The most likely reason for failures during installation of the Sourceforge driver, I think, is that the some or all of the Video4Linux software stack has been manually updated beyond the level provided by the Ubuntu 11.04 repository, for example by [B]downloading and compiling source code from

[http://linuxtv.org/downloads/](http://linuxtv.org/downloads/)[/B] 

or by backporting Video4Linux modules from Ubuntu 11.10 (Oneiric).  Of course, there may be other reasons which I have overlooked so far.

Mike
That's true, I downloaded code from there and compiled it. I had to do that so that my dvb-t stick would work. :)

I will try the instructions above, I don't need sound so that's no problem for me.

PS: when I first plugged in the easycap stick, I saw that the LED was on.

---

### Post by evilxsystems on 2011-07-31
Hi-

I've got a easycap dc60...the drivers off sourceforge are working great for the video, but I can't seem to get the audio to work at all.  The first time I ran the testNTSC.sh script the sound was audible but very choppy.  Subsequently I have been unable to get any sound out of the device.   I've been reading through the 200some posts here but it's unclear to me if the easycap's sound will work on 10.10?  I do not have a /dev/dsp file....can the sound work?   I'm on a netbook and have no other audio inputs, so routing it to my soundcard is not an option for me.

---

### Post by rmt1947 on 2011-08-01
Hi,

Version 0.9 of the Sourceforge driver should give both video and audio on Ubuntu 10.10.  For this version you don't need /dev/dsp, but when the EasyCAP is plugged in you should be able to find

/proc/asound/EasyALSA#

where '#' means a digit such as 0, 1, etc.  Presumably you do have this, because I think the script ./testNTSC.sh fails totally if it is missing.

EasyCAPs vary greatly for one to another as regards sound quality.  Some are very good, but others give scratchy or hissy audio, particularly those which have no dedicated audio chip of any kind:

[http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/3746051](http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/3746051)

You can find out whether your EasyCAP has a dedicated audio chip either by opening the case and having a peep or non-intrusively by running the script ./frequency.sh.  A full-specification EasyCAP gives the result

Audio frequency is 48000 Hz

whereas an EasyCAP without dedicated audio chip gives

Audio frequency is 32000 Hz

(Please note that, as far as I know, the 4-CVBS EasyCAPs do not have a dedicated audio chip by design, and this should not be regarded as a defect.)

If your audio is breaking up (intermittent), there may be a simpler explanation such as a poor electrical connection.  There's always the possibility, I suppose, that PulseAudio is implicated somehow, but I can't comment on this because I know so little about it.  I'd be inclined to experiment with different cables, connectors and alsamixer settings in an attempt to revive the sound which you heard initially.

If you have access to a second computer, you could test the EasyCAP on that, either with the Windows driver or with the Sourceforge driver if the second machine is running Linux.  If you cannot get any audio from the EasyCAP on the second machine I'd begin to suspect that a hardware fault has developed in the EasyCAP's internal audio path.

Mike

---

### Post by evilxsystems on 2011-08-02
I would not say it is intermittent.  It only worked the first time I plugged it in and has never worked since (I've been fighting with it for days).  I have opened it up and the connections look good and the audio source when plugged into another system is outputting audio.  I have not been able to try the easycap on a different OS to see if the audio works.  The frequency.sh script lists it as having a 48Khz rate.  The sound control panel has the stereo inputs for the easycap, but the levels for the on screen mixer show no signal.  Also alsamixer lists the device as having no controls for capture...ie there is nothing to adjust in alsamixer for the device.  Interestingly, if I connect the device after the computer is on, instead of EASYALSA the device is called USB Capture (something or other) and that device has a digital capture control (that you cannot adjust the levels of) in alsamixer.  This really seems like it must be a driver issue or a pulseaudio issue, but I'm not sure what to try.

---

### Post by rmt1947 on 2011-08-03
If /dev/video0 and /proc/asound/EasyALSA0 are both present while the EasyCAP is plugged in we can infer that the driver is almost certainly working correctly.  If /dev/video0 is present and /proc/asound/EasyALSA0 is missing, it means that the EasyCAP's sound channel was not properly recognized at the moment the EasyCAP was plugged in.  The solution then is to unplug the EasyCAP, run ./install.sh and plug in the EasyCAP again.  This procedure should restore /proc/asound/EasyALSA0.  As far as I know, you won't get any sound from the EasyCAP if the "USB Capture" thing gets control of it.

When /dev/video0 and /proc/EasyALSA0 are both present and you run ./testNTSC.sh you will see diagnostics written by mplayer in a file called ./testeasycap0.log or something similar.  It would be interesting to see what's in that file.

Driver version 0.9 really should behave nicely on Ubuntu 10.10.  I'm assuming you haven't downloaded any video or audio packages from more recent repositories (see post #211 above).

Mike

---

### Post by evilxsystems on 2011-08-04
No I haven't been updating V4L or anything....here;s the log file:

```
Config pushed level is now 2
Config pushed level is now 3
Setting tv=driver=v4l2:norm=NTSC_M:width=640:height=480:outfmt=uyvy:device=/dev/easycap1:input=0:fps=30:buffersize=16:alsa:amode=1:forcechan=2:audiorate=48000:adevice=plughw.1,0:forceaudio:immediatemode=0
Setting hardframedrop=-ao
Setting ao=alsa
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 10
CPU: Intel(R) Atom(TM) CPU N455   @ 1.66GHz (Family: 6, Model: 28, Stepping: 10)
extended cpuid-level: 8
extended cache-info: 33579072
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/mark/.mplayer/codecs.conf'
Reading /home/mark/.mplayer/codecs.conf: Can't open '/home/mark/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --disable-arts --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --target=i586-linux --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
CommandLine: 'tv://' '-tv' 'driver=v4l2:norm=NTSC_M:width=640:height=480:outfmt=uyvy:device=/dev/easycap1:input=0:fps=30:buffersize=16:alsa:amode=1:forcechan=2:audiorate=48000:adevice=plughw.1,0:forceaudio:immediatemode=0' '-hardframedrop' '-ao' 'alsa' '-msglevel' 'all=9'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/mark/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/mark/.mplayer/input.conf'
Can't open input config file /home/mark/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 91 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('.conf') -> '/home/mark/.mplayer/.conf'

[[[init getch2]]]

Playing tv://.
get_path('sub/') -> '/home/mark/.mplayer/sub/'
STREAM: [tv] tv://
STREAM: Description: TV Input
STREAM: Author: Benjamin Zores, Albeu
STREAM: Comment: 
seek to 0x0
s->pos=0  newpos=0  new_bufpos=0  buflen=0  
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: video fd: /dev/easycap1: 3
Selected device: EasyCAP DC60
 Capabilites:  video capture  audio  read/write  streaming
 supported norms: 0 = PAL_BGHIN; 1 = NTSC_N_443; 2 = PAL_Nc; 3 = NTSC_N; 4 = SECAM; 5 = NTSC_M; 6 = NTSC_M_JP; 7 = PAL_60; 8 = NTSC_443; 9 = PAL_M; 10 = PAL_BGHIN_SLOW; 11 = NTSC_N_443_SLOW; 12 = PAL_Nc_SLOW; 13 = NTSC_N_SLOW; 14 = SECAM_SLOW; 15 = NTSC_M_SLOW; 16 = NTSC_M_JP_SLOW; 17 = PAL_60_SLOW; 18 = NTSC_443_SLOW; 19 = PAL_M_SLOW;
 inputs: 0 = CVBS0; 1 = CVBS1; 2 = CVBS2; 3 = CVBS3; 4 = CVBS4; 5 = S-VIDEO;
 Current input: 0
 Format UYVY   (16 bits, uyvy): Packed UYVY
 Format YUYV   (16 bits, yuy2): Packed YUY2
 Format RGB24  (24 bits, rgb24): RGB 24-bit
 Format RGB32  (32 bits, rgb32): RGBA
 Format BGR24  (24 bits, bgr24): BGR 24-bit
 Format BGR32  (32 bits, bgr32): BGRA
 Current format: UYVY
v4l2: set format: UYVY
v4l2: set input: 0
Selected norm : NTSC_M
v4l2: set norm: NTSC_M
v4l2: set width: 640
v4l2: set height: 480
Selected input hasn't got a tuner!
==> Found video stream: 0
v4l2: get format: UYVY
v4l2: get fps: 30.000000
v4l2: get width: 640
v4l2: get height: 480
Plug PCM: Rate conversion PCM (48000, sformat=S16_LE)
Converter: libspeex (builtin)
Protocol version: 10002
Its setup is:
  stream       : CAPTURE
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 44100
  exact rate   : 44100 (44100/1)
  msbits       : 16
  buffer_size  : 120422
  period_size  : 3763
  period_time  : 85333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 3763
  period_event : 0
  start_threshold  : 0
  stop_threshold   : 120422
  silence_threshold: 0
  silence_size : 0
  boundary     : 986497024
Slave: Hardware PCM card 1 'easycap_alsa' device 0 subdevice 0
Its setup is:
  stream       : CAPTURE
  access       : MMAP_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 131072
  period_size  : 4096
  period_time  : 85333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 4096
  period_event : 0
  start_threshold  : 0
  stop_threshold   : 131072
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
  appl_ptr     : 0
  hw_ptr       : 0
v4l2: set audio samplerate: 48000
Plug PCM: Hardware PCM card 1 'easycap_alsa' device 0 subdevice 0
Its setup is:
  stream       : CAPTURE
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 131072
  period_size  : 4096
  period_time  : 85333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 4096
  period_event : 0
  start_threshold  : 0
  stop_threshold   : 131072
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
  appl_ptr     : 0
  hw_ptr       : 0
v4l2: get audio format: 9
==> Found audio stream: 0
v4l2: get audio samplerate: 48000
v4l2: get audio samplesize: 2
v4l2: get audio channels: 2
  TV audio: 2 channels, 16 bits, 48000 Hz
Audio capture - buffer 256 blocks of 16384 bytes, skew average from 16 meas.
Using a ring buffer for maximum 13 frames, 7 MB total size.
v4l2: set Brightness: 127 [0, 255]
v4l2: set Hue: 128 [0, 255]
v4l2: set Saturation: 175 [0, 255]
v4l2: set Contrast: 191 [0, 255]
[V] filefmt:9  fourcc:0x59565955  size:640x480  fps:30.000  ftime:=0.0333
get_path('sub/') -> '/home/mark/.mplayer/sub/'
v4l2: going to capture

fps = -1.000000, interval = 0.000000, a_skew = 0.000000, corr_skew = 0.000000
vcnt = 0, acnt = 0
DEMUX: Append packet to d_video, len=1228800  pts=0.000  pos=0  [packs: A=0 V=1]
grab_audio_frame(priv=0xa377e30, buffer=0xa383a88, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=0.085  pos=0  [packs: A=1 V=1]
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] This driver only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1024x600 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1

fps = 23.194322, interval = 0.043114, a_skew = -0.057894, corr_skew = -0.025868
vcnt = 0, acnt = 0
[VO_XV] Using Xv Adapter #0 (Intel(R) Textured Video)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 2048x2048
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Packed UYVY)
Trying filter chain: vo
vo_debug: query(Packed UYVY) returned 0x437 (i=0) 
VDec: using Packed UYVY as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO Config (640x480->640x480,flags=0,'MPlayer',0x59565955)
VO: [xv] 640x480 => 640x480 Packed UYVY 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x434d5658 (XVMC) planar

fps = 29.250885, interval = 0.077301, a_skew = -0.057894, corr_skew = -0.046380
vcnt = 1, acnt = 0

fps = 29.923993, interval = 0.110719, a_skew = -0.057894, corr_skew = -0.057894
vcnt = 2, acnt = 0
using Xvideo port 71 for hw scaling

fps = 30.947297, interval = 0.143032, a_skew = -0.055518, corr_skew = -0.055518
vcnt = 3, acnt = 1
Selected video codec: [rawuyvy] vfm: raw (RAW UYVY)
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
dec_audio: Allocating 2048 + 65536 = 67584 bytes for output buffer.
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Trying preferred audio driver 'alsa', options '[none]'
alsa-init: requested format: 48000 Hz, 2 channels, 9
alsa-init: using ALSA 1.0.23
alsa-init: setup for 1/2 channel(s)
alsa-init: using device default
alsa-init: pcm opened in blocking mode

fps = 29.200491, interval = 0.177278, a_skew = -0.054543, corr_skew = -0.054543
vcnt = 4, acnt = 1

fps = 30.212393, interval = 0.210377, a_skew = -0.054745, corr_skew = -0.054745
vcnt = 5, acnt = 2
alsa-init: got buffersize=96000
alsa-init: got period size 1500
alsa: 48000 Hz/2 channels/4 bpf/96000 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: ALSA-0.9.x-1.x audio output
AO: Author: Alex Beregszaszi, Zsolt Barat <joy@streamminister.de>
AO: Comment: under developement
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Starting playback...
ds_fill_buffer(d_audio) called
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=0.171  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=0.256  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 29.741546, interval = 0.244000, a_skew = -0.054819, corr_skew = -0.054819
vcnt = 6, acnt = 0

fps = 30.336124, interval = 0.276964, a_skew = -0.054891, corr_skew = -0.054891
vcnt = 7, acnt = 0
DEMUX: Append packet to d_audio, len=16384  pts=0.341  pos=0  [packs: A=1 V=1]
Increasing filtered audio buffer size from 0 to 65536
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 30.275507, interval = 0.309994, a_skew = -0.055496, corr_skew = -0.055496
vcnt = 8, acnt = 0

fps = 17.244352, interval = 0.367984, a_skew = -0.055911, corr_skew = -0.055911
vcnt = 9, acnt = 0
DEMUX: Append packet to d_audio, len=16384  pts=0.427  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 23.802723, interval = 0.409996, a_skew = -0.055043, corr_skew = -0.055043
vcnt = 10, acnt = 0

fps = 29.417821, interval = 0.443989, a_skew = -0.054847, corr_skew = -0.054847
vcnt = 11, acnt = 0
DEMUX: Append packet to d_audio, len=16384  pts=0.512  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=0.069  pos=0  [packs: A=0 V=1]
*** [vo] Exporting mp_image_t, 640x480x16bpp YUV packed, 614400 bytes
(imgfmt: 59565955, planes: (nil),(nil),(nil) strides: 0,0,0, chroma: 0x0, shift: h:0,v:0)
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=0.124  pos=0  [packs: A=0 V=1]

fps = 30.316811, interval = 0.476974, a_skew = -0.054964, corr_skew = -0.054964
vcnt = 10, acnt = 0
Unicode font: 5103 glyphs.
Unicode font: 5103 glyphs.
OSD chg: 6  V: no  pb:-1  
OSD chg: 5  V: no  pb:-1  
OSD chg: 3  V: no  pb:-1  
OSD chg: 2  V: no  pb:-1  
*** ftime=0.000 ***
delay=0.259083
A:   0.3 V:   0.1 A-V:  0.226 ct:  0.000   2/  2 ??% ??% ??,?% 1 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 29.448142, interval = 0.510932, a_skew = -0.054985, corr_skew = -0.054985
vcnt = 11, acnt = 0

fps = 30.244375, interval = 0.543996, a_skew = -0.055260, corr_skew = -0.055260
vcnt = 12, acnt = 1
DEMUX: Append packet to d_audio, len=16384  pts=0.597  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 30.267260, interval = 0.577035, a_skew = -0.055382, corr_skew = -0.055382
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 29.379793, interval = 0.611072, a_skew = -0.055507, corr_skew = -0.055507
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=0.683  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 30.372980, interval = 0.643996, a_skew = -0.055131, corr_skew = -0.055131
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 30.275507, interval = 0.677026, a_skew = -0.055024, corr_skew = -0.055024
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=0.768  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=0.169  pos=0  [packs: A=0 V=1]
*** ftime=0.055 ***
delay=0.293083
A:   0.5 V:   0.1 A-V:  0.387 ct:  0.002   3/  3 ??% ??% ??,?% 2 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 16.678898, interval = 0.736982, a_skew = -0.055011, corr_skew = -0.055011
vcnt = 12, acnt = 0

fps = 24.971283, interval = 0.777028, a_skew = -0.055021, corr_skew = -0.055021
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=0.853  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 29.331534, interval = 0.811121, a_skew = -0.055257, corr_skew = -0.055257
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 30.390518, interval = 0.844026, a_skew = -0.055346, corr_skew = -0.055346
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 29.461155, interval = 0.877969, a_skew = -0.055437, corr_skew = -0.055437
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=0.939  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=0.199  pos=0  [packs: A=0 V=1]
*** ftime=0.045 ***
delay=0.313688
A:   0.7 V:   0.2 A-V:  0.509 ct:  0.003   4/  4 ??% ??% ??,?% 3 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 30.286510, interval = 0.910987, a_skew = -0.055110, corr_skew = -0.055110
vcnt = 12, acnt = 0

fps = 30.288345, interval = 0.944003, a_skew = -0.055035, corr_skew = -0.055035
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=1.024  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 29.326373, interval = 0.978102, a_skew = -0.055040, corr_skew = -0.055040
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 30.385901, interval = 1.011012, a_skew = -0.055043, corr_skew = -0.055043
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 30.303949, interval = 1.044011, a_skew = -0.055046, corr_skew = -0.055046
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=1.109  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=0.232  pos=0  [packs: A=0 V=1]
*** ftime=0.030 ***
delay=0.292604
A:   0.9 V:   0.2 A-V:  0.657 ct:  0.004   5/  5 ??% ??% ??,?% 4 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 17.864480, interval = 1.099988, a_skew = -0.055296, corr_skew = -0.055296
vcnt = 12, acnt = 0

fps = 22.663917, interval = 1.144111, a_skew = -0.055156, corr_skew = -0.055156
vcnt = 13, acnt = 1

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=1.195  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 29.512454, interval = 1.177995, a_skew = -0.055098, corr_skew = -0.055098
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 30.303949, interval = 1.210994, a_skew = -0.055042, corr_skew = -0.055042
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=1.280  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 29.292012, interval = 1.245133, a_skew = -0.055072, corr_skew = -0.055072
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 30.433989, interval = 1.277991, a_skew = -0.055076, corr_skew = -0.055076
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=1.365  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=0.265  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.263937
A:   1.1 V:   0.2 A-V:  0.871 ct:  0.006   6/  6 ??% ??% ??,?% 5 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 28.562452, interval = 1.313002, a_skew = -0.055208, corr_skew = -0.055208
vcnt = 12, acnt = 0

fps = 31.158472, interval = 1.345096, a_skew = -0.055259, corr_skew = -0.055259
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 30.397909, interval = 1.377993, a_skew = -0.055312, corr_skew = -0.055312
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=1.451  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 30.296604, interval = 1.411000, a_skew = -0.054736, corr_skew = -0.054736
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 17.548170, interval = 1.467986, a_skew = -0.054160, corr_skew = -0.054160
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=1.536  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=0.299  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.305937
A:   1.3 V:   0.3 A-V:  1.014 ct:  0.007   7/  7 ??% ??% ??,?% 6 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 23.248245, interval = 1.511000, a_skew = -0.055049, corr_skew = -0.055049
vcnt = 12, acnt = 0

fps = 29.325513, interval = 1.545100, a_skew = -0.055471, corr_skew = -0.055471
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=1.621  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 30.399757, interval = 1.577995, a_skew = -0.055452, corr_skew = -0.055452
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 29.433407, interval = 1.611970, a_skew = -0.055477, corr_skew = -0.055477
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 29.821370, interval = 1.645503, a_skew = -0.055501, corr_skew = -0.055501
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=1.707  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 30.769231, interval = 1.678003, a_skew = -0.055117, corr_skew = -0.055117
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 29.420418, interval = 1.711993, a_skew = -0.054942, corr_skew = -0.054942
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=1.792  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called

fps = 30.135005, interval = 1.745177, a_skew = -0.055101, corr_skew = -0.055101
vcnt = 13, acnt = 0
DEMUX: Append packet to d_video, len=614400  pts=0.332  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.265417
A:   1.5 V:   0.3 A-V:  1.240 ct:  0.008   8/  8 ??% ??% ??,?% 7 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 30.460873, interval = 1.778006, a_skew = -0.055224, corr_skew = -0.055224
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=1.877  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 16.955475, interval = 1.836984, a_skew = -0.055393, corr_skew = -0.055393
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 24.371222, interval = 1.878016, a_skew = -0.055446, corr_skew = -0.055446
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=1.963  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 29.425612, interval = 1.912000, a_skew = -0.055243, corr_skew = -0.055243
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 30.088762, interval = 1.945235, a_skew = -0.055111, corr_skew = -0.055111
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 29.630508, interval = 1.978984, a_skew = -0.054977, corr_skew = -0.054977
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=2.048  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=0.365  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.245917
A:   1.8 V:   0.3 A-V:  1.445 ct:  0.009   9/  9 ??% ??% ??,?% 8 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 30.282842, interval = 2.012006, a_skew = -0.055172, corr_skew = -0.055172
vcnt = 12, acnt = 0

fps = 30.269092, interval = 2.045043, a_skew = -0.055264, corr_skew = -0.055264
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 29.471575, interval = 2.078974, a_skew = -0.055369, corr_skew = -0.055369
vcnt = 13, acnt = 1

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=2.133  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 30.279174, interval = 2.112000, a_skew = -0.055416, corr_skew = -0.055416
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 30.293850, interval = 2.145010, a_skew = -0.055464, corr_skew = -0.055464
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=2.219  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 16.956912, interval = 2.203983, a_skew = -0.055125, corr_skew = -0.055125
vcnt = 13, acnt = 0

video buffer full - dropping frame

fps = 24.370629, interval = 2.245016, a_skew = -0.054971, corr_skew = -0.054971
vcnt = 13, acnt = 0

video buffer full - dropping frame
DEMUX: Append packet to d_audio, len=16384  pts=2.304  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=0.424  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.527167
A:   1.8 V:   0.4 A-V:  1.411 ct:  0.009  10/ 10 ??% ??% ??,?% 9 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=0.465  pos=0  [packs: A=0 V=1]
*** ftime=0.058 ***
delay=0.526896
A:   1.8 V:   0.4 A-V:  1.353 ct:  0.010  11/ 11 ??% ??% ??,?% 10 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=0.499  pos=0  [packs: A=0 V=1]
*** ftime=0.041 ***
delay=0.524521
A:   1.8 V:   0.5 A-V:  1.315 ct:  0.011  12/ 12 ??% ??% ??,?% 11 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=0.532  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.521500
A:   1.8 V:   0.5 A-V:  1.284 ct:  0.011  13/ 13 ??% ??% ??,?% 12 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=0.566  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.518875
A:   1.8 V:   0.5 A-V:  1.253 ct:  0.012  14/ 14  0%  7% 369.0% 13 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=0.599  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.516479
A:   1.8 V:   0.6 A-V:  1.222 ct:  0.012  15/ 15  0%  7% 346.8% 14 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=0.792  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.545604
A:   1.8 V:   0.6 A-V:  1.191 ct:  0.013  16/ 16  0%  6% 327.5% 15 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=0.966  pos=0  [packs: A=0 V=1]

fps = 29.347029, interval = 2.279091, a_skew = -0.055210, corr_skew = -0.055210
vcnt = 5, acnt = 0
*** ftime=0.193 ***
delay=0.542646
A:   1.8 V:   0.8 A-V:  1.001 ct:  0.013  17/ 17  0%  5% 247.8% 15 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=1.155  pos=0  [packs: A=0 V=1]
*** ftime=0.174 ***
delay=0.538937
A:   1.8 V:   1.0 A-V:  0.830 ct:  0.013  18/ 18  0%  4% 203.2% 16 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=1.368  pos=0  [packs: A=0 V=1]
*** ftime=0.189 ***
delay=0.536687
A:   1.8 V:   1.2 A-V:  0.643 ct:  0.014  19/ 19  0%  3% 169.9% 17 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=1.566  pos=0  [packs: A=0 V=1]
*** ftime=0.213 ***
delay=0.532208
A:   1.8 V:   1.4 A-V:  0.435 ct:  0.014  20/ 20  0%  3% 143.5% 17 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=1.800  pos=0  [packs: A=0 V=1]
*** ftime=0.198 ***
delay=0.527625
A:   1.8 V:   1.6 A-V:  0.242 ct:  0.014  21/ 21  0%  2% 125.3% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=2.067  pos=0  [packs: A=0 V=1]
*** ftime=0.234 ***
delay=0.524458
A:   1.8 V:   1.8 A-V:  0.011 ct:  0.014  22/ 22  0%  2% 109.0% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=2.334  pos=0  [packs: A=0 V=1]
*** ftime=0.267 ***
delay=0.520646

fps = 30.422878, interval = 2.311961, a_skew = -0.055291, corr_skew = -0.055291
vcnt = 0, acnt = 0

fps = 29.399659, interval = 2.345975, a_skew = -0.055382, corr_skew = -0.055382
vcnt = 1, acnt = 1

fps = 30.293850, interval = 2.378985, a_skew = -0.055434, corr_skew = -0.055434
vcnt = 2, acnt = 1

fps = 30.284676, interval = 2.412005, a_skew = -0.055485, corr_skew = -0.055485
vcnt = 3, acnt = 1
A:   1.9 V:   2.1 A-V: -0.125 ct:  0.014  23/ 23  0%  2% 95.0% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=2.389  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=2.475  pos=0  [packs: A=1 V=1]
delay=0.516708

fps = 29.428210, interval = 2.445986, a_skew = -0.055197, corr_skew = -0.055197
vcnt = 4, acnt = 0

fps = 30.308541, interval = 2.478980, a_skew = -0.055081, corr_skew = -0.055081
vcnt = 5, acnt = 0

fps = 30.292933, interval = 2.511991, a_skew = -0.055167, corr_skew = -0.055167
vcnt = 6, acnt = 1
A:   2.1 V:   2.1 A-V:  0.007 ct:  0.015  23/ 23  0%  2% 95.0% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=2.560  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=2.367  pos=0  [packs: A=0 V=1]
*** ftime=0.267 ***
delay=0.535417= 6.516429, a_skew = -0.055349, corr_skew = -0.055349
vcnt = 12, acnt = 1
DEMUX: Append packet to d_audio, len=16384  pts=6.571  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=6.138  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.468646
A:   6.1 V:   6.1 A-V: -0.000 ct:  0.017 126/126  0%  2% 35.1% 18 0 [J ds_fill_buffer(d_video) called

...

fps = 29.345306, interval = 15.692020, a_skew = -0.056530, corr_skew = -0.056530
vcnt = 12, acnt = 0
A:  15.2 V:  15.2 A-V:  0.000 ct:  0.016 372/372  0%  2% 16.8% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.315  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.487187
A:  15.3 V:  15.3 A-V:  0.000 ct:  0.016 373/373  0%  2% 16.8% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=15.787  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.348  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.484125

fps = 17.569135, interval = 15.748938, a_skew = -0.056597, corr_skew = -0.056597
vcnt = 11, acnt = 0
A:  15.3 V:  15.3 A-V:  0.000 ct:  0.016 374/374  0%  2% 16.8% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.382  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.482521

fps = 23.203471, interval = 15.792035, a_skew = -0.056641, corr_skew = -0.056641
vcnt = 11, acnt = 0
A:  15.3 V:  15.3 A-V:  0.000 ct:  0.016 375/375  0%  2% 16.7% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.414  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.480771

fps = 30.288345, interval = 15.825051, a_skew = -0.056499, corr_skew = -0.056499
vcnt = 11, acnt = 1
A:  15.4 V:  15.4 A-V:  0.000 ct:  0.016 376/376  0%  2% 16.7% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=15.872  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.448  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.477938

fps = 29.436006, interval = 15.859023, a_skew = -0.056389, corr_skew = -0.056389
vcnt = 11, acnt = 0
A:  15.4 V:  15.4 A-V:  0.000 ct:  0.016 377/377  0%  2% 16.7% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.481  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.476938

fps = 30.154087, interval = 15.892186, a_skew = -0.056281, corr_skew = -0.056281
vcnt = 11, acnt = 0
A:  15.4 V:  15.4 A-V:  0.000 ct:  0.016 378/378  0%  2% 16.6% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.515  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.474333

fps = 30.502684, interval = 15.924970, a_skew = -0.056474, corr_skew = -0.056474
vcnt = 11, acnt = 1
A:  15.5 V:  15.5 A-V:  0.001 ct:  0.016 379/379  0%  2% 16.6% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=15.957  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.549  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.471417

fps = 29.442940, interval = 15.958934, a_skew = -0.056556, corr_skew = -0.056556
vcnt = 11, acnt = 0
A:  15.5 V:  15.5 A-V:  0.000 ct:  0.016 380/380  0%  2% 16.6% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.582  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.469813

fps = 30.193237, interval = 15.992054, a_skew = -0.056585, corr_skew = -0.056585
vcnt = 11, acnt = 1
A:  15.5 V:  15.5 A-V:  0.000 ct:  0.016 381/381  0%  2% 16.5% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=16.043  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.648  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.467396

fps = 30.373903, interval = 16.024977, a_skew = -0.056617, corr_skew = -0.056617
vcnt = 11, acnt = 0
A:  15.6 V:  15.6 A-V:  0.000 ct:  0.016 382/382  0%  2% 16.5% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.681  pos=0  [packs: A=0 V=1]
*** ftime=0.067 ***
delay=0.465354

fps = 29.363401, interval = 16.059033, a_skew = -0.056651, corr_skew = -0.056651
vcnt = 11, acnt = 0
A:  15.6 V:  15.6 A-V:  0.000 ct:  0.016 383/383  0%  2% 16.4% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=16.128  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.714  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.492417

fps = 17.577164, interval = 16.115925, a_skew = -0.056401, corr_skew = -0.056401
vcnt = 11, acnt = 0
A:  15.7 V:  15.7 A-V:  0.000 ct:  0.016 384/384  0%  2% 16.4% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.749  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.491500

fps = 23.204010, interval = 16.159021, a_skew = -0.056440, corr_skew = -0.056440
vcnt = 11, acnt = 1
A:  15.7 V:  15.7 A-V:  0.000 ct:  0.016 385/385  0%  2% 16.4% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=16.213  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.806  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.489167

fps = 30.284676, interval = 16.192041, a_skew = -0.056521, corr_skew = -0.056521
vcnt = 11, acnt = 0
A:  15.7 V:  15.7 A-V:  0.000 ct:  0.016 386/386  0%  2% 16.3% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.849  pos=0  [packs: A=0 V=1]
*** ftime=0.057 ***
delay=0.486083

fps = 29.436873, interval = 16.226012, a_skew = -0.056604, corr_skew = -0.056604
vcnt = 11, acnt = 0

fps = 30.376671, interval = 16.258932, a_skew = -0.056615, corr_skew = -0.056615
vcnt = 12, acnt = 1
A:  15.8 V:  15.8 A-V:  0.000 ct:  0.016 387/387  0%  2% 16.3% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=16.299  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.882  pos=0  [packs: A=0 V=1]
*** ftime=0.043 ***
delay=0.490521

fps = 30.279174, interval = 16.291958, a_skew = -0.056647, corr_skew = -0.056647
vcnt = 12, acnt = 0
A:  15.8 V:  15.8 A-V:  0.000 ct:  0.016 388/388  0%  2% 16.2% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.915  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.510750

fps = 29.336697, interval = 16.326045, a_skew = -0.056679, corr_skew = -0.056679
vcnt = 12, acnt = 0
A:  15.9 V:  15.9 A-V:  0.001 ct:  0.016 389/389  0%  2% 16.2% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=16.384  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.948  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.508396

fps = 30.342568, interval = 16.359002, a_skew = -0.056453, corr_skew = -0.056453
vcnt = 12, acnt = 0
A:  15.9 V:  15.9 A-V:  0.000 ct:  0.016 390/390  0%  2% 16.2% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=15.981  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.506479

fps = 28.302154, interval = 16.394335, a_skew = -0.056342, corr_skew = -0.056342
vcnt = 12, acnt = 0
A:  15.9 V:  15.9 A-V:  0.000 ct:  0.016 391/391  0%  2% 16.1% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=16.469  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.015  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.495583

fps = 31.646571, interval = 16.425934, a_skew = -0.056476, corr_skew = -0.056476
vcnt = 12, acnt = 0
A:  16.0 V:  16.0 A-V:  0.000 ct:  0.016 392/392  0%  2% 16.2% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.049  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.504729
A:  16.0 V:  16.0 A-V:  0.000 ct:  0.016 393/393  0%  2% 16.1% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.082  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.469375

fps = 16.948865, interval = 16.484935, a_skew = -0.056618, corr_skew = -0.056618
vcnt = 11, acnt = 0
A:  16.0 V:  16.0 A-V:  0.000 ct:  0.016 394/394  0%  2% 16.1% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=16.555  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.116  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.466979

fps = 24.376569, interval = 16.525958, a_skew = -0.056633, corr_skew = -0.056633
vcnt = 11, acnt = 0
A:  16.1 V:  16.1 A-V:  0.000 ct:  0.016 395/395  0%  2% 16.1% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.172  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.465750

fps = 30.206917, interval = 16.559063, a_skew = -0.056664, corr_skew = -0.056664
vcnt = 11, acnt = 0
A:  16.1 V:  16.1 A-V:  0.000 ct:  0.016 396/396  0%  2% 16.0% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.215  pos=0  [packs: A=0 V=1]
*** ftime=0.057 ***
delay=0.462542

fps = 29.521167, interval = 16.592937, a_skew = -0.056521, corr_skew = -0.056521
vcnt = 11, acnt = 1

fps = 30.304867, interval = 16.625935, a_skew = -0.056411, corr_skew = -0.056411
vcnt = 12, acnt = 1
A:  16.2 V:  16.2 A-V:  0.000 ct:  0.016 397/397  0%  2% 16.0% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=16.640  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.249  pos=0  [packs: A=0 V=1]
*** ftime=0.043 ***
delay=0.499875

fps = 30.243460, interval = 16.659000, a_skew = -0.056301, corr_skew = -0.056301
vcnt = 12, acnt = 0
A:  16.2 V:  16.2 A-V:  0.000 ct:  0.016 398/398  0%  2% 15.9% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=16.725  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.283  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.519354

fps = 29.325513, interval = 16.693100, a_skew = -0.056484, corr_skew = -0.056484
vcnt = 12, acnt = 0
A:  16.2 V:  16.2 A-V:  0.000 ct:  0.016 399/399  0%  2% 15.9% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.316  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.486708

fps = 30.482229, interval = 16.725906, a_skew = -0.056558, corr_skew = -0.056558
vcnt = 12, acnt = 0
A:  16.3 V:  16.3 A-V:  0.000 ct:  0.016 400/400  0%  2% 15.9% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.349  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.484771

fps = 30.270925, interval = 16.758941, a_skew = -0.056587, corr_skew = -0.056587
vcnt = 12, acnt = 1
A:  16.3 V:  16.3 A-V:  0.000 ct:  0.016 401/401  0%  2% 15.8% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=16.811  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.383  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.481958

fps = 29.403981, interval = 16.792950, a_skew = -0.056620, corr_skew = -0.056620
vcnt = 12, acnt = 0
A:  16.3 V:  16.3 A-V:  0.000 ct:  0.016 402/402  0%  2% 15.8% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.415  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.480979
A:  16.4 V:  16.4 A-V:  0.000 ct:  0.016 403/403  0%  2% 15.8% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 17.861927, interval = 16.848935, a_skew = -0.056498, corr_skew = -0.056498
vcnt = 12, acnt = 1
DEMUX: Append packet to d_audio, len=16384  pts=16.896  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.451  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.499625
A:  16.4 V:  16.4 A-V:  0.000 ct:  0.016 404/404  0%  2% 15.8% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.482  pos=0  [packs: A=0 V=1]
*** ftime=0.035 ***
delay=0.506896

fps = 22.740193, interval = 16.892910, a_skew = -0.056352, corr_skew = -0.056352
vcnt = 11, acnt = 0
A:  16.5 V:  16.5 A-V:  0.000 ct:  0.016 405/405  0%  2% 15.8% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)

fps = 30.178658, interval = 16.926046, a_skew = -0.056416, corr_skew = -0.056416
vcnt = 12, acnt = 1
DEMUX: Append packet to d_audio, len=16384  pts=16.981  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.542  pos=0  [packs: A=0 V=1]
*** ftime=0.032 ***
delay=0.484604
A:  16.5 V:  16.5 A-V:  0.000 ct:  0.016 406/406  0%  2% 15.9% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.583  pos=0  [packs: A=0 V=1]
*** ftime=0.059 ***
delay=0.472208

fps = 29.470706, interval = 16.959978, a_skew = -0.056501, corr_skew = -0.056501
vcnt = 11, acnt = 0

fps = 30.324165, interval = 16.992955, a_skew = -0.056583, corr_skew = -0.056583
vcnt = 12, acnt = 0
A:  16.5 V:  16.5 A-V:  0.000 ct:  0.016 407/407  0%  2% 15.8% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.616  pos=0  [packs: A=0 V=1]
*** ftime=0.041 ***
delay=0.505208

fps = 30.313135, interval = 17.025944, a_skew = -0.056600, corr_skew = -0.056600
vcnt = 12, acnt = 1
A:  16.6 V:  16.6 A-V:  0.002 ct:  0.016 408/408  0%  2% 15.8% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=17.067  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.649  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.494917

fps = 29.434273, interval = 17.059918, a_skew = -0.056636, corr_skew = -0.056636
vcnt = 12, acnt = 0
A:  16.6 V:  16.6 A-V:  0.000 ct:  0.016 409/409  0%  2% 15.8% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.682  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.494250

fps = 30.069762, interval = 17.093174, a_skew = -0.056672, corr_skew = -0.056672
vcnt = 12, acnt = 0
A:  16.6 V:  16.6 A-V:  0.000 ct:  0.016 410/410  0%  2% 15.7% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=17.152  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.715  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.491771

fps = 30.508268, interval = 17.125952, a_skew = -0.056438, corr_skew = -0.056438
vcnt = 12, acnt = 0
A:  16.7 V:  16.7 A-V:  0.000 ct:  0.016 411/411  0%  2% 15.7% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.750  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.490938

fps = 29.468969, interval = 17.159886, a_skew = -0.056327, corr_skew = -0.056327
vcnt = 12, acnt = 0
A:  16.7 V:  16.7 A-V:  0.000 ct:  0.016 412/412  0%  2% 15.7% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=17.237  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.782  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.480375
A:  16.7 V:  16.7 A-V:  0.000 ct:  0.016 413/413  0%  2% 15.7% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.816  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.517917

fps = 17.529713, interval = 17.216932, a_skew = -0.056503, corr_skew = -0.056503
vcnt = 11, acnt = 0
A:  16.8 V:  16.8 A-V:  0.000 ct:  0.016 414/414  0%  2% 15.7% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.850  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***
delay=0.483125

fps = 23.127804, interval = 17.260170, a_skew = -0.056603, corr_skew = -0.056603
vcnt = 11, acnt = 0
A:  16.8 V:  16.8 A-V:  0.000 ct:  0.016 415/415  0%  2% 15.6% 18 0 [J ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.905  pos=0  [packs: A=0 V=1]
*** ftime=0.034 ***
delay=0.481729

fps = 30.388671, interval = 17.293077, a_skew = -0.056606, corr_skew = -0.056606
vcnt = 11, acnt = 1
A:  16.8 V:  16.8 A-V:  0.000 ct:  0.016 416/416  0%  2% 15.6% 18 0 [J ds_fill_buffer(d_audio) called
grab_audio_frame(priv=0xa377e30, buffer=0xb5217518, len=16384)
DEMUX: Append packet to d_audio, len=16384  pts=17.323  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.949  pos=0  [packs: A=0 V=1]
*** ftime=0.056 ***
delay=0.477125

fps = 29.356505, interval = 17.327141, a_skew = -0.056641, corr_skew = -0.056641
vcnt = 11, acnt = 0

fps = 30.465513, interval = 17.359965, a_skew = -0.056502, corr_skew = -0.056502
vcnt = 12, acnt = 1
A:  16.9 V:  16.9 A-V:  0.000 ct:  0.016 417/417  0%  2% 15.6% 18 0 [J 
*** uninit(0xECB)
Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: pcm
Uninit video: raw
DEMUXER: freeing TV demuxer at 0xa3771c0

fps = 30.287428, interval = 17.392982, a_skew = -0.056393, corr_skew = -0.056393
vcnt = 13, acnt = 1

video buffer full - dropping frame
v4l2: 476 frames successfully processed, 47 frames dropped.
v4l2: up to 13 video frames buffered.
DEMUXER: freeing sh_audio at 0xa378240
DEMUXER: freeing sh_video at 0xa373018
Successfully enabled DPMS

[[[uninit getch2]]]
alsa-uninit: pcm closed
vo: uninit ...

Exiting... (Quit)
max framesize was 1228800 bytes
```

I also tried running the testNTSC with test #64  ie audio only...this resulted in a wav file that began with a burst of digital noise and then silence.

---

### Post by rmt1947 on 2011-08-04
Your log file shows that mplayer is actively processing both video and audio, but there does seem to be something strange about the audio data.  I've just run a quick test with one of my own EasyCAPs, and I do not see any mplayer messages of the kind


DEMUX: Append packet to d_audio, len=16384  pts=16.555  pos=0  [packs: A=1 V=1]
ds_fill_buffer(d_video) called
DEMUX: Append packet to d_video, len=614400  pts=16.116  pos=0  [packs: A=0 V=1]
*** ftime=0.033 ***


I do not know enough about mplayer to say what the significance of these messages is.  I've seen a report of similar behaviour before - see the lengthy post #25 at:

[http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/4024036/index/page/1](http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/4024036/index/page/1)

But I never did find a solution to that problem - see my defeated post #5 at:

[http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/4024036/index/page/2](http://sourceforge.net/projects/easycapdc60/forums/forum/1071438/topic/4024036/index/page/2)

I'm not sure what to suggest next.  Ideally one would like to exclude the possibility of a hardware fault in the EasyCAP's internal audio path by testing the EasyCAP on a different machine, preferably one running Microsoft Windows, but I understand that it's not possible for you to do that.  One thought:  is your audio source generating a reasonably large analogue signal?  The EasyCAP expects "Line-In" amplitudes rather than "Microphone" levels.

Mike

---

### Post by evilxsystems on 2011-08-04
it's coming out of a VCR so I think it should be line level.  I really think this is an alsa issue since there isn't a control for the device showing up in alsamixer.  I'll try it on a windows machine to make sure the chips are ok.

---

### Post by rmt1947 on 2011-08-04
Yes, a VCR should be fine - it's what I used for all the development work.

On my Debian Squeeze (which shouldn't be too different from Ubuntu 10.10 I guess), hitting F6 in alsamixer shows


Sound Card
-  (default)
0  HDA Intel
1  easycap_alsa
   enter device name...


I don't have PulseAudio installed, although I doubt that's relevant.  I've never had any feedback from users demonstrating that PulseAudio is responsible for EasyCAP audio problems.  Of course, there can always be a first time.

Mike

---

### Post by evilxsystems on 2011-08-04
what happens when you switch to the easycap and then capture (f4) in alsamixer.  Does it have a control you can adjust?

---

### Post by rmt1947 on 2011-08-05
When I select easycap_alsa I get a display:

 ```
This sound device does not have any controls.
```

and when I then hit F4 nothing at all happens.   On closing alsamixer and running ./testPAL.sh I get perfect video and sound.

Mike

---

### Post by justinfroot on 2011-08-05
go to Drivers:
[http://sourceforge.net/projects/easycapdc60/](http://sourceforge.net/projects/easycapdc60/) for drivers and [http://www.youtube.com/watch?v=Gl_DTRh2h2Q](http://www.youtube.com/watch?v=Gl_DTRh2h2Q) for Linux EasyCAP Tutorial

---

### Post by movieplayer on 2011-09-28
has anyone mentioned what to do if your usb id is not the "408" ?
[B][U]
my easycap dc60 usb id is:[/U][/B]

[SIZE=4]**Bus 001 Device 010: ID 1b71:3002**[/SIZE]


the driver installs fine but it says it only works if your hardware has 408 in the usb id... (mine doesn't)
[SIZE=4]
what do you do if you have a DIFFERENT usb ID?
[/SIZE]

---

### Post by rmt1947 on 2011-09-28
Hi,

I'm sorry to say that I am unaware of any Linux driver for the EasyCAP with USB ID 1b71:3002.

If anybody knows of a suitable driver in existence or in development, it would be nice to hear about it, either on this forum or over at:

[http://sourceforge.net/projects/easycapdc60/forums/forum/1071439/topic/4692009](http://sourceforge.net/projects/easycapdc60/forums/forum/1071439/topic/4692009)

Mike

---

### Post by firefox834 on 2011-10-11
How do i install the driver for easycap, i'm fairly new to all this. I have extracted the download and now have the easycap folder on my desktop but im stuck on how to go to that directory

---

### Post by rmt1947 on 2011-10-15
For the EasyCAP USB ID 05e1:0408, people using the recently released Ubuntu 11.10 (Oneiric Ocelot) do not need to download the SourceForge driver at all.  In Ubuntu 11.10 the kernel (3.0.0-12 or thereabouts) has an easycap driver which works out of the box.  To test it, plug in the EasyCAP, open a terminal window (Unity users click on the topmost Ubuntu icon and type "terminal" in the search box) and try the command:

```
mplayer tv:// -tv driver=v4l2:norm=PAL_BGHIN:outfmt=uyvy:device=/dev/video1:input=0:buffersize=16:noaudio -hardframedrop -vo xv
```

If this doesn't work, replace the string "/dev/video1" by "/dev/video0" or something similar - the required digit depends on what other video-capture hardware is present on the computer.  On my laptop, this command brings up a window within which smooth video is displayed, but there is (intentionally) no sound.

To test the audio capability, try the command

```
mplayer tv:// -tv driver=v4l2:norm=PAL_BGHIN:outfmt=uyvy:device=/dev/video1:input=0:buffersize=16:alsa:amode=1:forcechan=2:audiorate=48000:adevice=plughw.2,0:forceaudio:immediatemode=0 -hardframedrop -vo xv -ao alsa
```

The string "plughw.2,0" here may well need to be replaced by "plughw.1,0" or something similar, depending on what audio hardware is present.  On my test machine the command

```
ls -l /proc/asound
```

generates output containing the line

lrwxrwxrwx   1 root root 5 2011-10-15 16:00 EasyALSA1 -> card2

which means, I think, that the string "plughw.2,0" is right for me, but it certainly won't be right for everybody.

In fact, I could not get the sound working on my computer.  Nothing was audible, and moreover the video was extremely jerky, with many dropped frames, when I used the second mplayer command above.  I can't offer any suggestions as to how to fix this.  It might be a trivial problem, it might not.

Mike

---

### Post by adrianj2012 on 2011-11-05
I've been trying to get the easyCAP to work, but I don't know how to apply the two patches- what commands would I need to run in order for them to apply the patch to the files? A response would be greatly appreciated.

---

### Post by visit on 2011-11-25
"... Nothing was audible, and moreover the video was extremely jerky, with many dropped frames, when I used the second mplayer command above.  I can't offer any suggestions as to how to fix this.  It might be a trivial problem, it might not...."

Mike[/QUOTE]

I have this problem, too... How to fix it?
hi, visit

---

### Post by sjhupp on 2011-11-26
Hi all, would anyone be able to enlighten me on how one would go about getting the driver working in Lucid 10.4 desktop 64bit (kernel 32.34) for an EasyCAP002, with four CVBS inputs and microphone input. The USB ID is 05e1:0408 and the manufacturer is Syntek Semiconductor Co., Ltd. given the driver has been withdrawn from sourceforge now?
I'd rather not upgrade my home server from 10.4LTS, as everything else works pretty well as is.
Is there now a package I can download to get this working?
Would like to use with Zoneminder, just for home use.
Thanks.

---

### Post by ianmillington on 2011-12-20
Hi I have an Easycap DC+ (the one with the Empia 2861 chip). Running kubuntu 11.10 on a dell 630m laptop. I got it to convert a load of VHS footage. Whilst being aware that it was only really intended by the makers for this to work on Windows I thought it was worth a shot.

Some months of fiddling later I am very nearly there. I have been unable to get audio working on this card at all. To me, that's trivial as I can simply by-pass the card with a 2xRCA into 3.5mm jack cable into the Mic socket and the audio works fine. If I use a composite connection within VLC I simply open the capture device, select video mode 1, press play and the video is there. With S video connection it's even easier as S video is option 0 so you don't need to set the video mode.

Recording is a different matter entirely. The video streams flawlessly. However, (I think) because of my computers limited resources I cannot use VLCs convert/save option as the result is awful. Using the default (avi) set by VLCs record button the files are huge (30 Gb for 25 minutes of footage) and are always broken (seeking). VLC plays them fine. However I try to convert them, they are always then messed up, in particular the audio. It's either out of synch or missing altogether. I have been unable to get any help from the VLC forum on (for example) getting VLC to split the footage into more manageable pieces (as smaller test recordings don't have this problem) so I assume it can't be done.

With Kdenlive the situation is rather more odd. Carefully ensuring the card's settings match those of the project, and substituting "/dev/video0" with "///dev/video0" (which is the VLC description of the card) I can "play" the streaming video in the clip monitor, However, hitting the record button either freezes the video or produces a black window with "invalid" going across it. Anything recorded contains sound but no video. 

My sons offer of his Windows 7 laptop with Sony Vegas on it to do my project is looking rather attractive right now, but before I give up on this entirely and reluctantly take him up on it, I would appreciate any ideas you may have.

---

### Post by SteveDee on 2011-12-21
> **ianmillington said:**
> Hi I have an Easycap DC+ (the one with the Empia 2861 chip)....

Take a look at this thread which is about the same device: [http://ubuntuforums.org/showthread.php?t=1642985&highlight=dc60](http://ubuntuforums.org/showthread.php?t=1642985&highlight=dc60)

I may be able to do some tests for you, but I'm not running the same OS.

---

### Post by ianmillington on 2011-12-21
Hi Steve 

Thanks for your reply. I did in fact read that thread (and this one)some time back and I attempted some of the things suggested a little while back to no effect. 

Assuming VLC for video capture, the solution to the video turned out to be very straightforward - tell the system whether the input is composite or s-video. If it's composite you could either evoke a one-line command 
"v4l2-ctl -d /dev/video0 -i 0"

 or more elegantly select video option 1 in the "open capture device" advanced settings. Recently I tried S-video and found that to be the default i.e no config required.

Audio - At the early stages I gave up on that as from the output generated from a command (which I'll post if you need) it was clear that the audio driver did not load (the error message "AC97 device not recognised"). Rather than faff about with it I simply bypassed the card and plugged a 3.5mm jack into the mic socket card and the audio worked perfectly.

So my question now is not about the hardware per se but rather the limitations of the applications available to me which are:

At this point I was going to go on a rant about 
VLCs huge files that break
Kdenlive's ability to view the footage but it cannot record it due, I suspect, to an issue with mlt
Guvcview crashing every time I hit the record button.

However, I have installed cheese and although I don't have a video source available it

a) doesn't crash when I hit record
b) saves the files as OGV which can be played in dragon player etc and imported to kdenlive 
c) The files seem to be a tiny fraction of those generated by VLC.

When I get home tonight I will know if I have found the answer - I hope so, and will post back.

Regards

ian

---

### Post by ianmillington on 2011-12-21
Success!

Here is what you do if you have this card.

Forget about audio via the card, it will not work properly, if at all. Establish a direct link between the source and your sound card - quality should be fine.

Video - this should be all you use the card for. It will be installed as soon as you plug it in. If you have a powerful computer and loads of hard drive space you can probably use VLC, If like me you are at the lower end of the scale, Cheese will do the job.

If you are planning to use RCB/Composite (i.e the yellow plug) for your video then you will need the system to accept it. If using cheese launch a terminal and issue the command referred to in my post above. If using VLC you need video mode 1 in the advanced settings of the open capture device section.

If you are using an S Video source, I can confirm that no config is required in either VLC or Cheese. It just works.

I think the biggest problem with VLC is that the default resolution appears to be 768x576 with uncompressed avi with no obvious way to change them. With Cheese you can in preferences, and it saves as an ogv file. As a result, the footage that was between 23 and 30Gb with VLC is 560mb with Cheese, It's probably lower quality but as the source was a VHS tape I wonder how important that is. A more powerful machine could work on a higher resolution I'm sure.

Hope this helps someone

---

### Post by lkraemer on 2012-01-04
rmt1947,
I purchases a Sabrent USB Video Capture Adapter from Newegg.  The Item Number is USB-AVCPT and "lsusb" shows the device as:
> 
Bus 002 Device 006: ID 05e1:0408 Syntek Semiconductor Co., Ltd STK1160 Video Capture Device


I have downloaded your easycap_dc60.tar.gz from my gmail account.

I've extracted the source and compiled the code without errors.
I have installed mplayer, and I want to use VLC when I am finished.
When I try the test scripts everything works now.
```

   ./testNTSC.sh 1         for NTSC and a "CVBS+S-VIDEO" EasyCAP

```
and
```

   ./vlcNTSC.sh            for NTSC and either EasyCAP (input 0 or 1)

```
as per the README file.  Also, the generated testeasycap1.log file
gives the user lots of good information........to apply to
mencoder & vlc.


I'm running Debian 6.0 "SQUEEZE" and my Sabrent Dongle is at:
> 
larry@debian:~/easycap/easycap_dc60.0.9$ ls -alt /dev/video*
crw-rw----+ 1 root video 81, 1 Jan  4 14:20 /dev/video1


The two links exist at:
> 
lrwxrwxrwx 1 root root 6 Jan  4 14:20 /dev/easycap1 -> video1
lrwxrwxrwx 1 root root 5 Jan  4 14:21 /proc/asound/EasyALSA1 -> card1


I would also like to use S-Video when I get the device working.
What input will I use for S-Video?  **input=5 = S-Video**

I have enclosed a Photo of the settings I used in VLC to get Video
and Audio.  Why don't I have a /dev/easy??? for sound?  How do I address
plughw:1,0 if I use mencoder from a Terminal?  **plughw.1,0**


THANKS for ALL your Driver work!

Larry

---

### Post by purdobol on 2012-04-02
Hello
I am using 05e1:0408 dc60 to play Gamecube games on my monitor ( broken tv ). 
Im using this command to play some US and Japan games (PAL gamecube)
```
mplayer tv:// -tv driver=v4l2:norm=PAL_60:width=720:height=576:outfmt=rgb24:device=/dev/video0:input=0:fps=30:buffersize=16
```
Everything is fine except weird black dots running diagonally across the screen. Anybody know what could cause that problem ?

Edit: It appears to be a mplayer bug. On VLC picture is normal and has better colors.
On the other hand VLC has 0.5 s lag...

---

### Post by ubf2012 on 2012-06-09
Hi, I am new here and i also have a major issue with my unit.
**lsusb** lists it as "05e1:0408 Syntek Semiconductor Co., Ltd STK1160 Video Capture Device". and it has 4 video inputs and 1 audio.
The video is decent but my main problem is that all four channels only show what is input into channel 1 ( input 1) and seem to ignore anything into inputs 2, 3 & 4.
I would like to use it with zoneminder.
Is there a fix for this?

Thanks .

---

### Post by SteveDee on 2012-06-09
> **ubf2012 said:**
> ...my main problem is that all four channels only show what is input into channel 1....

You haven't given us much information, but I should imagine that this device produces 4 video streams. So these may correspond to 4 devices like this:-
/dev/video0
/dev/video1
/dev/video2
/dev/video3
...does this help?

---

### Post by ubf2012 on 2012-06-09
Only  /dev/easycap0 & /dev/easyoss0

---

### Post by SteveDee on 2012-06-10
> **ubf2012 said:**
> Only  /dev/easycap0 & /dev/easyoss0

OK, so it looks like input selection should be via the "input" parameter (e.g. input=1, input=2 & so on) which seems to be backed up by comments here ([http://easycap.blogspot.co.uk/p/recording.html#mtvcgui](http://easycap.blogspot.co.uk/p/recording.html#mtvcgui)) but you indicate you have already tried this. So I don't have any more suggestions.

---

### Post by ubf2012 on 2012-06-10
Thank you for. I appreciate your attempt.

---

### Post by ubf2012 on 2012-06-13
Still I have not resolved this problem as yet.
Any new ideas or pointers?
Anybody????

---

### Post by evildeejay on 2013-01-03
Does anyone know how to use two easycap together?
When i plug the second one I successfully obtain /dev/video1 and /dev/video0 of the first one.
If I use one of them each time everything works perfectly, but when i plug the second one, the last one doesnt work.
Seems like a conflict of driver or something similar.
Can you help me?
Thanks,

Marco

---

### Post by evildeejay on 2013-01-03
I can add additional information.

When I have both two easycap plugged in, only the first that i plugged works.
BUT...
If i use "sudo rmmod easycap"
and the
"sudo modprobe easycap"
I can choose which easycap start and it works.
Of course when i try to launch the other one, it doesnt work.

Any ideas?

Marco

---

### Post by SteveDee on 2013-01-04
> **evildeejay said:**
> I can add additional information.

When I have both two easycap plugged in, only the first that i plugged works...

I think you will find that the first EasyCap will be allocated most of the USB controller bandwidth, so the second EasyCap won't run.

If your computer has more than one USB controller (I don't mean just more USB sockets connected to a single controller) they should work when correctly connected to separate controllers.

---

### Post by evildeejay on 2013-01-04
Thank yo very much.
I thought that the problem could be linked to the bandwith, so i tried to use two different controller:
1. first easycap was plugged on a PCI exp board   with four USB
2. second easycap was plugged in the motherboard USB.
So i'm not sure but i think they should be two different controller. Isn't it?

I think that the driver can support only one easycap.
So i'm trying to use two different driver for the two easycap.
The problem is that the two easycap have the same identifier so when i plug the second one the driver of the first one uses the device.
I should modify the driver in order to let it to use only one device (is it possible? I'm not so advanced on Unix)

Marco

---

### Post by SteveDee on 2013-01-05
> **evildeejay said:**
> ...I think that the driver can support only one easycap.
So i'm trying to use two different driver for the two easycap.
The problem is that the two easycap have the same identifier so when i plug the second one the driver of the first one uses the device....

With both of your EasyCap devices plugged in, they are being recognised and attached as /dev/video0 & /dev/video1. So there is not an identification problem.

There are many types of EasyCap (mine are called EzCap) and several different drivers, as you would have discovered from reading this thread.

I suggest you install qv4l2 (thats a lower case "L") and do some initial checks.

Also take a look here: [http://easycap.blogspot.co.uk/](http://easycap.blogspot.co.uk/)

---

### Post by thekgr on 2013-05-06
I was thinking of getting the 4 input version of this. I wanted to use it like a security DVR, and save all 4 inputs. Any idea what sort of frame rate, and at what resolution, I can save as. From the specs it says 30fps for NTSC (across all 4 channels), but with all the switching and syncing the video signal its unlikely I can get that. So was wondering what sort of frame rates people who have the 4 input version are getting.

---

### Post by rosswin on 2013-09-16
Hi,

I am having issues with installing the Somagic EasyCap device.
I have followed all the instructions here [https://code.google.com/p/easycap-somagic-linux/wiki/GettingStarted](https://code.google.com/p/easycap-somagic-linux/wiki/GettingStarted)

I have managed to extract the firmware. However when I run somagic-init I get the output: ```
Failed to open USB device: Permission denied


```.

When I run lsusb I get: ```
Bus 002 Device 005: ID 1c88:0007 Somagic, Inc. SMI Grabber (EasyCAP DC60+ clone) (no firmware) [SMI-2021CBE]


```.

I realise that I am having issues with the firmware on the device.

Is anyone able to advise me on how to fix thir.

Thanks,
Rosswin

---

### Post by rosswin on 2013-09-16
Sorry fixed it thought i was in root, but i wasn't.

---

