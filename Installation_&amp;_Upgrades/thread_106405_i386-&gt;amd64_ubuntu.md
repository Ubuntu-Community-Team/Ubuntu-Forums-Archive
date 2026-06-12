---
title: "i386-&gt;amd64 ubuntu"
date: 2005-12-20
forum: Installation &amp; Upgrades
---

### Post by Lofticus on 2005-12-20
Hi People!

I yet have another question that waits to be answered (-:

I have installed on my AMD64 Ubuntu (the "normal" 386 version) and now it seems that some applications won't function (like cedega).

I just wanted to ask: Is there any way I can install Ubuntu64 so that it will replace my old Ubuntu **WITHOUT** losing all my data and stuff or reformat?

I use it for some time now and I really really really ... really don't want to lose all of my stuff and settings..

Ty for your time reading and hopefully answering!

Lofticus

---

### Post by Ocxic on 2005-12-20
yes, go into the synaptic package manger, click a package and type linux, you'll find the 64-bit kernel you can install there, reboot and select your new kernel from the boot menu.

---

### Post by Lofticus on 2005-12-22
I can't find a module called linux-amd64 or something.

Can you specify which linux kernel I have to download?

TY

Lofticus

---

### Post by Lofticus on 2005-12-23
I could need help with that plz (:

---

### Post by Yagisan on 2005-12-23
[QUOTE=Lofticus]Hi People!

I yet have another question that waits to be answered (-:

I have installed on my AMD64 Ubuntu (the "normal" 386 version) and now it seems that some applications won't function (like cedega).[/quote]
You would need to build an i386 chroot to install cedega on the amd64 version of ubuntu anyway.

[QUOTE=Lofticus]I just wanted to ask: Is there any way I can install Ubuntu64 so that it will replace my old Ubuntu **WITHOUT** losing all my data and stuff or reformat?[/quote] Yes, **but** when you installed ubuntu you must have made a seperate /home partition, which means that unless you did a custom install, you will need to backup, and install amd64 version of ubuntu.

If you did make a seperate /home partition (which is unlikely), stick in the amd64 ubuntu cd, and format all partitions except the one /home is on when you install it.

---

### Post by Lofticus on 2005-12-23
Hmm.. I just backupped everything and now I'm trying to install Fedora Core 4.

I will leave Ubuntu on my notebook because I think there is nothing better (-;

thanks for the help anyways (;

---

