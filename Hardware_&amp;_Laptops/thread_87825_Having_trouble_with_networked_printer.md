---
title: "Having trouble with networked printer"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by Noah0504 on 2005-11-08
I have a HP PSC 1210 printer hooked up to my Windows XP machine.  I attempted to setup the printer over the network with Ubuntu.  All seemed to go well and I tried to print a test document in Gedit.  I waited and began to hear the printer, however, nothing was ever printed.  Now when I attempt the same thing, nothing happens at all.

Any ideas?

---

### Post by frost_ad on 2005-11-09
I have this exact same problem. I have a PSC 1210 running on my XP desktop and I can't print from my ubuntu laptop. I also managed to get some noise out of the printer. Also, I did get a bunch of print jobs stacked up when I looked at the printer in windows.

Any help would be VERY appreciated. I have been scouring the forums and irc for an answer. If I find one I will definitely post it here.

---

### Post by terrien on 2005-11-09
I had the exact same problem with the exact same printer... I was never able to find a decent solution, but I do remember something about MS's Services for Unix needing to be installed in order for it to work. I never tried it personally, but maybe it'll work for you.

[http://www.microsoft.com/windowsserversystem/sfu/default.mspx](http://www.microsoft.com/windowsserversystem/sfu/default.mspx)

---

### Post by Noah0504 on 2005-11-09
[QUOTE=frost_ad]I have this exact same problem. I have a PSC 1210 running on my XP desktop and I can't print from my ubuntu laptop. I also managed to get some noise out of the printer. Also, I did get a bunch of print jobs stacked up when I looked at the printer in windows.

Any help would be VERY appreciated. I have been scouring the forums and irc for an answer. If I find one I will definitely post it here.[/QUOTE]
Yep, that's *exactly* my problem.

Well, I suppose if I can't fix this problem, it will be the only flaw I've really discovered in Ubuntu.  Hmm, anyway, maybe someone will come along with a solution.  I think I may try installing the Windows Services for Unix.  I'll report back once I have.

---

### Post by Noah0504 on 2005-11-11
Okay, I've solved the problem.

From your Windows machine (I have XP), select Printers and Faxes, right click on your shared printer, go to ports, and make sure "Bi-directional
support" is disabled.

I'm now happily printing from my Ubuntu laptop.  Let me know how it works out for you.

---

### Post by frost_ad on 2005-11-12
Hell yes! Thanks a lot. I finally have got mine to work now too. How/Where did you find this solution.

---

### Post by Noah0504 on 2005-11-12
[QUOTE=frost_ad]Hell yes! Thanks a lot. I finally have got mine to work now too. How/Where did you find this solution.[/QUOTE]
I ran a search on Google (about the 100th one on the problem) and found a post on these forums that gave the same solution for a different printer.  I thought I'd give it a try and what would you know, it worked!

---

### Post by drpatt on 2005-11-17
[QUOTE=Noah0504]Okay, I've solved the problem.

From your Windows machine (I have XP), select Printers and Faxes, right click on your shared printer, go to ports, and make sure "Bi-directional
support" is disabled.

I'm now happily printing from my Ubuntu laptop.  Let me know how it works out for you.[/QUOTE]

Not working here. I have Win2k. My DeskJet 810C is on LPT1 on the Win box. The Bi-di support checkbox is greyed out and is not selected. The printer doesn't even make noise; I just get a timeout error.

Everything else is working pretty well, but my experiecne with Linux over the years has been this; it's always *something*.

---

### Post by janrinok on 2005-11-22
I'm a bit confused with your comments on 810C.  Is it connected to your ubuntu box or to your win2k box?  Are you trying to share your printer over a network?  If it is connected to the ubuntu box, have you got a USB cable?  My 810 connected perfectly using USB.

---

