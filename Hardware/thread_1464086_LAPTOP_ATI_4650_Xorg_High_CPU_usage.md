---
title: "LAPTOP ATI 4650 Xorg High CPU usage"
date: 2010-04-27
forum: Hardware
---

### Post by Troca on 2010-04-27
HI i am very new to ubuntu Experienced windows user but like i said extremely new to ubuntu. I tried to get in to ubuntu 2 years ago but had so much problems with my wifi card and memory card reader on my laptop that i gave up. 

Now i have a new laptop and want to get back in to the game. I think mt ATI card is whats causing my Xorg Cpu usage to go from 20-50% when scrolling in firefox and moving windows about. If i drag a windows left to right fast i can get 80% cpu usage out of xorg.

I have googled for a week now tried different things unofficial drivers with no compiz effects and offical drivers with and without compiz all the same result. I was using 9.10 version of ubuntu but im now on the 10.04 beta verson due to i thought that might have been fixed i am going back to 9.10 tomorrow and im using 64bit version but have also tried 32bit makes no differens.

I have found that i can edit Xorg.conf in X11 folder i have tried some different options none have helped so far.

So if anyone can help me i would be very greatefull atm i am getting kinda putt off by ubuntu and linux due to all these hard to find out problems. 

PS Remeber i am extremely new to linux so dont use expert explanations due to i would prob not know what you are talking about.


I have an ATI 4650 mobile radeon card in a VGN-FW51ZF Sony Vaio Laptop 

specs here if that helps you 

