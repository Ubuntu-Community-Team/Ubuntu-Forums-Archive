---
title: "CD/DVD-RW drive won't mount on my laptop"
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by cengelsma on 2007-03-06
I'm a relatively new Ubuntu user (since Sept. 06) and I've never had a problem with the CD/DVD-RW drive until about a week ago, where I'll put a cd or dvd in and it won't show up.  The drive spins as though it's doing something and then stops.  I've searched the forums for similar problems but haven't found one that was resolved, so I thought I'd ask for your help.

I am running edgy on an IBM ThinkPad T43

A print-off of my lspci: [ATTACH]26753[/ATTACH]

And a quick scan of my dmesg reveals this in relevance to my cd-rom drive reveals [ATTACH]26752[/ATTACH]

I've tried mounting it in the terminal with $ sudo mount /mnt/cdrom which returns "No medium found" and $ sudo mount /dev/hdc /mnt/cdrom which returns "special device /dev/hdc does not exist"

I feel like I'm stabbing in the dark right now, can anyone help me out please?

---

