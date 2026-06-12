---
title: "Video driver question"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by TomB19 on 2009-05-02
My question is this:

If I can boot the 9.04 live install CD and the desktop looks and functions properly (which it does), does that mean the installed 9.04 desktop system will also work properly?

It's an AMD 790GX/SB750 system.

---

### Post by Monsieur Gonzalez on 2009-05-02
It should, but take a look at this [thread here]("http://ubuntuforums.org/showthread.php?t=1133950"). Looks like Ati/AMD does not care as much for its linux costumers as Nvidia.

---

### Post by TomB19 on 2009-05-03
**The x68_64 Kubuntu 9.04 install**

I told myself I was going to wat a couple of months for Jaunty to stabilize before installing it on my main machine.  I've had too many problems in the past to take the risk and Ibex was working perfectly.

I did a Jaunty upgrade on my Dell Optiplex machine at work (Intel IGP) and it worked extremely well.  It was slow as molasses until I shut off desktop effects.  Other than that, it was pretty much perfect.

Yesterday morning, I found myself backing up my root partition for the purposes of installing Jaunty.  I swapped boot partitions (I boot from a USB stick: since all of my partitions are RAID5 arrays it makes it easy to boot with any kernel).  While I was doing it, I knew it was a mistake and I knew there was a strong possibility the install would fail.

The install was a gong show.  I had to do it four times to get the process to complete.  I've got so many partitions, the graphical partition manager can't display them all on screen and it has no facility for scrolling (6 drives with 3 partitions each + 4 drives with 1 partition + 2 USB sticks + 3 MD arrays).  I had to install with the alternate install which is not nearly as sorted out as the GUI install process.  The installed OS came right up, though.

There are several bugs.  The application launcher goes into a state where it won't open sometimes but I can get it un-stuck by... right click->switch to classic menu style->right click->switch to kickoff menu style.  Sometimes I get an odd blue box that appears above the pager panel for seemingly no reason, even when the mouse isn't even in the neighborhood, but a refresh takes care of that.  There are other bugs too but they aren't that significant.

I like it and look forward to improved stability in the next few months.

# uname -a
Linux static65-87-244-151 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

Hardware

AMD 9850be (Phenom 1, 4 cores @ 2.5 GHz)
Foxconn A7DA-S (AMD 790GX/SB750, AM2+)
8 GB RAM
DVI connected Flat panel @ 1680x1050


The two reasons I upgrade are:

- no kweather panel applet in Ibex
- Ktorrent in Ibex does not support RSS feed automation


Both of these Ibex shortcomings have been rectified in Jaunty.



:guitar:

---

### Post by TomB19 on 2009-05-03
Perhaps this thread should move to Testimonials & Experiences.

If a moderator were to do that, I would consider it a favor.  :)

---

