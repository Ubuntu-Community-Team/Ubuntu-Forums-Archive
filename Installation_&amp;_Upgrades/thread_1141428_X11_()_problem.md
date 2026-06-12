---
title: "X11 (?) problem"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by fronty on 2009-04-28
Hi,

I installed two days ago latest Kubuntu to thumb drive. I didn't have any CD's with me, so I installed it using VMware Player. Kubuntu boots fine from it, but mouse and keyboard don't work with X. Keyboard is Microsoft's wireless keyboard, mouse is HP's PS/2 wheel mouse. Keyboard works fine in recovery shell. I don't know about mouse, didn't find anything like moused in FreeBSD

I ran Xorg -configure, but it didn't work with configure file it created. I added InputDevice sections from it to original configuration file and wrote new ServerLayout, but nothing changed.

Does someone have any kind of idea how to fix this?

J

---

### Post by fronty on 2009-04-30
This forum needs built in bumping system.

---

### Post by Monsieur Gonzalez on 2009-04-30
Can you look for any errors/clues in Xorg's logs? (located in /var/log/Xorg.0.log)

---

### Post by fronty on 2009-05-02
After I read the log, I added Option "AllowEmptyInput" "false" to my xorg.conf and everything seemed to start to work. Keyboard's repeat rate was too high, I couldn't write even password like "aaabbbccc" and backspace didn't work, I had to use Control+U. I booted to recovery shell and tried to look everywhere for something related to keyboard repeat rate. When I start KDM from recovery shell, repeat rate is good, but it won't let me log in with any user. When I go straight to KDE, everything seems ok. But now when I try normal boot, keyboard and mouse won't work anymore. Now when I think, I don't know does the whole thing hang or not, it didn't even get to login screen. I'm not sure, must check it tomorrow.

[This](www.kopteri.net/koti/joonas.hilska/Xorg.0.log) is log X produced in time before I disabled AllowEmptyInput in xorg.conf, now it doesn't write anything to log file, even after I added Option "Log" "flush".

---

### Post by fronty on 2009-05-03
It seems to me that sometimes kdm freezes before login screen appears and sometimes not.

---

### Post by fronty on 2009-05-10
I created Live USB and installed Kubuntu via it and things still don't work.

AKA bump

---

