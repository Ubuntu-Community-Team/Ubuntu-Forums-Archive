---
title: "swap partition"
date: 2008-07-22
forum: General Help
---

### Post by sulekha on 2008-07-22
Hi,

Is it possible to create swap parition that can be used by both windows and linux O.S es,independant of filesystems, in a dual boot system ?

---

### Post by tamoneya on 2008-07-22
no because windows doesnt use swap partitions it uses a swap file which they call the "paging file".  since one uses a file and one uses a partition it is a little difficult to share them.  It is however simple to use the same swap file across multiple linux distros.

---

### Post by Rocket2DMn on 2008-07-22
Indeed, Windows has the pagefile.sys file which it uses in the same manner that linux uses a swap partition.

---

### Post by Gallienus on 2008-07-22
Actually, it's possible to set up Ubuntu to use a swap file rather than a swap partition -- I did it on my computer (Hardy) using the following information.

[https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?) 

I wonder if it would be possible to set up Ubuntu so that it uses the pagefile.sys on the Windows partition instead of its own swap file? Note, that's something I _haven't_ tried, so it could well be very risky. I very much doubt that the two swap file formats are compatible.

---

### Post by grim4593 on 2008-07-22
Actually, you can share the pagefile.sys file. Windows clears it on every boot, so anything that is put there by linux is wiped out. So in order to get linux to use the file sucessfully, you have to mkswap pagefile.sys and turn it on every boot. The only issue is that you can't hibernate on one system, and then boot the other without messing up the swapfile.

I have successfully done this.

Howto: [http://hype-free.blogspot.com/2007/08/setting-up-laptops.html](http://hype-free.blogspot.com/2007/08/setting-up-laptops.html)

---

