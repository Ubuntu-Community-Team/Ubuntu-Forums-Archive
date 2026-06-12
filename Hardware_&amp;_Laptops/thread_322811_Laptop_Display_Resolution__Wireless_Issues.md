---
title: "Laptop Display Resolution / Wireless Issues"
date: 2006-12-21
forum: Hardware &amp; Laptops
---

### Post by mlissner on 2006-12-21
Hello All. Long time no visit to Ubuntu, but I'm back on the horse, fresh with questions.

Two in particular actually:
1. I just reinstalled Ubuntu on my Asus S96F laptop (no brand, homemade if you can believe that), and the display settings seem to be off. This computer is brand new, has only ever run Ubuntu, so I don't really know what they should be. Alls I know is that the compuer is widescreen, and the settings in the screen resolution dialog don't give me anything useful. Does anybody know the fix for this? 

2. I've FINALLY gotten wireless working, but it takes FOREVER to connect (like more than a minute). I watch my friends on Windows connect in half as long on old computers, and it hurts me. Ubuntu did this before to me on other computers, so I wonder, what's the deal? Is this normal for Linux, or is there a faster way to make it happen?

Thanks for the help, this stretched out screen is bizzare and must go!

---

### Post by nsleiman on 2006-12-21
Hi, 
i think you need to know the graphic card first in order to install the proper driver! there is plenty info on the forum.
as for the wireless, try to add the essid and the wep key directly in the system settings/network settings/eth0. personally i can connect in 2 secs after booting my laptop! much much faster than XP can do :)

---

### Post by acturneruk on 2006-12-21
> **mlissner said:**
> 1. I just reinstalled Ubuntu on my Asus S96F laptop (no brand, homemade if you can believe that), and the display settings seem to be off. This computer is brand new, has only ever run Ubuntu, so I don't really know what they should be. Alls I know is that the compuer is widescreen, and the settings in the screen resolution dialog don't give me anything useful. Does anybody know the fix for this?

What size is the screen? Can you measure it? For example, on my laptop the screen is 15.4in and has a widescreen resolution of 1280x800.

HTH

---

### Post by mlissner on 2006-12-23
Hey, thanks for the support guys. I think I figured out my woes on my own somehow.

I didn't want to spend a lot of time browsing forums, so I made that post, but I guess it was time well-spent. 

The fix went like this: while I was installing something else, I saw something spectacular in Synaptic: 915resolution. Its description looked like what I needed, so I installed it. Lo and behold, it worked. Graphics - Done.

For the wireless, I guess it's the setting up new networks that takes forever because yes, now that it's set up, it seems to come up automatically on boot, and seems to do so quickly at that.

Remaining projects / (semi) Rhetorical Questions:
- printer - Fedora made it work automatically without extra work, but it's running CUPS 1.2.7. Any easy way to update CUPS?
- microphone - Does it work, do I need something to make it work?
- dvd burning - Does it work? How?
- dvd playing - Does it work? How?
- flashy cube graphics and pretty themed desktop - What's this program called? What's it take to make it go like in Fedora?
- transferring files to this computer - SSH - no questions asked.
- get java compiler going - Why is this so hard?
- install and configure amarok - Got to do it.

Anybody who says completely setting up a new Ubuntu computer is a breeze is kidding themselves. This is all AFTER running Automatix2....oye...

---

### Post by tuxcantfly on 2006-12-23
> - printer - Fedora made it work automatically without extra work, but it's running CUPS 1.2.7. Any easy way to update CUPS?

Maybe try upgrading to ubuntu 6.10 (edgy eft)?

> get java compiler going - Why is this so hard?

make sure you have the multiverse reops enabled, then:

sudo apt-get install sun-java5-jdk

> - install and configure amarok - Got to do it.

sudo apt-get install amarok

EXAILE is pretty good, though. Get it at getdeb.net; it integrates better with GNOME

> - flashy cube graphics and pretty themed desktop - What's this program called? What's it take to make it go like in Fedora?

That's compiz you're looking for. Scrounge around the forums; there's a million guides. Don't use beryl; it's unstable as hell.

---

### Post by mlissner on 2006-12-30
Fantastic bit of help:
Java - Automatix2 did this - it works.
Amarok - apt-get did the trick on this.

New additions to the list (still haven't done any research on these):
- Get memory card slot working.
- Sort out the power management stuff. Return from Hibernate is very slow.

I figure I'll keep this list updated as I work so people can maybe use this someday...that, and I can use it if I ever start over.

---

### Post by mlissner on 2007-01-04
Well, I got the memory card going. All it took was an upgrade to edgy. This killed my computer temporarily (see my [other thread]("http://www.ubuntuforums.org/showthread.php?t=331053") about that), but the fix is in, and things are almost working again (though the screen freezes every now and again).

Oh well. More to come...hopefully somebody is reading this. If you're not, please let me know...

---

### Post by mlissner on 2007-01-15
OK, some progress to report.

First, I got the printer going, and it wasn't so bad in the end. To upgrade CUPS, all I had to do was go to cups.org, download the latest version 1.2.7, do a ./configure, make, make install, and that was pretty much that. I followed the directions that come with the download. Once that was installed, interestingly it didn't just start working like it did in Fedora, so I got the lpr and cupswrapper modules from the brother site and installed them. To get the brother lpr modules going, I had to install lpr via synaptic first.

- Neither my built in nor my mic jacks work...but I haven't worked on them yet.
- DVD and CD burning works, but both of them work VERY slowly. WHY? I have a 52X burner, so I ought to be able to clock along pretty quickly, but the fastest they go is 2.5X.
- Amarok is installed, but I want the visualizations to work.
- I gave up on Beryl and Compiz. I was reading around for a while, and from what I could tell, most people got it to work, but not without a serious amount of pain. At this point, I just want my computer to do things quickly. The bling can come next year when all the hardware works.

New problems I've run into:
- The biggest one is that my computer freezes on a regular basis for 30 seconds, and I can't figure out why.
- The next biggest is that Suspend and Hibernate don't work.
- After that is the CDROM slowness I mentioned a second ago.
- Next is the Fn keys not working to turn down the volume. I started a thread about that, but to no avail [here]("http://www.ubuntuforums.org/showthread.php?t=335205").
- CPU scaling doesn't work on my dual core despite installing the special kernel to get both cores going.

Honestly, I really do want to get things going here, but my progress is VERY slow. It's rather discouraging, I must say.

---

