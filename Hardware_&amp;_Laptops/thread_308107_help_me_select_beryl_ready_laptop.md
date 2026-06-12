---
title: "help me select beryl ready laptop"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by shrndegruv on 2006-11-27
So I want to get a new laptop that can handle all the nifty stuff that beryl does.  From my research, seems nvidia is the way to go as their driver will allow beryl to function without using xgl/aiglx.  

Is it possible to get nvidia laptops to hibernate/sleep correctly?

Also, I want to be able to hook an external monitor up to the laptop. Is it possible to do more than one?  I also like slim form-factors for laptops, something not too bulky.  

Any suggestions/success stories for this sort of thing?

---

### Post by racmar on 2006-11-27
I can not tell which laptop will work the best for your needs, but I can share my experiences.  I have a Lenovo ThinkPad with an integrated Intel chip, and I have been using AIGLX /w compiz / beryl since dapper.  I have also used several mini-pc computers with Intel GPUs without trouble.

So, I will suggest anything with an Intel GPU. It works great for all the wonderful eye-candy and is extremely easy to setup using edgy.  I'm fairly sure that edgy has AIGLX enabled by default these days, so that helps.  Another great plus is that the Intel drivers are open-source -- not binary only like ATI / NVIDIA

On Hibernation: I consistently have problems with hibernate/resume on every machine I've ever used /w linux ( > 20).  I just wish someday it will work as well as XP; hell, I'd settle with working at all.

-Rob

---

### Post by meldroc on 2006-11-28
I'm not willing to settle for Intel GPUs - they're way too slow for me.  No T&L, and they share main memory instead of having their own video RAM.

I was hoping that I could deal with ATI's drivers, but it seems they're way too buggy.  They're slow, they'll crash if you try to suspend or hibernate or switch virtual terminals, and they're a pain to get working.  For a laptop, suspend/hibernate is not optional.  I should be able to shut the lid, have it automagically go dormant, and when I open the lid again, it should wake up and Just Work.  100% of the time, no exceptions.  That's an important feature, and a laptop owner shouldn't have to put up with that not working.

So I guess that leaves NVidia.  At least on the desktop, they seem to work rather well.  I haven't seen them on laptops, and I'm not sure if things like suspend/hibernate work correctly (sometimes, from all the posts I read, it looks like nobody's figured out how to make that work right.)

Any suggestions on which NVidia-equipped notebook I should buy?  I'd take a ThinkPad T60 if they had an NVidia GPU instead of Intel or ATI, but Lenovo doesn't do NVidia. :(

---

### Post by meldroc on 2006-11-28
Just discovered System76.  They have a forum here on Ubuntu Forums, and they make desktop and laptop systems with NVidia GPUs and Ubuntu pre-installed.  Just from reading their forum and looking at their web site, it looks like they go to a lot of trouble to make sure nearly every bit of hardware works right and is supported in Ubuntu.

I'm highly tempted.  Any reason why not?

---

### Post by shrndegruv on 2006-11-29
the system76 stuff is pretty cool, but my main problem is their laptops are not configurable enough.  Unless its a typo, their top end notebook only gives 1200x800 resolution.

---

### Post by shrndegruv on 2006-11-29
alienware seems to be the best option.  The offer a machine with 256MB Nvidia GeForce Go 6600.  Will that be sufficient for beryl to run smoothly?  the 7600 is $200 more....

---

### Post by meldroc on 2006-11-29
Ewww, not Alienware.  After what my roommate went through with his Alienware laptop.  It fritzed out, losing sound, and crashing very frequently (even on reinstall of Windows) and we had to send it back to them twice.  The first time it came back, they said "No problem found." even though it would crash within five minutes of being powered up.  The second time, they actually fixed it.  On top of that, we spent hours upon hours talking to call center agents in third-world countries who could barely speak English and didn't have a clue how to diagnose computer problems.

---

### Post by jerich007 on 2006-11-29
I'm running Edgy with Beryl 0.12 on my T43, using the ATI drivers.  Overall, performance is stable.  I've been able to work around some minor annoyances, most notable with suspend/hibernation modes.  Suspend will work, but occasionally not when using the function key shortcut (Fn-F4).  In those occasions, I suspend from the Exit applet on the top task panel.  Hibernate works, but if I have a lot of apps open, I get a msg saying "Not enough free memory" even though my swapfile is 2GB.  I find that if I log out to the main Ubuntu screen, I can suspend to disk correctly.

I'm addicted to the Beryl eyecandy, so I'm willing to make some sacrifices.  ;)

---

