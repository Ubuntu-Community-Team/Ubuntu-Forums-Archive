---
title: "Problems with LG laptop - LE50-5LTP1"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by roger_rf on 2007-05-05
Hi all,
I've just installed Kubuntu Feisty Fawn on my LG LE50-5LTP1 laptop, and I have two problems. First, I have no sound. Alsa actually finds the sound card and lists two mixer channels, "Caller-ID" and "Off-Hook", but I don't get any sound output :( Second, the system runs OK for a few minutes, and then all of a sudden the USB mouse and the internal ethernet network card stop working. This doesn't always happen, and it occurs after both long and short periods of uptime, i.e. it could happen after just 5 minutes or 2 whole hours. Any ideas? Here are the technical specifications for the laptop:

[http://br.lge.com/md/product/prodcategorylist.do?actType=detail&currPage=1&categoryId=1000000088&parentCategoryId=0000000403&categoryLevel=4&productId=1100000433](http://br.lge.com/md/product/prodcategorylist.do?actType=detail&currPage=1&categoryId=1000000088&parentCategoryId=0000000403&categoryLevel=4&productId=1100000433)

Thanks,
Roger

---

### Post by KuruOujou on 2007-05-05
I'm having a similar problem. My sound card works fine, try changing the module from alsa to oss, not sure if it will work but it did on my other computer.  I'm not sure what the issue could be with your network card, are you sure it doesn't even detect it? Finally, I am having the same problem with my USB devices, can anyone else help us there? I'm running a Toshiba Satellite, so I don't think its model specific...

---

### Post by roger_rf on 2007-05-06
Hi KuruOujou,
Thanks for replying. The sound card problem has to do with a bug in Alsa, it seems:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103379](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103379)

As for the network card, it's detected properly. The problem is that, after I login, it stops working for no reason after a random period of time :( I'm downloading something, I'm browsing the net, I'm on IRC, then all of a sudden the card dies, along with my USB mouse. I don't have the links handy, but it seems to be a problem with frglx, which is unstable, and things should work if you use the open source, stable "ati" driver in X.org (my laptop has an ATI video card). Unfortunately, after reading so many positive reviews and having several friends recommend me to install Ubuntu, having such a bad experience mostly ruined my interest it this distribution. Now I'm going to try OpenSuse. Thanks,

Roger

---

### Post by KuruOujou on 2007-05-08
Well, I'm sorry to hear that. I did find a solution with my USB devices, which might work with your network card to. It has to do with GRUB, you have to set something in the grub config. I can't remember the exact solution nor the forum post in which I found it. (sorry). I could find it for you but I am having another issue -- the caps lock key starts blinking and the entire computer freezes. I have no idea why, I only have about 30 minutes before it happens again so I have to find a fix fast. Sorry.

EDIT: Ok, found my fix. Anyway, try adding "irqpoll" to the end of your kernel line and your #defoptions line in /boot/grub/menu.lst. For example, here is my #defoptions line:

```
# defoptions=quiet splash acpi=force irqpoll
```

and my kernel line (this is directly below ## ## End Default Options ## ##
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7273a7d4-ca6b-4cdb-a3c7-c017ddd07786 ro noapic nolapic quiet splash acpi=force irqpoll
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```

Try that, it should work, it's what worked for me. If not, I haven't a clue. Good luck :D

---

