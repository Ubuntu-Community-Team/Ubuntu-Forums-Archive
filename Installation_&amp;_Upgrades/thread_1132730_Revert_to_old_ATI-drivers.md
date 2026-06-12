---
title: "Revert to old ATI-drivers?"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by malloq on 2009-04-22
Hi

I've upgraded to the Ubuntu 9.04 RC a couple of days ago, and I'm tormented by a terribly slow graphics experience. In 8.10, most thing were quite smooth (although it isn't a state-of-the-art computer I'm using), but with the new ATI-drivers shipped with 9.04 it takes more than a second to open the Applications menu. It also takes quite some time to go between tabs i Firefox.

So I was wondering, is there some way to use the old drivers? They seemed more efficient for my hardware.

I have also tried to follow this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide) in order to use ATI restricted drivers. But when running "sudo aticonfig --initial -f" (near the end of the guide), it reports that I don't have a supported device.

---

### Post by FaizanKazi on 2009-04-22
hmmm... I waited a while before replying to this thread, didnt want to give you my third rate opinion but seeing as no one has answered yet, maybe this will help you out.

anyways, 9.04 has issues with proprietary ati drivers. I havent tried the RC myself but the Beta seemed to be working quite all right on my Ati Radeon Mobility x1400. I must've been getting about 300 to 600 fps with "glxgears" using the regular ubuntu-provided open source drivers.

I also heard that proprietary ati drivers are not working well in 9.04 with serious compatibility problems because ati hasnt officially released any 9.04 compatible drivers and therefore 9.04 will ship with "beta"-ish (restricted?) drivers because they will be based on an upcoming release and are not the final product.

now, im not exactly quoting this, i read an article or two in a hurry and its all i seem to remember. bottom line is, stick with the open source drivers until ati makes its first official release for 9.04 (and those might still be buggy). they really are quite horrible when it comes to linux drivers. maybe we can all bombard their servers with requests till they breakdown and give in to our demands ;)

---

### Post by markbuntu on 2009-04-22
The driver from ati, 9.4, does not support the RV200-RV500 series cards and future drivers will not either. ATI has dropped everything before RV600 from their drivers for linux and windows starting with 9.4.
 
Previous ati drivers will not work with the Jaunty xserver. 
Anyway the 9.4 driver seems to be very broken in general with no big desktop and crappy performance compared to previous drivers.

Do not install/use this driver if you have RV200-500 or dual monitors.

---

### Post by FaizanKazi on 2009-04-22
OUCH! that seriously sucks.
next time i buy a graphics card im buying nvidia. im a huge fan of ati and amd, but i think amd is the only one worth bothering with. i wish their takeover of ati was having a greater effect, but it seems they got too much catching up to do in terms of software support.

---

### Post by malloq on 2009-04-23
Ok, thanks for the replies. The computer I have tested on have an RV250, so I guess Ubuntu 9.04 isn't the right choice for this computer.

---

### Post by FaizanKazi on 2009-04-23
hold on, dont give up hope yet. the official release of ubuntu might contain some decent open source drivers.

> **malloq said:**
> Ok, thanks for the replies. The computer I have tested on have an RV250, so I guess Ubuntu 9.04 isn't the right choice for this computer.

---

### Post by vivedekananda on 2009-04-23
malloq, I suggest you try the open source drivers xorg-driver-ati this should work quite well with your hardware;
I also happen have one of those older ati cards that aren't supported by the never fglrx drivers anymore. I would like to know how well the open source driver works for the cards before I upgrade (although I expect the open sorce drivers to get better in the near months).
Btw, I had great experience with nvidia on linux 2 years ago, but found some articles on the web, that the recent nvidia drivers got worse. I am a real fan of ati since they seem to support the open source dirver efforts, but it seems to take soo long;)

---

### Post by FaizanKazi on 2009-04-23
so the new release is out officially!! get a torrent for it from 

[http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)

and install it and once its running, run glxgears in the terminal and let me know how it goes. like i said... i get around 660 fps with the open source (default) drivers, and 900 with the ati drivers, funny thing is the ati drivers dont seem smoother... it works in bursts. ill get a whole bunch of frames and then it'll stick... sticks so i can just about see it pausing (just a little bit). which really is bad considering im not running a high end game!!

my download should be done in an hour but im going to sleep and im gonna get up WAY early and install a whole bunch of crap :)

---

### Post by markbuntu on 2009-04-23
glxgears is pretty useless as a test for gpu speed.

---

### Post by FaizanKazi on 2009-04-24
its the only readily available test that i know of :( (as in... everyone has it on their system)
what would you recommend??
I like the compiz benchmark overlay that can be enabled from "ccsm"

> **markbuntu said:**
> glxgears is pretty useless as a test for gpu speed.

---

