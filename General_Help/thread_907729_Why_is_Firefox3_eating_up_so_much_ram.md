---
title: "Why is Firefox3 eating up so much ram?"
date: 2008-09-01
forum: General Help
---

### Post by logos34 on 2008-09-01
I just decided to upgrade to the latest Firefox/swiftweasel 3.0 (I was waiting for all my addons/plugins to be supported), but I have noticed that the memory footprint is HUGE--like 25-30% of ram!  WTF is going on?  Same settings as 2.0, yet the older version toips out at ~22 %.  Can't figure it out.  I'm not doing anything differenty, don't have zillions of tabs open.  

Anyone noticed this?  Do the browser have a mem leak or something?

---

### Post by mrsteveman1 on 2008-09-01
I've noticed it uses quite a bit less actually, i've had hundreds of tabs open at the same time and it's been fine for me.

---

### Post by prshah on 2008-09-01
> **logos34 said:**
> I just decided to upgrade to the latest Firefox/swiftweasel 3.0 but I have noticed that the memory footprint is HUGE--like 25-30% of ram!

```
top -b -d 1 -n 1 | head -7 | tail -1 &&[color=red] top -b -d 3 -n 10 | grep -i firefox[/color]
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
18721 user  20   0  215m  89m  21m S    0  8.9   1:44.49 firefox            
18721 user  20   0  215m  89m  21m S    4  8.9   1:44.61 firefox            
18721 user  20   0  215m  89m  21m S    5  8.9   1:44.75 firefox            
18721 user  20   0  215m  89m  21m S    2  8.9   1:44.81 firefox            
18721 user  20   0  215m  89m  21m S    5  8.9   1:44.97 firefox            
18721 user  20   0  215m  89m  21m S    1  8.9   1:44.99 firefox            
18721 user  20   0  218m  89m  21m S    4  9.0   1:45.11 firefox            
18721 user  20   0  215m  89m  22m S   13  8.9   1:45.51 firefox            
18721 user  20   0  215m  89m  22m S    4  8.9   1:45.64 firefox            
18721 user  20   0  215m  89m  22m R   16  8.9   1:46.11 firefox
``` This is with about 15 tabs open, and it seems reasonable to me; Note while virtual memory is 215m, actual RAM in use is only 89m (out of 1Gb).

btw, the current version is 3.0.1.

Note I have no flash images running right now in any of the tabs; it will be interesting to see what happens when I load a flash heavy site.

btw2, the real work is done by the command in red; the rest is just window dressing.

---

### Post by logos34 on 2008-09-02
> $ top -b -d 3 -n 10 | grep -i swiftweasel
 9458 user1     20   0  3944  556  464 S  0.0  0.1   0:00.00 swiftweasel                                       
 9460 user1     20   0  3944  600  484 S  0.0  0.1   0:00.00 swiftweasel                                       
 9467 user1     20   0  409m  69m  20m S  0.0 14.5   0:22.22 swiftweasel-bin                                   
 9467 user1     20   0  409m  69m  20m S  0.3 14.5   0:22.23 swiftweasel-bin
That;s with all the addons disabled and one tab (no flash) open.  

I just don't get it.  But if only that was it. Instead it goes way into the 20-25% range.  FF3 is even worse as I said.  I checked prefs--cache is turned down to like 5 mb.  

What could it be?

---

### Post by baggins on 2008-09-02
I had some of the same problems right after I upgraded to Hardy (and thus firefox3). I have a theory that some setting in the firefox profile I kept from firefox2 made problems for firefox3
I gave up on finding the cause, exported my bookmarks moved the firefox profile, and started over with a clean .mozilla/firefox/ 

It took some time to get everything back the way I want, but I think it runs better now. 
Unfortunately I don't have any hard data to back the claim up, but it sure feels snappier :)

-- Jon

---

### Post by logos34 on 2008-09-03
> **baggins said:**
> I had some of the same problems right after I upgraded to Hardy (and thus firefox3). I have a theory that some setting in the firefox profile I kept from firefox2 made problems for firefox3
I gave up on finding the cause, exported my bookmarks moved the firefox profile, and started over with a clean .mozilla/firefox/ 

It took some time to get everything back the way I want, but I think it runs better now. 
Unfortunately I don't have any hard data to back the claim up, but it sure feels snappier :)

-- Jon

that just gave me an idea: i'll try making a new user profile. maybe that'll do the trick

---

### Post by todak on 2008-09-03
Look here: [http://kb.mozillazine.org/Browser.cache.memory.capacity](http://kb.mozillazine.org/Browser.cache.memory.capacity) and here: [http://kb.mozillazine.org/Browser.cache.memory.enable](http://kb.mozillazine.org/Browser.cache.memory.enable) to see if this will help you.

---

### Post by logos34 on 2008-09-04
> **todak said:**
> Look here: [http://kb.mozillazine.org/Browser.cache.memory.capacity](http://kb.mozillazine.org/Browser.cache.memory.capacity) and here: [http://kb.mozillazine.org/Browser.cache.memory.enable](http://kb.mozillazine.org/Browser.cache.memory.enable) to see if this will help you.

no, that's not it--I implemented that tweak a long time ago (turned it down to like 8 mb)...

I just ripped everything out and reinstalled swiftweasel 2.0.0.14, adding addons one at a time, leaving out a few I really don't need.   Better--starts off ~50 mb, but soon climbs to ~70, tops out ~105 mb.  That's with flashblock enabled and only like 3 tabs open.  But I'm sorry, that's still unacceptable in my book...something has got to be done about these memory hog browsers.  I wish there was a viable alternative to FF, but there isn't (and Opera doesn't cut it for me)

---

