---
title: "Upgrade manager: packages can't be parsed"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by nickolasemp on 2009-07-22
First of all, I don't know where to go to file the problem...

Second of all, is there a solution? I can;t upgarde to anything let alone a new program...
[[img=http://img33.imageshack.us/img33/7128/problemg.th.jpg]](http://img33.imageshack.us/i/problemg.jpg/)

edit:So far the only solution I've come up to is to # every pavkege that was causing the problem. But why all of sudden this change? Even wine does not find the sector-header thing...

---

### Post by tommcd on 2009-07-22
The screenshot you posted says you have duplicate sources for the ppa.launchpad.net repos in your sources.list. 
Post the output of your /etc/apt/sources.list.

---

### Post by Partyboi2 on 2009-07-22
Hi, can you open a terminal (Applications>Accessories>Terminal) and post your sources.list
```
cat /etc/apt/sources.list
``` looks like you have a duplicate entry.

---

### Post by nickolasemp on 2009-07-22
That is weird, i can;t seem to find anything that is duplicate...

Result of cat /etc/apt/sources.list:

[[IMG]http://img300.imageshack.us/img300/913/problemood.th.jpg[/IMG]](http://img300.imageshack.us/i/problemood.jpg/)

---

### Post by nickolasemp on 2009-07-22
In case someone else in the future has the same problem:

Disabling(#) and then enabling(removing) them from gedit while running synaptic (and not update manager) and reloading in between seems to fix the problem...

What the problem really was, I don't know.

Thanks for the help though.

---

### Post by tommcd on 2009-07-22
> **nickolasemp said:**
> 
Disabling(#) and then enabling(removing) them from gedit while running synaptic (and not update manager) and reloading in between seems to fix the problem...

Perhaps one of the ppa.launchpad repos was listed incorrectly in your sources.list. Removing, reloading synaptic, and then adding them again and reloading again corrected the problem.
I didn't see anything obvious is your sources.list either. I don't use those launchpad repos though.

---

### Post by nickolasemp on 2009-07-22
That's the weird part, I didn't delete them, I just commented them and them put them back in....:confused:

Anyway, since the problem is now solved I don't know how else I could contribute as to what I did and what was causing the problem... I no longer can reproduce it.

---

