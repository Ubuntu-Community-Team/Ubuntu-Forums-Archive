---
title: "Can't install X-Fi drivers in 9.10"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by mab1376 on 2009-10-29
```
make -C /lib/modules/2.6.31-14-generic-pae/build M=/home/mark/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic-pae'
  CC [M]  /home/mark/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/mark/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/mark/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c: In function &#8216;ct_card_probe&#8217;:
/home/mark/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function &#8216;snd_card_new&#8217;
/home/mark/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/mark/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/mark/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic-pae'
make: *** [all] Error 2

```

build-essential is installed as well as kernel headers for:

```
linux-headers-2.6.31-14-generic-pae is already the newest version.
```

Any ideas?

-------------Edit------------------

It actually is already installed, I just needed to un-mute it because the ATI HDMI driver took precedence.

---

### Post by NoAngel777 on 2009-10-31
I have the same problem. No sound :(

---

### Post by seanj on 2009-10-31
I have sound for some reason, but line-in doesn't work. Glad everyone else is having fun with their new OS while we sit here struggling to get our sound working.

---

### Post by mab1376 on 2009-10-31
Yeah mine is working fine, it was just muted by default because i have 2 audio devices, I un-muted it and it works fine, didn't test line in yet.

---

### Post by Webe12 on 2009-11-12
My solution may not work for all. But I ended up giving up on my X-Fi working under any version of Linux. I'm multi booted. I installed my old Sound Blaster Live. Now I have two sounds cards running on my system. The Linux uses the SB Live, while Vista runs the X-Fi. Works perfectly because Vista doesn't see the SB Live and Linux doesn't see the X-Fi. Also, I run 64 bit versions of both.

---

### Post by kostkon on 2009-11-12
Your X-Fi should/may work on 9.10 after installing the
```
linux-backports-modules-alsa-karmic-generic
```
and rebooting.

---

### Post by agilman on 2010-01-31
I installed oss drivers (oopensound.com), then had to delete /dev/mixer and /dev/dsp and make new links to point to the right devices.
Now I have some sound, for example I have sound when I use firefox, but not in applications that use gstreamer (everything else).

---

### Post by agilman on 2010-02-01
OK, nevermind the OSS, I got it working with alsa.
Remove the OSS and follow these steps:
[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

---

### Post by rosseto on 2010-02-16
I know that it's not the best solution.. but after a bunch of tries it worked for me =)
I simply removed the include directives of sound/driver.h present in xfi.c and ctac.h
After I comment the following statement in xfi.h
//card = snd_card_new(index[dev], id[dev], THIS_MODULE, 0);
(the  function snd_card_new probably is called from sound/driver.h)
After that I successfully compiled and installed and after a reboot the sound was working fine good.

---

