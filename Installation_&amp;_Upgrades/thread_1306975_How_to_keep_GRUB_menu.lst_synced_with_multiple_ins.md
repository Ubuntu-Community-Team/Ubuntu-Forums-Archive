---
title: "How to keep GRUB menu.lst synced with multiple installs of Ubuntu?"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by coverup on 2009-10-30
Hi all,

Wondering if anyone knows how to keep the menu.lst file synced when you have two distributions of Linux running on the same PC?  My current setup is Ubuntu Studio Jaunty on one hard disk (not just a separate partition, a separate drive) and Karmic Koala on another.

Everytime I do a kernel upgrade in the distro that's not on the drive that GRUB uses for menu.lst, if I want to be able to boot into the new kernel and not the old one, I have to go in and edit the entry by hand.  It's a real pain to have to do this everytime we get a kernel update.  Is there some way that this can be done automatically?

How are you all keeping your separate distros straight?  Thanks!

---

### Post by Rumpty on 2009-10-30
I'm in exactly the same position, but it really is no great problem to edit menu.lst for the new kernel. Only one digit to change in each of four lines. 

I can't think of an automatic way to have it done.

---

### Post by louieb on 2009-10-30
The easiest way is to chainload  one Linux install from the other.  The chainload entry never changes. and each install  keeps its own Grub menu up to date. 

Search for chainload on this page [IDBS GRUB Page]("http://members.iinet.net.au/%7Eherman546/p15.html")

---

### Post by Rumpty on 2009-10-31
> **louieb said:**
> The easiest way is to chainload  one Linux install from the other.  The chainload entry never changes. and each install  keeps its own Grub menu up to date. 

Search for chainload on this page [IDBS GRUB Page]("http://members.iinet.net.au/%7Eherman546/p15.html")

Thanks, I'm following that up.

---

### Post by Mylorharbour on 2009-10-31
Herman's multi-boot site helped me a lot when I started. 
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Particularly this page:
[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)

That said, I'd probably investigate using GRUB 2 now it's the default for Karmic. It can also be downloaded for use on Jaunty. I suggest you take a look at Herman's pre-release pages, [http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

Cheers

---

