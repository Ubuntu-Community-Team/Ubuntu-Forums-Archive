---
title: "Network printing prints in reverse?"
date: 2005-11-09
forum: Hardware &amp; Laptops
---

### Post by darthsabbath on 2005-11-09
Hey guys,

Interesting little problem here... just did a clean install of Breezy, on the PC my printer is connected to.  Both it and my notebook are dual booting Breezy and Windows XP.  My wife's computer uses Windows XP Pro.  The printer is an HP 5740.  

The issue is... well... when printing from either of the remote Windows boxes, the print comes out in reverse... such as

[RIGHT]tseT tseT tseT[/RIGHT]

rather than

Test Test Test

Printing from Ubuntu, both remotely and locally, works fine.  Printing from Windows XP locally works fine.  If I have the PC the printer is hooked up to booted into Windows XP, and print remotely, it works fine from any computer.  It's just printing remotely from Windows XP, to Ubuntu, prints in reverse.

I've Googled for the answer to no avail, and don't even know where to begin.  The same printer drivers are used for both printing to XP and Ubuntu, so... I have no freakin' clue.

Any hints? :D If I need to post any logs/config files, let me know what ya need.

Phil

---

### Post by glauber_ananda on 2006-04-28
[QUOTE=darthsabbath]Hey guys,
The issue is... well... when printing from either of the remote Windows boxes, the print comes out in reverse... such as

[RIGHT]tseT tseT tseT[/RIGHT]

rather than

Test Test Test
Phil[/QUOTE]

Hi fill, I got the same problem on my HP dj3745 and solved this way:

Dowloaded the Adobe generit postscript driver here (Brazilian Portugues - you should try the english version): [http://www.adobe.com/support/downloads/detail.jsp?ftpID=1495](http://www.adobe.com/support/downloads/detail.jsp?ftpID=1495)

I Installed the drivers on my windows machine, filling the printer location field like this: [http://myubuntuhost:631/printers/Deskjet-3740](http://myubuntuhost:631/printers/Deskjet-3740)

Then I selected the generic postscript driver and, yeah, it worked.

Of course, my cups server on my ubuntu machine was listening on port 631.

I hope it will work with you.

Sorry for my bad english, I hope you understand me =(

-- Glauber Machado Rodrigues

---

### Post by glauber_ananda on 2006-04-28
[QUOTE=glauber_ananda]Hi fill, I got the same problem on my HP dj3745 and 
Dowloaded the Adobe generit postscript driver here (Brazilian Portugues - you should try the english version): [/QUOTE]

Hi Phill, here is the english version of the driver =D

[http://www.adobe.com/support/downloads/detail.jsp?ftpID=1500](http://www.adobe.com/support/downloads/detail.jsp?ftpID=1500)

---

### Post by BoyOfDestiny on 2006-11-30
> **glauber_ananda said:**
> Hi Phill, here is the english version of the driver =D

[http://www.adobe.com/support/downloads/detail.jsp?ftpID=1500](http://www.adobe.com/support/downloads/detail.jsp?ftpID=1500)


Thank you, this solved it for my home network. Although I think another fix would have worked eventually (having only GNU/Linux machines, working on it... ;) )

---

