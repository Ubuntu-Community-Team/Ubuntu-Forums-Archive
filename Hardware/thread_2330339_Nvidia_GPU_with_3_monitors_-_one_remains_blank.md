---
title: "Nvidia GPU with 3 monitors - one remains blank"
date: 2016-07-10
forum: Hardware
---

### Post by doug-ravennasprings on 2016-07-10
I've been having this problem for ages and with the new Ubuntu 16.04 LTS the problem remains.
With 16.04 the Nouveau driver at long last supports 3 monitors using the default installation configuration, that's a big advancement that brings Ubuntu up to something that looks like Windows 98 monitor support levels.
However, this configuration is not using the Nvidia drivers thus isn't using much of the capabilities of my expensive video card. (So it's not even Win98 level of support)

I've read and followed numerous "solutions" on the interwebs which generally entail variations of "apt-get remove --purge..." then reinstalling.
This leaves me with at most two functional monitors and a blank one.
Some instructions leave me with only one functional monitor.

My question is simple:

Does anyone have installation instructions that support the Nvidia drivers with three active monitors on Ubuntu 16.04?

Thanks!

Note: if you have not installed 3 monitors on 16.04 using an Nvidia GPU, please don't respond, no matter how helpful you feel you are.
Thanks.

---

### Post by nitblast on 2016-07-17
My nvidia gpus wont output to more than 2 monitors concurrently.  My solution was 2 gpus, a second x screen, and xinerama. I use cheap old gpus which I  have on a shelf. Now I output to a projector and two monitors. It isnt ideal but it works.

---

### Post by doug-ravennasprings on 2016-07-20
Thanks for the response.
I have the GeForce 690 which is 2 680's on a single card effectively SLI preconfigured so it comes with 4 video outputs.
This shouldn't be rocket science but no one seems to know how to configure it.
If I return to the defailt Nouveau driver, all three monitors work fine... it's annoying.

---

### Post by redking3 on 2016-07-21
I have gtx 960 with 1x 3440x1440 and 2x 1920x1080 monitors on Ubuntu, only thing I can think of that I have done in regards to the gpu is just installing the proprietary driver ubuntu recommends, But tbh I think it worked fine with all 3 monitors with the Nouveau driver without having to do anything aswell. I can also confirm that 3 monitors work fine with "ASUS Radeon R7 240 2GB DDR3" in Ubuntu. 

Will test the Nouveau also driver and come back to you a bit later.

---

### Post by Mads_Unneberg on 2016-07-24
I also have three monitors but in my case two are blank and one is working.
And I am also running a Nvidia (gtx960). I bought the Nvidia just before I upgraded to 15.04 and every thing was fine until I started to use 16.04.
The hole time I`w been using the Nouveau driver and it was all perfect until I installed "Handbreak" a transcoder for DVDs through Ubuntu Software.
This install made the monitors go completely wild. I am not that good in terminal work so i triad to fix it all through the graphics by changing the drivers. It actually got better but that was just for 20 - 30 min. I went through all the defaults and I even went back and forth a couple of times because I couldn&#8217;t find any posts ore threads about this issue any were. I probably over did it because now there is an electricity sound going from left to right in my speakers and I am left with one monitor.... 

Now "Error- Messages" has started to pop up.
- Could not switch the monitor configuration. - Could not set the configuration for CRTC 65. I have had the no. 61, 41 and the last one was 444.
And then a long one - Kernel command line : Boot_Image = /vmlinuz-4.4.0-21-generic root = /dev/mapper/ubuntu--vg-root ro recovery numodeset.
Build Date: 07 April 2016  09:18:50 AM    Xorg-Server 2:1.18.3-1 ubuntu2 (For Technical Support please see [http://www.ubuntu.com](http://www.ubuntu.com)). 
- Witch I have done but it and I haven&#8217;t come to a thing... I am totally numb about this  :confused: and I have no idea how to solve it.

So in completely desperation I formatted my hhd and are now running "Ubuntu MATE 16.04". Her I have at lest done the PPA for Nvidia and have  now tried out 4 other drivers given by them. Nothing has worked and this distro doesn&#8217;t even recognise my monitors witch Ubuntu 16.04 did to the point.
- So please could any one help me with this ???
Regards
Mads Unneberg

---

