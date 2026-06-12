---
title: "Using Debian packages with Ubuntu??"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by Steven45 on 2009-05-14
Hi

I was just wondering if it was safe to use Debian's packages with Ubuntu. For example, if I were to download DVD's of Debian "Squeeze" from the "testing" branch, would I be able to load these DVD's into Synaptic and install these packages on Ubuntu 9.04?. Would they work?. Would the necessary dependencies be installed as well?. I've heard that Ubuntu uses the "unstable" branch but a lot of the packages I see in Debian's "testing" branch seem to match the versions in Ubuntu 9.04.

Thanks,Steve

---

### Post by x33a on 2009-05-14
if there aren't any ubuntu packages available, i think you can give it try. 

i am using mediainfo's debian packages without a problem.

but, perhaps  you should wait for a more informed reply.

---

### Post by mc4man on 2009-05-15
I would be very wary of adding or using a debian branch as a source. While many packages are compatible/similar there are naming differences and also some dependencies that are nonexistent in ubuntu. 
At some point you may (will) get jammed up or have issues particularly when something requires a 'specific' version vs. "an equal or greater version"

On the other hand on an individual basis you can usually determine or anticipate  whether your headed for trouble.

To me the exception could be debian-multimedia. For intrepid I added it immediately after installing/updating and have had no issues whatsoever. My  intrepid install is in much better 'shape' than a stock one in terms of audio/video libraries  and to some extent more updated than jaunty.

(more useful because I build new versions of certain apps then for a general purpose install

I do refrain 100% from adding any package from debian-multimedia that would require a debian branch package for installation.

---

### Post by dtoronto on 2009-05-15
To answer the question you most certainly can use debian packages with Ubuntu.  I use a number of .deb packages on some of my servers, but be prepared to troubleshoot.  I usually don't recommend going outside of the Ubuntu repos, unless you're familiar with compiling your own sources.  Good Luck though

---

### Post by Keithhed on 2009-05-15
I also use the .deb source for mainstream packages when i cant get them through the package manager.  Works fine for me

---

### Post by Steven45 on 2009-05-15
Thanks so much, very helpful indeed!

---

