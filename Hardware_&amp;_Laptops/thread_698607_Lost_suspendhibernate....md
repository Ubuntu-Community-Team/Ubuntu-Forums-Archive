---
title: "Lost suspend/hibernate..."
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by neocortex on 2008-02-16
Hello ALL!
I have HP nx8220 and Dapper on it. It was easy to make everything work at that time. Now, I realized that my fan is running all the time, and that my battery-life is quite poor (much shorter than under dual-booted Win). I started to tweak a bit, I did not managed to fix my fan or battery, but now I have lost Suspend/Hibernate completely. I do not when and where, I must admit. Can anyone help me? To give me guidance how to put everything back into baseline state? What configuration files do I need to change, and how etc.

Thanks in advance! Best,
PM

---

### Post by maturin on 2008-02-16
Sorry - don't have the answer, just a similar problem:

When I first installed Kubuntu (Toshiba Satellite U205, Intel G945 graphics), suspend/hibernate worked fine.  After spending a few days with it, both stopped working (screen blanks, then immediately returns to login screen).

After a re-install, everything (again) worked fine.  This time I tried to track when/if suspend/hibernate stopped stop working.  It stopped working after I set the monitor off time (in Monitor & Display under Control Center), AND the screen turned off for the second time after setting this.  Since then suspend/hibernate don't work.  Some other things I've noticed that might help diagnose the problem:

- now, whenever the screen turns off the second time, the Xorg process goes nuts requiring a hard reboot or ssh'ing into the laptop and killing the Xorg process.

- in an attempt to stop the Xorg process going beserk, I turned off xset (by turning off all permissions).  This results in the screen blanking just fine when the laptop lid is closed (repeatedly), though obviously it no longer turns off after the set time.

- booting with the live CD shows that suspend/hibernate still work (no surprise).  It will continue to work even if I then set the monitor off time, but the screen will then refuse to turn off the second time it's supposed to.

I've spend a fair amount of time going through the forums here and elsewhere, but no luck so far.  Any advice would be welcome - is there any way (as neocortex asks) to return the suspend/hibernate routines to a baseline state (without requiring a re-install??)

Thanks

---

### Post by maturin on 2008-02-18
Anyone?....

---

### Post by neocortex on 2008-02-19
Dead silence, what can I say. I tried and looked here and there, but nothing.
It must be something simple and stupid. I did not made any big changes and in many files.

---

### Post by maturin on 2008-02-21
Well, I'll keep trying things and going through forums and stuff.  If I find anything that works, I'll post it here.

---

### Post by bw44 on 2008-02-21
> **maturin said:**
> Well, I'll keep trying things and going through forums and stuff.  If I find anything that works, I'll post it here.I started a similar thread ([http://ubuntuforums.org/showthread.php?t=702101](http://ubuntuforums.org/showthread.php?t=702101)) a couple of days ago, but didn't realize that the correct terms were "suspend" and "hibernate."  

As I described there, I've go a very similar problem, though I'm not sure whether the suspend/hibernate function ever worked on my Compaq (HP) Presario laptop.  I didn't test it until long after I had been applying updates and making other changes to get things working (wireless, modem, etc.).

I'll keep looking for a solution too and post to this thread if I figure anything out.

bw44

---

### Post by StevenRoose3 on 2008-02-21
same PC (Toshiba Sattellite) and same problem.

anwser allready found somewhere else?

---

### Post by bw44 on 2008-02-22
Like a lot of others, I have combed the forums for an answer to the suspend/hibernate problem with my laptop.

My conclusion (obvious to anyone but a newbie) is that it's always going to be hardware/software dependent.  So unless someone with the same laptop, the same version of Ubuntu, the same device drivers and so on, has solved the problem and posted their solution, you ain't going to find it.

What to do?  Well, until a more generic solution is offered by the folks at Ubuntu (and I'm sure they are concerned about it and will eventually come up with something), we can only try to solve the problem for our particular machines and post anything that seems generally applicable.

Here are some links to resources and articles that may help get you started.  I can't remember where I first saw them posted, so can't thank the people who pointed them out.  Sorry about that. I haven't tried all the things recommended, so can't personally vouch for them.  But if any of this information leads me  to a solution, or to more helpful sites, I'll post it here.

The most common suspend/resume problem: 

[https://fedoraproject.org/wiki/KernelCommonProblems#head-dfdd3eb7cba58cc5643d06f7866dd83cb769db4a](https://fedoraproject.org/wiki/KernelCommonProblems#head-dfdd3eb7cba58cc5643d06f7866dd83cb769db4a)

Really interesting site with links to some hardware-specific "Quirks":

[http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-index.html](http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-index.html)

A useful procedure to get you out of trouble if the Gnome display manager hangs (which could happen if you are testing suspend/hibernate/resume scripts):

[http://www.arsgeek.com/?p=787](http://www.arsgeek.com/?p=787)

The last one above may be common  knowledge to more experienced Ubuntu users, but I hadn't seem it before.

If anyone comes up with other helpful sites/info maybe they could post it to this thread -- not exactly a "how-to," but a "start-to."  

Cheers.

---

### Post by bw44 on 2008-03-02
Doesn't look like anyone else is following this thread.  I'm not going to post on this topic suspend/hibernate/resume) again until after the offical release of 8.04 (Hardy Heron). 

Hopefully, there will be some improvements in this area with the 8.04, and I  guess questions should be asked and problems reported relating to the new software.  If I can't make suspend/resume work under 8.04, I'll start a new thread!

Thanks for listening! :)

---

