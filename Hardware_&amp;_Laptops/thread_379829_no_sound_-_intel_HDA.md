---
title: "no sound - intel HDA"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by buildblue on 2007-03-08
hi, 

I dont really play games so i decided to give ubuntu a go (again). I had it insalled shortly on another pc a while ago and it worked well for me out of the box. I have since ugraded my laptop and i cant seem to get the audio to work with the latest version of ubuntu. 

I have followed the guide in these forums but it seems my problem lies deeper. I am starting to get pretty frustrated...

I have a toshiba satelite p100.
According to:
 [http://gentoo-wiki.com/HARDWARE_Toshiba_Satellite_P100#Series_Specs](http://gentoo-wiki.com/HARDWARE_Toshiba_Satellite_P100#Series_Specs)
my soundcard is supported under linux however i have no idea about how to implement the changes needed to get the sound working. It seems i need to use a patch on ALSA to get it to work. I tried to follow the pretty vague guide but i still have no sound. Not only that but gcc would not compile at first so i spent a bit of time figuring out why that was... that seems to be working fine now.

Are my linux days numbered? I need my music. 

Thanks in advance.

---

### Post by cspiroff on 2007-03-08
If someone answers this please include me.  I have installed Ubuntu on my Gateway m520 laptop with an Intel 82801DB-ICH4 card.  Everything works great except no sound.  Please help because I would really like to stick around with this great group and not have to go out and get Red Hat or something like that,  And BTW, I am a total Linux Newbie, so please use simple terms.

Thanks

---

### Post by SendDerek on 2007-06-13
I just finished setting this exact laptop up for a friend.  In fact, I'm using it to type right now.

Everything is working in fiesty except for the wireless.

To enable the sound, you need to goto the terminal and type "alsamixer" and MUTE the External Amplifier all the way to the right side of the screen by hitting "M" when "External Amplifier" is highlighted.  That should take care of it!

---

### Post by DagMan on 2007-06-13
[http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)
worked for me with a toshiba a100
I still had problems with flash audio crashing firefox and have tried something differnat but haven't tested it yet.
If this doesn't work for toshiba sound, search the entire forum, from the front page, for toshiba sound and toshiba sound fix and there are lots of threads because lots of people are having troubles.

---

