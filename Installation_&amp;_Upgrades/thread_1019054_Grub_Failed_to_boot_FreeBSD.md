---
title: "Grub: Failed to boot FreeBSD"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by imhotep1 on 2008-12-22
Ubuntu 8.10 is installed on hd0,0,a 
Then I created another partion for FreeBSD and successfully installed it on hd,2,a

In the /boot/grub/menu.lst, there is an entry like that:

title FreeBSD 7.0
root (hd0,2,a)
kernel /boot/loader
boot

When I choose the FreeBSD, the it nevertheless boots Ubuntu and I don't know why. I tried you several times but nothing worked till now.
Have you any idea?
Thanks so much in advance...

---

### Post by logos34 on 2008-12-22
What about just:

> title FreeBSD 7.0
root (hd0,2)
kernel /boot/loader
boot

> 
If you need to specify which slice number should be used, use something like this (hd0,2,a). By default, if the slice number is omitted, GRUB searches the first slice which has a partition.

[http://www.freebsd.org/doc/en_US.ISO8859-1/books/faq/disks.html#BOOTEASY-LOADER](http://www.freebsd.org/doc/en_US.ISO8859-1/books/faq/disks.html#BOOTEASY-LOADER)


(hd0,2) = /dev/sda3 (freebsd / is your *third* partition, right?)

---

### Post by Cracauer on 2008-12-22
I use the chainloader when I want to bring up FreeBSD through grub.

But I usually have the BSD boot selector in the disk MBR and grub in the partition MBR. That gives you the best of all worlds.

---

### Post by logos34 on 2008-12-22
> **Cracauer said:**
> I use the chainloader when I want to bring up FreeBSD through grub.

yes, [like this]("http://ubuntuforums.org/showthread.php?t=1017870")

---

### Post by imhotep1 on 2008-12-23
Hello my dear friends

It is successful. Thank you very much for your precious advice.
It runs with the entry

rootnoverify (hd0,2)
chainloader +1
boot 

With the entry

title PC-BSD
root (hd0,2,a)
kernel /boot/loader
boot 

it didn't work. Do you know why? Just interesting to know that:P

---

### Post by logos34 on 2008-12-23
> **imhotep1 said:**
> 
title PC-BSD
root (hd0,2,a)
kernel /boot/loader
boot 

it didn't work. Do you know why?

no, I wish I knew.  The docs say sth about how bsd sees the partitions as 'slices'...

Did you try this as suggested above:

> [URL="http://www.cyberciti.biz/tips/configure-ubuntu-grub-to-load-freebsd.html"]title FreeBSD 7.0
root (hd0,2)
kernel /boot/loader
boot[/URL]

?

What about 

> [URL="http://nixcraft.com/ubuntu-debian/12370-grub-entries-being-displayed-after-selecting-os-mutli-boot.html"]title FreeBSD 7.0
root (hd0,2,a)
kernel /boot/loader
savedefault
makeactive
chainloader +1[/URL]

Just paste the both to bottom of grub menu.lst and post back with the results.  

One more thing: you did write grub to the FreeBSD / partition before using the 'chainloader' entry, did you not?

---

### Post by Cracauer on 2008-12-23
> **imhotep1 said:**
> Hello my dear friends

It is successful. Thank you very much for your precious advice.
It runs with the entry

rootnoverify (hd0,2)
chainloader +1
boot 


Good :)

> **imhotep1 said:**
> 
With the entry

title PC-BSD
root (hd0,2,a)
kernel /boot/loader
boot 

it didn't work. Do you know why? Just interesting to know that:P

Sorry, but.  GRUB is just a POJ, half of what's in there doesn't work.  Have you tried to even build it's PXE boot support?

The direct FreeBSD load never worked for me, and I tried it on and off for 10 or so years.  Might be able to load a.out kernels (FreeBSD 2.x) only or something.

---

### Post by logos34 on 2008-12-23
> **Cracauer said:**
> Sorry, but.  GRUB is just a POJ

don't agree, but that's not to say it can't stand a bit of improvement (Grub2  addresses the shortcomings..should be out soon)

> 
title PC-BSD
root (hd0,2,a)
kernel /boot/loader
boot 

The direct FreeBSD load never worked for me

a lot of people seem to have problems with it, but then I read other posts where it works fine.  I just wish I knew why...

---

### Post by imhotep1 on 2008-12-23
Yes I tried it out with your suggestion and that didn't work as well.

---

### Post by logos34 on 2008-12-23
> **imhotep1 said:**
> Yes I tried it out with your suggestion and that didn't work as well.

in that case if this topic ever comes up again I'll just cut to the chase and recommend chainloader method over the bsd direct boot entry...

---

