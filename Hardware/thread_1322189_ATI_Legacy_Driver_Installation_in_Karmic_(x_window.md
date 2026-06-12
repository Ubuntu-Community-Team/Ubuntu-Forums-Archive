---
title: "ATI Legacy Driver Installation in Karmic (x windows ? etc)"
date: 2009-11-10
forum: Hardware
---

### Post by spinsane on 2009-11-10
I just got into ubuntu (I prefer Xubuntu, but I can't get Thunar to read network shares, so I'm holding off on that) and I am loving it. As a total linux newbie, I've had some hiccups here and there, but nothing that I couldn't solve with some extensive reading. There is one not uncommon problem out there that I'm having some troubles resolving, despite reading quite a bit.


So, How can I install an ATI Legacy Driver (Catalyst 9.3 for Radeon Xpress 1100) on Karmic Koala?*

*firstly, I assume that I need to because the graphics quality is not very good. Vsync issues and a few hiccups for the extended desktop. Otherwise it doesn't look bad at all, the open-source drivers ARE good, but to watch HD videos from my dinky laptop I will need the original drivers. I definitely don't want to give up on Linux (I need the 64-bit support), but I don't have a reason to keep linux on if I can't get the video card working up to a spec that is at least competitive with the driver for XP.

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat92-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat92-inst.pdf)

Aftering following the instructions;

```
Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.31-14-generic; make sure that the version is being
correctly set by --iscurrentdistro
```

I decompressed the .run file and found the /default_policy.sh to see if I could rewrite the code and create a simple bypass (I don't mind breaking ubuntu, I just installed it!) or just read some of the files and understand what I needed to do. Alas, even for me, it's going a bit too far before asking for help.

[http://tan-com.com/posts/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/posts/technology/fix-ubuntu-904-ati-driver-issue)

Says it doesn't work for Karmic- but the process seemed interesting. Tricking aptitude into thinking you're on intrepid- which uses an older version of X that also supports the drivers necessary, and then holding upgrades on the files involved, then installing the .run (or, I guess you technically aptitude the 9.3).

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I've also read these, but I'm ... not feeling too confident at the moment. I don't really understand what the spiel is with the RadeonDriver, I believe it is the one I'm using now- but the performance isn't satisfactory. Are there any tricks to modifying this guy so that it actually works nicely?

My understanding is this-- X is a window managing system that is used as a base for many desktops. It inherently has a lot to do with graphics and hosting all your windows and plays a role in rendering whatever is in them (?); so it makes sense that X is the architecture that is using/providing any given graphics driver for X windows involving any graphical processes (so, everything that shows up on your screen, X paints with the drivers provided).

So- the most recent version of X, which Karmic uses, is one that does NOT provide support for the 9.3 catalyst driver that I need to use, AND Karmic CANNOT use the OLDER versions of X, unlike Jaunty. So there's a double cock-block going on here of Karmic not wanting old X and new X not working with old Video card. IS THIS CORRECT?

So, supposing that I actually wanted to use my video card, I could install Intrepid and it would work right away OR install Jaunty and then downgrade the X. In an ideal scenario, I could compile a custom version of X (it is open source) that might satisfy both Karmic and my Catalyst 9.3, but I certainly don't have the time for that.

If I tricked the catalyst driver to install anyways, it SHOULD break X and, by inheritance, Ubuntu. But I'm thinking there has got to be some simpler way to ghetto-rig this that may actually work-- right now I'm thinking that maybe I can mix an old version and new version of X (kind of cut and pasting relevant code) and then tricking catalyst into ignoring the version and installing anyways. With that, all conditions (aside from lame-version checking pitfalls that are probably EVERYWHERE) would, in my currently limited perspective, be cleared.

Now, I'm a COMPLETE Linux NOOB, so I'm not sure if i missed something or what, but I need help. I want to escape Microsoft RIGHT NOW, but with this video card chained to my leg I cannot! Help this penguin fly!

Thank you!

On a side note, are there any basic tutorials out there that deal with modding X files?

---

### Post by spinsane on 2009-11-12
I kinda doubt anybody can give me any insight, but in the case that somebody can... *Bump*

---

### Post by ssri on 2009-11-12
1)  The legacy driver Catalyst 9.3 only support kernels 2.6.28 and below.  There is a patch for bumping up kernel support up to 2.6.29.  So, if you want to use the legacy driver in karmic, you will have to downgrade the default kernel down, highly unrecommended.

2) Catalyst 9.3 only supports xserver 1.5.x.  Jaunty shipped with v1.6.0.  So, you will have to downgrade xserver down to 1.5.2, the one installed on intrepid.

