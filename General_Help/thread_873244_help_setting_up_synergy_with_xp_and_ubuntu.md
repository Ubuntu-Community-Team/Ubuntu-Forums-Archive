---
title: "help setting up synergy with xp and ubuntu"
date: 2008-07-28
forum: General Help
---

### Post by steve51184 on 2008-07-28
hey all i want to setup xp and ubuntu 7.10 with synergy and have xp as the server but i can only find help on how to setup a server on ubuntu and the help i can find to setup a server on xp is VERY confusing

i have xp on my left monitor and ubuntu on the right and have synergy install on both systems with quicksynergy also installed on ubuntu (if i need it) and again i want xp as the server but how do i setup the server on xp?

---

### Post by steve51184 on 2008-07-30
well that was hard but i did it ;)

---

### Post by qiepenguin on 2008-10-30
Hi Steve,

How did you do it?  I am striving for the same setup.  I have synergy installed on both and quicksynergy on ubuntu, want to run the server from xp.  When I try to connect nothing happens.

David

---

### Post by n00rt on 2008-11-15
if you still need to know the answer this may help.
start synergy on xp and click ' share this computers mouse and keyboard'
click configure and in the screens box click +
type in your xp ip address ie 10.0.0.7
repeat for your ubuntu ip
now click + in the links section and change it to say '0-100% of the right of 10.0.0.7 (your ip) goes to 0 - 100% of 10.0.0.4 (your ubuntu ip)
repeat for the other way round 
0-100% of the left of 10.0.0.4(ubuntu) goes to windows...
 
on quicksyn share tab put windows ip in the left box and in the 'use' tab

start both up and it should work fine..

---

