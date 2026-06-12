---
title: "Separate Home Partition"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by colintivy on 2009-03-09
Hi folks,

Looking towards installing 9.04 sometime (now 8.04).

I now have my Home folders in the main partition as installed from original 8.04 Live CD. The install was on a clean HD so no dual boot and Windows problems. I read that, when installing new or other OS's, it is desirable to repartition with an additional partition for Home stuff first so that there is no danger of overwriting archive material during the new installation. Is this so? If it is, where can I find the technique for doing so?? Clearly there could be a minefield of potential disasters awaiting.

Words of wisdom please!

colintivy.

---

### Post by Neo_The_User on 2009-03-09
I keep everything on 1 partition and if I'm doing kernel hacking, I use 2 partitions. 1 for '/' and 1 for '/boot'. I personally never have home on any other partition than '/' because it confuses me.

---

### Post by NWSmart on 2009-03-09
> **colintivy said:**
> Hi folks,

Looking towards installing 9.04 sometime (now 8.04).

I now have my Home folders in the main partition as installed from original 8.04 Live CD. The install was on a clean HD so no dual boot and Windows problems. I read that, when installing new or other OS's, it is desirable to repartition with an additional partition for Home stuff first so that there is no danger of overwriting archive material during the new installation. Is this so? If it is, where can I find the technique for doing so?? Clearly there could be a minefield of potential disasters awaiting.

Words of wisdom please!

colintivy.
Hi,

I have recently moved my /home out of the main directory so that if I upgraded then I would not 'loose' all my settings and docs.

I used the following link for advice

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I found this very good but do suggest you read through it carefully first. I had to use a couple of the modifications/adjustments and fixes for mine to work so it was not totally straightforward but using this guide it did work

Jim

---

### Post by myonta on 2009-03-09
I'm doing something similar: I'm reinstalling Ubuntu (from scratch) on a 320gb. I've already backed up my important files, so this is a clean partition and format. Also, unlike most posts I've found, this is a Windows-free box: Ibex only.

So, I want to get the most out of the drive. Here's what I'm thinking:
 - 200mb for /boot
 - 50gb for / (is this too much?)
 - ~260gb for /home
 - 6gb for swap (3x2gb RAM)

Am I'm being excessive in my allocation? I want to be able to easily reinstall in the future without losing my /home files.

Mainly looking for recommendations. Hope I'm not hijacking the original intent of the post.

~Jon

---

### Post by colintivy on 2009-03-09
> **NWSmart said:**
> Hi,

I found this very good but do suggest you read through it carefully first. I had to use a couple of the modifications/adjustments and fixes for mine to work so it was not totally straightforward but using this guide it did work

Jim

Hi Jim,

Thanks for that, I thought that there would be minefields ahead. Can you specify the Mods/adjustments that you found necessary please (if you think they are relevant). I have 60GB HD so will ahve to be a mite careful of sizing the new partition. I have printed out the ref you quoted for very careful study!!!

colintivy :P:P

---

### Post by colintivy on 2009-03-09
Hi Myonta,

Not at all, very much grist to the mill.

Some of us are just a bit envious of your set-up. My HD quite miniscule in comparison but all that I could afford!

colintivy :-)

---

### Post by kidux on 2009-03-09
I've had a seperate /home directory for years. Makes it so much easier when I upgrade or distro hop.

---

### Post by myonta on 2009-03-09
Good good. Just thought I'd check about that :)

I pretty much use this machine as an "everything" box. We've been an Ubuntu household for about a year and a half now. That being said, I want to maximize my /home partition (for RAW video & photo editing, network multimedia streaming, ISO storage, and whatever other high capacity files I can think of ;) )

I guess my part of the question boils down to how much room I need for the root install. Is 20gb enough? Is 50gb wasteful?

~Jon

(btw, partitioning /home seems like a brilliant idea to me, especially for system recovery/reinstalls. Makes me wish I could afford a secondary HDD for it, lol)

---

### Post by Neo_The_User on 2009-03-09
I mean there is nothing wrong with having a separate home partition but I personally just don't use one because I never needed it and I seek no benefits. :popcorn:

---

### Post by w2vy on 2009-03-09
I finally spent $50 and have a 320gb drive to upgrade my 12gb

