---
title: "Extending my root ex3 partition"
date: 2009-02-24
forum: Hardware
---

### Post by Teacher Lion on 2009-02-24
Presently, I have a 12.74 gig partition which I use for running Ubuntu 7.10 (64-bit). I want to extend it so that I can use the 19.53 gigs of unallocated space. In my Windows partition I have a copy of Partition Magic which is NTFS friendly but not very keen on ex3. In the Ubuntu partition I'm running gparted, which is rather keen on ex3 but doesn't particularly like NTFS. The attached image should give you a pretty good idea of what's going on.

The question: How can do I merge the Ubuntu partition and the unallocated space together?

Thank you in advance for any help provided!

Teacher Lion

---

### Post by Panzor on 2009-02-24
A gparted live cd should do anything you want. It's a useful little tool for anything you need to do regarding partitions. Resizing takes a while though. Hours. I recommend you let to run overnight.

I would go through the algorithm of the exact thing you need to do, but it'll be obvious once it starts up.

---

### Post by Teacher Lion on 2009-02-25
Thank you, I'll get that Live CD burnt and running when the work day's over.

For some bizarre reason I can't find the necessary button to thank you more formally! Hold tight, I'm sure it'll turn up later on!

I'll mark the thread as solved when I know whether I've messed something up or not!

Kind regards,

Lion

---

### Post by Teacher Lion on 2009-02-25
Well, it didn't work.

The good news is that I did manage to get both the NTFS drives and the swap area shifted over to the left. It's a bit tidier now and the unallocated space that I want merged with ex3 is sitting directly next to it. That's the good news.

The bad news: First off, for some reason the screenshot function on the LiveCD didn't work. It said all the right things but when it came to it the image files weren't were they were supposed to be. I've attached a screenshot of what things look like in gparted now.

Secondly, when I press on the ex3 partition and proceed to click on 'resize/move', it doesn't want to expand into the unallocated space. It says it's got 0 megs of free space on both sides!

What am I doing wrong?!

Thanks again,

Lion

---

