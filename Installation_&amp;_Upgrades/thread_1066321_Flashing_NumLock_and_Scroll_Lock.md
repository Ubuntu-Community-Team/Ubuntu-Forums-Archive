---
title: "Flashing NumLock and Scroll Lock"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by MavKato on 2009-02-10
I have tried to install 8.10 from both the CD and from Wubi.  With both, the install gets part way through, then hangs up and the capslock (not numlock as the title says) and scroll lock lights start flashing, requiring a hard reboot.  With Wubi, it will get most of the way through the process before hanging.  With the CD, it hangs almost right away.  I have previously installed 8.04, but removed it because i could not get my wireless connection to work.  

I am getting frustrated, and close to giving up on linux, even though i don't want to.  :frown:

---

### Post by MavKato on 2009-02-12
update:

i tried using the alternate install cd.  i was able to install 8.10, but now when i get to the login screen, it does the same thing after a few seconds.  the keyboard and mouse stop responding, and the caps lock and scroll lock lights start flashing.

---

### Post by chris.rickey on 2009-03-04
This numlock/scroll lock flashing lockup happens to me about once a day.  Ubuntu 8.10 64bit runs fine most of the time, but then this happens.  I tried updating my dell d830 bios from a05 to a14, but still happening.  I can't trace it to any particular app, but usually am running a vmware player, amsn, and firefox.

---

### Post by lwhitmore on 2009-04-23
I've had the same thing happen twice - on 9.04.  It's bizarre.

Are any of you using madwifi (atheros) drivers?

---

### Post by UncoElite on 2009-05-13
This means the you are having a Kernel Panic. For some reason some hardware or a driver (or something) is not working correctly causing your machine to have a Kernel Panic, which pretty much just dies leaving the flashing numlock/scroll lock lights

---

### Post by WMarkTHarrison on 2009-08-16
Some people seem to have cured this by updating to a newer version.
For me it was teh opposite.  I had a happy, working system with 8.10, but now I get this freeze with flashing Caps Lock / Scroll Lock a second or so after putting in my password.  
How can you fix something like this?  I can't get the system running to make any changes, check the last driver loaded or anything.  Maybe back to 8.10 with a new CD?

---

### Post by lwhitmore on 2009-08-16
Well - it hasn't happened to me again (touch wood, I'm running the latest kernel, and I've changed BIOS vs a few times).  Not sure what caused the change though.

---

### Post by Harper45 on 2009-08-16
no i m not using midiffi drivers ...

---

### Post by chrisme52 on 2009-08-21
i'm on jaunty 64bit.
i just insatlled a wireless card and updated my system and now it randomy freezes up with caps and scoll lock lights flashing. I've had problems with different wireless cards before, so i wouldn't be surprised if thats the problem.

---

### Post by kevinjfry on 2010-10-22
For me, it was a memory issue.  I took out the memory that was causing the computer to lock up, and it resolved the issue, the computer has not locked up since.  It may be the same way in some of these instances.  Try different scenarios of memory and see if this resolves the issue.

---

