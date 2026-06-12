---
title: "Ubuntu 10.04 more Memory intensive?"
date: 2010-04-30
forum: Hardware
---

### Post by Zyrtec on 2010-04-30
Anybody else that upgraded to Lucid notice that it's more Memory intensive? 

I guess it's to be expected a little bit, but I was wondering if there was any background programs that I could stop at launch that might help?

Thanks

---

### Post by kill4killin on 2010-04-30
[http://www.webupd8.org/2010/04/xorg-memory-leak-bug-in-ubuntu-1004-fix.html](http://www.webupd8.org/2010/04/xorg-memory-leak-bug-in-ubuntu-1004-fix.html)

There was a memory leak bug in the RC, they patched it for release I think...

---

### Post by dino99 on 2010-04-30
use gconf-editor

---

### Post by Julita on 2010-04-30
You can look here: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491) (switching off unnecessary processes, etc)

---

### Post by robert.matear on 2010-04-30
I'm getting around 680 - 700 MiB memory usage after the upgrade. Is that normal? I suppose its not that much with 4gig of RAM. :-S

---

### Post by Julita on 2010-04-30
> **robert.matear said:**
> I'm getting around 680 - 700 MiB memory usage after the upgrade. Is that normal? I suppose its not that much with 4gig of RAM. :-S

I am having 550 MB (with Opera, Transmission, Claws Mail running); I am using Netbook Remix (Gnome) though...

---

### Post by MysticGold04 on 2010-04-30
I just installed Lucid on a P4 2.8ghz system with 768MB of RAM, when I first booted, it was using close to 400mb of ram. I disabled Bluetooth Manager and Visual Assistance in Startup Programs and under a fresh boot now am only using 180MB of RAM idle.

---

### Post by wykedengel on 2010-04-30
I'm noticing around 500MB after a fresh boot. It's around where Windows 7 is, but still uses less memory than Vista.

---

### Post by Zyrtec on 2010-04-30
My computer has 4GB of DDR3 1333 RAM, and before the update (I was using Karmic), I hardly ever got above 1GB. I was almost always at around 700-800MB in use.

Now with Lucid, it has stayed pretty steadily at 1.4 - 1.5GB

I thought it seemed a little strange since Karmic was always so low. I dunno...:confused:

---

### Post by phico on 2010-05-01
There seems to be a Huge memory leak in Ubuntu 10.04 64 bit final release  ... I have never seen that ..

I start with 500Mb which seems normal then the memory increases just by doing nothing (browser, nautilus ..) and never decreases, now I am already at 1300Mb after 15' uptime ????

Update ...

It just go down to 870Mb .. so the memory is free sometime maybe this is not a memory leak
but anyway it uses a lot of memory

---

### Post by axyelp on 2010-08-23
i wanted to begin a new thread, but I guess i'd continue here.

i too am having real problem with memory management on my laptop. i use compiz and can't do without it. But on my desktop(3.0 ghz core2duo, 3gb ddr2), the memory never went above 700mb. on my laptop, as soon as i boot, 1.2gb(60%) of memory is already used and around 25% in cached. browsing becomes nearly impossible! forget vmware which was one of my requirement while buying this laptop.

even without compiz, even without gnome for that matter, on lxde, it is 50% used up as soon as i login. and 30% cached on top of it.
machine's: 2.4 ghz i5 450M, 2gb ddr3@1066, 
i tried various workarounds,.. nothing seem to work here!

well, i copied my /home from the desktop. could that cause problems? any outputs i'm require to post?

thanks!

---

