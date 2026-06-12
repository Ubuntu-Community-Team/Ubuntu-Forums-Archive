---
title: "The &quot;new&quot; way to force nodma on ide"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by somnorosul on 2008-12-18
Hi, I have invested a night in this and I think it is worth it.
So that you will not lose the same night.
The Problem.
Compact Flash (CF) does not support dma.
Or for some other reasons (80 pin cable does not detect)
You want to force the ide not to use dma.
If you don't do this the boot will take a long time because the ide driver will timeout on dma
Actually we should not talk about ide but about libata because here is the mix-up. Almost all you see about disabling dma say use ide=nodma or hda=nodma.
But ubuntu does not use ide anymore it uses libata so any fix with ide params will not work.
In short if you want to disable the dma on an ide device you have to use the libata.force param
I found an explanation here:
[http://www.mail-archive.com/linux-ide@vger.kernel.org/msg15962.html](http://www.mail-archive.com/linux-ide@vger.kernel.org/msg15962.html)
For me the stept where like this:
ubuntu 8.10
edit the /etc/modprobe.d/options
add to libata line the option: force=1.0:pio4
sudo update-initramfs -u
reboot
and ... the cf works.

---

