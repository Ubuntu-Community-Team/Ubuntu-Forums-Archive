---
title: "ATI Driver Issue (Black/Blank/White Screen)"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by the lush on 2008-12-09
This issue has been covered in numerous threads, but not a single one of them seems to contain a working solution so far.

The issue is that after installing, the machine displays nothing but a black, blank, or white screen, and appears to have been caused by the change to xorg 7.04, which doesn't work.

At this point, is there no choice but to wait for 9.04 and hope that the problem is fixed then, or is there going to be a new version of 8.10 that fixes the problem? Is anything being done to fix the problem? It was known about before launch, but still there don't appear to be any fixes.

I always install using Wubi from CD, but is there a possibility that when xorg is fixed, Wubi could download the new files if I install from the internet?

Alternatively, is there a way to get an install CD that has the older, working version of xorg?

---

### Post by jtravisp on 2008-12-10
I have the same problem. I also have had no luck finding a solution. The best luck I've had is when it boots into safe graphics mode, but I'm not sure why it does this.

Any ideas out there?

---

### Post by eb sol on 2009-03-25
same problem here :confused: ..

try to use the graphic save mode ( pressing F4 - second option )

---

### Post by starman38 on 2009-03-27
ditto this problem

---

### Post by JF_Sly on 2009-03-27
Not sure if it is the same but I had similar situation with Compaq EVO 510  when going to Ubuntu 8.1  

I Found this solution (from Jerry) on another post here in the forum.  Worht a shot.

Might be the same black screen problem I've been getting with Intel graphics since Aug 13. Excerpting Developers comments from my Launchpad Bug #259385:

"== Desktop effects and Intel 830MG and 845G video cards ==

There is a bug in the intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and freeze the system."

From what I've seen on the posts there are a LOT More chips that have symptoms like this.

My workaround is:
Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

If that works you're O.K. except no special visual effects. If you want to try compiz again, install with Synaptic.

Jerry

---

