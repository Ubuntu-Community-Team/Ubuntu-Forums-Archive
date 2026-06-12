---
title: "HP nc 8430 install problems"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by carlo bolzonello on 2007-08-01
Hi Guys,

i have a HP NC 8430 Laptop, which im am currently running windows XP on. I have decide to make the move to Ubuntu, i have the original cd, with version 7.04 fiesty, but when i boot from  the disk, it gets going then fails  because of a x- server problem. 

I have gone to [http://wiki.x.org](http://wiki.x.org) to have a look, but im a windows user still :) have no idea what i am looking for. Can anyone help?

---

### Post by carlo bolzonello on 2007-08-10
i have tried to re-install again, and i have the exact error now.

" Failed to start the x server ( your computer interface). It is likely that is is not setup correctly. Would you like to view the x server output to diagnose the problem?"

so i clicked on yes and got this:

x window system version 7.20
release date: 22 January 2007
xprotocol version 1.1 , revision 0, release 7.2
build operating system: linux ubuntu 2.6 20-15- generic
# 2 smp sun build date: 04 April 2007

if this helps any one, i think it could be two thigs, the graphics chipset on my notebook or the sata drives, i have no other idea.

---

### Post by iAndrew on 2007-08-10
Did you look into the more advanced one? If so, look for an error.

Like "No screen detected" or something.

Um, also do you have integrated graphics? if so, you might want to look at xubuntu.

I got that working for my laptop.

---

### Post by carlo bolzonello on 2007-08-10
ok, solved my own problem, my graphics card, a ati mobility radeon x1600 is not supported, so you have to do some hacking to make it work, found this info in the hardware compatibility section.

---

### Post by iAndrew on 2007-08-10
oh, okay. Great. Can you change the topic name to:

[SOLVED] HP nc 8430 install problems

Thanks, Andrew.

---

