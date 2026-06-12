---
title: "logitech harmony one on ubuntu 10.10"
date: 2010-12-22
forum: Hardware
---

### Post by surfer on 2010-12-22
i followed [this]("http://ubuntuforums.org/showthread.php?t=781059") thread but could not get concordance or congruity to connect to it... any ideas?

---

### Post by odinb on 2010-12-22
Since you ask a generic question without specifying what or where it went wrong, or what error-messages you experience, it is hard to answer specifically.

Here are however something to try:

Have you tried the manpages for concordance?
[http://manpages.ubuntu.com/manpages/maverick/man1/concordance.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/concordance.1.html)

...or even the concordance webpages?
[http://www.phildev.net/concordance/index.shtml](http://www.phildev.net/concordance/index.shtml)

These webpages also offers a link to a GUI for concordance:
[http://sourceforge.net/projects/congruity/](http://sourceforge.net/projects/congruity/)


Good luck!

---

### Post by surfer on 2010-12-23
you are right, of course. i will update my post as soon as i get home...

---

### Post by surfer on 2010-12-23
i installed Concordance 0.23 from

```
deb http://ppa.launchpad.net/mathieu-tl/ubuntu maverick main
```

then:
```
$ sudo concordance -i
[sudo] password for ***: 
Concordance 0.23
Copyright 2007 Kevin Timmerman and Phil Dibowitz
This software is distributed under the GPLv3.

Requesting Identity:  50%          ERROR: failed to requesting identity
Failed with error 1

```

and as condordance can not identify the device, there is nothing congruity can do with it.

---

### Post by odinb on 2010-12-23
You are using a Harmony one?

Could it be because it is not supported?

[http://www.phildev.net/concordance/supported_models.shtml](http://www.phildev.net/concordance/supported_models.shtml)

I use XP in a Virtualbox to do my harmony upgrades.

---

### Post by surfer on 2010-12-24
you're right again...

hmmm... i am completely windows free... will have to try to configure it on someone else's computer.

thanks!

---

