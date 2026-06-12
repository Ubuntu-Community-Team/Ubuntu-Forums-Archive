---
title: "Dual boot with media partition"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by sreister on 2009-02-12
Hello, I'm fairly new to the linux experience, but do really enjoy it.  I was having problems with my cheap laptop and decided it wasn't worth it and used it as a guinea pig for ubuntu.  I love it.  Anyway, that got me started on the idea to dual boot my desktop with Vista and Ubuntu.  I pretty much understand how to do it, as I did go and try the Windows 7 beta and am already ready to uninstall it for Ubuntu.  

Basically, the only question I have is, is there a way to put all my media, Music, Video, etc., on a 3rd partition so both Ubuntu and Vista can share them?  And if there is, point me in a good direction as the best way to do it?  Thanks.

---

### Post by sleepyjon on 2009-02-12
Yes, you can do that. Just format the third partition as either NTFS or FAT32.

Also, once you will probably want to edit your fstab so it automatically mounts the third partition.

---

### Post by sreister on 2009-02-12
OK, I think I understand.  One problem I foresee is that I don't want to clean install my Vista and all it's media.  What would be the best way to move all my media to a partition first, and then create a ubuntu partition after I have the Vista and Media partition done?  

1.)Vista
2.)Create an empty Media partition
3.)Move all media to Media partition
4.)Take newly acquired space from Vista partition to make ubutnu partition

Does that sound reasonable?  The reason I ask is I'm dealing with only a limited amount of space, 250gb.  I currently have 40gb for the Windows 7 partition but will probably add on to that to have that be the Media partition.  After all that space on the Vista partition gets cleared from moving all my media to the Media partition, I should have enough for a ubutnu partition.  

I'm fairly new to all of this, so I would like someone to help me out with a game plan rather than doing this spur of the moment.  

Thanks again.

---

### Post by Mark Phelps on 2009-02-12
Sounds OK but use the Vista "shrink" function when you're done to reduce the size of the Vista partition; don't use Ubuntu or GParted.  If you do, you run the risk of corrupting the Vista boot -- which can only be fixed by booting into a Vista DVD and running Startup Repair.  If you have such a DVD, it's not a big problem.

---

