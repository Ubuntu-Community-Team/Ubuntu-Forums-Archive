---
title: "Problem with adjustable screen brightness at 11.04"
date: 2011-05-03
forum: Hardware
---

### Post by valtinldb on 2011-05-03
Hi, I have a Dell Vostro 3500, it comes with a video card geforce 310M. I just installed ubuntu 11:04 10:04 previously using, for who has a laptop with this video card knows that the video driver it is problematic, it can not operate the adjustment of screen brightness alone, for this to work you must install a nvidiabl-dkms driver called, but the driver is not working on new version of ubuntu.
Someone who knows more about it can give me a solution for that?

Obs.: Forgive me for English, I'm using the google translation tool.

---

### Post by PowerKiKi on 2011-05-15
Same problem as you, I used to add one line in xorg.conf with Ubuntu 10.04 but it does not work anymore under Natty.

See my other thread there: [http://askubuntu.com/questions/39391/adjusting-brightness-on-dell-vostro-3500-wont-work](http://askubuntu.com/questions/39391/adjusting-brightness-on-dell-vostro-3500-wont-work)

---

### Post by neostack on 2011-05-18
I'm having the same problem with Vostro 3300 and Geforce 310M. Used to work fine with Ubuntu 10.10.

---

### Post by PowerKiKi on 2011-05-18
Hey,

I found out the solution with help of Novarg. Please see my thread over there:

[http://askubuntu.com/questions/39391/adjusting-brightness-on-dell-vostro-3500-wont-work/43683#43683](http://askubuntu.com/questions/39391/adjusting-brightness-on-dell-vostro-3500-wont-work/43683#43683)

It's basically two files to edit: xorg.conf and /etc/default/grub

---

