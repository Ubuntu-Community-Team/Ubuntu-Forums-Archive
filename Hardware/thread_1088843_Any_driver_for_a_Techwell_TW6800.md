---
title: "Any driver for a Techwell TW6800?"
date: 2009-03-06
forum: Hardware
---

### Post by Paul82 on 2009-03-06
Hello,
Anyone know if there are any drivers in the world of Linux for a surveillance video card: QSPDVR04.
The chip is Techwell TW6800. 
Hopefully there is a driver out there for this.
Thank you in advance,
Paul

---

### Post by configt on 2009-06-11
I have been in search of the elusive tw6800 linux driver also.

The closest I've come to finding one so far was here:

[http://gitorious.org/tw68](http://gitorious.org/tw68)

The driver is currently for tw6801/6802/6805, and I have not been able to get it working for tw6800.  The author is unable to spend any time on it until later and of course makes no guarantees.

If no driver for the tw6800 pops up within a month or so, I will be forced to give in and buy a bluecherry card.

[http://store.bluecherry.net/category_s/63.htm](http://store.bluecherry.net/category_s/63.htm)

---

### Post by moorsey on 2009-10-19
Hey guys, I'm in the same boat, eventually came upon that driver, but cannot get it to make, tons of errors, no clue why!

Is that Bluecherry site the best place to get guaranteed supported Linux CCTV capture cards?  Price looks similar for this dodgey Chinese Techwell one and that's delivered to the UK!!!

I didn't find the ZM support hardware very helpful in the run up to buying hardware

---

### Post by hackeron on 2009-11-10
Also not able to compile thw TW6800 driver:

Version v4l gives:

```

# make
make -C /lib/modules/2.6.31-14-generic/build M=/root/module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /root/module/tw68-video.o
/root/module/tw68-video.c: In function ‘video_open’:
/root/module/tw68-video.c:929: error: implicit declaration of function ‘lock_kernel’
/root/module/tw68-video.c:937: error: implicit declaration of function ‘unlock_kernel’
/root/module/tw68-video.c: At top level:
/root/module/tw68-video.c:1695: warning: initialization from incompatible pointer type
/root/module/tw68-video.c:1696: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/root/module/tw68-video.c:1734: warning: initialization from incompatible pointer type
make[2]: *** [/root/module/tw68-video.o] Error 1
make[1]: *** [_module_/root/module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2

```

And version v4l2 gives:

```

# make
make -C /lib/modules/2.6.31-14-generic/build M=/root/tw68-v2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /root/tw68-v2/tw68-core.o
  CC [M]  /root/tw68-v2/tw68-cards.o
  CC [M]  /root/tw68-v2/tw68-i2c.o
/root/tw68-v2/tw68-i2c.c:145: error: unknown field ‘client_register’ specified in initializer
/root/tw68-v2/tw68-i2c.c:145: warning: missing braces around initializer
/root/tw68-v2/tw68-i2c.c:145: warning: (near initialization for ‘tw68_adap_sw_template.dev_released’)
/root/tw68-v2/tw68-i2c.c:145: warning: initialization makes integer from pointer without a cast
/root/tw68-v2/tw68-i2c.c:145: error: initializer element is not computable at load time
/root/tw68-v2/tw68-i2c.c:145: error: (near initialization for ‘tw68_adap_sw_template.dev_released.done’)
make[2]: *** [/root/tw68-v2/tw68-i2c.o] Error 1
make[1]: *** [_module_/root/tw68-v2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2

```

Was anyone able to compile this?

---

### Post by moorsey on 2009-11-10
looks similar to the errors I got.  Will be returning my card (not fit for purpose with Windows software) and getting one from the US Bluecherry site, unless anyone has a UK alternative?  Hopefully ZM will prove more functional than the Windows software I have been trying to get working!

---

### Post by hackeron on 2009-11-10
> **moorsey said:**
> looks similar to the errors I got.  Will be returning my card (not fit for purpose with Windows software) and getting one from the US Bluecherry site, unless anyone has a UK alternative?  Hopefully ZM will prove more functional than the Windows software I have been trying to get working!

Got it to work with some help from the mailing list - very helpful guys!

Simply remove tw68-i2c.c from the Makefile and then it compiles - then modprobe bttv before you insmod tw68.ko and presto, it works!

No audio though :(

EDIT: Also, if you use a PCI-E version, you may need to try putting it in another slot. I had to swap the techwell and graphics card places or my system would lock up.

---

### Post by moorsey on 2009-11-12
ahh, superb, I will take a look at this as soon as, cheers!

---

### Post by moorsey on 2009-12-06
me again, I really ain't getting anywhere with this.  Just had chance to give the new suggestion ago, but looks like the above fix of removing tw68-i2c.c has been updated into the Gitorious project.

So, just testing this from a live CD, it still errors out, similar to before.  Are there any packages I should be installing before trying to "make" this?

If someone could point me in the right direction please.

Cheers

---

### Post by acho on 2009-12-06
You can try share the problem to your vendor....

Usually they will give u some solving problem for ubuntu driver....

Go to this link [http://www.techwellinc.com/support/contact.html]("http://www.techwellinc.com/support/contact.html")

Have a nice day.... :popcorn:

---

### Post by hackeron on 2009-12-06
> **moorsey said:**
> me again, I really ain't getting anywhere with this.  Just had chance to give the new suggestion ago, but looks like the above fix of removing tw68-i2c.c has been updated into the Gitorious project.

So, just testing this from a live CD, it still errors out, similar to before.  Are there any packages I should be installing before trying to "make" this?

If someone could point me in the right direction please.

Cheers

How do you expect to be helped if you're not telling us exactly what you're doing and what errors you are seeing?

---

### Post by moorsey on 2009-12-29
oky, quite right, not much info in last post.  I have had some time to play with this over Xmas.

Driver has had some more updates and now compiles fine, but when trying xawtv to see if I get any output, "no video grabber device available"

Maybe I am missing a step in the driver install?

1. cd into the extracted driver directory

2. sudo make

3. modprobe bttv

4. insmod tw68.ko

I have no idea about 3 and 4, just lifted from hackeron's post!

I tried running "make install" but get:

"make: *** No rule to make target `install'.  Stop."

Cheers

---

