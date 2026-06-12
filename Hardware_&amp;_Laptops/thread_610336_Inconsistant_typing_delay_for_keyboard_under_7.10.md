---
title: "Inconsistant typing delay for keyboard under 7.10"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by thepineApple on 2007-11-11
Hello everyone,

This problem is really annoying.... and it has been with me since day 1 of Gutsy...

I have a wireless logitech keyboard that works fine in Windows. When I installed Gutsy, everything is find except that when I'm typing, doesn't matter where, in the X or Ctrl+Altt+F1, there's always this delay and it's inconsistant.

Forr examplle if type "hello", "he" may come out with no problem but it stops for like, 1 second even though I am still typing, then the rest of the word just pops out all the sudden. 

I've tried with a wired keyboard, same problem.

If any one could help, you will be the man

thanks in advance!


the P.A

---

### Post by Nerdriot on 2008-01-31
Hey, I had the same issue, with a Logitech wireless mouse + keyboard. After messing around a while, I found a solution (that worked for me). I posted it here:

[http://ubuntuforums.org/showthread.php?t=658446&highlight=logitech+wireless+keyboard]("http://ubuntuforums.org/showthread.php?t=658446&highlight=logitech+wireless+keyboard")

I hope this helps!

---

### Post by shan420 on 2008-02-18
Hi there, I've tried this fix, it doesn't really work for me, there's one weird thing i've noticed, when I enable the Advanced Desktop Effects Settings, there's no delay or lagging problem with the keyboard, when i switch back to Normal Mode in Advanced Desktop Effects Settings, I get the same delaying in typing (Keyboard response) as if processor is really over loaded with applications...

Any help would be appreciated. thanks

[My System configuration Dell Inspiron 9200, ATI Radeon 9700, 100 GB Hdd ]

----------------------------------------------------------------------------------------------------------
Quote:
Originally Posted by Nerdriot View Post
Ok, hopefully, this is a fix for it. After testing a little more, I added noapic in /boot/grub/menu.lst:

title Ubuntu 7.10, kernel 2.6.22-14-rt
root (hd0,3)
kernel /boot/vmlinuz-2.6.22-14-rt root=UUID=4195995d-914f-4478-a7a0-2cd911e20166 ro quiet splash noapic
initrd /boot/initrd.img-2.6.22-14-rt
quiet

It's been running just fine ever since then, and it's been about a week. I hope this helps someone.

---

