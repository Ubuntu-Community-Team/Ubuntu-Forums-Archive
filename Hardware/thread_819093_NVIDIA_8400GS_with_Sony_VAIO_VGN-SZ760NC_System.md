---
title: "NVIDIA 8400GS with Sony VAIO VGN-SZ760N/C System"
date: 2008-06-05
forum: Hardware
---

### Post by w1nD on 2008-06-05
Hey everyone,

First of all, I would like to say that this forum has been very helpful in the past and still very helpful, even today.

I have already researched my problem for quite a while. But I haven't found a solution to it. There were many similar cases, but they all didn't work.

Right now, I'm using Ubuntu 8.04 with my Sony VAIO VGN-SZ760N/C. It has a NVIDIA 8400GS video card, which works fine, but does not work with Compiz! Every time I try and select the "Extra" visual effects from Appearance tell> Visual Settings , the system tells me I need to enable a restricted driver (compatible with 8400GS). I used EnvyNG to install the driver, but after restarting the computer, my screen becomes messed up, and says "low resolution" after. I had to go to Recovery Mode and fix Xserver before I restarted my computer again, returning back to normal with normal resolution, but without the "Extra" visual effects.

This probably means the driver does not work well with my 8400GS. Is there any way to fix this problem?

Thanks!

---

### Post by ideaton on 2008-08-29
I have a very similar problem. 

I'm running Hardy with my Vaio VGN-S580, with a Nvidia geforce 6200/6400 graphics card.  The nv driver that installed with Hardy works just fine, but, as soon as I try to enable any desktop effects, my system becomes unstable.  I've run Envy a few different times, installing various Nvidia drivers and rolling them back when they fail.  The drivers *can* be enabled, but Compiz cannot in any case enable desktop effects.  

Does anyone have any experience with this problem?  Any solutions?

---

### Post by nicedude on 2008-08-29
Yes this is a simple to fix problem, just install envyng which is a software to download a better Nvidia or ATI driver for your system and will make "extra" desktop effects be available.


To install it use this command in a terminal ( To open a terminal go to Applications -> Accessories -> Terminal )

sudo apt-get install envyng-gtk

Once installed look in Applications -> System Tools -> EnvyNG and start it up.

Now just click Nvidia and install and let it do its thing for you :-) When it asks if you want it to configure your xorg.conf file for you say yes as well.

Once that is all done you may have to press Ctrl+Alt+Backspace to restart the desktop and then try enabling the "extra" setting and it should work fine :-)

Hope that helps you 2 get your compiz fusion going it works for my 8400M Nvidia chipset just fine.

Goodluck

---

