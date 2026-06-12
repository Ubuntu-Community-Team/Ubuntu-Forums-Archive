---
title: "Video driver issue"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by Tamvolan on 2009-09-21
I'm running Jaunty, with a Radeon 9600 video card.  I've been told that my card is too old to get a proprietary driver for it.  However, this limits the games/applications that I can run.  It's a good video card, but the games/apps only see a generic card.

Is there another version of Ubuntu that I could run instead, in order to be able to install the "latest" driver that ATI does have on their site for my card?  I just can't go out and get a new card at this point...

I am an Ubuntu newb, so any help is greatly appreciated.

---

### Post by sideaway on 2009-09-21
8.10 will work with your card fine. Jaunty's xorg isn't compatible with older ATi drivers, however, 8.10 or 8.04 LTS will be fine, hope this helps :)

---

### Post by Tamvolan on 2009-09-21
What does the LTS mean?  Also, I see 8.04 LTS available for download, but I don't see 8.10.  Is one better than the other, and if the answer is that 8.10 is better, how can I get it?

---

### Post by UpsideDownFace on 2009-09-21
LTS means "Long Term Support" i.e it doesn't go out of date every 6 months.

I started with 6.06 LTS and now use 8.04 LTS. Presumably the next one will be 10.04 LTS. The number before the point is year, and the number after is month.

I care mainly about stability and consistency, so the latest releases are only of interest if they allow me to do something I couldn't do before.
The latest releases also have the latest bugs.

8.04 LTS desktop is being maintained till the next LTS is out.
To keep it up to date go into "System > Administration > Synaptic Package Manager" and choose "Settings > Repositories".
Then if you need restricted drivers, (like for several makes of video card), tick the boxes with descriptions which include"restricted".

I find it essential to have a separate /home partition, which I get on installation by choosing "Manual" for the partition method. Of course this means learning a bit about partitioning, but the separate /home partition allows you to do a relatively painless reload of the operating system if anything has gone seriously wrong - like it will for a beginner.

About once a year I open a terminal and type
sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude dist-upgrade
Usually this takes a long time, but normally works OK.

Linux is dead good once you get used to looking on google and forums.

---

### Post by Tamvolan on 2009-09-21
Thanks for that info :)  I'll download 8.04 LTS tonight, and see what happens.  Luckily, it's pretty early in the implementation, so I won't lose too much when I reload.

---

