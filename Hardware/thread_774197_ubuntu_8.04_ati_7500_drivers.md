---
title: "ubuntu 8.04 ati 7500 drivers"
date: 2008-04-29
forum: Hardware
---

### Post by sgissinger on 2008-04-29
Hi all.
I upgraded to Hardy Heron yesterday and I have a few problems.
I have an [COLOR="Red"]ati mobility radeon 7500 GPU[/COLOR] which was fully supported by gusty, so I had [COLOR="Red"]compiz-fusion[/COLOR] installed. Unfortunately it appears that my GPU is no longer supported in this new ubuntu release. I tried to re-activate the restricted drivers from the gnome manager but ati's rd doesn't appears, so I tried reinstalling fglrx from synaptic but still without success and I cannot activate gnome extra display features which are the KEY to compiz-fusion as you probably know.
Please help me, I heard someone talking about some [COLOR="Red"]SKIP-CHECK[/COLOR] option but I didnt find any more details about it.
My second (minor) problem is that many booting scripts show-up after the logo loading sequence and I'm looking for a way to desactivate this script displaying option.
Thanks in advance.

---

### Post by sgissinger on 2008-04-29
UP
:cry:

---

### Post by tuwxyz on 2008-05-02
It's pretty wired that this gpu worked well in every distro before.
Now we have to downgrade driver to: xserver-xorg-video-ati=1:6.7.195-1ubuntu2
(have to add gutsy repos; xserver core etc will be downgraded too).

---

### Post by starcannon on 2008-05-30
in a terminal type:

```
SKIP_CHECKS=yes compiz &
```

badda bing, badda boom, you gots your compiz... works on this Dell 5100 with ATi 7500 anyway.

---

### Post by sgissinger on 2009-01-18
I was using xcompmgr to be able to have a cool cairo-dock, I had to terminate it to launch compiz but the skip check option doesn't change anything, it just allows compiz to run. CCSM now runs horribly slow, I guess I have to reinstall Xgl...

---

