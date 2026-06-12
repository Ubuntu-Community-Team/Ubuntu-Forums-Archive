---
title: "problems with startup, shutdown, hibernation and standby"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by morganpatrick on 2008-02-24
Hello,

I'll keep this as brief as possible.

1) when I boot my laptop, grub starts up, then I get a few lines saying 'cannot allocate pci resource something something' and i get a black screen until my gnome login eventually works. This concerns me because if my laptop is shut down improperly, i have no way of knowing whether the startup is checking my disks or not.

2) when I leave my laptop idle and then come back to it, it's usually sluggish and certain apps like firefox don't work properly.

3) when I try to hibernate, my laptop just starts to shut down but it never fully does. it just goes into suspened animation.

4) same with 'suspend). 

I have a relatively new Toshiba laptop with 438.8 megs of RAM, 60 gigs of hard disk space ad a 1.60ghz processor. Let me know if you need any more information.

Thanks so much for your help.

---

### Post by cdtech on 2008-02-24
what flavor of ubuntu are you using?
are you using any boot options in grub (noapic irqpoll noirqdebug)?

```
uname -a
```

---

### Post by morganpatrick on 2008-02-25
I'm running gutsy and I haven't specified any special grub boot parameters.

---

### Post by morganpatrick on 2008-02-29
Also I ran the command you posted and got this:

Linux puddin-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

---

### Post by morganpatrick on 2008-03-18
*bump* any ideas? If no one knows what the specific problem is, should I re-install my grub? kernel? os?

---

