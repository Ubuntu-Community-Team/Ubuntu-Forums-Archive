---
title: "Dual Monitor Freeze Help"
date: 2010-02-07
forum: Hardware
---

### Post by ma5t3rw1tt on 2010-02-07
Hello everyone,
I really need some help here. I have a Dell Inspiron E1405 laptop and I am trying to get dual monitors to work.

I installed Ubuntu 9.10 on a 8GB flash drive. Well I am trying to setup dual monitors. Well when I boot into Ubuntu with the 2nd monitor plugged in which is an Acer monitor, it shows a mirror screen on my 2nd monitor when I boot in. When I finally get booted and try to disable the mirror and set things up the way they are suppose to be setup and I click "Apply" both screens goes black and freezes.

I don't know if this is cause I am booted from the flash drive cause I have this same problem when I have dual booted as well.

My graphics card is an Intel Integrated 945GM Express Chipset Graphics card. However my friends have the same or relative same computer has no problems what so ever.

Is there a manual way I can change this without maybe using the GUI or something, cause I wanna eventually use Ubuntu as my main OS one day and I figure now is a better time than any to fool around with all this. Please & thank you.

---

### Post by rogue_0111 on 2010-02-07
I use "lxrandr" for dual screens. Easy to set up and use.

To install:
apt-get install lxrandr

To use:
Open a terminal and type: lxrandr

A nice GUI pops up. Click the check box for the external screen and choose a resolution. Hit OK.

That easy. 
To end dual screen session, close the terminal.

---

### Post by ma5t3rw1tt on 2010-02-07
Whoa thank you. 
Actually after posting my problem, mysteriously the thing started working using the resolution thing. I will use what you suggested though if anything starting going funky again. Thank you so much :)

---

### Post by Yowzaboodle on 2010-03-10
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/419328?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/419328?comments=all)

---

