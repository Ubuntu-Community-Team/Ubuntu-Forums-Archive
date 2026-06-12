---
title: "Does suspend/hibernate work for Meerkat with an HP6910p?"
date: 2010-10-24
forum: Hardware
---

### Post by frogotronic on 2010-10-24
as asked in the title...

- CH    :popcorn:

---

### Post by sgarman on 2010-10-27
If this helps at all, I have an HP EliteBook 6930p and suspend/resume locks the system up most of the time. This is a regression bug that I did not have with Ubuntu Lucid. 

I'm still digging through forum posts to see what I can do. As a last-ditch effort I'm planning to try the kernel from Lucid. If that works for me, I'll stick with it. Otherwise I need to use a different distro on the laptop. :(

Scott

---

### Post by frogotronic on 2010-10-28
Okay, so its basically the same machine - I know it.

Have you tried a "fresh install"?  That's (suspend/hibernate) the **one** thing that will break (if anything does) on an upgrade.

I use BACKINTIME (Synaptic) to backup & restore from external HDD - works well.

- CH

---

### Post by Toz on 2010-10-28
I've had success with a kubuntu 10.10 install on a 6550b and with an aptosid install on an 8510p by using s2ram from the uswsusp package in place of the built-in pm-utils package.

---

### Post by sgarman on 2010-10-28
Yes, I did a fresh install of 10.10 on the EliteBook, but still had suspend/resume problems.

So far so good with using the latest kernel from Lucid, though. Here is a tutorial on how to do this that I found helpful:

[http://www.thanhsiang.org/faqing/node/129](http://www.thanhsiang.org/faqing/node/129)

Then you can go to packages.ubuntu.com and find the lucid-updates packages for linux-image, linux-headers, and linux-headers-2.6.32-25-generic.

I promise to update this thread if I discover that the Lucid kernel *does not* fix the problem. Otherwise I recommend it as a workaround.

HTH,

Scott

---

### Post by ianc1 on 2010-11-08
I don't think this is a problem specific to HP machines as I have the same issue on an Advent machine and know of a friend with the same issue on what I think is a Dell.

If try to hibernate the machine or the system tried to suspend I just get a blank screen with a blinking cursor in the top left hand corner of the screen.

---

### Post by frogotronic on 2011-03-31
any updates?

---

### Post by Dutch70 on 2011-03-31
> **cement_head said:**
> any updates?

How much RAM & Swap do you have?

---

### Post by frogotronic on 2011-03-31
Sorry.  I'm asking the community as to whether or not suspend/hibernate works with a HP6910p laptop running Ubuntu 10.10.

- CH

---

### Post by Dutch70 on 2011-03-31
Yes, I read the question... and although I can't answer it directly, I can tell you that no computer will successfully hibernate or suspend without the correct amount of Swap. How much Swap you need, depends on how much physical RAM you have.

Hence the question...
How much RAM & Swap do you have?

But, looks like you've been around here a while, so you probably know all about it. :)

Best regards

---

### Post by frogotronic on 2011-04-20
> **sgarman said:**
> Yes, I did a fresh install of 10.10 on the EliteBook, but still had suspend/resume problems.

So far so good with using the latest kernel from Lucid, though. Here is a tutorial on how to do this that I found helpful:

[http://www.thanhsiang.org/faqing/node/129](http://www.thanhsiang.org/faqing/node/129)

Then you can go to packages.ubuntu.com and find the lucid-updates packages for linux-image, linux-headers, and linux-headers-2.6.32-25-generic.

I promise to update this thread if I discover that the Lucid kernel *does not* fix the problem. Otherwise I recommend it as a workaround.

HTH,

Scott

Do you have X freezes with Lucid?

---

### Post by sgarman on 2011-04-20
> **cement_head said:**
> Do you have X freezes with Lucid?

I assume you mean with the Lucid kernel. No - everything works quite well on my EliteBook 6930p as long as I stick with the Lucid kernel. It's been rock solid stable since I posted the workaround.

Scott

---

### Post by frogotronic on 2011-04-20
> **sgarman said:**
> I assume you mean with the Lucid kernel. No - everything works quite well on my EliteBook 6930p as long as I stick with the Lucid kernel. It's been rock solid stable since I posted the workaround.

Scott

Yes, with the Lucid Kernel.

I'm getting random freezes when I use dual head and OpenGL compositing.

- CH

---

