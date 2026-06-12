---
title: "need help upgrading graphics drivers"
date: 2010-04-24
forum: Hardware
---

### Post by gregnorc on 2010-04-24
So I have a [Thinkpad X201]("http://www.thinkwiki.org/wiki/Category:X201"), which has been freezing up randomly when using Ubuntu 9.10.

According to [Thinkwiki]("http://www.thinkwiki.org/wiki/Intel_HD_Graphics") the integrated graphics on the i5 require a very recent Linux distribution with kernel 2.6.33 and Intel Xorg driver 2.10 or newer.

So I got the kernel upgraded, and now just need to upgrade the intel xorg driver. I got the source and am trying to compile it, but keep getting errors when I run sudo make I get this error (sorry if there's some typos, I'm only able to run from the command line right now, so I am copying this text by hand from the laptop next to me to post the error):

```

make[3]: Entering directory '/usr/src/xf86-video-intel-2.11.0/src'
 CC     i810_accel.lo
In file from i810.h:60,
     from i810_accel.c:41:
/usr/include/GL/glxint.h:36:19: error: GL/gl.h: No such file or directory 
In file included from i810.h:60
     from i810_accel.c:41
/usr/include/GL/glxint.h:103: error: expected specifier-qualifier-list before GLboolean
make[3]: ***[i810_accel.lo] Error 1
make[3]: leaving directory '/usr/src/xf86-video-intel-2.11.0/src' 
make[2]: *** [all recursive] Error 1
make[2]: leaving directory '/usr/src/xf86-video-intel-2.11.0/src'
make[1]: ***[all-recursive] Error 1
make[1]: leaving directory '/usr/src/xf86-video-intel-2.11.0/src'
make: *** [all] Error 2

```

If anyone has any suggestions as to how I can eliminate this error and compile this driver, it'd be much appreciated.

---

### Post by wojox on 2010-04-24
Try adding the xorg-edgers [Part D (Bleeding-Edge)]("http://ubuntuforums.org/showthread.php?t=1130582")

---

### Post by shaka_zulu on 2010-04-24
What integrated graphic card you have?

---

### Post by gregnorc on 2010-04-25
> **wojox said:**
> Try adding the xorg-edgers [Part D (Bleeding-Edge)]("http://ubuntuforums.org/showthread.php?t=1130582")

Thanks, one question: It seems if I follow that, it'll put Kernel 2.6.30 on my machine? I need to keep 2.6.33... or will going up to the point where it has me doing apt-get dist-upgrade I can instead just install the newer drivers?

> **shaka_zulu said:**
> What integrated graphic card you have?

Intel HD graphics, it's the integrated graphics card on an i5
[http://www.thinkwiki.org/wiki/Intel_HD_Graphics](http://www.thinkwiki.org/wiki/Intel_HD_Graphics)

---

### Post by wojox on 2010-04-26
It says on the ppa wiki

[== New in Karmic ==]("https://launchpad.net/~xorg-edgers/+archive/ppa/+index?start=75&batch=75") 

Install a 2.6.32 kernel or newer from the Mainline Kernel PPA or from lucid.

Which you already have.

---

### Post by Yellow Pasque on 2010-04-26
xorg-edgers is the easiest way, but for future reference, you need the appropriate -dev packages to build stuff from source.
```
sudo apt-get build-dep xserver-xorg-video-intel
```

---

### Post by gregnorc on 2010-04-26
Ok so I followed the steps I found online, and supposedly installed 2.6.33, now when I boot I get a black screen (whereas before I had gotten an actual GUI - it just froze up randomly)

That config came from 9.04 via the alternate install CD. I am still very confused as to what to do... I understand I need to install these video drivers and 2.6.33 or better kernel, but actually doing that is really escaping me. If someone could clarify, I'd appreciate it. 

So I should install xorg-edgers? What about the kernel, how should I handle that?

To recap: To be able to ID what was going wrong, I installed the 2.6.33 kernel, using these instructions:
[http://www.unixmen.com/linux-tutorials/780-upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint](http://www.unixmen.com/linux-tutorials/780-upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint)

Alternatively, I might try installing 10.04, but everywhere I've read people are having the same issues...

---

