---
title: "ATI Radeon graphics card works fine... except for 3d"
date: 2010-07-24
forum: Hardware
---

### Post by Oriana on 2010-07-24
Ubuntu 10.04, fresh install and update, also followed Comprehensive Media installation stuff from [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Graphics card is "ATI Technologies Inc RC410 [Radeon Xpress 200M]" which is, I believe, built into the motherboard of my Toshiba Satellite a135-s2276.

System>>Administration>>Hardware Drivers shows nothing. An empty box.

Blender works ...okay, although the menus are FREAKING SLOW and I have to move the panels to get them to update or display the color change window (luckily, scroll button on lasermouse does not dismiss the color picker window)

But the real issue is with SecondLife ...erm, cough, OSGrid, that really cool 3d virtual world game chat ...thing. I've tested the Hippo viewer, Imprudence viewer, and standard LL viewer, and the best I get is this: 

[URL="http://www.flickr.com/photos/windychrome/4822698744/"]
[IMG]http://farm5.static.flickr.com/4082/4822698744_2c335e852f_m.jpg[/IMG][/URL]

I see a bunch of solutions for Gutsy, but when I try them (adjusting the obvious names from gutsy to lucid) I keep getting "E: Couldn't find package "... whatever I'm trying to install. 

On this forum, [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1475045](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1475045) , response #5 says something about 3d, but I'm not sure it applies to me, especially since I am not having the exact same issue as the original speaker. In #17 RavanH says "Anyway, to those with scrambled graphics: have you tried with different shared video memory sizes? On my machine that problem seems to be limited to 32Mb shared memory." , but I don't really understand what they're talking about...

I guess what I need most at this point is more knowledge. For instance, the correct technical terms might be helpful - as descriptive as it is, "second life looks like broken glass" really doesn't get a lot of useful hits in google. Mostly poetry.

So, yeah, any kind of advice or knowledge would be much appreciated!

EDIT: something like this is what I'm supposed to be seeing in OSGrid:
[http://www.adamfrisby.com/blog/wp-content/uploads/osgrid_lbsa1-680x404.png](http://www.adamfrisby.com/blog/wp-content/uploads/osgrid_lbsa1-680x404.png)

EDIT X2: I'm kinda interested in learning more about the Radeon driver mentioned here: [http://ubuntuforums.org/showthread.php?t=1525254](http://ubuntuforums.org/showthread.php?t=1525254)

---

### Post by JHCKX on 2010-07-24
I've found that Ubuntu 10.04 had poorer video performance on my Packard Bell EasyNote MZ35 compared to Ubuntu 9.04. Installing the Xorg-edgers PPA solved this. That gives you the latest versions of video drivers but it does mean you're using beta software so there's some risk involved. But I'm having no problems.

See also [http://ubuntuforums.org/showthread.php?t=1526576](http://ubuntuforums.org/showthread.php?t=1526576)

and
 [https://bugs.launchpad.net/ubuntu/+s...ti/+bug/576125]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/576125")

Good luck,
John Hendrickx

---

### Post by Oriana on 2010-07-24
Thanks for the help, I'm definitely trying this out!

*crosses fingers*

---

### Post by Oriana on 2010-07-24
Okay, so that was an experiment in craptastic FAIL. It brought my computer from "be almost fully operational" to "throw error in prompt, don't let you read it, flash Barney-colored screen and go black. And then don't respond." 

However, thank you anyway.

Btw, you might mention to people to install ppa-purge first. Incredibly useful, that program is! I got it (after the fact) by starting root terminal from Recovery Mode, then:

```
# apt-get install ppa-purge
```

(I believe this will only work if you have xorg-edgers' ppa installed, btw, but I'm sure you already knew that) 
and then I removed the offending ppa by:

```
# ppa-purge xorg-edgers
```

Restarted, and yay! I can see Chrome again! :D

So, even though the idea presented didn't work, I got a side-benefit (and I don't think there's any cost)! Thanks!

---

### Post by JHCKX on 2010-07-26
Sorry to hear you had so much trouble. Strange, xorg-edgers works just fine on my machine. But if I recommend it to anyone else, I'll be sure to tell them about ppa-purge as well.

---

