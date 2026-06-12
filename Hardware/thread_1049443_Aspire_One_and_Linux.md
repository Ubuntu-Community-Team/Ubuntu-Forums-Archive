---
title: "Aspire One and Linux"
date: 2009-01-24
forum: Hardware
---

### Post by SaintStewart on 2009-01-24
Hey all.  Its been a while since Ive posted here.  Haven't had any problems with running Linux till now.  I got an Acer Aspire One (XP version - ZG5).  I love Linux, and have been runnning it fine on my old notebook (a Dell D600).  Well, since this came with XP, I wanted to shrink it down to bare minimum and get Linux on this bad boy.  

Long and rambling story short, no matter what I do, I cant get ANY distro working on this thing correctly.  On Ubuntu, the wireless doesnt work (I get it working, then after I reboot, it doesnt, and no amount of fixing does anything to get it moving again).  On EEEbuntu Standard, it all works out of the box - until I have to update.  Then again, the wireless doesnt work.  On Mint, I can get the wireless working, even after multiple reboots, but then the video craps out and wont resurrect.  On openSUSE, I cant get 3D accel no matter what, and wireless also cuts out.  I could go on and on with all the distros Ive tried, but it would take a couple of pages.  

Sorry to whine, but I am *really* frustrated.  Im not a guru, or even an expert.  Id think myself a mid level linux user who knows how to tinker the common stuff between distros, but I do have to look stuff up.  

I guess over all, my question is - what distro?  Is there any one that works best with the One, and will it work consistently?  I love this laptop, but Id hate to have to leave Windows on here as Im thinking it might need to be.  I hope not, with all your help.  Thanks in advance, and apologies for being so long winded.  Ask any clarification questions if needed - I may not be too coherent.

---

### Post by pjalegria on 2009-01-24
maybe this can help you... 

[https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L)

to me it help, i have a fully working Acer Aspire One with ubuntu 8.10 + Netbook Remix, and i am very happy with it...

---

### Post by teaker1s on 2009-01-24
ubuntu intrepid ibex with mad wifi is fully working and stable. 
[https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")

if you get stuck reply again on this thread

---

### Post by SaintStewart on 2009-01-24
> **pjalegria said:**
> maybe this can help you... 

[https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L)

Thanks, really, its appreciated, but I already knew about that.  That's the page I learned how to get the wireless working in the first place.  Google is your friend.  :D

I can *get* it working.  On most distros.  The problem is *keeping* it working.  After a reboot, it stops and won't come back on for anything.  Im clueless as to what to do.

---

### Post by teaker1s on 2009-01-24
the issue is modprobing the module to manually start it or setting it to start on boot
```
sudo gedit /etc/modules
```

---

### Post by pjalegria on 2009-01-24
And i forgot, with that optimized Kernel....

[http://www.ubuntuaone.com/content/slckb0ykuki-kernel-2628-v02-acer-aspire-oneundervolt](http://www.ubuntuaone.com/content/slckb0ykuki-kernel-2628-v02-acer-aspire-oneundervolt)

---

### Post by sloggerkhan on 2009-01-24
I put fedora 10 on mine. No problems. If you look up fedora and aspire one, you should get some useful pages.

Everything seems to work for me.

---

### Post by pjalegria on 2009-01-24
And you have other alternatives...

[http://www.linux4one.it/](http://www.linux4one.it/)

or...

[http://www.kuki.me/](http://www.kuki.me/)

---

### Post by SaintStewart on 2009-01-24
Thanks for the suggestions...I'll try some things out and see what I can do.  Back to the grind!

---

### Post by neu2buntu on 2009-01-24
[http://ubuntuforums.org/showthread.php?t=1012973](http://ubuntuforums.org/showthread.php?t=1012973)

heres link to get wifi working fully

---

### Post by SaintStewart on 2009-01-25
Ok, well, I got it working consistenly on all fronts...for the moment.  Ubuntu 8.10.  

Now, one last question for you all.  As the resolution is 1024x600, I notice that some boxes/windows are off the bottom of the screen when I use them.  

I have read that using the ALT key and clicking to move it around solves the problem.  I was wondering...is there any way to make it permanent?  As in force the windows to just fit to the screen, rather than having to move them around all the time?  

Thanks again in advance.

---

### Post by SaintStewart on 2009-01-25
*bump*

---

### Post by sloggerkhan on 2009-01-26
Some windows there's no fix for, but many apps will fullscreen with f11.
Really it just depends. (For example, no matter what you do, inkscape won't really be usable.)

---

### Post by SaintStewart on 2009-01-27
> **sloggerkhan said:**
> Some windows there's no fix for, but many apps will fullscreen with f11.
Really it just depends. (For example, no matter what you do, inkscape won't really be usable.)

Hrm, yeah, thats basically the comclusion I came to.  Thanks!  :)

---

### Post by easybake on 2009-01-28
I just put Fedora 10 on mine and its sweet.

---

### Post by Tomatz on 2009-01-28
You want Easy Peasy (formerly ubuntu eee)!

It is ubuntu based and works on the aspire one "out of the box" (personal experence):

[http://www.geteasypeasy.com/](http://www.geteasypeasy.com/)

There are howtos on their homepage to install from a flash drive.

;)

---

### Post by Tomatz on 2009-01-28
Screenshot:

[IMG]http://www.ubuntu-eee.com/wiki/images/UbuntuEee8041.png[/IMG]

---

