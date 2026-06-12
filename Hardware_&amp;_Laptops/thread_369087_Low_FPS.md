---
title: "Low FPS?"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by unimatrix on 2007-02-24
Hello.
I have a GeForce 6600 with 256MB of RAM on an AMD64, running Ubuntu 6.10.
I've been doing some tests on my machine using: ```
glxgears -printfps
```
And the results I've been getting were around 500FPS when I used GDM (Gnome Desktop Manager). Later I switched to KDM (KDE Desktop Manager), and now I'm getting around 650FPS. But whenever I turn on Beryl-manager i get around 1400FPS.

Is this normal?
I would love to see some comparaison with somebody who has a similar configuration.
Normally it wouldn't bother me, because 650FPS isnt bad... i guess? But my Cedega test fails due to not enough FPS. On the other hand it doesn't fail when i'm running Beryl. (the funny thing is games and such run slower with beryl on).

---

### Post by louis_nichols on 2007-02-24
Beryl does indeed, amazingly enough, give you more fps on the desktop. However, it will interfere with running games and such, so it's better turned off in those cases. For now, at least.

---

### Post by chewearn on 2007-02-24
I have opposite results: about 630fps with beryl on, and 1300fps off.  The glxgears animation was choppy with beryl on, but very smooth when off.  Anything to do with wrong beryl settings?

---

### Post by unimatrix on 2007-02-24
> 
I have opposite results: about 630fps with beryl on, and 1300fps off. The glxgears animation was choppy with beryl on, but very smooth when off. Anything to do with wrong beryl settings?


That was exactly why I was worried.
This is the way it should work... logically. Beryl shouldn't disburden your machine. Or well, I wouldn't mind having 1300FPS+ in both cases.

What kind of drivers are you using?
I'm using nVidia beta drivers version 1.0.9742.

---

### Post by chewearn on 2007-02-24
I have integrated nVidia GeForce 6150.  I'm using released driver version 1.0-8776.

---

