---
title: "How to Uninstall an application that has been compiled from source?"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by dushyantkum on 2009-01-09
Hey.
Well I installed G2ipmsg from source by configuring and installing it.
Now I am in a fix. I cant remove it. It has been behaving weirdly over last few days. I tried to reinstall it, it did without any glitch but the problem seems to persist.

Hence, I want to know which command or method will remove it from my system completely or should I go about deleting individual files one by one and then reinstalling it?

Thanks in advance

---

### Post by taurus on 2009-01-09
In the same directory that you ran the ./config && make && sudo make install, just run the uninstall to remove it.

```
sudo make uninstall
```

---

### Post by donkyhotay on 2009-01-09
Did you use scons or make to install it? The only way I know to remove something installed with scons is to remove the files manually (which is a pain). Often though you can do
```
sudo make uninstall
```
if it was done through make. Take a look at this link for more information
[http://www.linuxquestions.org/questions/linux-newbie-8/source-uninstall-with-make-uninstall-howto-230225/](http://www.linuxquestions.org/questions/linux-newbie-8/source-uninstall-with-make-uninstall-howto-230225/)

---

### Post by dushyantkum on 2009-01-10
Hey,
I did sudo make uninstall..it removed everything. But the software is behaving weirdly even after fresh install..maybe some bug in g2ipmsg..weird, it worked nicely for sometime, maybe some upgrade or something screwed it..

nway, thanks guys

---

