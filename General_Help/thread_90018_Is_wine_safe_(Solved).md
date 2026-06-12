---
title: "Is wine safe? (Solved)"
date: 2005-11-14
forum: General Help
---

### Post by clackey on 2005-11-14
Hello, I just installed wine, and configured it with sidenet-wine-configuration. all windows programs i've installed work great with no problems; however i have one question:

I know Windows and some of it's programs can be very unsafe/virus-prone, and I'm wondering if by using windows programs with wine (or even just by configuring it using the sidenet method), that I might be putting my machine at risk somehow? If anyone has an opinion or any facts, it would be greatly appreciated. 
I'm loving how well my windows programs are working under wine, I just wanna make sure that by doing so I'm not somehow compromising my system... 

Thanks!

---

### Post by manicka on 2005-11-14
Window programs are pretty much just as vulnerable under wine as they are in Windows. Explorer is still explorer no matter how you look at it or make it run. 
It is unlikely that they will effect the Linux side of things though.

---

### Post by 23meg on 2005-11-14
Since wine itself is non-MS code, vulnerabilities caused by flaws in the Windows API may not exist in wine, so in theory it can even be safer than running the application natively. If the application itself is poorly coded and relies on other poorly coded MS (or other) libraries it will be just as vulnerable as it would be when running natively.

---

### Post by ltmon on 2005-11-14
Have a look at this article... I suspect the tests were more for fun than anything else, but it's an interesting read:

[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

---

### Post by clackey on 2005-11-14
haha, that article was classic. well, i guess the conlusion, then, is that apps running under wine can be unsafe, but only really to other wine apps or wine configurations?
puts my mind at ease anyway, thanks alot!

---

### Post by SickTwist on 2005-11-14
Since Wine is run as a normal user, it would not be able to destroy system files in Linux. I image the worst damage it could do would be to delete all of the files in the Wine user's home directory.

I guess if you wanted to be really safe you could create a new user account that you would use whenever you wish to run Wine. It is probably excessive but it is an option.

---

### Post by Malphas on 2005-11-14
[QUOTE=clackey]haha, that article was classic. well, i guess the conlusion, then, is that apps running under wine can be unsafe, but only really to other wine apps or wine configurations?
puts my mind at ease anyway, thanks alot![/QUOTE]
I hope you didn't derive your conclusion from that article.  Bare in mind that those viruses would have to be intentionally installed, they couldn't just install and run themselves on Ubuntu without you setting them up to work through WINE.

---

### Post by clackey on 2005-11-14
not just the article, the previous replies to it referred to potential damage to wine and it's programs, not necessarily anything outside of that. I understand that there still might be risks, but thus far no one has replied with their experiences of having wine screw up ubuntu through holes in the programs it runs...

and when you say:

> Bare in mind that those viruses would have to be intentionally installed, they couldn't just install and run themselves on Ubuntu without you setting them up to work through WINE.

do you mean that there's even less chance of viruses like those screwing up linux through wine than demonstrated in that article (unless intentionally installed)?

---

