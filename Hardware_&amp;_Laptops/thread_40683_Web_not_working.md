---
title: "Web not working"
date: 2005-06-09
forum: Hardware &amp; Laptops
---

### Post by storybookhero on 2005-06-09
ok heres the problem....
I will log onto Ubuntu through my User name etc. Everything boots up fine it even connects to the ubuntu site for the time yada yada. but heres where things go wrong. I try to access the internet and the ubuntu site works just perfectly, Linux.com works great kdelook.org works awesome but when ever I try to connect to anything oher than those three sites it will idle forever and it tells me that its timed out. seems a bit strange to me. I'm really new to linux and extremely new to Ubuntu...can anyone help me with my problem.

The network card that I have is onboard but its an Abit Gigabit connection so It should be working smoothly. I have the Abit AV8 socket 939 if that helps any.

---

### Post by 23meg on 2005-06-09
try disabling ipv6 in firefox if you're using it. type about:config in the adress bar, type ipv6 in the filter box, and set the only line that comes up to "true".

---

### Post by storybookhero on 2005-06-10
thanx dude...that totally worked! but one other thing I want to change my screen resolution to something  other than 800x600 and 1024x768 is there any other way to get another value to appear? also I want to install the Nvidia Driver...is  there an easy way in doing so...if not then how do you go about installing it? again thanks for getting me hooked up man

---

### Post by 23meg on 2005-06-13
you're welcome. to tweak your resolution settings you'll need to edit your xorg.conf file. do a search on the forum for "xorg.conf resolution" and if you can't find any specifics, start a new thread on the subject..

---

### Post by AMP on 2005-06-13
[QUOTE=23meg]you're welcome. to tweak your resolution settings you'll need to edit your xorg.conf file. do a search on the forum for "xorg.conf resolution" and if you can't find any specifics, start a new thread on the subject..[/QUOTE]
 log in as fail-safe terminal and run sudo dpkg-reconfigure xserver-xorg and take it from there

---

