---
title: "Epson Stylus CX5400 not detected"
date: 2005-11-10
forum: Hardware &amp; Laptops
---

### Post by clackey on 2005-11-10
Hello, I'm having a problem with my Epson Stylus CX5400 all-in-one scanner/printer/blah, blah, blah (hooked up by USB)... When I'd been using Warty, it was detected and recognized right away, it worked great; however, now i've upgraded to Breezy, and although the printer model is listed as a supporeted printer, it's not being detected at all. 
I've gone into the "New Printer" dialog and looked under "use a detected printer", but it only sais "no printer detected".
Hope someone might have some insight into the problem?
Thanks in advance!

PS. I've searched the forums for threads with the same topic, however, the only problem others have are with scanning capabilities, thus no solutions to the printing problem... The contraption scans just fine, it just won't print.

---

### Post by clackey on 2005-11-10
Nevermind, I found out what the problem was and fixed it. it was due to the cupsys bug, in which it will not recognize a new printer without having to be restarted. to restart cupsys to recognize a plugged-in printer, just use this:

```
sudo /etc/init.d/cupsys restart
```

it should work fine after that! hope this helps for anyone who ever has the same problem!

---

### Post by escobar on 2005-11-19
[QUOTE=clackey]Nevermind, I found out what the problem was and fixed it. it was due to the cupsys bug, in which it will not recognize a new printer without having to be restarted. to restart cupsys to recognize a plugged-in printer, just use this:

```
sudo /etc/init.d/cupsys restart
```

it should work fine after that! hope this helps for anyone who ever has the same problem![/QUOTE]

I've NEVER gotten my printer to work on any distribution, period. I finally decided to stop being lazy and give it a go. I use the same model as you, worked like charm. I wonder if this is a bug? Thanks alot.

---

### Post by clackey on 2005-11-20
glad it worked for you, too!

... and yes, it's listed as a bug on a certain bug-report page, i forget exactly what the URL is, but i know that the developers are working on it.

---

### Post by Cheule on 2005-11-20
[QUOTE=clackey]glad it worked for you, too!

... and yes, it's listed as a bug on a certain bug-report page, i forget exactly what the URL is, but i know that the developers are working on it.[/QUOTE]

Excellent, I'll give it a try myself. I have a CX5200, and like you guys the printer was in the manual list but never detected automatically. I'll let you know how it went :)

---

### Post by Cheule on 2005-11-20
Excellent, it worked a treat, thank you!:KS

---

