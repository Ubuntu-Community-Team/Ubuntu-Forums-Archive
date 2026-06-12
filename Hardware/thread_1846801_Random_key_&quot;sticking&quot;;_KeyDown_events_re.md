---
title: "Random key &quot;sticking&quot;; KeyDown events repeat forever"
date: 2011-09-19
forum: Hardware
---

### Post by park4122 on 2011-09-19
This may not be related to hardware specifically but it seems like a good place to start.

Please see my description of this keyboard issue here: [http://askubuntu.com/questions/60435/sticky-key-like-bug-keypress-release-events-repeat-indefinitely](http://askubuntu.com/questions/60435/sticky-key-like-bug-keypress-release-events-repeat-indefinitely)

Dell Latitude 6520 running 64 bit 10.10

---

### Post by An Sanct on 2011-09-19
Welcome to the forums!

I also use Maverick (10.10 64bit)

I have also experienced the same problem for a few months now. There seems to be no simple solution nor is it related to stuff like: uptime, memory usage, CPU usage, network usage, database usage...

It just appears and all you can do is use the mouse, save your work and restart the machine - if possible.

As far as I have traced this, it has something to do with PS2 keyboards, I have never seen it happen with an USB keyboard attached to my machine. A bug was filed ages ago (2+ years), but it went back and forth from assigned, critical, fixed, tamed, ... and all the other statuses (-would like to see the changelog on that -> "what _exactly_ in the source code was changed, what made it fixed???") - Its a kernel thing and altho it is flagged fixed, its still present.

Also it is not hardware related or physical, the key repeatedly "gets pressed", even if you physically unplug the keyboard (so its not because of keyboard stickiness or dust or something like that...)

PS. sometimes it is 'l', 'r', '3', 't', ... I've even seen it happen with Alt and other special keys...

some external links, you might want to check out ...
launchpad bug report [194214]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/194214"), [124406]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/124406"), [linux questions]("http://www.linuxquestions.org/questions/ubuntu-63/ctrl-button-stuck-in-ubuntu-673161/") and all the "duplicates"

[LIST]
[*]       [ Bug #149507]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/149507")
[*]       [ Bug #178817]("https://bugs.launchpad.net/bugs/178817")
[*]       [ Bug #187855]("https://bugs.launchpad.net/bugs/187855")
[*]       [ Bug #190615]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/190615")
[*]       [ Bug #192331]("https://bugs.launchpad.net/bugs/192331")
[*]       [ Bug #193545]("https://bugs.launchpad.net/bugs/193545")
[*]       [ Bug #194343]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/194343")
[*]       [ Bug #194637]("https://bugs.launchpad.net/bugs/194637")
[*]       [ Bug #201010]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/201010")
[*]       [ Bug #208518]("https://bugs.launchpad.net/bugs/208518")
[/LIST]
 It's quiet a huge list ... and I don't see it fixed ....[URL="https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/194214"]

[/URL]

---

### Post by park4122 on 2011-09-20
Thanks for the help, and the list of bugs.  I have actually seen most of those during my hopeless search for solutions.  That is unfortunate that it will likely not be addressed.

It doesnt happen only in 10.10 I see, and not all the time obviously or it would be a hotter issue.  Do you think I can just recompile the kernel or reinstall maverick altogether and maybe it will go away?

---

### Post by An Sanct on 2011-09-20
I'm sorry to say, that I think this will not solve the issue ... As said, I have seen this happen a lot, searched the web a lot and found a lot of posts on this forum about this issue ... even with 11.04 etc... so the kernel is not "misscompiled", It functions as it should (as designed ;)) recompiliing will not make the problem go away.

My solution was to get myself a USB keyboard ... PS2 is dieing out anyway, like COM and LPT ports... it has the advantage of being just small enough, not to be pesky for hardware designers :) ... the more expensive way is to buy a PS2-to-USB converter, if you like your keyboard so much, otherwise, buy a 5$ USB one, it will never fail you with this issue...

---

### Post by park4122 on 2011-09-20
Im so glad I need to buy a USB keyboard for my *laptop*. Maybe ill just go to 11.04 and hope that slew of productivity-impending bugs is less severe.

---

### Post by An Sanct on 2011-09-20
Well, the keyboard connection in a laptop was always a mystery to me :) apparently they still use PS2...

I'm sorry to hear you have such problems.

---

### Post by Galfonz on 2012-11-24
Allow me to add my own experience to the data stream. I have been running a Toshiba Portege laptop on 64-bit Ubuntu 12.04 for a few months now, and have just yesterday and today started seeing this happen to me, three times in two days. It has always been "3" repeating for me, and is accompanied by the Unity "imitate Apple" icons on the left getting numbers showing on top of them (which I don't know what that indicates; it doesn't happen when I actually hold down the 3 key), and apparently my LibreOffice Writer (3rd icon) gets launched and is where the 3's all show up, and it becomes impossible to type in other applications when it happens, although actually typing in LibreOffice Writer can interrupt the 3's and allow typing for a bit, but only in that window.

Restarting the computer seems to recover to a working state.

---

### Post by overdrank on 2012-11-24
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

