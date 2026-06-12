---
title: "Installed but get &quot;Error 28: Selected item cannot fit into memory&quot;"
date: 2008-06-05
forum: Hardware
---

### Post by adam1835 on 2008-06-05
Hey,

I recently dug out a Toshiba Satellite 2610
433mhz Celeron
64MB RAM
800x600 16bit screen

I am going to get hold of a linux compatible PCMCIA wireless card and use it to browse the net.

I tried installing xubuntu on it but it froze I then tried TinyMe but that didn't work either. So I eventually got DSL installed and after a bit of tweaking/learning on my behalf managed to get it to boot using the vga=788 boot command (and additionally "lowram" + "mem=64M".)

Though I wasn't happy with not having the nice feel of xubuntu I searched and found this.
[https://bugs.launchpad.net/ubuntu/+bug/219263](https://bugs.launchpad.net/ubuntu/+bug/219263)

So i left the install of over a day and this morning it finally finished!

Anyways, when selecting to boot in Grub I just get: "Error 28: Selected item cannot fit into memory"

I tried adding "vga=788 lowram mem=64M" to an additional line in grub was that right or do I need to add it to the end of another line already there?

I have seen some posts regarding this error and a lot of them say reinstall. I really don't want to let it install for almost 2 day again!!! Worst come to worst I can try other distro's or go back to DSL.

I know it's a long post but I wanted to cover everything.

Regs.
Adam

---

### Post by adam1835 on 2008-06-05
Nobody think of anything?

---

### Post by zootsim on 2008-06-30
Well did you get it 100%?
I have the same lap top but with 192Meg ram. Tried Puppy Linux, no joy, video drivers. Tried BLAG it instlled quick but I don't like the look of it.

With Ubuntu I get to step 2 of 7 what's your time zone? I tell the program and then black screen and flashing cursor.  Should I leave it and walk away for 3 days?

Thanks for your help in advance.

---

### Post by adam1835 on 2008-06-30
Hey man, I gave up with Ubuntu on this laptop atm
I wouldn't have expected issue with that amount of mem though, or at least not from what most articles on the web hint at.

Have you tried the "cheats" I mentioned above.

I am using DSL now. When I get round to it I have a caddy at work to put laptop drives in desktop PCs. I am going to install it that way when I have the time.

---

### Post by zootsim on 2008-06-30
> **adam1835 said:**
> Have you tried the "cheats" I mentioned above.



Cheating now and waiting. 

While I'm waiting I am looking at DSL.

I'll let you know how it all turned out.

---

