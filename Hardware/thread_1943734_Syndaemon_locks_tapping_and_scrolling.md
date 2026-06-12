---
title: "Syndaemon locks tapping and scrolling"
date: 2012-03-20
forum: Hardware
---

### Post by fidolip on 2012-03-20
Hi,

Since ubuntu's unity started to be too heavy for my little Acer Aspire One I decided to switch to lubuntu. Everything works pretty much as it used to (just a tad faster), with one exception - touchpad remains active while I type and there is no option to change it in Settings-Keyboard and Mouse.

So, I tried to run syndaemon, but it behaves weird - it does disable tapping and scrolling (with -t parameter), but it doesn't re-enable it after the time specified by -i parameter. What's more, after killall syndaemon, tapping and scrolling remains disabled. I'm confused.

Has anyone encountered similar issue?

---

### Post by fidolip on 2012-03-26
OK, solved it. I didn't put the at sign (@) in front of the line in the autostart file. now it works flawlessly.

thanks to Walter Lapchynski from Lubuntu Official Facebook group.
[http://www.facebook.com/groups/lubuntu.official/](http://www.facebook.com/groups/lubuntu.official/)

---

