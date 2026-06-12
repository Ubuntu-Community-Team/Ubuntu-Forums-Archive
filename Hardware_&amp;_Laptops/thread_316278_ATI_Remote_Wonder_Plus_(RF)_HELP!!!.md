---
title: "ATI Remote Wonder Plus (RF) HELP!!!"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by ghstzr0 on 2006-12-10
I am running Edgy.

I have an ATI Remote Wonder Plus (came with my All-In-Wonder X800) that plugins in via USB.

I have looked at many howtos to get this to work but IT DOES NOT.

My remote doesn't work right after install... no response for xev from the remote...

Next, I tried installing LIRC:  Doenleaded source, untarred, ran ./setup.sh.  I have tried with both of the ATI options that are under 'USB' but to no avail.  Niether have any response!

In both cases lircd starts fine, and so does irw (or mode2 for that matter).  I push buttons, but no events are logged!.

I KNOW ITS NOT THE BATTERIES, as the remote works fine in Windows (dual boot).

ANY HELP???

---

### Post by Noky on 2007-03-01
LIRC is for IR remotes. I'm assuming that the original Remote Wonder is infact IR while the Remote Wonder Plus is RF.

I don't believe there are any drivers out for the remote wonder plus. If anyone has any ideas to get this remote to work that'd be great.

If I find any time I'll look into ndiswrapper. I've never used it before but supposedly it wraps windows drivers and get them to work under linux. Sort of a last resort seeing as my programming skills don't go much furher than hello world.

If anyone has any ideas to solve this problem. I appreciate any input seeing as I'm looking to get my remote working and I found this thread through Google so I decided to reply instead of creating a whole new thread.

---

### Post by potsofdirt on 2007-03-22
A few months ago I found some information about using the RWP with lirc, and ended up writing a patch for the kernel module.

I created a page about it at [http://mythtv.wbond.net/remote_wonder_plus_linux/](http://mythtv.wbond.net/remote_wonder_plus_linux/). There you can find the mirrored copy of the original lirc code to get the RWP working, as well as my patch for the ati_remote.c kernel module. I don't run Ubuntu, but if you need some help with the kernel module patch, please post on the forum at [http://mythtv.wbond.net/remote_wonder_plus_linux/forum/](http://mythtv.wbond.net/remote_wonder_plus_linux/forum/).

Hopefully this info will help!

---

### Post by hot_rod_hippie on 2007-05-22
Using the HowTo from the forum 'potsofdirt' linked, I got my remote wonder plus working quite well.

Josh

---

### Post by MonsterMaxx on 2008-02-04
I bought 2x of the Remote Wonder Plus for my Myth setup and now I see that this might not have been the best choice.

It seems that the patches aren't avail for the latest kernal 2.6.22 which it seems I have.

Should I use the 2.6.20 patch? or set these things aside until a patch is released?

---

