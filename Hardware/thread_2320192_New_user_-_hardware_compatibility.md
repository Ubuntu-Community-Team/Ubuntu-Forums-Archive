---
title: "New user - hardware compatibility"
date: 2016-04-11
forum: Hardware
---

### Post by space3 on 2016-04-11
Hi, 

I am planning on building a new computer this summer. I cannot justify spending $100+ on windows, so I want to try Ubuntu. However, after doing some research I have found that Ubuntu does not support all hardware. My question is: will my hardware be supported by Ubuntu? Below is the list of parts that I plan on using. Oh, and I plan on installing version 14.04.4 or 16.04. Any help that you guys could give me would be greatly appreciated.

Part list-

[http://pcpartpicker.com/p/XHZ723](http://pcpartpicker.com/p/XHZ723)

Thanks in advance.

---

### Post by slickymaster on 2016-04-11
Have you already checked [http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/) and this long thread: [Laptop COMPATIBILITY List]("http://ubuntuforums.org/showthread.php?t=1543006")

---

### Post by QIII on 2016-04-11
By way of clarification: it is very seldom the case that Ubuntu doesn't support hardware.  It is actually that the hardware manufacturers don't support Linux with drivers.  

Windows does not support hardware, either.  Microsoft does not write drivers for third party hardware.  The manufacturers of the hardware do.  That just about everything works with Windows has nothing to do with microsoft and everything to do with the fact that OEMs know if hat if their hardware doesn't run on Windows, they will go out of business.

So...

Rather than looking for whether Ubuntu supports this or that, investigate whether the OEM provides support for Linux.

---

### Post by space3 on 2016-04-11
Thanks for the tip, I will do some looking.

---

### Post by jay_bowles2 on 2016-04-11
From my own experience with Linux and system building I would say that the best thing is not to buy into the latest tech without research. Having said that I haven't had any problems with any of the systems I have built. The two most important ones to verify are very new CPU's and video cards. Now I know your AMD Processor will work as I have used many from the same family. Your choice of AMD graphics card, I have no experience with; so that's definitely worth checking. Ubuntu provides proprietary driver installation which may provide better results.... of course that would then not be free and open source. Others will probably be better with answering this. The safer option in my opinion would be to try Nvidia cards (again not bleeding new) as the Nouveau driver (open source) works very well.

---

### Post by jay_bowles2 on 2016-04-11
Also I have just remembered that proprietary support for AMD graphics will be depricated with 16.04 

[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-16.04-Dropping-fglrx](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-16.04-Dropping-fglrx)

---

### Post by space3 on 2016-04-11
Thanks for the good info. So you think that the two most important parts to confirm compatibility with are the CPU and GPU?

---

### Post by jay_bowles2 on 2016-04-12
IMHO yes! The amd motherboards haven't really changed much in the last few years, nor the AMD processors to be honest. With the deprecation of AMD proprietary video support that will affect you only really if you intend to play 3D games.... This will be fixed in the future obviously but it depends what you intend to do with your new pc out of the box. Having said that you could use the 14.04.4 LTS version in the mean time as this still has a few years support left. I would personally go for an Nvidia device though.

---

### Post by ihatewindows522 on 2016-04-12
Personally if I were in your shoes, my only concern would be graphics and possibly networking, instead of processor. On Linux, you can't go wrong with either Intel integrated or nVIDIA. Actually, let me qualify that. There are some very gifted people out there I can think of that actually can mess it up. You're likely not one of them. ;) I can tell you from experience that AMD cards suck with Linux, and if you do get one you're a heck of a lot better off using the open source driver if you're cursed enough to end up with one. 
Networking can be a slight issue at times, but usually it's just a matter of finding a little package hidden in a little dark corner of the manufacturer's website. But you're likely going to be surprised at [what will work]("http://www.geek.com/microsoft/linux-users-rejoice-heres-ubuntu-on-the-surface-pro-3-1594864/").
Hope this helps.

---

### Post by pqwoerituytrueiwoq on 2016-04-12
You may have a hiccup with the onboard audio, see here:
[http://ubuntuforums.org/showthread.php?t=2234198](http://ubuntuforums.org/showthread.php?t=2234198)
I would expect the onboard LAN to work, but don't expect the WOL feature to work (it does not on the E2200)
I would suggest using a Nvidia GPU over a AMD one for linux, the price/performance ratios are not the same as with windows as they use different drivers

If you do get that ram be aware it will prevent a lot or large after-market CPU coolers from fitting

---

### Post by space3 on 2016-04-12
Thanks for all the help you guys. I am definitely going to go for a nVidia GPU after hearing your thoughts on the subject. I appreciate all of your feedback as it has made the choosing process a lot easier.

Thanks again.

---

