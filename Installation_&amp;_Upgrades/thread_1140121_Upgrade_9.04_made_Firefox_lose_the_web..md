---
title: "Upgrade 9.04 made Firefox lose the web.  ???"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by quixote on 2009-04-27
The upgrade was flawless except for one thing:  I have two Firefox installed: 3.5b3 in my /home directory (the one I use all the time), and 3.0.9 that's part of the system.  The ordinary one that I don't use can see the web just fine.  The Firefox in my /home directory suddenly can't find the web after the upgrade!

What do I have to fix to solve this?  I can't live without my FF 3.5!  Please help!  :)

In case it's relevant: I have a 64-bit system, also when I was using Intrepid on this same machine, but I'm pretty sure my 3.5b3 is 32-bit.  However, all was fine under Intrepid.

---

### Post by quixote on 2009-04-28
Apparently, this weird behavior was a symptom of a deeper problem.  I started getting demands to run fsck during bootup.  Turned out (I think) that I had a bad block on my hard drive.  To find the bad blocks, I booted from a liveCD, made sure those partitions were unmounted, and then ran```
 $sudo e2fsck -c -k -v /dev/sda2
``` (in my case it was /dev/sda2).  And then ```
 $sudo e2fsck -f -y -v /dev/sda2
``` 

I DON'T know what I'm doing, but I got the impression from the man page on e2fsck the -c looks for and adds any bad blocks to the list, -k keeps the ones the system already knows about, -v for verbose.  Then, -f to force a second check, and -y to answer yes to fix anything e2fsck might find.

Unfortunately, by the time I realized I had this problem there were enough damaged files floating around that the Gnome desktop and GDM itself were very flaky.  A clean install seemed like the only way to go.  So I did that.  It wasn't too painful, since I have /home on a separate partition and didn't lose any data or my various settings.

Now all I have to do is get the stupid flash working again.  :x  When is Ubuntu just going to make that nonsense  a 1-click thing, like the #$^% proprietary drivers?  Or change the world so we don't need them? :)

I have to say, Jaunty was worth the trouble!  Lightning fast, and it looks stunning!

---

