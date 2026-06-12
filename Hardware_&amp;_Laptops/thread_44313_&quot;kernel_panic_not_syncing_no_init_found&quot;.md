---
title: "&quot;kernel panic not syncing no init found&quot;"
date: 2005-06-25
forum: Hardware &amp; Laptops
---

### Post by geearf on 2005-06-25
Hello,

i have a small problem there,

I managed with gentoo live cd to transform my partitions / and /home into reiser4 without too much problem, and i used the grml 2.6.12 kernel for the reiser4 support.
All seemed good.

Then today i played a bit with my windows Partitions, and now ubuntu cant boot with the error message :

"kernel panic not syncing no init found"

Also it seems that my / and my / home that were hde7 and hde6 are now reversed as hde6 and hde7.

I have a /boot partition too which is hde2.

When i look at the /boot i see no initrd.img for my new kernel, but as i booted before i don't know what to say, did it disappear ? or was it never there in the first case ?

What can i do ? (i still have the ubuntu dvd, and the gentoo livecd for reiser4 purpose).

Thanks for any help,

---

### Post by geearf on 2005-06-25
if cannot find anything i will try this : 

1- switch back the / to an ext3 partition and try with the 'old' kernel to see what happens.
2 if this does not work reinstall it (again) :(

---

