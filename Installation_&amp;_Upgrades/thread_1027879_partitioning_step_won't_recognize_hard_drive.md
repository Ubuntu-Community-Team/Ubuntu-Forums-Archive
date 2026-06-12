---
title: "partitioning step won't recognize hard drive"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by standingchair on 2009-01-01
Hi Ubuntu forums, 

I think I already know the answer to my question, but I was hoping someone could verify.

I want to install Ubuntu on my old laptop. 
My old laptop, which I got in a fight with a few months back, and might have been a bit rough on it, I may have even punched it dead center of the keyboard. 

Since then, it won't recognize the OS, just shows the boot screen. I'm a little more comfortable with computers now, 
so I figured, what the hey!
I'll install Linux, and so I burned the ISO image and booted my laptop. The CD runs as a live session, but when I get to step 4 of partitioning my drive, it won't recognize any drives.

It probably is, and this is most likely a redundant question,
but I'll ask, did my punching my computer break the hard drive, and now I have none?
And I guess I'll throw this one in here, even though I know I could google it, can I install a new hard drive? It's a Gateway MX6448 (but I'm not asking for specifics or anything, just is it hard)?
Thanks for all your help
Jenn

---

### Post by WikipedianMarlith on 2009-01-01
I am having the same problem here. The internal hard drive dosen't show up and I can't partition it.

---

### Post by Mark Phelps on 2009-01-02
Same reply to both of you ...

Open a terminal and enter "sudo fdisk -lu" (That's a lower-case ell, not a one).  That will display what Ubuntu thinks are the hard drives and their resident partitions.

---

