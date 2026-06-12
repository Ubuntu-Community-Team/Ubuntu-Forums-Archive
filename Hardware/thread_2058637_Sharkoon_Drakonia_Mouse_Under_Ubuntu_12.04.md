---
title: "Sharkoon Drakonia Mouse Under Ubuntu 12.04"
date: 2012-09-16
forum: Hardware
---

### Post by Toyface on 2012-09-16
Hi, 

First post here so firstly, if this is in the wrong section - I apologise. 

Secondly, if this is has been settled already then I again apologise however I've searched high and low to no avail.

I've recently bought a new PC and have enough HDD space to run Windows as well so I can play games again. I've bought a new mouse, the Sharkonia Drakonia laser mouse and I love it. However, it doesn't seem to want to work in Ubuntu.

Like an idiot, I decided to not check beforehand - having used Linux since I was 14 - 21 now - I've found everything I buy to pretty much just work. This doesn't and whilst I know my way round the terminal and knowledge of linux itself - I've never gone anywhere near xinput or anything like it before.

Any logs asked for will be provided and I thank anyone or everyone in advance - I don't want to stay in Windows much longer ha ha!!

Tom

---

### Post by Urumiko on 2012-10-11
I have the same issue on Lubuntu/Ubuntu.

I think I found a solution here all be it on SUSE but it's beyond my ability to follow.

[http://forums.opensuse.org/english/get-technical-help-here/hardware/473200-usb-gaming-mouse-04d9-a078-not-working-linux-plus-workaround.html](http://forums.opensuse.org/english/get-technical-help-here/hardware/473200-usb-gaming-mouse-04d9-a078-not-working-linux-plus-workaround.html)

If anyone could offer a solution (ideally one which doesn't involve re-compiling the kernel i'd appreciate it :P

---

### Post by Toyface on 2012-10-11
There's no way at all to get it running without recompiling the kernel however, I stuck at it at got it working after a decent nights sleep and some good coffee.

This guide will tell you how to compile the kernel - it's really not that difficult just follow instructions v carefully.

[http://mitchtech.net/compile-linux-kernel-ubuntu-12-04-lts/](http://mitchtech.net/compile-linux-kernel-ubuntu-12-04-lts/)

Of course, you'll want to change the kernel name to the latest. 

All you have to do is change the file in the OpenSUSE solution, then follow the rest of the guide. 

Depending on what hardware you have running, ie Nvidia or AMD graphics, you'll ned to reinstall drivers.

---

