---
title: "Is Compiz stable for you?"
date: 2008-11-11
forum: General Help
---

### Post by quickk on 2008-11-11
Hi everyone, 

   I was wondering if anyone has managed to use desktop effects in Ubuntu 8.10 without any problems.  My main problems:

-running out of video memory 
-lots of glitches: window decorations (especially title bar) get corrupted, windows get stuck in maximized mode, etc. 

Is this related to my relatively old graphics card (nvidia 6800, 128MB mem), or is it just that compiz isn't stable enough yet?

Thanks for your help!

---

### Post by Whisp3r on 2008-11-11
Except for the issue with OpenOffice software and menus not showing up, Compiz seems to work pretty well (8.10.) I wonder if part of my problem is I'm using an older computer, with a 64MB GForce FX Card (Hey, it was free).

---

### Post by Roinator on 2008-11-11
I have a 256MB integreated card for graphics.  I know it sucks because it is integrated, but under 8.04 compiz ran very smooth, even with all the bells and whistles.  Now my wobbly windows are buggy, and I dare not use a relfection for my cube =(

---

### Post by transmition on 2008-11-11
Everything works fairly well for me on my macbook 4.1. Although when I try and shade windows they occasionaly get stuck.

---

### Post by eternalnewbee on 2008-11-11
I had some issues in the past, while still using Hardy, but I must say it's very stable now.
There is just a little "glitch" with Emerald, which sometimes tend to get unresponsive. This usually happens when changing themes too fast.

---

### Post by chrisby on 2008-11-11
The only issue I have is the twitching window bug with wobbly windows.

---

### Post by outofnicks on 2008-11-11
It's kind of buggy for me, although I'm surprised how well it does work considering the low RAM I have.

My titlebars and window borders disappear and come back and I had to quit and restart Firefox to be able to type a reply to this. For some odd reason, the input box just wouldn't accept any input. Other programs worked OK, just a Firefox thing.

After I switched from Extra Effects to Standard Effects I seemed to have less quirks. The really fancy stuff isn't very practical until I get additional RAM. 

Half an hour ago, all titlebars and window borders were missing (or transparent) then after I enabled Zoom Desktop, they returned.

Also, rotating the Cube sometimes causes windows to hide themselves--I can't figure out how it happens.

---

### Post by sharkster2007 on 2008-11-11
I have an P4 2.4Ghz with 1gb Ram & Nvidia 6600GT Graphics(AGP Version)

I have the title bar problem, but apparently a lot of other Ubuntu 8.10 users do to, it seems to be down to the Nvidia driver. ( Until they make a new one were stuck with this :-( )

No other Problems to report, everything else seem to work fine :-)

---

### Post by quickk on 2008-11-12
Thanks for all the replies!  It's good to know that others are having some stability problems too.  

> Half an hour ago, all titlebars and window borders were missing (or transparent) then after I enabled Zoom Desktop, they returned.


I'll give this a try and see if it works for me too!  The thing that I find strange is that it seems that 128MB of graphics card ram isn't enough to run compiz smoothly: for example, with too many windows open, I can't watch a video full screen.  It's not like were talking about a complex 3d game here!  Am I missing something?

---

### Post by binbash on 2008-11-12
Everything + every extra plugins (except stack plugin, i could not compile it ) working fine even with crap beta ati drivers :)

---

### Post by outofnicks on 2008-11-12
> **outofnicks said:**
> 

Also, rotating the Cube sometimes causes windows to hide themselves--I can't figure out how it happens.

Just figured it out--a quick movement of the mouse to either edge of the screen (but not over the edge) minimizes the active window.

*[couple minutes later]*
And the same movement returns the window to maximized. Who'da thunkit? :biggrin:

---

### Post by mihaiv on 2008-11-12
I have rare (once every few hours) and random crashes, probably of X (the entire system freezes and does not respond to any input). I have an ATI video card (Radeon X600)  and I use the open source drivers.

---

### Post by motin on 2008-12-19
No, it is not stable and has never been. At first I though nvidia drivers were needed: [http://ubuntuforums.org/showthread.php?t=811747](http://ubuntuforums.org/showthread.php?t=811747)

Now I know it is simply impossible to attain a stable compiz setup. Most current issue: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/309739](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/309739)