It is one partition - yes I am going to break out /home and more

> **myonta said:**
> 
 - 200mb for /boot
 - 50gb for / (is this too much?)
 - ~260gb for /home
 - 6gb for swap (3x2gb RAM)


Is there a good reason for putting /boot outside of / ?
(maybe it is already.. df -k does not show it)

I have seen other suggestions of 10gb for /
What makes sense guys?

Swap in the range of 2xRAM size

I would also move /var/www to /home/www since webpages are data...

I guess any DB's (mysql etc) should also move storage to /home

tom

---

### Post by Neo_The_User on 2009-03-09
200MB for boot? Jeeze what are you compiling? I use 32MB it works just fine. And I compile a new kernel every few days (git snapshots)

---

### Post by myonta on 2009-03-09
Well, that's just it: I don't mind reinstalling, even recompiling, in the future, but I'd rather setup my partitions for the longterm so I don't have to repartition and mess around with the files in /home. I know you can repartition without losing data, but it's always a risk and, frankly, more trouble than it's worth if I setup good partition sizes now.

At least, that's my line of thinking. I'm more than willing to be corrected :D

As for the /boot being 200mb, I found that number on an Ubuntu-install how-to. At this point in time I don't even need a separate /boot, but why not future-proof? Though, other than grub, what's gonna be there?

Again, though, what's a good size for the / partition? Remember, size isn't really an issue.

---

### Post by Neo_The_User on 2009-03-09
I set '/' partition at 78 GB. (89 GB on my old PATA drive I never touch)

---

### Post by BGFG on 2009-03-09
> **Neo_The_User said:**
> I set '/' partition at 78 GB. (89 GB on my old PATA drive I never touch)

@myonta also, My '/' partition is 13 gigs and even with big 3D game packages it doesn't really cross 6 gigs if so much. so for '/' at most I'd recommend 15 gigs if you want to be REALLY safe. 

As to the separation of '/' and'/Home' I'd suggest it. Take my case: I prefer 'clean' installs rather than using the upgrade tool as upgrades can sometimes mess up dependencies.
So with Jaunty, as i inquired just yesterday, I can simply overwrite my existing '/' with the new Jaunty filesystem and have all my data in my /home directory intact.

---

### Post by Neo_The_User on 2009-03-09
70GB of free space doesn't hurt. Besides I compile stuff a lot from source so my HDD gets eaten up pretty quick depending on what I'm doing.

---

### Post by myonta on 2010-03-12
Hey all...

Don't mean to defibrillate this post, but thought I might *add a cavea*t from what I've learned after a year of use:

I went with approx. 15GB for '/', 280GB for '/home', and (originally) 75MB for '/boot'. Turns out after certain upgrades and updates 75MB isn't enough for /boot, so I g-parted it up to 100MB.

Well, now I'm in the same boat again so (and this goes out to you, Neo) I'll be resizing /boot to 200MB (ironically the figure I was looking at back before I had tried it).

All that said, the '/' partition is plenty big enough (only half used with lots of apps) and **a separate /home partition is a must for any and all Linux boxes** I'm responsible for (just simplifies upgrades, updates, system recovery, and whatever other problems may come my way). 

Like I said, I don't want to turn this post into the walking dead, but if you decide to make your /boot separate from '/' (not sure if that was the best choice for a single-boot system after all) give yourself the benefit of the doubt and go slightly bigger--else you may be risking your hard drive each time you run gparted & resize.

~Jon

(this is the program I'm talking about, if you need it: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) )

---

### Post by w2vy on 2010-03-13
> **myonta said:**
> 
I went with approx. 15GB for '/', 280GB for '/home', and (originally) 75MB for '/boot'. Turns out after certain upgrades and updates 75MB isn't enough for /boot, so I g-parted it up to 100MB.


Maybe you should look into removing old kernels from /boot

I checked my /boot and I have kernels going back to when I
started running the system in 2007.

My menu.lst also has each one listed, clean it up too.

Not many people would need more than 4 kernels in /boot

I would move stuff to /boot/old and then reboot and then delete.

That way if you move too much by mistake you can recover more
easily from a Live CD, if needed...

tom
ps. I am no expert in this area, just a thought...

---

