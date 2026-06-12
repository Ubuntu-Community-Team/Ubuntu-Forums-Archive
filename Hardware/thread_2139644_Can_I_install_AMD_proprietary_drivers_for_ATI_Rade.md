---
title: "Can I install AMD proprietary drivers for ATI Radeon HD 3200 in Ubuntu 13.04"
date: 2013-04-27
forum: Hardware
---

### Post by hil4vitkutin on 2013-04-27
Well, the question comes out in the title pretty clear... On the AMD driver website it reads the following:

"Automated installer and Display Drivers for Xorg 6.9 to Xserver 1.12 and Kernel version up to 3.4"

I guess raring ringtail has later versions, but I wonder is there a way to install these drivers anyway...

---

### Post by Mark Phelps on 2013-04-27
Basically -- NO.  AMD dropped restricted Linux driver support for the HD 2x/3x/4x series last summer -- and now, their drivers will not work with 12.10 or 13.04 because the newer Ubuntu versions uses a new X-server version which is not compatible with the older drivers.

---

### Post by hil4vitkutin on 2013-04-28
Okay thanks for the reply, fortunately the open-source drivers work well, gaming performance is only a bit low.

---

### Post by nachwaal3ab on 2013-04-28
[COLOR=#000000]Okay thanks for the reply, fortunately the open-source drivers work well, gaming performance is only a bit low.[/COLOR]

---

### Post by jefersoncatarina on 2013-05-17
Goog morning.. 

Sorry of my english. I am brazilian. 

In my laptop the driver of ATI Radeon HD3200 work fine in the legacy driver. 

How to:

Add repository:
# add-apt-repository ppa:makson96/fglrx


Install driver:
# apt-get install fglrx-legacy


Make the conf file with command:
# aticonfig --initial


Configure your adapter in utilite AMD:
# amdcccle

Thanks

---

### Post by QIII on 2013-05-17
STOP before doing the process suggested above.  I am becoming increasingly disturbed by the fact that such methods are carelessly tossed out as "solutions" when they are actually hacks that could cause a lot of trouble down the road.

It is one of many automated methods for downgrading X Server, changing the kernel and installing the legacy driver.  In effect, it breaks your Ubuntu install in ways you may not understand.  Nobody knows *for sure *what difficulties may arise in the future when you update your system.  You may run into dependency issues.  You may not be able to make critical security updates to your kernel.

If the open source driver suits your needs, just use it.

If not, you would be much better off going back to 12.04 or 12.04.1, which will work with the proprietary driver in the repo.  It is supported for 4 more years and you will not risk breakage.

Be advised that 12.04.2 will not work this way since it uses a different kernel and X Server from 12.04 and 12.04.1, just as 12.10 does.  So, if you want to use 12.04 with those cards, do not use 12.04.2.

---

### Post by Tjkhan on 2013-05-17
i have ati 7770. but i m unable to install .run file. plz help with code. thank u

---

### Post by QIII on 2013-05-17
Hi, Tjkhan!

It would be best for you to start a new thread rather than hijacking this one.

Yours is a different problem and your question will probably not get the attention you want here.

Thanks and best wishes.

---

### Post by hil4vitkutin on 2013-05-18
Hello,

I'm familiar with that downgrading process... It doesn't sound very good to downgrade just parts of the system.

And yes, the performance I get with the open source drivers suit well my needs. Simple games run well with them :)

I'll rather use the latest Ubuntu than use older version just to get better performance with my video card &#8211; cool features just keep coming ;)

---

