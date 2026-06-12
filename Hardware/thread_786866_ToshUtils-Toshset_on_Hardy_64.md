---
title: "ToshUtils-Toshset on Hardy 64"
date: 2008-05-08
forum: Hardware
---

### Post by WadiJM on 2008-05-08
Hi all! I have a toshiba SP-A205 with ubuntu hardy 64. I still can't use bluetooth. I read some were that there is an untility for this called toshutils or toshset. I can't find any of them for hardy 64. I downloaded the src code to compile toshutils but I says that my OS is not suported.
Should I go and reinstall 32 bit version?Would that take advantage of all capabilities(core 2 duo and 4gb of ram)?
Thanks in advance,
Regards,
Wadi

---

### Post by ShodanjoDM on 2008-05-08
Does it has Phoenix BIOS? If so, you may want to look here: 
[http://omnibook.sourceforge.net/doku.php](http://omnibook.sourceforge.net/doku.php)

I've got bluetooth and LCD brightess hotkeys working on my Toshiba Satellite M-200 after compiling the necessary omnibook kernel module.

---

### Post by WadiJM on 2008-05-08
THanks Shoda, I think I do not have that bios. I'll check that, but if I don't have, I think I just should install ubuntu 32 bits version.
Thanks for your help!

---

### Post by WadiJM on 2008-05-12
Hi Shoda, is there a way to install it without the need to compile anything?via apt-get? I tried the recomended links but they all failed with synaptic.Why can't this jus be sudo apt get install omnibook????????????
THanks in advance,
Wadi

---

### Post by WadiJM on 2008-05-14
Ok! I just check out the code from the svn and things went ok. I just had to use the ectype=12 for my Toshiba A205 and bluetooth is working!Now I just have to make it work with conduit!
Thanks!

---