[http://www.sony.co.uk/product/vn-fw-series/vgn-fw51zf-h](http://www.sony.co.uk/product/vn-fw-series/vgn-fw51zf-h)

---

### Post by Troca on 2010-04-28
bump

---

### Post by khelben1979 on 2010-04-28
Have you tried with [ATi drivers]("http://support.amd.com/us/gpudownload/Pages/index.aspx") directly from the ATi homepage?

I would not recommend it though if you don't carefully follow all their installation instructions. As a newbie you definitely want working graphics, so proceed with caution if you do.

---

### Post by Troca on 2010-04-28
Thanks for the reply and yes i have tried their drivers and they dont work ether or well they work but i still have very high cpu usage on Xorg

---

### Post by Troca on 2010-04-30
seriously no expert that can help ?

---

### Post by Troca on 2010-05-01
oh well i gues i give up and goback to windows i have reinstalled ubuntu about 10 times now tryed every information i can find on google notthing works i give up

---

### Post by mountainstumble on 2010-05-02
Also running a Sony Vaoi VGN-FW5 with ATi 4650. Just upgraded to 10.04 and have noticed that Xorg now seems to be consuming more CPU than it used to under 9.10.

If I have no apps running then it drops down and sits quietly but as soon as you start using anything (eg, firefox, chrome or thunderbird),  Xorg sits between 30 and 40% (which then kicks the fan in). This system used to run very quietly under 9.10 (especially when just browsing the web).

Can anyone make any suggestions as to how I start debugging this and find out whats causing the problem? 

Also.. can anyone tell me what a good level of cpu usage is for Xorg to consume when using apps such as firefox, etc?

Thanks in advance!

---

### Post by thankyousam on 2010-05-02
I'm having similar problems with my Radeon 4870 (not to hijack this thread). I've tried a few things with no luck. :confused:

---

### Post by mountainstumble on 2010-05-02
Hijack away.. If it helps troubleshoot this, its worth it!

Quick question.. do you have Compiz installed? I have and stopped the process and I noticed that xorg dropped down to about 20% but it didn't completely quieten down so I don't think its the main problem!

Is anyone else seeing this or got any recomendations on how to address or attack the issue?

Cheers in advance!

---

### Post by bonzer on 2010-05-03
I've got the same problem of Xorg suddenly having high CPU utilisation following an upgrade to 10.04 from 9.10. Didn't have the problem under 9.10.

I think I notice the problem the most when scrolling Firefox (3.6.3) or moving the window. Sometimes the mouse pointer becomes jumpy and it interrupts my mp3 player that I'm using at the same time.

I've got an ATI Radeon 9550 based card. I'm using the open source radeon driver (xserver-xorg-video-radeon 1:6.13.0-1ubuntu5). I do have compiz installed. I'm using a custom xorg.conf that I found I needed to get 3D working and get the right res on my monitor under 9.10.

---

### Post by mountainstumble on 2010-05-03
Bonzer, Have you tried using the proprietary ATI drivers instead of the open source ones? Not sure if it will help or not but most things I have read regarding these type of issues suggest trying them!

---

### Post by bonzer on 2010-05-03
> **mountainstumble said:**
> Bonzer, Have you tried using the proprietary ATI drivers instead of the open source ones? Not sure if it will help or not but most things I have read regarding these type of issues suggest trying them!

Thanks. I did but I never got it to install on 9.10 properly. The legacy version of the ATI driver for my card ([9.3 for Radeon 9550]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.25&lang=English")) doesn't specify Ubuntu 9.10 as a supported option in the installer (and definitely not 10.04). I tried to install it with options for Ubuntu 9.04 but it didn't work and I just got various dependency problems.

To be honest I find video drivers on Ubuntu a bit of a black art. Once I got it to work reasonably well with the open source driver, didn't dare touch it again! :D

---

### Post by KvS2 on 2010-05-04
I thought I'd mention here I have the same problem. Not with an ATI card but with an integrated Intel graphics chipset on an Acer laptop. Things were fine in 9.10, but since the upgrade Xorg is using 30-40% of the CPU. :(.

---

### Post by metallus on 2010-05-07
1: Backup your /etc/X11/xorg.conf (run in terminal: sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak)
2: Run in a terminal: sudo aticonfig --initial
3: Reboot.
Problem solved for me after upgrade to lucid from karmic.
Also I noticed the problem after I enabled Direct2DAccel (with the command: aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE ). Might be related...
Good luck!   ):P

---

### Post by Robert Ayrapetyan on 2010-10-12
Thanks, **metallus**.
However, 1,2,3 had no effect (CPU usage raised to 100% again after some browsing in chrome and scrolling in Nautilus).
But Direct2DAccel change did the trick. Exactly:

1. sudo aticonfig --set-pcs-str=DDX,Direct2DAccel,FALSE
2. reboot

moved all slowness caused by Xorg on ATI cards away.
My OS ver: Ubuntu Lucid x32, video: ATI Radeon HD4850.

UPD: no success :( xorg again eats up all cpu, scrolling in chrome is almost impossible

---

### Post by hazica on 2011-02-26
Same issue here. Actually I'm using the same hardware as the original poster, a VGN-FW51ZF Vaio, and I'm seeing Xorg idle at between 3-5%, when I move the mouse it shoots up to 30-35%. Using Kubuntu 10.10 with Kwin compositing enabled and with the proprietary ATI driver.

The compositing is not the issue though, since i get the same CPU-usage pattern without compositing. I tried disabling the 2d acceleration, as suggested above and my first - subjective - impression was positive but, looking at the numbers, I realised nothing had actually changed.

Any other ideas?

Thanks.

---

### Post by hazica on 2011-03-23
Ok, I am definitely hijacking this thread. 

Is nobody aware of a cure for the ailment that has befallen the unfortunate owners of ATI's Radeon 4650 when used in conjunction with the closed source, proprietary driver provided by the aforementioned manufacturer?

Because this **** is getting on my nerves. Compositing on or off, X keeps hugging the CPU like I would a bottle of Single Malt.

There has to be some way of at least trying to debug this.

Muchas gracias.

---

### Post by jdsmofo on 2011-03-26
I am having the same problems with a Dell XPS m1330, which uses an nvidia graphics card.  It's slower than my Commodore 64.  I posted detailed information on the Kubuntu forum, but have gotten no help there:
 
[http://kubuntuforums.net/forums/index.php?topic=3116110.0](http://kubuntuforums.net/forums/index.php?topic=3116110.0)

---

