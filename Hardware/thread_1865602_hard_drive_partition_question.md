---
title: "hard drive partition question"
date: 2011-10-20
forum: Hardware
---

### Post by solutionorppt on 2011-10-20
Hi all...

I've been running 10.04 on my home desktop for about 18 months and after a pair of blue-screenings yesterday, I installed it on my laptop this morning.

I partitioned my hard drive to create 68 GB for the Ubuntu install, but I couldn't put it there (possibly because I didn't format it correctly?).

Anyway, here's a screenshot of what it looks like in the disk utility:
[http://imgur.com/Q4stq](http://imgur.com/Q4stq)

What are the steps I need to take to allow Ubuntu to use/access this partition?

---

### Post by diasf on 2011-10-20
that partition (68Gb) is a ntfs..... try ext4 or something more linux, or less windows NT FileSystem

---

### Post by solutionorppt on 2011-10-20
Will do, but is there a way for me to merge it with the current partition that was created on installation?

---

### Post by diasf on 2011-10-20
You can always erase both and create a new one. YOU WILL LOSE DATA if you just do this, so back up before doing. So maybe it's a good time to have a good read on the installation documentation, or gparted help :)

---

### Post by Sef on 2011-10-20
> Will do, but is there a way for me to merge it with the current partition that was created on installation?


What partition do you want to merge it with?

---

### Post by solutionorppt on 2011-10-20
> **Sef said:**
> What partition do you want to merge it with?
The extended partition cerated for Ubuntu - I'd like to set aside some more space for Swap if possible.

Am I better off reinstalling and doing an advanced/manual partition?  If so, is there a good walkthrough available?

---

### Post by solutionorppt on 2011-10-23
The ones labeled "Extended" and "New Volume" in the image above, to be precise.

---

