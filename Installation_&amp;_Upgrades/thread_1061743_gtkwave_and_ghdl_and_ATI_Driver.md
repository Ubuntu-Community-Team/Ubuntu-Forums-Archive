---
title: "gtkwave and ghdl and ATI Driver"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by ubunpete on 2009-02-06
Hello,

I've just installed Ubuntu 8.10 and I have to say it's a great alternative to Windows.

But I have 2 Problems:
I wanted to install gtkwave. I found out that it should be in the "universe" repository but unfortunately apt-get install/the synaptic package installer does not find it, even though "universe" is in the repository list.
Which repository do I have to add?
I could install gtkwave manually, I know, but I would have to install a lot of other packages manually.

The second problem is not so important but still annoying.
I have installed the proprietary fglrx driver. When I run aticonfig --initial=dual-head to set up a configuration for my notebook and my external monitor I always get an error like: (EE) fglrx(0) Unknown EDID version 0 when I restart.
If I run aticonfig --initial the external monitor works but with wrong dimensions.

I would really appreciate,
if anyone of you knows an answer to one of my questions.

Thanks in advance!

---

### Post by Partyboi2 on 2009-02-06
Adding 'Universe' should have down the trick. Make sure you have updated the package list before trying to install gtkwave. Can you open a terminal (Applications>Accessories>Terminal) and
```
sudo apt-get update
sudo apt-get install gtkwave 
``` if you still cannot install it can you post your sources.list
```
cat /etc/apt/sources.list
```

---

