---
title: "Why oh Why does Xorg hate my browsers so?"
date: 2008-07-10
forum: General Help
---

### Post by unc0nn3ct3d on 2008-07-10
I have searched high and lo, and although have encountered a ton of threads and reports indicating that this problem is widespread I have yet to find a solution or work around.

I'm on 8.04 and whenever firefox is loading a page, using a lot of java or especially scrolling down a page heavy in content and/or java xorg freaks out and jumps up to 80-90% until the scrolling or loading is finished where it then sits idling at around 15% or so.  

Turning on or off Compiz does nothing to solve this.

I'm running an AMD Athlon 3200+
2 GB DDR ram
and a Geforce 8800 GT w/512 GDDR3

Anyone at all found a solution for this as it makes browsing such a trial in ubuntu

---

### Post by apswartz on 2008-07-10
I am using Kubuntu and Firefox2 w/o problems. What exactly are you using (including extensions)?

---

### Post by kerry_s on 2008-07-10
that sounds normal to me, more content will use more processing, flash sites will use constant cpu, i recommend flashblock & adblock+ to cut out some of the crap and save cpu. it should drop down to 0%, but if your using font smoothing, it will never get that low.

how do you expect it to work?

---

### Post by unc0nn3ct3d on 2008-07-11
> **kerry_s said:**
> that sounds normal to me, more content will use more processing, flash sites will use constant cpu, i recommend flashblock & adblock+ to cut out some of the crap and save cpu. it should drop down to 0%, but if your using font smoothing, it will never get that low.

how do you expect it to work?


Well I would expect it to work as well as it was on my windows box before switching away from that OS.

I mean I was just writing a facebook email, and xorg just stayed at 90% the entire time.. You can't honestly tell me that there is something about the email screen on facebook that is worthy of 90% of my CPU.  Scrolling slowed to a crawl.

I will install adblock right now, thanks for that tip.

Ok, well Adblock is definitely a good thing, I can see my web experiencing being a lot better with it.. however sitting on my profile page for facebook, not doing a thing, the browser window isn't in focus and Xorg sits at 70%.  There is no flash, nothing going on or being loaded just sitting idle.

---

### Post by kerry_s on 2008-07-11
my guess would be some kind of background scripting is happening. you could try the noscript plugin and see if it's doing anything strange.

[https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

have you tried disabling all extensions to rule them out?

i know a little late, here i am having you add things and now i'm asking if you tried with out. :lolflag: just a thought.

---

### Post by PadreSol on 2008-07-12
There's definitely something wrong.  I can't figure it out.  It might be ff3 issues.  I suspect Xorg.  But I can't find even how to increase log verbosity level.  Does anyone know where you add command line options for Xorg?  I've grep'd the hell out of /etc/ .  I tried xserverc, no luck.

Seems like an old Xorg we're using.

 Xorg -version

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)

---

### Post by PadreSol on 2008-07-12
Sounds similar, I don't get a "soft" lockup. Mine has to be rebooted.

[https://bugs.freedesktop.org/show_bug.cgi?id=16260](https://bugs.freedesktop.org/show_bug.cgi?id=16260)

---

### Post by kerry_s on 2008-07-12
i don't think it's xorg, if it was xorg then when you look at top, you would see xorg using the cpu instead of firefox.

how are you checking cpu use?

---

### Post by prolapse on 2008-07-12
I am having the exact same thing happen with firefox 3. When I go to facebook my cpu usage goes way up, when I look at top i see that xorg is using up anywhere between 70% and 90%. When I navigate away from facebook the cpu usage goes back to normal.

I just noticed this today. Its strange :/

---

### Post by unc0nn3ct3d on 2008-07-13
> **kerry_s said:**
> i don't think it's xorg, if it was xorg then when you look at top, you would see xorg using the cpu instead of firefox.

how are you checking cpu use?

Oh it's definitely Xorg that is using the CPU.  

> 
6068 root      20   0  555m 134m  15m R 76.8  6.7 204:55.09 Xorg     



NoScript Definitely shows that it is some background JS's that cause this huge spike.. with Noscript installed my CPU usage has dropped down between 8% and 25%.  Now this is all good and great, but why is it that these JS's are causing this, especially why in Ubuntu and not Windows.

It would also be interesting to know if other distro's suffer this same fate.  I think I've read that Debian does but not sure about the rest

---

### Post by tjabri on 2008-07-13
I have the same issue, and it's only on Facebook. It's really weird, but everything slows to a crawl and it's rather annoying. Still googling to see if I can find a solution, but so far, nada.

---

### Post by apswartz on 2008-07-13
> **unc0nn3ct3d said:**
> It would also be interesting to know if other distro's suffer this same fate.  I think I've read that Debian does but not sure about the rest

Well, I don't think it is fair to even say that Ubuntu is suffering from this fate since most of us don't have the problem. :-) I use Facebook every day w/o noticing any slowdown in my system.

