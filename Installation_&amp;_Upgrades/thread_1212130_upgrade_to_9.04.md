---
title: "upgrade to 9.04"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by alimooghashang on 2009-07-13
Hi 
i have downloaded the 9.04 Desktop version
and now i have 8.04
how to upgrade it?


and one more question about repositories.
how could i add a folder of deb packages to repository to be listed in synaptic package manager?
is there any site which let me search and download packages in deb format and add thel to the folder i told before???

thanks

---

### Post by raymondh on 2009-07-13
> **alimooghashang said:**
> Hi 
i have downloaded the 9.04 Desktop version
and now i have 8.04
how to upgrade it?


and one more question about repositories.
how could i add a folder of deb packages to repository to be listed in synaptic package manager?
is there any site which let me search and download packages in deb format and add thel to the folder i told before???

thanks


Single or dual-boot?  With a separate /home or none?  

Basically,

1.  back up your files first
2.  Try out the liveCD and check for defects, hash, and try it out to see how it reacts with your system specs' and hardware.
3.  If decided, you can do a manual install.  **Know and identify which partition is Ubuntu ROOT (/)**.
a.  Choose Manual, choose the root partition you've identified, mount (/) and EXT3 or 4 (your choice) for format.
b.  No need to touch existing SWAP unless you want it bigger.
c.  If you have a separate /home.... mount /home but do not FORMAT.

If you need a guidance, post back a screenshot of gparted and/or

```
sudo fdisk -l
``` (**small L** not 1 nor i)

That'll give the forum a visual of what your HD looks like.

As for moving apps and dependencies, see this link if it works for you. Note, I have not tried it yet but am considering/reviewing it as well.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Good luck.  Back up first ;)

---

### Post by alimooghashang on 2009-07-13
thanks
but i have a folder on my desktop
how to add it to the repositories?
where to add this folder the same as CD added to the repositories?

---

