---
title: "Thinking about changing to Ubuntu, potential issues?"
date: 2008-05-09
forum: Hardware
---

### Post by seth1991 on 2008-05-09
I am thinking about changing my OS to Ubuntu. I have an IBM Thinkpad T40p. 1gb RAM, 40gb HDD, 1.6ghz Pentium M. I have a Ubuntu 6.06 disk and will likely install that if I go about it. I have a couple of questions.
1. If I install Ubuntu, will it permanently delete the IBM Windows recovery partition? I don't want it to do this as I don't have a Windows disk if I want to switch back (I am in the science field and some software is only windows based).
2. Are there any known issues with the installation of this version on this particular laptop? I am running the Live CD currently while typing this and have not come across any incompatabilities. 
3. Will websites such as Hulu.com or youtube work properly?
Thanks!
Seth

---

### Post by .nedberg on 2008-05-09
Testing the LiveCD is the way to go!

You could also try Ubuntu 8.04 as that version is newer and has better hardware support.

It is no problem to keep the Win partition, but you should backup important data first.

Youtube works fine, hulu I don't know, but if it uses flash I see no reason why it shouldn't.

---

### Post by LeoSolaris on 2008-05-09
Definitely download either 7.10 or 8.04. Much better hardware support. I have heard quite a few positive things out of IBM's with Ubuntu. Use the LiveCD, it will let you run Ubuntu off the CD before you install it to test hardware. (Video card will not run under the LiveCD, just so you're aware.)

When you go to install Ubuntu, use GParted to partition the hard drive. You will need to make at least two partitions, one main one for Ubuntu, and one for swap that's about a gig. I know for a fact that the easy partitioner that is built into the installer in 7.10 doesn't partition properly, I have no idea if that was fixed in 8.04. 

GParted is in System->Administration->GParted

Leo

---

### Post by seth1991 on 2008-05-09
> **.nedberg said:**
> Testing the LiveCD is the way to go!

You could also try Ubuntu 8.04 as that version is newer and has better hardware support.

It is no problem to keep the Win partition, but you should backup important data first.

Youtube works fine, hulu I don't know, but if it uses flash I see no reason why it shouldn't.

How do I go about keeping the Win partition for the IBM Recovery programs?

---

### Post by hallgeirl on 2008-05-09
> **seth1991 said:**
> How do I go about keeping the Win partition for the IBM Recovery programs?

During the installation of Ubuntu you can manually partition your disk - thus you can choose to keep whatever partitions you want. You need to make a new partition that is large enough for Ubuntu though (around 8GB should do nicely, though I'd recommend 10).

---

### Post by .nedberg on 2008-05-10
If you download 8.04 it will also include wubi. A way of installing Ubuntu as a "program" in windows. It will use the windows bootloader and you will not have to think about partitioning. Just tell ubuntu how much space it should use and away you go. If you don't like it you can remove it with "Add/remove programs" from Windows Control Panel.

---

