---
title: "partition showing up as a separate volume"
date: 2008-11-02
forum: General Help
---

### Post by iris-n on 2008-11-02
I'm having a cosmetic glitch, but quite annoying as it defies my ubuntu knowledge.

I have two extra partitions in my HD. One is /home, and don't show up anywhere as a separated volume, and that's what I expected. The other one is /home/<username>/video, and shows up as a separate volume both in my desktop and my Places. I wonder why, since I mount them with the exact same options in fstab, and if there's some way to make it disappear.

---

### Post by pauljz on 2008-11-03
It's not really the answer you want, but one solution might be to mount it elsewhere in your file system and just symlink it into /home/<username>/.  This is assuming the problem is caused by having the 3rd partition mounted somewhere within the 2nd, which it might not be at all.

You also might compare the two in /etc/mtab, for a hint about how to keep digging for a solution.

---

### Post by iris-n on 2008-11-04
Well, I wouldn't make a simlink to it, would just hide the problem rather than solving it.

And, you're right, tried mounting the partition to other places in my pc, it only appears when i mount it inside /home. And mtab shows no difference between them =/

---

### Post by iris-n on 2009-05-03
I've found a solution, in the case this is of anybody's interest. There's a gconf key in /apps/nautilus/desktop called volume_visible. It does exactly what you think. The downside is that you don't see anymore icons of mounted cds and pen drives. That is okay with me, since I like to have nothing on my desktop. 

A real solution would be finding out why partitions mounted under ~/ are considered a separate volume, but for me this is enough.

---

