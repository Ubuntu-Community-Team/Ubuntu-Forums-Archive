---
title: "Unloading a module from gdm or xorg?"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by chele on 2007-05-14
I have an issue with a module, vesafb, causing resume from supend to  fail. I can rmmod vesafb once booted to fix it, but next time the laptop restarts, vesafb loads again. I have tried blacklisting it and I have tried nosplash in grub, but it still is there.

I want to take a different approach, simply unloading, maybe from gdm or when xorg starts?

---

### Post by teaker1s on 2007-05-25
because nobody has a better answer
have you looked in xorg config? 
it could also be in init.d
or running with update rc.d  link to determine run levels

---

### Post by tturrisi on 2007-05-25
dpkg-reconfigure xserver-xorg
select your exact display driver & and don't install the frame buffer.

---