---

### Post by motin on 2008-12-19
A meta-bud that denotes that 3d desktop effects simply aren't stable at all yet: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/309747](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/309747)

---

### Post by motin on 2008-12-19
A meta-bud that denotes that 3d desktop effects simply aren't stable at all yet: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/309747](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/309747)

---

### Post by stderr on 2008-12-19
As much as I love compiz (especially CCSM - it's so cool), I have to say it seems to be rather buggy for me. Most of the time I just use metacity so I can get on without worrying about it.

Problems: 

 - fullscreen with flash in firefox [edit: now appears to be resolved under Ibex!]
 - something related to how much screen estate can be used for video before the app crashes (VRAM? but it's 256...)
 - occasional loss of the WM buttons in the top right of windows (probably an Emerald issue)
 - odd issues with *some* wine windows, depending

As much as I hate the bugs (which may not be actual bugs with Compiz anyway) I love the compiz experience. I'm looking forward to everything being ironed out :D

---

### Post by Usufruct on 2008-12-19
In a word, yes.

The biggest graphical bugs I had were issues with the nVidia driver, and they have all been resolved with the 180.06 beta driver.

---

### Post by mmilitia9 on 2008-12-19
Yeah, I find it very stable for me.  I don't use any of the crazy effects like the fire though.  I just use what makes my life easier and it's never crashed on me before.

The only time it's ever been buggy is when I use to pair it up with Emerald.  They worked perfectly, until you trigger something to cause the window border to disappear on you which was very annoying because then you would have to restart X again.. yuck.  So I just don't install emerald anymore and Compiz is fricken awesome =)

---

### Post by mmilitia9 on 2008-12-19
> **Usufruct said:**
> In a word, yes.

The biggest graphical bugs I had were issues with the nVidia driver, and they have all been resolved with the 180.06 beta driver.

When you installed Ubuntu 8.10.  Did you run into the issue with Compiz where it would not load up at all and when you enabled desktop effects(After enabling the driver Ubuntu recommended, of course) an error popped up with something along the lines of "Desktop effects cannot get started"? 

That is the only issue I have with compiz right now.  It seems to me that after I updated my entire system from a fresh install of 8.10 my compiz stopped running automatically and when I went to "Desktop Effects" to check off "Extra", that error would pop up for me.

I recently got around that though with fusion-icon.. but still, it use to be simpler by just.. uhh, starting up with the rest of the things in the background? haha. 

Anyway, did you have that issue too before the beta driver?

---

### Post by Usufruct on 2008-12-19
> **mmilitia9 said:**
> When you installed Ubuntu 8.10.  Did you run into the issue with Compiz where it would not load up at all and when you enabled desktop effects(After enabling the driver Ubuntu recommended, of course) an error popped up with something along the lines of "Desktop effects cannot get started"? 

That is the only issue I have with compiz right now.  It seems to me that after I updated my entire system from a fresh install of 8.10 my compiz stopped running automatically and when I went to "Desktop Effects" to check off "Extra", that error would pop up for me.

I recently got around that though with fusion-icon.. but still, it use to be simpler by just.. uhh, starting up with the rest of the things in the background? haha. 

Anyway, did you have that issue too before the beta driver?

I did not have that issue before the beta driver :-/

My 8.10 install was not fresh though, I had the beta from the day it was released, and I was upgrading from Hardy.  I suspect that might have something to do with me not having the issue?  I'm not sure though.

---

### Post by dkev on 2008-12-19
It actualy works good for me on my desktop. Nvida 8600 GT with 4 gigs of ram. My beam up effect, I just use for menu higlights which is awesome when used that way. And window shift is fluid. I just don't have any issues. I think it's just too easy to overload an older or economy vid card with too many effects. So I try to keep my effects kind of elegant and not obnoxious. It seems to be a good balance.

---

### Post by jcm4 on 2008-12-20
Pretty stable, had my first problem with it a few minutes ago messing with transparency.

---

