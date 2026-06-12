---
title: "Imaging and partitions for new Netbook install"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by Mouth on 2009-10-16
I am getting a new Eee PC netbook in the next few days. Here is my plan of attack:

1. Create a Karmic Netbook Remix install on USB stick from ISO download (via UNetbootin)
2. Boot NetBook from USB stick
3. Run disk imaging app, and make an image/copy of the existing factory Win Xp install, and save the image back to the USB Stick or USB hard disk
4. Run Gparted and reduce the Win XP partition down to minimal size (eg. 3Gb)
5. Use Gparted to remove all other partitions, and use the rest of the disk for Ubuntu Remix partitions
6. Install Ubuntu Remix

I have a couple of questions from the above ...

1. From step 3 above, does the Ubuntu Remix Live including an app for imaging a disk partition If so, which app is it? If not, what app is suggested/recommended?

2. For step 5 above, what is the suggested/recommended partitions and size for Ubuntu Remix? 2Gb for /, 2Gb for /var, 2Gb for swap, and the rest for /home ?

Thanks.

---

### Post by earthpigg on 2009-10-16
1) dd. it comes preinstalled on damn near any unix/linux system, including live cd's. [http://en.wikipedia.org/wiki/Dd_(Unix](http://en.wikipedia.org/wiki/Dd_(Unix))

2) depends on how much RAM and how large a hard drive. on my mini 9 with an 8gb SSD, i have a 400mb swap and just leave the rest in /. next time i reinstall, ill probably dump the swap all together - ff and pidgin are about the only apps i ever use. im pretty sure the performance benefits of seperate partitions for /home and whatnot are significantly depreciated on SSDs.


edit:

oh, and when you are googling around and reading the man page of dd and eventually use it... dont get the 'if' and 'of' parts backwards. thats the kind of mistake there really is no recovering from :D


edit 2:

ah, it appears you dont have a SSD on that netbook. well, then just go ahead and think of it as any other computer.... no special partitioning scheme is needed. the most 'normal' ubuntu partitioning scheme is 10-20gb for /, 2gb for swap, and the rest /home.

the 2gb for / you suggest in your post is woefully inadequate. i suggest at least 10.

---

### Post by ztomic on 2009-10-16
this link works a little better:
[http://en.wikipedia.org/wiki/Dd_(Unix)]("http://en.wikipedia.org/wiki/Dd_(Unix)")

---

### Post by Mouth on 2009-10-16
> **earthpigg said:**
>  dd. it comes preinstalled on damn near any unix/linux system, including live cd's. [http://en.wikipedia.org/wiki/Dd_(Unix](http://en.wikipedia.org/wiki/Dd_(Unix))

Ah of course dd, thanks. Does dd only image used blocks in a partition for reduced file size of the resulting image, similar to what the likes of clonezilla does? I couldn't get the answer to this from Wikipedia or Google :)

> **earthpigg said:**
> it appears you dont have a SSD on that netbook. well, then just go ahead and think of it as any other computer.... no special partitioning scheme is needed. the most 'normal' ubuntu partitioning scheme is 10-20gb for /, 2gb for swap, and the rest /home.

the 2gb for / you suggest in your post is woefully inadequate. i suggest at least 10.

Yup, just a HDD no SSD. Ooops, I missed a zero for / partition size in my OP and meant 20Gb :) I have 20Gb / size on my current notebook, of which 13Gb is used.

Thanks for your answer, most helpful.

---

### Post by earthpigg on 2009-10-16
> **Mouth said:**
> Ah of course dd, thanks. Does dd only image used blocks in a partition for reduced file size of the resulting image, similar to what the likes of clonezilla does? I couldn't get the answer to this from Wikipedia or Google :)


dd makes no attempt to understand what it is copying. just reads raw ones and zeros directly off the device.

and that is a good thing: there is no chance of a 'misunderstanding' if there is no attempt at understanding and using 'clever' compression algorithms to begin with.

---

