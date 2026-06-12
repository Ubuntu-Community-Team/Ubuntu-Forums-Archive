---
title: "Netbook remix on Sony W Netbook?"
date: 2009-12-09
forum: Hardware
---

### Post by Ion007 on 2009-12-09
Hi all,

I have recently bought a Sony Vaio Netbook VPCW12S1E, with Windows 7 Starter installed on it.
I would like to install Ubuntu's Netbook Remix on it. I have made the bootable usb stick, but the problem is I can't find how to enter it's bios to make the netbook startup from usb.
I've tried Delete while booting, but it doesn't work. I also get no screen that says 'push delete for setup' or something like that. Windows directly loads and that's all.

I would really like to install Ubuntu on my netbook and I was wondering if there are others encountering the same problem, or know a solution?

Thanks and have a nice day!
Wim.

---

### Post by m4tic on 2009-12-09
what happens when you press F10

---

### Post by Ion007 on 2009-12-09
> **m4tic said:**
> what happens when you press F10
Nothing...

Thanks, Wim.

---

### Post by Ion007 on 2009-12-09
Found it... F2 is the magic key.
Thanks! Wim.

---

### Post by marty pain on 2010-01-15
How did you get on with the install mate? I'm trying to choose between the HP mini 110 and the Sony Vaio.

Any problems after you installed it??

---

### Post by premsted69 on 2010-01-15
I've installed UNR on a Vaio. It worked a treat once I'd got in the BIOS but you have to enable the new first boot device. Than it ran like a charm. It has been trouble free overall but it doesn't reliably resume after it's been asleep and somnetimes, when the resume does work, the mouse pointer is frozen and I find it easiest to teke out the battery and start again. Hope this helps.
 
Andy

---

### Post by Ion007 on 2010-01-15
Hi!

Well honestly I still haven't installed Ubuntu on the Netbook...
I made the usb boot stick, but when I tried the boot manager gave me some option wich seemed to be 'looping'... could not advance any further than that.
I haven't really had the time to figure it out.

Cheers, Wim.

---

### Post by yaoooo on 2010-03-26
I just tried to install the latest beta version 10.4 on my vpcw221ax. everything works perfect except some small tweaking and you can find almost all the solutions online. I'd say it's 100% worth doing it because now I got a machine which loads non-windows systems. (I'm a mac guy and  I wish this small pc could have mac but now ubuntu seems good enough!)

---

### Post by archonix on 2010-06-13
Hello

I have installed UNR 10.4 on Sony Vaio VPCW12S1E.
The installation process is flawless, just take care to set big enough swap partition.

About the resume/hibernation issue.

@premsted69
> It has been trouble free overall but it doesn't reliably resume after  it's been
> asleep and sometimes, when the resume does work, the mouse  pointer is 
> frozen and I find it easiest to take out the battery and  start again.
I'm thinking that the swap partition size could have some impact on that, because the
RAM content should be stored somewhere in the process of the hibernation.
Vaio VPCW12S1E has 1GB RAM, I've made 2 560 000MB swap partition and for now
I don't have any troubles with hibernation.

---

