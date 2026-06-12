---
title: "Resizing ext3"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by geearf on 2005-12-28
Hello,

As I have not use windows for a lot of time, I wanted to shrink the ntfs partition to give some more room to my / .
I shrinked it with Qtparted without any problem, and I moved the partitions with PM to be able to add the free space to my /.
But my problem is that QTparted does not allow me resize the partition (I tried on a live-cd from ubuntu, kubuntu and gentoo, same problem ..), Gparted just crash now when I start it (before it used to start), and PM let me chose to resize and when I push apply, it says there is a problem (without saying which) and stops.

Is changing from 3.7 GB to 7GB impossible ? I don't have much free space on the partition (about 300MB now) could it be the problem ?

Thanks for any information,

---

### Post by plors on 2005-12-28
[QUOTE=geearf]Hello,

<snip>

Gparted just crash now when I start it 

<snip>
[/QUOTE]

That always interests me :)
Does it say anything if you start it from a terminal?
What versions of gparted/libparted do you use?

You could also try a livecd with gparted on it ( [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php") )

cheers..

---

### Post by geearf on 2005-12-28
Hello,

I don't get much output no, at first I see the scrolling bar searching for devices, and after a few minutes it freezes the comp, and then after it crashes gparted.

I used the gparted version on the live CD (for ubuntu and gentoo, and for kubuntu's live cd I used the one from the repo).

But anyway I tried various stuff, and finally by moving the partition around a few times in PM I was finally able to get it to the size I wanted, so it's good for me now.

Thanks,

---

