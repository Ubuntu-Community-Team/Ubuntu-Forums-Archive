---
title: "new kernel caused grub error"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by cholericfun on 2009-07-15
Hi,
 am on 8.04 LTS and did todays (15.7.2009) kernel update.
while installing it asked me if i wanted to keep my old menu.lst or whether i'd want to get a new one, beeing lazy and busy i clicked on "make a new one" (cant remember the exact name of the option)

anyhow, now when i try to boot i get an error to the effect that HD is not found.
i am now on a LiveCD and i checked menu.lst

entries are in the form:
title           Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root            (hd0,2)

but my ubuntu installation is actually on sda4, so i would think that menu.lst should say : root (hd0,3)

is this correct or are there other things at play here?
there seems to be an older menu.lst~ with the same "error" (if it is one)
so i'm not too sure.
 
SO anyone any ideas what best to do?

thank you very much.

---

### Post by master_kernel on 2009-07-15
You're correct, the root partition should be (hd0,3). I have no idea how Ubuntu could have screwed up that bad if you used the official repos.

---

### Post by cholericfun on 2009-07-15
OK, 
so its Error 17: cannot mount selected partition

i tried grub and it said that root is on hd(0,3)
it then rewrote grub but in menu.lst it still says hd(0,2)
i dont get that..

---

### Post by cholericfun on 2009-07-15
It's working now,

i manually edited the menu.lst to point to hd(0,3)
(for my 4th partition on which ubuntu resides)
all up and running as if nothing happend

strange and irritating is:
grub did manage to do the same mistake

is this a bug and why are not more people complaining then?

---

### Post by master_kernel on 2009-07-16
It must have to deal with multiple partitions and Ubuntu. I'd suggest filing a bug on 'grub' on Launchpad.

---

