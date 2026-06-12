---
title: "[SOLVED] Missing disk space?"
date: 2008-07-20
forum: Hardware
---

### Post by tristevoix on 2008-07-20
Hello,

How's you all?

Right! Just decided to switch from windows to ubuntu yesterday, after having tried the live cd for some time. I'm still slightly overwhelmed, but not yet desperate! o_O

This is a question about hd space. Not sure if it's the right place to ask (though it looked like it from the search) and sorry if the question has already been asked and all (couldn't find an answer, but maybe I'm just too clueless!). Feel free to simply redirect me to those answers/tutorials if they exist. ^_^

Anyway, when I was using the live cd and wanted to search my hard disk, I would select the 320 gb media. However, now that I've actually installed ubuntu (Hardy Heron 8.04), things look different.

GNOME system monitor tells me (under file system) that I have 2 devices -- /dev/sda1 and gvfs-fuse-daemon. Both have total: 286 gb, free: 282 gb, available: 268 gb, used: 4 gb. I don't know how to make this add up to 320. And what's the difference between free and available?

Looks like I messed something somewhere!

Thanks for your help! ^__^

---

### Post by nbayiha on 2008-07-30
Dude i really can't understand your problem, but available mean the space you still can use in your disk.

---

### Post by Potatoj316 on 2008-07-30
When you installed ubuntu some of the space of the HD was partitioned off for use as swap.  Windows has a swap file and linux usually has a seperate partition which makes it look like you have a smaller HD.  Also the disk migh be avertised at 320GB but it is probably a little smaller.  

You can ignore the gvfs-fuse-daemon, from what I can see about that it just ends up showing you your HD twice.

---

### Post by evets25 on 2008-07-30
Also, the OS always reserves a little bit of space for the filesystem itself, which takes up some space. Think of your hard drive total capacity as open, empty space. You can't store anything in it without a way to organize it with containers and walls and whatnot. The filesystem is like a container or box, but even a box takes up some space. So if the Hard drive is 300gb, a partition is created on it, and a filesystem is created on the partition. The OS goes in the filesystem, and what's left over is your available capacity. As other people mentioned, another partition may have been created for swap, which also takes up some space.

Hopefully my explanation didn't make you more confused... >.>

---

### Post by tristevoix on 2008-07-30
Between boxes and walls and bad advertising I guess somehow it all sorts of make sense, so thanks mucho for the explanations, people! As long as it looks kind of normal, then I guess it's fine, though that's still lots of GB's under. ^_^

---

