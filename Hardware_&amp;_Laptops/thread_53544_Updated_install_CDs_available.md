---
title: "Updated install CDs available?"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by weimer on 2005-08-01
Hi,

is there a updated version of the 5.04 install cd available? My system (Dell Precision 380) is only supported by very recent linux kernels. And the one on the install cd is to old and hangs on boot. If there is no newer install cd, what else can I do to install ubuntu?

Thanks in advance,

Markus

---

### Post by adwait on 2005-08-01
I guess you could try the Breezy CD, although it is rather unsafe, since it is in the development stage at the moment.

---

### Post by weimer on 2005-08-03
So there is nothing like the updated install CDs available in the debian world? I guess than I'l wait till the next release of ubuntu and see whether this one works.

Thanks anyway!

Markus

---

### Post by heimo on 2005-08-03
Maybe there is a workaround for your problem? If you could post details (maybe on a new thread to get more viewers), maybe someone will come up with boot parameters, BIOS settings or other solution. You may have already tried it, and yes, it's perfectly possible that you need latest kernel to install "out-of-the-box", but if you really *want* Ubuntu installed, there's probably some way. I'm not going to promise anything ;) Just if you want to share your experience / details.

Thanks!

---

### Post by weimer on 2005-08-04
Hi,

OK, I'l explain my problem in more detail:

My System is a Dell Precision 380, which does activate USB 2 at the BIOS level. The same is true for the Dell Precision 370. As I read on the net (can't remember the URL ATM   :-? ), the USB driver in the linux kernel up to some version assumes that the USB controller is in USB 1 mode and activates USB 2 on its own. This fails on my system and I get the error message: 

Host Controller Process Error

in many copies on the screen ;-)

The obvious solution:
[list=1]
[*]Deactivate USB
[*]Install Ubuntu
[*]Update Kernel
[*]Reactivate USB
[/list] 

does not work because the only mouse and keyboard I have are USB devices.

So my second idea was to fetch some minimal install cd with a current kernel which downloads the packages from the net or another CD. I have a debian background (some years ago), and there these install cds where quite common.

I have ubuntu installed in a vmware. Maybe I can use this to install Ubuntu on the 'real' second harddrive?

Thanks in advance for any pointer.

Markus

---

### Post by heimo on 2005-08-04
:-\ :-/ I'm sure you've already gone through lots of options and all the BIOS settings. I'll give my thoughts anyway. Is there PS/2-"emulation" for USB keyboard/mouse in BIOS? Any effect? Could this be combined with *nousb* kernel boot parameter to avoid hangup? 

Is there PS/2 port? Why not borrow / buy one keyboard for this. I don't like solving problems this way, but sometimes it's just easier than ](*,)

Hopefully you can get this solved.

---