That's not to say that your problem isn't very real. Is it possible it is connected to an extension or combination of extensions you are using in Firefox?

---

### Post by johnnybravo666 on 2008-07-13
Try disabling all your firefox extensions and/or using a different browser and see if you still get problems.

---

### Post by Steve Fisher on 2008-07-13
Definatly seeing this too. Facebook cause Xorg to consume all available cpu cycles. Switching to another tab (ubuntuforums for eg) returns Xorg to a reasonable rate again. Tried disabling all my extensions, but no change.

Just love to know why Xorg would have anything to do with what page I'm looking at in Firefox? I'm using gnome with no desktop effects enabled.

---

### Post by altonbr on 2008-07-13
No, this is a driver/Xorg problem. I've noticed the same thing with my GeForce 6800 on Ubuntu vs. Windows using free and non-free drivers for Ubuntu.

GMail seems choppy in Ubuntu, but not in Windows, especially while scrolling, it's really sad. This will also happen when you have a cheap, integrated GPU, but that's not the case for me, nor for you.

Nothing seems to compare to Windows when it comes to driver usability and performance.

---

### Post by Execute_Method on 2008-07-13
same problem here!!! It just started happening (***within 1 week***)

It also is killing my cpu scaling!

[http://ubuntuforums.org/showthread.php?t=854484](http://ubuntuforums.org/showthread.php?t=854484)


I am using:

ati x1650 (rv535)

xserver 2:1.4.99 from git
OpenGL version string: 1.3 Mesa 7.1 rc1
xserver-video-ati 1:6.8.0 from git
      
        *using above since beginning of march*

compiz 1:0.76

ubuntu studio 8.04

firefox 3
flash10 beta


Problem persists w/:

firefox2 after purge of ff3
with fresh & modified about:config (ff3)
flash 9 & flash 10beta
w/ or w/o compiz


Why all of a sudden? Maybe one of the updates?


I thinks this may be related: It started happening around the same time!!(xorg?)

[http://ubuntuforums.org/showthread.php?t=96068&page=5](http://ubuntuforums.org/showthread.php?t=96068&page=5)

---

### Post by Execute_Method on 2008-07-13
> **altonbr said:**
> No, this is a driver/Xorg problem. I've noticed the same thing with my GeForce 6800 on Ubuntu vs. Windows using free and non-free drivers for Ubuntu.

GMail seems choppy in Ubuntu, but not in Windows, especially while scrolling, it's really sad. This will also happen when you have a cheap, integrated GPU, but that's not the case for me, nor for you.

Nothing seems to compare to Windows when it comes to driver usability and performance.

Yes, the differences in driver performance compared to windows is and issue. However, I don't think it applies here.

This is occurring on many different cards with open and closed drivers. It seems likely that there is something else going on here. 

Especially since this just started occurring for me within the last week, and not since making a driver change or somesuch.

Logically it would seem that one of the recent updates broke this, but what was it? It wasn't the flash 10 beta update, because it occurred before this was released.

---

### Post by Execute_Method on 2008-07-14
bump this thread!!

I tried using Opera (which I can't stand) and the problem did not occur.... This suxxors.... I don't want to be "Forced" to use Opera or Epiphany, or any other ugly (Opera) or under-featured (the rest) browser.... I really enjoy using FF and I think it is a shame that I may not be able to until some improvements are made. Since switching to Linux, I haven't been "turned off" about anything but this... That said, I will NEVER go back to microslop. I will have to find a way to work around it, even if that means using a less than ideal browser fo a little while :(

---

### Post by Steve Fisher on 2008-07-14
After a bit of playing I've found that by using NoScript to block Facebook, Xorg settles back down to a reasonable level.

I just can't visualise how a script-heavy website could have any effect on the underlying windowing system.... and now only time will tell whether Facebook is useable without scripts running.

---

### Post by Steve Fisher on 2008-07-14
Just a quick update for this...

Facebook is fairly unuseable with NoScript blocking it, but I have found that reverting back to version 9 of Flash has solved this for me.

... So what was good about v.10?

---

### Post by Execute_Method on 2008-07-14
> **Steve Fisher said:**
> Just a quick update for this...

Facebook is fairly unuseable with NoScript blocking it, but I have found that reverting back to version 9 of Flash has solved this for me.

... So what was good about v.10?

HMM... I'll revert back too however, I am certain this was happening with version 9 for me too... That's why I updated (from adobe labs site, before the update came out in ubuntu)

---

### Post by kerry_s on 2008-07-14
have you tried the css fix?
[http://www.ghacks.net/2008/06/28/fix-choppy-scrolling-in-firefox/](http://www.ghacks.net/2008/06/28/fix-choppy-scrolling-in-firefox/)

---

### Post by unc0nn3ct3d on 2008-07-19
> **kerry_s said:**
> have you tried the css fix?
[http://www.ghacks.net/2008/06/28/fix-choppy-scrolling-in-firefox/](http://www.ghacks.net/2008/06/28/fix-choppy-scrolling-in-firefox/)

Hmm, thanks for the tip but pretty sure this is a Java issue as Xorg still freaks out to 90% with this fix implemented.

Another thing I've noticed is that flash movies have a horrendous framerate in full screen.  When I watch the daily show in windowed its smooth as a baby's bottom but full screen brings it down to 5 fps or so.

---

### Post by kerry_s on 2008-07-19
> **unc0nn3ct3d said:**
> Hmm, thanks for the tip but pretty sure this is a Java issue as Xorg still freaks out to 90% with this fix implemented.

Another thing I've noticed is that flash movies have a horrendous framerate in full screen.  When I watch the daily show in windowed its smooth as a baby's bottom but full screen brings it down to 5 fps or so.

i think i read some where that full screen flash was still broken on linux, i think the last time it worked right was back at flash7. :(

i'm out of ideas on the xorg thing, sorry.

---

### Post by unc0nn3ct3d on 2008-07-20
> **kerry_s said:**
> i think i read some where that full screen flash was still broken on linux, i think the last time it worked right was back at flash7. :(

i'm out of ideas on the xorg thing, sorry.

No worries, it would seem the entire community is out of ideas.  I'm content though, I'll take windowed flash and slow java to be able to use Ubuntu any day of the week and twice on sunday..

---

### Post by apswartz on 2008-07-21
I have not had any of these issues. All I can think of is that I don't have Gnome install on my laptop. I usually use KDE and will occasionally use XFCE.

Those of you having the problems, do you have the same problem when using another DE?

---

### Post by unc0nn3ct3d on 2008-07-22
That is a good question.. Could any KDE users chime in on this ?  I really don't want to start yet another thread describing this problem that contains absolutely no solution or progress towards diagnosing the problem to create a solution down the road

---

### Post by sizzam on 2008-07-29
I'm experiencing the same issue - when visiting facebook.com (for example) with Firefox 3.0.1 on Hardy, Xorg starts using 99% CPU.  Here are some of my system specs:

Dell Vostro 1500, Intel Core 2 Duo T7500, 2.2GHz, 800Mhz FSB, 4M L2 Cache
2GB, DDR2, 667MHz 2 DIMM
256MB NVIDIA GeForce 8600M GT

I'm using the 'nvidia-glx-new' driver.  If anyone has any ideas or suggestions for logs to query, etc, I'd be happy to do so.

---

### Post by LowSky on 2008-07-29
try using [Swiftweasel]("http://sourceforge.net/project/showfiles.php?group_id=195473")

Its a firefox port that fixes alot of Mozilla issues that occur on Linux machines. they even have a .deb for easy install

---

### Post by sizzam on 2008-07-30
Is everyone who is experiencing this problem using an Nvidia video card with the 'nvidia-glx-new' package for the drivers?

---

### Post by unc0nn3ct3d on 2008-08-05
> **sizzam said:**
> Is everyone who is experiencing this problem using an Nvidia video card with the 'nvidia-glx-new' package for the drivers?

I am using the envy variant of those, but basically ya

---

### Post by Steve Fisher on 2008-08-05
I'm using the old Intel i810 driver, so you can rule out any driver issues.

I'd just like to reiterate that going back to Flash 9 completely solved this for me.

---

### Post by nittybitty on 2008-08-05
I have the problem with ATI Radeon. It is a firefox/javascript error imo bc opera has no issues.  WTF

---

### Post by c1rcu17 on 2008-09-20
It's a problem with flash 10. Once you revert back to flash 9, all is well. You can see what plugins Firefox is using by going to,
```
about:plugins
```
What I did was close Firefox, run
```
sudo aptitude remove flashplugin-nonfree
```
And let Firefox reinstall flash itself if needed. That worked for me.

---

### Post by timothius on 2008-09-20
Hi,

Try the new NVIDIA beta release:  [http://www.nvnews.net/vbulletin/showthread.php?t=119682](http://www.nvnews.net/vbulletin/showthread.php?t=119682)

With these configuration options:  [http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

(IPP = 1 works better for me)

They speed up firefox text rendering - but are a buggy as hell

---

