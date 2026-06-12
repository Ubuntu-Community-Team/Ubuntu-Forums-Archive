---
title: "Fn + Brightness-Key"
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by spacecookie on 2006-08-14
I have a Compaq Evo N620c wich has fn-key-shortcuts (like brightness control, enable/disable wlan etc..). The Problem is the shortcuts work while i am booting, but after booting they no longer work.

Searched all forums i found but no answer. Seems to be a common problem with N600+, but no one has any solution.

Any suggestion?

---

### Post by philcolbourn on 2007-08-11
A friend has the same machine as do I. He (and I guess I, thought I have not tested it) has the same problem as you.

However, I had an upgraded feisty from Dapper I think. Before I did a 'clean' install from a feisty CD, my brightness worked. There was no on-screen-display but I could increase and decrease the brightness. I could also operate the internal/external screen (although I didn't get it to actually work a monitor).

Now after the clean install, I can not control screen brightness.

---

### Post by rosegarden78 on 2008-01-19
Try typing the following command in a terminal:

xgamma -gamma 0.75

If that doesn't work you need to install xgamma from the repos.

I have posted my own solution here on setting it up:

[http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

---

