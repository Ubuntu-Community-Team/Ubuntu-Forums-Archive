---
title: "Need help uninstalling ubuntu on a dual boot system"
date: 2006-05-05
forum: Hardware &amp; Laptops
---

### Post by boris yeltsin on 2006-05-05
Not sure if this should go here, but here is the situation:

I have a Gateway Laptop, without a floppy drive, running Windows XP and ubuntu on a dual boot using the grub boot thing. (Sorry, my terms are rusty.) Anyways, the problem I have is that gateway has supplied me with a "System Recovery DVD" instead of a proper Windows XP CD. This disk seems to work like a regular windows disk and I installed the Recovery Console, although this seemed to acomplish nothing. My question is, how do I repair my Master Boot Record, using this CD, and then removing Ubuntu. (I assume once I repair the MBR I can just delete Ubuntu's partitions etc so the latter part isn't that big of a problem.

Thanks for any help you can offer.

---

### Post by Qrk on 2006-05-05
run the command:

fixmbr

from the recovery console.

---

### Post by encompass on 2006-05-05
Sure... to erase a Master boot Record with dos/windows... boot to console or safe mode or something like that... and try this...
[http://www.textfiles.com/hacking/MICROSOFT/dosundoc.txt](http://www.textfiles.com/hacking/MICROSOFT/dosundoc.txt)
> fdisk /mbr
But don't come too kill me if it doesn't work.

---

### Post by bluevoodoo1 on 2006-05-05
This might of use as well..

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by m.musashi on 2006-05-06
I don't mean to be all pesimistic but fixmbr did nothing for me but make the situation worse. Perhaps I'm just an idiot but when I had a similar problem I ended up doing a new reinstall. Give the above suggestions a try and if you are lucky something will work. However, I suggest backing up anything you don't want to lose and just doing a clean install. The cd from gateway should allow you to reinstall windows (or maybe there is a ghose image on the drive and a restore utility - check the manual or call gateway tech support). If all else fails, just make sure you backup and then reformat the whole drive and reinstall. If there is a restore partition make sure you don't wipe it. I hate to say it, but gateway tech support should be able to walk you through this. When you reformat, Ubuntu will be gone (sniff, sniff).

Conversely, if you are not short on drive space you can leave ubuntu there and just not boot into it. Perhaps someday you will find a use for it. I find it very useful for acquiring stuff from dubious web sites ;).

---

### Post by boris yeltsin on 2006-05-06
[QUOTE=m.musashi]I don't mean to be all pesimistic but fixmbr did nothing for me but make the situation worse. Perhaps I'm just an idiot but when I had a similar problem I ended up doing a new reinstall. Give the above suggestions a try and if you are lucky something will work. However, I suggest backing up anything you don't want to lose and just doing a clean install. The cd from gateway should allow you to reinstall windows (or maybe there is a ghose image on the drive and a restore utility - check the manual or call gateway tech support). If all else fails, just make sure you backup and then reformat the whole drive and reinstall. If there is a restore partition make sure you don't wipe it. I hate to say it, but gateway tech support should be able to walk you through this. When you reformat, Ubuntu will be gone (sniff, sniff).

Conversely, if you are not short on drive space you can leave ubuntu there and just not boot into it. Perhaps someday you will find a use for it. I find it very useful for acquiring stuff from dubious web sites ;).[/QUOTE]


I backed up my critical files and did the "fixmbr" and everything works fine. I will end up re-installing Ubuntu sometime, however I'm sticking with windows for the next little while. I had Fedora Core 4 before Ubuntu, and I must say Ubuntu was alot better.

Thanks for all your help. I ended up borrowing a freind's XP CD to run the Recovery Console.

---

