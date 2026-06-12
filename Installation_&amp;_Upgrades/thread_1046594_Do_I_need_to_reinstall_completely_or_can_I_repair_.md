---
title: "Do I need to reinstall completely or can I repair my system?"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by Seseli on 2009-01-21
Okay, so I had a problem getting my wireless card to work. Now my computer can't start up properly (not even in recovery mode). The problem seems to be caused by the program ndiswrapper, but I have no clue about how to remove it if I can't start the computer (the problems are described [[COLOR="Blue"]in this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1043143") in more detail, but I didn't get a reply). 

I was about to give up and do a complete re-install of the system from a CD, but then I read that this is very rarely necessary. So I thought I'd give it one last try: can I somehow repair my system without re-installing from scratch?

(Also, a stupid question: if I have files on my /home partition, they'll probably still be there if I re-install from a CD into the root partition, right?)

---

### Post by dabl on 2009-01-21
I wouldn't recommend you do the same thing over again, and expect a different result.  :D

I don't know your RTL-8185 wireless card, nor how ndiswrapper got installed in such a way that it is interfering with booting.  If you literally cannot boot, even in text mode to a console, then I guess you're doomed to reinstall the system.  But I would advise you study up on the Ubuntu procedure for configuring that wireless chip, before you try again:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

You might want to try 8.10, in case the support for that chip is better.  Good luck!  :)


p.s. Yes, if your data are on a separate partition, mounted as /home, then the only thing you need to worry about is the old desktop settings - they won't be changed in your new installation.  That may be a good thing, or a bad thing ...

---

### Post by donkyhotay on 2009-01-21
LiveCD's are your lifeline when you can't boot. Worse case scenario you can use the liveCD to back up your stuff but you might be able to use it to remove ndiswrapper to get the system bootable again (never used ndiswrapper so I have no idea what may have gone wrong). Of course this is assuming you have a liveCD to use or another computer with internet access to create a liveCD with.

---

### Post by Seseli on 2009-01-23
Okay, thanks for your advice! 

Weirdly, the problem resolved itself, and suddenly I could start normally again. I've now upgraded to Intrepid, and I'll do some more research about wireless cards, and maybe switch to a different one.

---

