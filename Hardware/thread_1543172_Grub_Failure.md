---
title: "Grub Failure"
date: 2010-07-31
forum: Hardware
---

### Post by DanielWEvans1982 on 2010-07-31
Okay here's the low down:

Installed vista using recovery discs (everythings fine here)
Installed another os of 7 (everythings fine) 
Installed ubuntu 10.04 in windows 7

Everything was great, the windows 7 boot loader still worked, and I could pick ubuntu then the grub would come up.

So I updated ubuntu, and it configured grub again, I was asked a couple questions which were obvious ( i don't recall what they were noww )

Anyhow, went to reboot and it said "no such device: 945u92jt093jf<--- with some number"

Then threw me into grub rescue mode.  I followed the steps on this page [https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)

And kept receiving the message "No such disk" 

When I type ls all that it says is (hd0), I've only got one drive, so what is the freaking deal is ubuntu seriously this shitty?

Anyhow help needed, thanks

---

### Post by drs305 on 2010-07-31
I haven't been on the forums much this week due to work, but I've seen several of these reports. It sounds like Grub2 installed/updated to the partition/MBR rather than update the files *within* Wubi itself.

You should be able to regain use of your Windows OS if this is the case by referring to this post:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

Here is a post on the "no such disk" error message. If your issue is in fact with a normal Ubuntu install and not Wubi, this may very well be the problem:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search")

If you continue to have problems, run *meierfra's* boot info script and post the results:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by Rubi1200 on 2010-07-31
I have just read a couple of posts about this issue, which is apparently cropping up on a more regular basis now.
 
See this post from forum member bcbc about the problem:
 
[http://ubuntuforums.org/showpost.php?p=9662218&postcount=5](http://ubuntuforums.org/showpost.php?p=9662218&postcount=5)
 
Check the link to the bug report on Launchpad.
 
If this is the problem, the answer seems to be reinstalling the Windows bootloader (as suggested above).
 
Hope this helps.

---

### Post by DanielWEvans1982 on 2010-07-31
DRS you are the man!  That worked!

Everything is back to normal again.  I like the design and the editing of grub but when it comes down to it ubuntu has gotta do soething about the dual / multi booting automatic configuration of grub.

IT ALWAYS FAILS on me.

Anyhow thanks for the help

---

### Post by DanielWEvans1982 on 2010-07-31
Now to figure out how to mark this thread solved and I'll be on my way :p

---

### Post by drs305 on 2010-07-31
DanielWEvans1982,

Glad it worked. If you would, please mark the thread SOLVED via the "Thread Tools" link at the top right of the original post. It will help others with the same problem find the solution.

Rubi1200,

Thanks for the link. I am going to put a note at the top of "Grub2 Basics" about this Wubi problem. I'll mention the solution and provide the bug link.

---

