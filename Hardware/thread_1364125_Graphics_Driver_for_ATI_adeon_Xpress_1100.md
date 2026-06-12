---
title: "Graphics Driver for ATI adeon Xpress 1100"
date: 2009-12-25
forum: Hardware
---

### Post by Snaer on 2009-12-25
Hi!
I installed ubuntu 9.10 yesterday and I've only used windows before.
I really really want to be able to use OpenGL 2.1 or later, but I can't find any drivers.
Right now I have the driver that was installed from the start and when I type glxinfo in the terminal it says: OpenGL version string: 1.5 Mesa 7.6 (and alot of other stuff).
Which I guess means I have version 1.5.

Someone in [this]("http://ubuntuforums.org/showthread.php?t=897003") thread seems to have the same card as me but can also use 2.1 (OpenGL version string: 2.1.7412 Release), so my card should support it. But what must I do?
When I go to system->administration->hardware drivers, no graphics drivers are listed.

I also tried to install the ati catalyst 9.3 driver but it gave me this output:
Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.31-16-generic; make sure that the version is being
correctly set by --iscurrentdistro

Any help would be greatly appreciated.

---

### Post by Snaer on 2009-12-26
Perhaps I should also tell you that I have a Acer Aspire 5101AWLMi if that matters.

---

### Post by Snaer on 2010-01-04
Do I just have to wait for 2.1 support in the open driver?
Is there anybody who knows about this problem?

---

### Post by night-wing on 2010-01-04
Hi there :)

I'm sorry to say, but ati has abandoned the x1100 / x1250 series from their support for drivers for linux. You have to use the open source driver from ubuntu and this is very slow... No way to play 3d games or anything like that. When you want to use your card with full 3d support, you only can install ubuntu 8.10 "intrepid ibex", which is the last one supporting this card with a proprietary hardware driver.

I have the same problem with my notebook...

Regards
Nightwing

---

### Post by alexfish on 2010-01-04
> **Snaer said:**
> Do I just have to wait for 2.1 support in the open driver?
Is there anybody who knows about this problem?

Hi

if your a novice Trying to compile a driver or forcing a driver from the backend

  could result in this see below  / result of a kernel patch that does not work

---

### Post by Snaer on 2010-01-13
Thanks for the replies!
I guess that's pretty bad news.
But will there be 2.1 support and perhaps more speed in the open driver soon?
It must be possible, right?
And, no I do unfortunately not know anything about driver development :(.

---

### Post by McCIUKEN on 2010-01-30
[http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html](http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html)

---

### Post by Yellow Pasque on 2010-01-31
> **McCIUKEN said:**
> [http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html](http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html)
Irrelevant link...

> But will there be 2.1 support and perhaps more speed in the open driver soon?

It's getting there...[http://www.phoronix.com/scan.php?page=news_item&px=NzY4Ng](http://www.phoronix.com/scan.php?page=news_item&px=NzY4Ng)

---

### Post by Dinmiller on 2010-01-31
I have the same laptop, with the same problem. So if I reinstall to ubuntu 8.10 "intrepid ibex" i will have support for the card video card? And also if linux drivers work the same as windows ati wise, the xpress 200m was the same . The drivers worked for either or, and I couldnt see an FPS diff with either. But anyways, yes will I be able to play 3d games on my laptop if i downgrade to 8.10? thank you

---

### Post by Snaer on 2010-02-01
Good to hear :)
Thanks!

---

### Post by harrylin on 2010-02-01
Do you people use the 64 bit or the 32 bit Ubuntu, and do you play games under Wine? 

I ask because I am trying the latest Mint (an Ubuntu derivative) Gnome X64 on my Acer Aspire 5051 with ATI Xpress 1100 and in Wine such things as 3DMark2000 give 1-2FPS 3D performance (didn't get the score because it crashed before the end). Thus I also thought of going back to a version that works with the ATI driver.

However, I also tested the 32 Mint version and o wonder, 3DMark2000 is rather smooth in 3D (around 20FPS) with a 3D score of almost 3000. :)
Probably the same will be true for Ubuntu (I didn't test it); there seems to be either a bug or a difference in development between the 32 bit and the 64 bit drivers for our card!

For me regressing to 32 bit Linux is clearly a more interesting alternative than regressing in Linux version. Apparently the only benefit of X64 for me (with 2Gb RAM)  is that some number crunching applications run faster; apart of that mostly the performance is about equal (and X64 swallows a few hundred Mb more memory too).

---

### Post by brooksby on 2010-10-06
Sorry to resurrect an old thread.
 
I was about to try and get World of Warcraft working on my Fujitsu Siemens laptop (AMD Turion X2, 2 GB RAM) running Ubuntu 10.04 (32 bit) and with an ATI Radeon Xpress 1100 graphics card.
 
I've now read that ATI no longer support the Radeon Xpress cards so I can't get a proprietary driver for the card to run under Ubuntu Lucid, otherwise, my box should be up to the job.
 
Has anyone got WoW running successfully using this graphics card and the open-source driver?
 
I have read the manual - :-) - but would very much appreciate someone confirming what I suspect, that the bottom line is that it would be a waste of time trying to get WoW working because the graphics card isn't up to the job?
 
Thanks for your attention,
 
B.

---

### Post by K3nnY89 on 2010-10-08
Hi i have problems with my ATI Xpress 1100 too

It seems that 3D acceleration is enabled but what about OpenGL? how do i find out taht it is enabled or not?

ig get the following outputs 
for glxinfo | grep vendor:
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: DRI R300 Project

for glxinfo | grep "direct rendering":
direct rendering: Yes

Does these mean that everything is enabled?

---

