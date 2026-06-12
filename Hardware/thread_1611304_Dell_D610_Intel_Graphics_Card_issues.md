---
title: "Dell D610 Intel Graphics Card issues"
date: 2010-11-01
forum: Hardware
---

### Post by The_Accursed_One on 2010-11-01
Okay, so I just finished a bit of searching on Google and it seems like the only way to change my graphics card RAM is to go into BIOS or use the Intel GMA tool. Well, here's the problem.

When I go into BIOS I look at my Graphics Card options and I look at the RAM and it will not let me change the allocated memory for it at all. I've done a bit of this research before and I was under t he impression you could use some system RAM as graphics RAM. Which brings me to the Intel GMA.

I just got done thoroughly looking through Google trying to figure out what Intel GMA I need, what graphics card I have, ect. to no avail. 

I need some kind of answers. I want to play all of these intense FPS games that require like 128Mb of  Graphics memory and it seems like my computer is giving me a measly sum of about 8Mb. I need to know what I can do to increase my graphics memory.

---

### Post by ianmillington on 2010-11-02
I suspect you may have the intel 915 Graphics card, with which I am also cursed. If so, you probably already have 256 Mb allocated to it by xorg.

Open a terminal and type 

sudo lspci -vv (I think theres a space between the 2 IIRC)

That will give a very verbose listing of the hardware, including your graphics. You need to do it as sudo otherwise the memory allocation display will be prohibited to you.

If you do have this card, I think your problem is rather more fundamental. The performance of this card (which itself was the cause of the "vista capable" scandal) is pretty dreadful, and with Linux generally is worse. Consider desktop effects to be getting towards the peak of its capability. In kubuntu 10.10 I have to switch off the KDE capability check to even have those.

Sorry that I can't really find anything good to say about this card, or the Linux drivers currently available for it. If you have a different card (which will be revealed by lspci) let us know please.

Sorry about the rant btw

---

### Post by The_Accursed_One on 2010-11-02
Yeah, this is the card that I have. I spent like 6 hours yesterday trying to find something to improve my situation. I guess what you're trying to say is that my graphics card is pretty much a lost cause? And if so, is there any graphics cards that are available that are better than this one and are available for my computer? Anyway, thanks for the help and hopefully I will find a solution to this without buying ungodly expensive chipsets :P

---

### Post by PRC09 on 2010-11-02
I have a couple of the D610 and the graphics cards are not replaceable.The ram allocation for the video is fixed at 8MB so it just doesnt have the horsepower to run any intensive games.They do however run just fine for Office tasks or surfing the net.....

---

### Post by ianmillington on 2010-11-02
If you are trying to make it do intensive stuff, then it probably is going to be problematic getting a lot out of it, under any OS.

Having said that, like PRC09 says, it should work okay for most other things. My main point is that under any OS, it's near the bottom of the table. If I find anything that improves it, I'll post back.

---

### Post by The_Accursed_One on 2010-11-03
Okay, thanks.

What I'd like to know also is if the D610 will support a graphics card that I buy from a store or something like that? Or is the built-in one the only one available for this computer?

---

### Post by ianmillington on 2010-11-03
Everything I read about this machine tells me it's a laptop - if that's the case then so far as graphics are concerned you are stuck with them I think. Only if it were a desktop would you readily be able to change the graphics card.

Did you run the lspci command I mentioned above, and did it show 256mb?

---

### Post by The_Accursed_One on 2010-11-03
Damn. Well, that sucks. And I have not tried the code you gave me because I forgot all about this post last night as I was doing college research but I will give you feedback on it as soon as i get to my home computer. Thanks for the help. My BIOS says that there is a dock for a graphics card? This is why I asked if there is a graphics card that is available for my computer. I'll look on my own here soon but I just wanted to ask for public knowledge. :P

---

### Post by The_Accursed_One on 2010-11-04
This is what I got:

[IMG]http://i1192.photobucket.com/albums/aa322/The_Accursed_One/graphicscard.png[/IMG]

---

### Post by wbrb on 2011-01-26
First, I'm currently running Xubuntu lucid on a D610 with the infamous:
> Mobile 915GM/GMS/910GML Express Graphics Controller

Second, I'm contributing this because I've spent hours/days trying to get the graphics working on my numerous dell D610's (corporate standard) in various flavours of Ubuntu

While you *are* stuck with what you're given but with enough tweaking you can make a D610 bearable for flash and OpenGL. Being a n00b myself I finally pieced together that a bunch of the Intel gfx chipsets have been rolled together into the xserver-xorg-video-intel package which can be installed with the standard:

```
sudo apt-get install xserver-xorg-video-intel
```

[https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel](https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel) for more info.

I'm not sure if that helped or not but after that one gentleman on a forum (sorry i rebooted and lost the link) recommended:
```
dpkg-reconfigure xserver-xorg-video-intel
```

Which seemed to increase performance quite a bit - it took GLMatrix which i was using to test from about 8fps@80% load to about 10fps@40% load. 

Not quite satisfied I dug up pretty much the best solution I've found at:

[http://www.insidesocal.com/click/2010/02/intel-82830-cgc-830m-graphics.html](http://www.insidesocal.com/click/2010/02/intel-82830-cgc-830m-graphics.html)

It's worth a read if you have time.

The key part of it for me was:

>  
To access that Boot Options line, just hit one of your arrow keys, and your cursor should appear. At the end of the Boot Options line &#8212; after quiet splash &#8212; enter the following:

i915.modeset=0


I booted ubuntu 10.04 live from my USB key and booted with the i915.modeset=0 switch and it ran GLMatrix like butter so this is relevant.

I looked up how to make it permanent and apparently in lucid one basically:
```
sudo nano /etc/default/grub
```
and insert the switch per:
[https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29](https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29)
then issue the command:
```
sudo update-grub
```

After this GLMatrix was running at 12fps@10% load. I can now watch youtube as it streams in 720p full-screen in chromium-browser without chop. That's as good as my XP boot and that's pretty much the most I'd expect from this old thing. On the other hand I'm amazed at how many D610's are still alive and kicking. If anybody more knowledgeable about what goes on behind the scenes with this wants to chime in I'd love to know more about who/what/where/when/why this works.

I hope this saves somebody some time. :)

---

