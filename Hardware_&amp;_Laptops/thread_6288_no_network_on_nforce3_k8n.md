---
title: "no network on nforce3 k8n"
date: 2004-11-27
forum: Hardware &amp; Laptops
---

### Post by scrooch on 2004-11-27
I used Ubuntu on my old computer for several months without any hardware detection problems. Now I got a new computer, and can't get the network up and running. 

Some information:

[list]
[*]nforce 3 motherboard
[*]gforce 6800
[*]1 harddisk (ide) with 1 partition as ntfs, the other partition as reiserfs (mounted as / )
[*]another disk (this one is sata) with a huge reiserfs partition, used for some pictures and the kind
[*]networkcard is 1394 netadapter (came with motherboard), other distro's use the forcedeth module for this one
[*]1 gig ram
[/list] 

I putted online some files with output of commands:
[http://members.home.nl/rgoessen/dmesg.txt](http://members.home.nl/rgoessen/dmesg.txt)
[http://members.home.nl/rgoessen/ifconfig.txt](http://members.home.nl/rgoessen/ifconfig.txt)
[http://members.home.nl/rgoessen/ifup.txt](http://members.home.nl/rgoessen/ifup.txt)
[http://members.home.nl/rgoessen/lsconfig.txt](http://members.home.nl/rgoessen/lsconfig.txt)
[http://members.home.nl/rgoessen/dhclient.txt](http://members.home.nl/rgoessen/dhclient.txt)

Simply modprobing forcedeth doesn't change any of the output unfortunately. It's extra painfully that at startup other distro's like gentoo and fc3 work flawlessly. Debian installer rc2 won't on the other hand even load forcedeth.

I hope somebody can help me out with this. It has to be Ubuntu since on other distro's it works alright with detecting the network. Since it doesn't work on debian installer rc-2 I'm afraid the network of next version of Ubuntu won't work neither on my computer.

---

### Post by scrooch on 2004-11-28
Thanks for the great help all..

I'm using now the closed sourced drivers from nvidia just because nobody can say a thing  =;   [-X

---

### Post by Gibbz on 2004-11-28
how did you get the sound working from the nvidia drivers? ive tryed to no avail!

---

### Post by scrooch on 2004-11-28
It just worked. I'm using a sb audigy as main sound-card though. What does the error say?

---

### Post by Gibbz on 2004-11-29
ah well if your using the sblive it would be using that driver...

---

### Post by scrooch on 2004-11-29
Well yeah, but allthough I didn't test the onboard sound, I didn't get any errors while installing that driver.

---

### Post by Gibbz on 2004-11-29
yeah install works, just i am required to edit a few files(that dont exist in ubuntu) but its ok :P

---

