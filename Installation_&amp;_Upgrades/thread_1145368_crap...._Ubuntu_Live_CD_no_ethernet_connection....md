---
title: "crap.... Ubuntu Live CD no ethernet connection..."
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by DracoJesi on 2009-05-01
I hope this is a quick fix...

I was messing around on my 9.04 live cd, had to do a hard shutdown, now my ethernet connection isn't being detected, and I could be wrong but I'm pretty sure it was before...

it acts like it really wants to work but it finally gives up and says I've been disconnected.

I hope it's not the disk, because the worst part is, I'm supposed to show it off over at my dads this weekend after showing him 8.10 on my lap top last time, may not look good for Ubuntu, of all times...

is there anything I can try before reformatting the live cd and burning it again?

---

### Post by DracoJesi on 2009-05-01
I can use an md5 checksum to make sure it's not the disk right?

what program do I use for that?

also, tell my what diagnostic commands you want me to run and I'll go do it, move data on my SD card and post it,

I'm guessing

ifconfig
lshw
route -n

?

---

### Post by DracoJesi on 2009-05-02
anyone? not to bump or anything but I really need this fixed by morning, and I'm pretty sure theres got to be an easy solution...

---

### Post by DracoJesi on 2009-05-03
a little reminder

---

### Post by Mark Phelps on 2009-05-03
You're not getting an answer because running in LiveCD mode can NOT change your PC settings in any way. Period.  It creates a RAMdisk to run from.  Nothing is saved to the hard drive.  Once you reboot or otherwise shut down, your PC is EXACTLY the way you had it before you booted fromm the LiveCD.

Now ...

If you installed it, then you could have done anything from accidentally added a second OS, to having completely overwritten everything that was there before.

If you installed it, you need to go to the networking subforum and do some searches on troubleshooting network problems.  It's not a simple one-command solution.

---

