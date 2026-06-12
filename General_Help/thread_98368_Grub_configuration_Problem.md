---
title: "Grub configuration Problem"
date: 2005-12-03
forum: General Help
---

### Post by Janherbergh on 2005-12-03
First of all tell you that I'm not english (I'm spanish) so you may find my english being terrible, sorry.

Well, my problem is that I don't know how to configure grub to recongnize a new windows XP installation in hdd1, when I have Ubuntu 5.10 installed in hda1. I installed windows disabling hd1 in the bios, so the windows installer think that it was installing it in the primary hd. So I need grub to continue fooling Windows XP and to be able to launch windows from grub screen... 

If I need to reinstall grub i would apreciate if somebody con explain me how, because i find so many metods in internet that i'm more confused than before.

If it's just a configuration problem, I need to tell you that I'm not an expert (just few months of experience).

Thanks!

PS: I hope you could understand me :-p

---

### Post by Janherbergh on 2005-12-04
Please, I really would apreciate some help, isn't there anybody who can help me?

---

### Post by Koybe on 2005-12-04
You should add some line like these, in your /boot/grub/menu.lst. An exemple is already in the file I think.

```
title Windows
root (hdx,x)           
makeactive
chainloader +1
```

with (hdx,x) should be (hd3,0) in your case if it's hdd1 as you said.

---

### Post by Janherbergh on 2005-12-04
Thanks! 

I'll try that configuration and I'll tell you how is working!!

---

### Post by UbuntuJohan on 2005-12-04
You have a bit more description on this at ubuntuguide.org
There a sample file is also available
[http://www.ubuntuguide.org/#changedefaultosgrub](http://www.ubuntuguide.org/#changedefaultosgrub)

---

