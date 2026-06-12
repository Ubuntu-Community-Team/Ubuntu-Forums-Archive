---
title: "[SOLVED] Someone help! Btmgr is f'd up!"
date: 2008-08-18
forum: General Help
---

### Post by summuner848 on 2008-08-18
Alright well...
This may seem a bit out of place, but this is the community i am most familiar with.
--
I found my old windows xp student edition disk (redistributable) and tried to install it on my external hard drive. all went well with the install until it asks you to restart. it restarted, i did not touch anything as suggested, and it booted xp to the windows load screen, then to the blue screen of death. seeing as i already had vista on there, i thought to restart into vista and remove xp from there. so... i boot normally, nothing plugged in (except for power cord, and my laptop boots into something saying something about hard drive wasnt found blah blah. Well, it turns out that the boot manager has deleted the boot to vista option and thinks that the only choice is to boot to a corrupted xp which is on my external hard drive. so, i booted to the xp disk again, and went to the partition manager thing to find that vista and my vista recovery partition* are still installed. I find that my problem is that xp swapped vista's boot manager with its own... what fun. so, im left with a few options. boot linux, try and fix it from there; boot xp disk again, try to figure something out (not likely); or complain to M$ for about a week trying to explain this and just get **** back until i must buy a vista boot disk to either lose all my stuff (over 40 gb of files that i need) or buy a new xp disk and try to install xp on my laptop.

*its a compaq, meaning that it does not have a boot disk, but instead a recovery partition [some idiot thought that that it would make it more convienient. may i say EPIC FAIL!]
--

So.. to my point. Does anyone in this forum have a clue how i could fix my vista btmgr through installing linux and continuing from there?

P.S. sorry about the long *** post.

---

### Post by summuner848 on 2008-08-18
Anyone? No?

---

### Post by summuner848 on 2008-08-19
oh, come on! no one???

---

### Post by caljohnsmith on 2008-08-19
I don't think you made it very clear what your setup is. Do you have Vista installed on your internal HDD, and then you tried to install Win XP to an external HDD? Or something different? And do you have linux installed anywhere, or no?

---

### Post by summuner848 on 2008-08-19
Ok, to clear this up:

Laptop HDD
[Partition1] Windows Vista Home Premium
[Partition2] Windows Vista Home Premium Recovery

Western Digital External HDD 250GB
[Partition1] Just my documents and stuff (normal external files)
[Partition2] Windows XP Pro *Corrupted*

--

I think what im asking is, if i install a distro of linux, can i replace xp's corrupted boot manager with a vista bootmanager?

---

### Post by summuner848 on 2008-08-22
For anyone who has this problem:

What i did to fix this is download a vista recovery disc iso (120mb) by searching google for "Download vista recovery disk" and the first result or so gave me a torrent download at [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"). For torrents, you will need a BitTorrent client such as [utorrent]("http://utorrent.com/"). Then, when thats done downloading, you will need to burn the iso to a standard compact disc (CD) and then just boot to the disc.

---

