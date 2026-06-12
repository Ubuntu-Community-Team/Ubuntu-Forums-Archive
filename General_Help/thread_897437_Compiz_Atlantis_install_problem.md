---
title: "Compiz Atlantis install problem"
date: 2008-08-22
forum: General Help
---

### Post by zx6r1033 on 2008-08-22
I followed the directions on [This thread]("http://ubuntuforums.org/showthread.php?t=601957") on how to install Atlantis. I copy/pasted everything so I know it was followed to the letter. 

When I get to "Make" and "Make install", this is what I get...



```
compiling : swim.c -> build/swim.loIn file included from swim.c:94:
atlantis-internal.h:89:18: error: cube.h: No such file or directory
In file included from swim.c:94:
atlantis-internal.h:113: error: expected specifier-qualifier-list before ‘DonePaintScreenProc’
swim.c: In function ‘FishTransform’:
swim.c:100: warning: implicit declaration of function ‘glTranslatef’
swim.c:100: warning: nested extern declaration of ‘glTranslatef’
swim.c:101: warning: implicit declaration of function ‘glRotatef’
swim.c:101: warning: nested extern declaration of ‘glRotatef’
swim.c: In function ‘FishMiss’:
swim.c:248: error: ‘AtlantisScreen’ has no member named ‘numFish’
swim.c:252: error: ‘AtlantisScreen’ has no member named ‘fish’
swim.c:252: error: ‘AtlantisScreen’ has no member named ‘fish’
swim.c:253: error: ‘AtlantisScreen’ has no member named ‘fish’
swim.c:253: error: ‘AtlantisScreen’ has no member named ‘fish’
swim.c:254: error: ‘AtlantisScreen’ has no member named ‘fish’
swim.c:254: error: ‘AtlantisScreen’ has no member named ‘fish’
swim.c:259: error: ‘AtlantisScreen’ has no member named ‘fish’
swim.c:261: error: ‘AtlantisScreen’ has no member named ‘fish’
swim.c:265: error: ‘AtlantisScreen’ has no member named ‘fish’
swim.c:269: error: ‘AtlantisScreen’ has no member named ‘fish’
swim.c:273: error: ‘AtlantisScreen’ has no member named ‘fish’
swim.c:273: error: ‘AtlantisScreen’ has no member named ‘fish’
make: *** [build/swim.lo] Error 1

```



Any ideas?  Writeups with code on how to install Atlantis are rather hard to come by.

---

### Post by zx6r1033 on 2008-08-22
Problem solved... I found a compilation by another member that included atlantis. :D

---

### Post by Wootyeah on 2008-08-24
Could you link it?

---

### Post by zx6r1033 on 2008-08-25
Absolutely. 


[Thread]("http://ubuntuforums.org/showthread.php?t=820802&highlight=atlantis")


Took me just a few seconds to install it that way.


EDIT:

Oh yeah, for those who don't already know how to install it...

Open your terminal. Change your directory to the folder where the file was downloaded. Then type "sh compizplugins.sh".  Do not install as root (As per the authors explicit instructions.)

That is all there is to it.  He really did a great job on that one, IMO.

---

### Post by dodophoenix on 2008-10-05
I've got the same errs mentioned in first post.
I've found a atlantis modification here. 
[http://forum.compiz-fusion.org/archive/index.php/t-4263.html](http://forum.compiz-fusion.org/archive/index.php/t-4263.html)
And i build it from 
git clone git://anongit.opencompositing.org/users/metastability/atlantis2
It worked perfect.

---

### Post by binbash on 2008-10-05
> **zx6r1033 said:**
> Absolutely. 


[Thread]("http://ubuntuforums.org/showthread.php?t=820802&highlight=atlantis")


Took me just a few seconds to install it that way.


EDIT:

Oh yeah, for those who don't already know how to install it...

Open your terminal. Change your directory to the folder where the file was downloaded. Then type "sh compizplugins.sh".  Do not install as root (As per the authors explicit instructions.)

That is all there is to it.  He really did a great job on that one, IMO.

I was looking for a pre compiled screensaver plugin.This solved my problem also thanks.

---

