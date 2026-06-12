---
title: "New to linux, install problem."
date: 2005-12-12
forum: Installation &amp; Upgrades
---

### Post by steelaz on 2005-12-12
Learning linux was always on my mind so recently I decided to just go ahead and do it. I took old P4 box with 15 GB hard drive, got myself ubuntu install cd and started install. Everything went smooth until partitioning part. I'm still a little confused about linux partitions so I went for guided option but got error saying: "error informing the kernel about modifications to partition". I googled it and found out that I should set my partitions first and then try to run install (this advice was for other distro, not ubuntu). Questions:

1. Would this work on ubuntu? Can I set partitions with partition magic and then just skip partitioning part on ubuntu install?

2. What partitions should I create for ubuntu, what sizes (for 15 Gb)?

Thanks for everyone helping out :)

---

### Post by NotJustANewbie on 2005-12-12
You can use M$ DOS programs such as PQ Magic etc for this process.

For a 15Gig, I'd recommend:

11Gb - / (ReiserFS)
3.5Gb - /home (ReiserFS)
0.5Gb - swap area

Hope this helps and solves your problem. Note, you must specify which partition is called which during the Ubuntu partitoning part of the install.

---

### Post by steelaz on 2005-12-12
Hey, thanks.

It turned out all I had to do is delete all my OLD partitions before starting install.
I used your advice on creating partitions and got pass that phase.

I was stuck on "Installing the base system" phase, but after searching forums, tried burning CD at lowest speed possible and it worked.

Still waiting for install to finish, crossing my fingers :)

---

### Post by steelaz on 2005-12-13
Its ALIVE! :)

Writing this post from my first linux install (on the same good old firefox)

Thanks for your help.

---

### Post by NotJustANewbie on 2005-12-13
No problem! Welcome to the community

---

### Post by amoun on 2005-12-13
Hi.

I first became aware of ubuntu via a free copy of 5.04 form Computer Shoper magazine.

I've created a disk for a proper install but stopped when it got to the partitioning part.

My fear is wiping away my current O/S and all my data.

 * I have two partitions of about 3G and 1G.
 * The 3G Partition already has some stuff on it, it's not too important and can be deleted, but there's about 1G used.
 * The 3G Partition is a primary partition the 1G is an extended partition.
 * They are both formatted as NTFS do I need to change it or will the install procedure do what's necessary?
 * winXP SP1 is my current O/S will I be able to select either at startup.



1. is that enough to install (version 5.1) which I've just requested.
2. does the install do anything other than put ubuntu on the partition I select.
3. will sytem restore undo everything if things go crazy?

Ok that's a start, waiting to see what it's like, will probably make a CD only version to test it out first.

All the best

Amoun

---

