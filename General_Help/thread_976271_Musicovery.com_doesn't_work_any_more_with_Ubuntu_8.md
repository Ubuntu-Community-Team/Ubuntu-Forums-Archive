---
title: "Musicovery.com doesn't work any more with Ubuntu 8.10"
date: 2008-11-09
forum: General Help
---

### Post by dsi0743 on 2008-11-09
Hi.
I listen often music on [Musicovery.com]("http://musicovery.com").
I got no probem with Ubuntu 8.04 and Firefox 3
But, after migration to Ubuntu 8.10, the site
doesn't work any more.
I can't click to get connected for instance.
I tried with Epiphany and Opera with no more success.
I just can use it with IE on XP using VirtualBox :confused:

I use pluginflash 10 from Adobe.

An idea ?

Thx

---

### Post by loskobosko on 2008-11-14
I get the same problem, too. I am not able to interact with musicovery, my clicks are in vane.

---

### Post by keto123 on 2008-11-17
Same problem here. Musicovery does not accept my mouse clicks. I'm running standard 64-bit Ubuntu 8.10 installation.

It can be solved (sort of) by navigating to flash movie directly: [http://www.musicovery.com/musicovery.swf](http://www.musicovery.com/musicovery.swf). That is apparently some older version of musicovery, but it works.

However, I did not find a way to login and listen to music in high quality.

---

### Post by ckomurlu on 2008-11-18
Same problem. Current version appears in firefox window but I cannot click anything, meanwhile everything is okay in the older version. Maybe we can report this problem to musicovery.com. People, there, can fix this bug since it doesn't occur on each site having flash. However, it might be a good idea that all of us mail them individually. This way, they can take this case into consideration.

---

### Post by keto123 on 2008-11-20
This is a HTML/CSS bug.

The problem disappeared when I changed this line of html code:
<div style="position: absolute; z-index: -40;">
to this:
<div style="position: absolute; z-index: 0;">

I reported the problem to musicovery. Hopefully, they will fix the page soon. 

In the meantime, you can install this greasemonkey script, which rewrites html automatically (install greasemonkey firefox addon first):
[http://userscripts.org/scripts/show/37257](http://userscripts.org/scripts/show/37257)

Happy listening! :)

---

### Post by Slodeine on 2008-11-26
The script doesn't seem to be working for me.

EDIT: My bad, just needed to restart the browser.   Working perfectly now, thanks!

---

### Post by John Deas on 2008-12-02
In the meantime, before the fix, use this address :

[http://www.musicovery.com/musicovery.swf](http://www.musicovery.com/musicovery.swf)

Which also seem to remove advertising...

---

### Post by John Deas on 2008-12-02
My bad, the solution has already been proposed :)

---

### Post by vinx on 2009-02-05
Is there a way to fix this with greasemonkey? I think this can be doen, by selecting the first div and replacing the style.

I'm  very new to greasemonkey and only succeeded to let my news-page say the news was old and obsolete, so can one of you help us out?

---

### Post by SolRebel on 2009-03-19
> **vinx said:**
> Is there a way to fix this with greasemonkey? I think this can be doen, by selecting the first div and replacing the style.

I'm  very new to greasemonkey and only succeeded to let my news-page say the news was old and obsolete, so can one of you help us out?

Post #5 was on the right track, but even after rebooting my browser, the fix seems to be obsolete now. Any one else out there have a fix for us?

---

### Post by SolRebel on 2009-03-20
Turns out I just needed to reboot the computer completely. Works great now! Thanks!

---

### Post by simormate on 2009-09-26
the easiest solution is by installing the user agent switcher addon in firefox and then switching to internet explorer. with this, you can register and login without problems.

seems that the musicovery site banned ubuntu.

---

### Post by vishal733 on 2010-04-07
Just install "Firebug" in firefox... it's a webpage editor for firefox.

then open the musicovery.com webpage, and make the change as was suggested earlier in Post 5.

the only problem with doing it using firebug is that i need to do it everytime i open the webpage..

---

### Post by vishal733 on 2010-04-07
> **simormate said:**
> the easiest solution is by installing the user agent switcher addon in firefox and then switching to internet explorer. with this, you can register and login without problems.

seems that the musicovery site banned ubuntu.

Moreover, the IE tab doesn't work under Ubuntu.. so the above solution is not feasible...

---

