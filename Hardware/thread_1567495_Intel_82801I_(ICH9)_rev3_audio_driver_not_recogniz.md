---
title: "Intel 82801I (ICH9) rev3 audio driver not recognizing all ports"
date: 2010-09-03
forum: Hardware
---

### Post by jjinthebay on 2010-09-03
First off I want to say a big thanks to all the hard workers that have made Ubuntu!!!!  I was a die hard Mac user and due to the economy unable to pay the extra $1000 for a laptop, luckily this brought me to Ubuntu.  It meets my needs for style and is "mostly" intuitive.  Runs fast too!

OK to the point.  Everything is working pretty sweet but the process of fixing things on here is driving me crazy.  I am not a coder, I'm a point and shoot kinda guy.

I have an Intel HDA Audio card with 4 ports.  1-line in 1-speaker 1-internal mic 1-line out

Sound Preferences says I only have 1 in and 1 out.  Speakers work.  Usb web cam/mic combo work fine.

I have tried so many configurations but cannot get the internal mic to work.

I found a newer asla driver but have not the skill to compile it myself and Synaptic Package Manager does not show this update and force is greyed out.  maybe that would not even solve my problem... 

alsa utils does show 4 ports but Sound Preferences does not.  All volumes are put at Max.  This has to be a common piece of hardware what is wrong here???

---

### Post by jjinthebay on 2010-12-21
solved by upgrading to ubuntu 10.10.  make sure your options are set correctly under sound preferences.

---

