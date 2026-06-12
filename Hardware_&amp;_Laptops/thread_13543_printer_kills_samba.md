---
title: "printer kills samba"
date: 2005-02-01
forum: Hardware &amp; Laptops
---

### Post by Davexc on 2005-02-01
I have one printer installed on ubuntu (Epson stylus 660)
it works fine
samba works fine (windows computer can share files back and forth, windows can print to the epson)

i try to add a second (USB) printer on ubuntu (HP Deskjet 3650)
and this prints fine as well... 
PROBLEM:

on reboot, ubuntu fails to start
it halts at:

Starting powernopwd...                      [ok]
Starting Samba daemons..




... dead ...

it doesn't go beyond this point
i can fix this by "apt-get remove" on samba through recovery mode
then reinstalling samba, and uninstalling the printer
and then ubuntu loads fine again

it seems this happens whenever i have more than 1 printer installed at once
any ideas?

---

### Post by Davexc on 2005-02-01
it seems that Samba crashes on startup whenever I have more than 1 printer installed at any one time

---

