---
title: "CCSM missing in 8.10 amd 64bit"
date: 2008-10-30
forum: General Help
---

### Post by CarnivorouZ on 2008-10-30
It cannot be found in synaptics or retrieved from terminal:
```
xxx@xxx-linux:~$ ccsm
The program 'ccsm' is currently not installed.  You can install it by typing:
sudo apt-get install compizconfig-settings-manager
bash: ccsm: command not found
xxx@xxx-linux:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
xxx@xxx-linux:~$ 

```

for the first time ever I can can enable desktop effects and they go and steal CCSM and every bit of control from me!

---

### Post by CarnivorouZ on 2008-10-30
I guess I shouldn't be so hasty.  I did another update & upgrade and all the missing packages in synaptic appeared.  I guess they are still working hard at getting this up and running for people.  My apologies.

---

### Post by Throwback on 2008-10-31
yeah, I'm not able to find it either but I also notice some of the repositories are not updating- I figure they are just really busy because of the new release. I may try downloading from the US mirrors instead. Either way I'll give it a couple of days before I start delving deeper.

---

### Post by talsemgeest on 2008-10-31
I've got it right now. It is definitely there...

---

### Post by Meetloaf13 on 2008-10-31
I just installed 8.1 as well.  CCSM worked great in 8.04.  But I don't even know if my nVidia drivers are installing correctly.

How do I get things to where I can use compiz??

---

### Post by talsemgeest on 2008-10-31
> **Meetloaf13 said:**
> I just installed 8.1 as well.  CCSM worked great in 8.04.  But I don't even know if my nVidia drivers are installing correctly.

How do I get things to where I can use compiz??
Just install the restricted drivers and you should be sweet.

---