It was not difficult to get the legacy drivers to work in Jaunty, but Karmic is another matter.

Here's the link to get it working in Jaunty.  Remember, if you screw up, you'll be greeted with a terminal-only login.

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

---

### Post by spinsane on 2009-11-14
Okay, that makes perfect sense. It'll just be a thousand times simpler to go with Jaunty then.

---

### Post by Melcar on 2009-11-14
I don't see why you would need it though.  The drivers _don't_ accelerate HD content, so even if the open source drivers are slower your CPU will still be doing most of the work.  The only reason right now to use the proprietary drivers for those old chips is to get proper OpenGL2.x acceleration (and with it better 3D performance).

---

### Post by ssri on 2009-11-14
> **Melcar said:**
> I don't see why you would need it though.  The drivers _don't_ accelerate HD content, so even if the open source drivers are slower your CPU will still be doing most of the work.  The only reason right now to use the proprietary drivers for those old chips is to get proper OpenGL2.x acceleration (and with it better 3D performance).

Exactly.  If one want to get the full capabilities of recent 3D games (OpenGL 2.x, GLSL), dynamic powerclocks, or easy VideoOut then use the proprietary drivers.  The opensource drivers are better in everyway outside those three things.

---

### Post by Melcar on 2009-11-14
Radeon has a few power management options you could load; check the radeon manual.  Radeon also has working TV-Out, although I will agree that it's a bit problematic on some devices.  It's a really crappy deal that they removed xorg.conf now though, since it was handy to easily configure options for your drivers; as is you have to generate on yourself (rather easy, but it would have been nice if they actually told us how to do it ahead of time).
Lastly, the particular device in the OP wouldn't even be able to properly use many of the advanced 3D features of OpenGL, so I don't see the point.  
The OP said he would be watching movies with it, and for that purpose radeon is actually better than the legacy fglrx; much better Xv acceleration and better image quality (not to mention better supported and less buggy).  Fglrx does not accelerate HD content either (neither does radeon however); there is a library being worked on that allows fglrx to properly accelerate HD content, but that will not be available for the legacy drivers.

---

### Post by ssri on 2009-11-14
> **Melcar said:**
> Radeon has a few power management options you could load; check the radeon manual.

However, afaik, changing different power usage/consumption is not dynamic, and has to be manually set in a static mode.  According to the ATI guys on phoronix, they will not start working on implementing something like dynamicclocks until the 3D work for all of the cards are finished.

As for VideoOut, notice that I said "easy", meaning point and click.  I know one could go into terminal and use xrandr to set the appropriate resolution and such, even though there are still some kinks with it.

[http://www.phoronix.com/forums/showpost.php?p=99532&postcount=2](http://www.phoronix.com/forums/showpost.php?p=99532&postcount=2)

[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)    (see powerplay)

---

### Post by Dinoyc on 2009-12-28
Hi All,

Even i am facing the same problem with my Acer 5100 series laptop where it has the below configuration

AMD turion 64 mobile technology
MK36 (2.0 Ghz,512k L2 cache)
15.4" widescreen WXGA wide Crystal brite TFT LCD
ATI Radeon Xpress 1100 Graphics Card
60GB PATA HDD
DVD-super Multi doule layer
(support DVD+R Doule Layer /DVD += RW)
512 MB RAM

I have installed Ubuntu 9.10 and i don't see any reason why we need to upgrade to 9.10 and degrade the kernel and XORG if that was the case then it would always be good to work on 8.10. I need to know if ubuntu is working with ATI to give us a legacy driver?
If yes then when is that day coming? is there a way we can mail the technical team of ubuntu to make them understand that issue?

Could someone suggest the best ATI graphics to upgrade to right now? which has a low budget and works in this configuration?

---

