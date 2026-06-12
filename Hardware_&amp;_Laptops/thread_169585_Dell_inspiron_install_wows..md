---
title: "Dell inspiron install wows."
date: 2006-05-02
forum: Hardware &amp; Laptops
---

### Post by cromestant on 2006-05-02
Ok, first of all, this is my system:
Dell inspiron 5150, intel p4 3.06ghz, 512 mb ram, nvidia geforce go fx 5200.

Now the problem, while installing, after the first part, where one has to reboot, to get the packages downloaded and installed, the system just crashes. Not a kernel panic, just it overheats and the system shuts down for safety reasons.

Now, the wierd thing is, I run windows ( by obligation) on the system, for days at a time, with 10 apps at the same time, the fan goes crazy but no notable overheating. 
So one might think it's a linux problem. 
But no. I 've been running gentoo stage one for almos 4 years no problems ( except the constant updating and kernel compiling and tweaking jus tot get it right, that just made me go crazy and that is why I tried ubuntu, on desktop first, now I want it on my laptop). So if a very fast smp kernel, runs under gentoo with no problem, why does the install of ubuntu just heats my cpu in that way?

I'd think that compiling in gentoo, takes the cpu to the highest temp posible, and that precomiled binary packages would just be a breaze for it.

Any ubuntu gurus out there that know what I might do?

As of this moment I am downloading the latest cd iso, maybe it's a bug in the previous 5.10 release, i don;t know

Thank you
Charles

---

### Post by cromestant on 2006-05-03
Ok, so I tried something else, I downloaded daper from the site, and installed it.
First of all , congrats to all the developpers on this one. This installer makes any other installer look... well plain.. it's a live cd that has a utility for install, really good, although still some bugs , but hey... WORKED great after restarting it.

So I installed it and now I have a fresh ubuntu daper on my laptop.

But ( always a but.) When I booted it up, I started to download the updates, and it crashed again while doing it, not because of a bug or flaw, just because my machine overheated again.

But I just spent yet again another entire day working on it in windows, and never crashed.
I'm wondering if this has to do with fan controls from ubuntu, that are just nos sensible enough. Any help would be apreciated.

Also i'm contacting dell with the error code, to see what they have to say about it, but I know it'll be something like, if it works in windows, then it works.

Thanks
Charles

---

### Post by cromestant on 2006-05-05
Ok , dell did actually use those words...
They would like to charge me about 200$ to try and fix this, so I said heck no.

Since My warantee is expired, I decided to do the deep cavity search for the problem, and decided to re-open my laptop.

Now this time I went farther... until the cooling fan was in my hand. And lo and behold, i saw what could be the problem : 4mm thick dust/hair/dunnowhattheheck cover on the back exhaust... so I cleaned it, delicatetly as to not move the grill of vents around, and I am now in a daper, no reboots so far ( 1 hour) and no heating whatsoerver, cpu running at half speed though.. but I don;t need much more than that at this moment. 

Thanks for reading this, hope it's solved.

Once again, great job you developpers. great distro.

EDIT: BTW is 51 degrees to much? for a p4 3.06ghz on a laptop?

thanks

---

### Post by slightly72 on 2006-05-05
I have an Inspiron 5160, p4 at 2.8, and it constantly runs at 50-58C, even while doing next to nothing and with all speed-stepping and p4-clockmod used. Aparently these 51xx inspirons have a pretty badly designed cooling system, so 51C on your laptop is to be expected.

---

### Post by DSn0wMan on 2006-05-06
[QUOTE=cromestant]Ok , dell did actually use those words...
They would like to charge me about 200$ to try and fix this, so I said heck no.

Since My warantee is expired, I decided to do the deep cavity search for the problem, and decided to re-open my laptop.

Now this time I went farther... until the cooling fan was in my hand. And lo and behold, i saw what could be the problem : 4mm thick dust/hair/dunnowhattheheck cover on the back exhaust... so I cleaned it, delicatetly as to not move the grill of vents around, and I am now in a daper, no reboots so far ( 1 hour) and no heating whatsoerver, cpu running at half speed though.. but I don;t need much more than that at this moment. 

Thanks for reading this, hope it's solved.

Once again, great job you developpers. great distro.

EDIT: BTW is 51 degrees to much? for a p4 3.06ghz on a laptop?

thanks[/QUOTE]


You might check out this thread. [http://www.ubuntuforums.org/showthread.php?t=122522](http://www.ubuntuforums.org/showthread.php?t=122522)

It seems that many people are having trouble with Dell 5150 overheating. Something about the heatsink / thermal paste etc.

---

