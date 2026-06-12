---
title: "Ubuntu &amp; RAID 5"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by RikkiUW on 2009-04-04
I am currently dual booting with Ubuntu 8.10/XP on a single HD, but I am looking into switching to a RAID 5 array, and was wondering how this would complicate things. Will Ubuntu be able to detect and install the necessary drivers without problem or would I need to install them?

Thanks,
--Rikki

---

### Post by ronparent on 2009-04-04
A current ubuntu 8.10 install will not recognize a raid array. With out going into detail, you might want to use ubuntu to assemble the array form your current drive and them use the partitioner (gparted) to copy your current ubuntu and windows partition to the array. Involke grub from a terminal to put the grub bootloader on the array to boot the ubuntu installed on the array. Shut down, disconnect your current drive, and boot. I think this would work. meierafra or Mark Phelps night be able to jump in and verify or correct.

---

### Post by RikkiUW on 2009-04-05
You mean this would put my current partitions onto a completely new array without reformatting? But how would I expand my XP partition, or would I be able to? I'm new to Ubuntu so some kind person will have to either give me detailed instructions or point to to instructions.

Thanks!
--Rikki

---

### Post by Slim Odds on 2009-04-05
Why do you think that you want RAID5?

---

### Post by RikkiUW on 2009-04-05
My main goal is redundancy but I would also like a speed increase as well. I could use RAID 1 but I'd prefer 5. Having said that I'm not sure how much of a speed increase I'd get but still...

---

### Post by Slim Odds on 2009-04-05
You're still not clear about why you prefer 5 over 1.

You're probably better off just using 1. It's much simpler and will likely perform better depending on how you use it.

Also, if you're a home user, even RAID1 is probably overkill. The only thing that these types of redundancy give you is the ability to hot swap drive without reinstalling your OS (perhaps without even powering down).

You still need to have a good backup strategy.

To setup RAID, you'll either need to use the alternate install CD or read up on how to load the proper tools during a Live CD session.

I've personally setup RAID0 using the alternate install CD and it's not too bad, but a little tricky the first time you do it.

---

### Post by RikkiUW on 2009-04-05
Maybe I will go with 1... The reason I want to set it up is because my external HD is failing. I can still get stuff off of it but really slowly. I used the external for portable storage but I don't really need it to be portable anymore so I'm just putting it on my desktop. I want redundency so that if I have another HD fail I won't risk loosing all of my stuff. I still back up but the thing is I don't do it that often as I usually forget, etc.

Having said that, correct me if I'm wrong but if I go with RAID 1 I can just hot-swap the second hard drive occasionally (like once a month or so), let it rebuild, and use the one I removed as an external backup.

Okay I think we've convinced myself, I'll go with RAID 1. Would you be able to tell me in more detail (or point me to instructions) how to do it? I am curious though, how would RAID 1 perform better than 5?

Thanks,
--Rikki

---

### Post by Slim Odds on 2009-04-05
> **RikkiUW said:**
> Would you be able to tell me in more detail (or point me to instructions) how to do it?

I used the alternate install CD which loads mdadm by default (for software RAID).

You create the partitions that you want to RAID and set them as Linux raid autodetect (type 0xfd).

Now this is the tricky part. If this is the first time that you've setup these partitions, you need to save them to disk and reboot (even if the installer doesn't tell you that).

Next time through the installer you'll see a new item at the top of the screen in the partitioner that allows you to combine the RAID partitions into the array that you want.

From there it's a breeze....

If you do the same thing from the Live CD, you actually have to load the Live CD and then install mdadm manually. The reboot still applies (and don't forget to load mdadm again).

>  I am curious though, how would RAID 1 perform better than 5?Random writes with RAID5 are very slow. It's better used for systems that are mostly "read" oriented (like database search type system).

---

### Post by RikkiUW on 2009-04-05
Thanks a lot. I won't have time to install it until the beginning of May or so (exam time...). I'll post back if I have any trouble.

Thanks!
--Rikki

---

