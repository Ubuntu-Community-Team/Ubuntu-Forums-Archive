---
title: "X on Feisty Fawn Live CD will not boot :("
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by Rovdjur on 2007-07-11
Well, I have Feisty Fawn 7.04 on CD, and it works great on my old Dell Laptop, however, on my Lenovo ThinkPad T60p, the X server fails to load.

I believe it is because of my video card. I have an ATI Mobility FireGL V5250. This card is not supported by ATI for even Windows, so I am not surprised that it is not supported by X.

Just wondering if anyone knows how to get this workstation graphic card working with the latest version of X.

Thanks!

P.S. - The previous versions of Ubuntu that I have do work and load just fine, it is only Feisty Fawn that I am having issues with.

---

### Post by EXCiD3 on 2007-07-12
It is probably that the default open-source ati driver does not support your video card. Use an alternate CD to install ubuntu, as it does not use xserver, once installed use the Envy script to install the ATI drivers for you card which can be found here: [http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html"). If all goes well you should be able to use the xserver. Unfortunately the ATI drivers are nowhere near as good as the Nvidia drivers...

---

### Post by qopit on 2007-07-12
I've got the same problem with an HP Compaq nw8240 laptop with an ATI MOBILITY FireGL V5000.

I just learned about the Envy script and am downloading the alternate cd to try that.  How do you go from the alternate X free install to a full blown ubuntu desktop?

I'm also interested to hear that only Feisty didn't work... maybe I'll try Edgy, too.

I was keen to try Beryl on my FireGL but have been pretty disappointed in getting nothing but blank screens.  My buddie's Dell D620 got running without a hitch.

I'll post to update on how it goes.

---

### Post by EXCiD3 on 2007-07-12
> **qopit said:**
> I just learned about the Envy script and am downloading the alternate cd to try that.  How do you go from the alternate X free install to a full blown ubuntu desktop?

I'm also interested to hear that only Feisty didn't work... maybe I'll try Edgy, too.

You see, the alternate CD will install it using a console like interface. It installs just like the live CD, except it has some extra options, such as rescueing a broken system. It will use the xserver just the same after you have completed installation. With the alternate cd you just cant try out ubuntu like you can with a live cd.

You will have to use ```
envy -t
``` to install the drivers, if i remember correctly, so that it runs in text based mode. 

And try Edgy is probably a worthless attempt as less hardware was compatible with it. Feisty is so much better than the previous releases as it added countless upgrades that help usability incredibly. I would recommend just using the Feisty alternate cd to install and then envy to get the driver running, next reboot should have the xserver correctly running. NOTE that you will have an error from the xserver the first time you boot and it will crash back to the console, install envy then, reboot and then, if all works our your way, you should be able to use the xserver just fine.

---

### Post by qopit on 2007-07-12
I've now got Feisty installed using the alternate CD and, as expected, X does not work at all.  I get a funky pixelated white screen that cycles through shades of white/grey in a psychedelic way.  Very neat.

Anyway... I've used recovery mode to get to the terminal and have managed to get the Envy deb, but can't install it for some reason.  There are a whole slew of dependencies missing:

build-essential
xserver-xorg-dev
module-assistant
dh-make
debhelper
dpatch
dpkg-dev
and maybe fakeroot

Any ideas why this would be the case?  Everything I've read indicated that Envy should have run easily...

---

### Post by qopit on 2007-07-13
Yahoo!  I now have an Ubuntu desktop.

I manually installed each one of those missing packages ("sudo aptitude install blahblah") and Envy then worked.

The bad news is that this is my trial load and I'll have to do it again after I partition it all properly.  And every time I want to play with distros... sigh.  Anyone know why I had to manually install all those packages?

fyi - The fglrx installation detected my card as an X700... I wonder if I'll be able to get my firegl card's opengl support to work...

---

### Post by bernt.ribbum on 2007-07-14
You've maybe read it, but I found easy instructions that worked pretty well for me here

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_Feisty_Fawn_on_a_ThinkPad_T60p](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_Feisty_Fawn_on_a_ThinkPad_T60p)

My problem is that the screen driver has only limited support for the hardware. No DRI.

[http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5250](http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5250)


- Bernt

---

### Post by qopit on 2007-07-14
Thanks... I had seen that first link (and several mroe like it) before.  Since my first successful Envy attempt I have successfully used the pre-packaged  xorg-driver-fglrx install to get Ubuntu working.  It looks like Envy goes direct to ATI and compiles, vs the pre-made package.  I can't tell how different the versions are with this.

My latest frustration is that I can't get Beryl to work.  I've tried many different ways from many different posts, but to no avail.  I can't even get XGL to give me a usable desktop.

This has been a succession of hour after frustrating hour... very annoying, since my buddy got his Dell working near instantaneously. :|  Dude, I should have bought one.

---

### Post by sparkingwire on 2007-08-19
qopit-I'm having the same thing happen where X fails when booting the live CD on my lenovo T60p with the ATI FireGL 5250. Just to be clear, all you did was to use the alt cd and then used envy to get things going?

Thanks!

---

