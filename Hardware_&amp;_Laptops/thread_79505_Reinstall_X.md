---
title: "Reinstall X?"
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by jc87 on 2005-10-20
2 days ago i acidentally damaged X by mistake throug synaptic , and yesterday when i turned on the pc i realized my error.

First i through it was xorg.conf that was damaged and tryed replace him for older versions , or repair it using stuff like dpkg -reconfigure xserver-xorg , but it wont worked , then i realised that was X itself that was damaged .

A friend of mine told me that would be something like this to reinstall X on ubuntu :

a)apt-get remove xserver

b)dpkg --purge xserver

c)apt-get install xserver

a) removed it

b) appears a message saying that ignores this command because xserver is already uninstalled 

c)appears 4 different to choose :

vncserver 3.3.7-7ubuntu1

tightvncserver 1.2.9-6 build1

xserver-xorg-dbg 6.8.2-77

xserver-xorg-core 6.8.2-77 

But never finds the package of any of them

I have breezy (upgrade from hoary) with the standart sources.list ( this dind´t happen with the upgrade , i booted it after the upgrade several times without any problems)

Thanks for any help you can give me (it would suck had to reinstall ubuntu).

---

