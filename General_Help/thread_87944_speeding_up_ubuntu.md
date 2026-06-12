---
title: "speeding up ubuntu"
date: 2005-11-09
forum: General Help
---

### Post by shadowhunter on 2005-11-09
Hi all,

Has anyone any hints that will speed up the boot-up?

GNOME seems to be so slow on Ubuntu, seems faster on other distro's, maybe it is something I did wrong?

Thanks.

---

### Post by Kyral on 2005-11-09
GNOME is a little slow, which is why I switched over to XFCE. You could try swapping out MetaCity for Openbox, or Prelinking.

Its nothing you did wrong, it seems to be a side effect of switching to Cairo

---

### Post by izmaelis on 2005-11-09
[QUOTE=Kyral]GNOME is a little slow, which is why I switched over to XFCE. You could try swapping out MetaCity for Openbox, or Prelinking.
[/QUOTE]
Yes. Switching from Metacity to Openbox and prelinking did the trick for me. I tweaked my system by doing that when I was using Hoary. I dist-upgraded and it still does work fine.

---

### Post by didit on 2005-11-09
use clearlooks-cairo! perhaps it may help you. At least it helps me speeding up my gnome :)

---

### Post by ruffneck on 2005-11-09
[QUOTE=Kyral]GNOME is a little slow, which is why I switched over to XFCE. You could try swapping out MetaCity for Openbox, or Prelinking.

Its nothing you did wrong, it seems to be a side effect of switching to Cairo[/QUOTE]


First off, thanks for the info. Can you (or anyone) state what the drawbacks (if any) may be if you swap out MetaCity For Openbox?

Thanks alot.

---

### Post by jamesford on 2005-11-09
how does one install the cairo thing?

---

### Post by ruffneck on 2005-11-09
I suspect that Cairo comes with GNOME and subsquently with Ubuntu. It's eventual support of SVG or vector-based graphics is what intrigues me the most about it. I'm not sure if it is currently supported in the version of GNOME that is pre-packaged with Ubuntu 5.10, however.

Edit: Here is a link on Cairo, BTW

[http://en.wikipedia.org/wiki/Cairo_%28graphics%29](http://en.wikipedia.org/wiki/Cairo_%28graphics%29)

---

### Post by TheIdiotThatIsMe on 2005-11-09
You can also try using a different kernel if you use a newer processor. The default 386 is the slowest but most compatible. If you use a P4 with HT, for example, you can use the 686-SMP (also works for dual cpu's). They also have k6 and k7 kernels.

Here's a guide to explain what I mean:

[http://ubuntuforums.org/showthread.php?p=465585](http://ubuntuforums.org/showthread.php?p=465585)

---

