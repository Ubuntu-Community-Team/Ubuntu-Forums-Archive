---
title: "Repartitioning?"
date: 2006-03-10
forum: Hardware &amp; Laptops
---

### Post by LadyDoor on 2006-03-10
Hi!

So...stupid question time. When I was installing Ubuntu, I ended up making my / partition waaaaaay too big 'cause I had /usr on there as well and thought it needed a lot of room, and now I regret it because I want more room for my /home partition...does anybody know how I would go about (safely) creating a /usr partition (I have some extra room to do that with), shrinking the / partition (I'm afraid of unmounting it while my computer's running, as the gparted claims is necessary--it seems like no good could ever come of that), and adding the difference (there's a *lot* of room (about 10 GB) I don't think will ever get used for anything if it's on either / or /usr) to my /home partition?

Any help would be much appreciated. And for clarity, here it is again:  create /usr and somehow get files over to it, shrink /, add space to /home.

Many thanks,
Door

P.S.:  Wow, I sound almost tech-savvy. But do not be deceived--I merely learn as I go along, especially when there's a problem.

---

### Post by glug101 on 2006-03-10
We all learn best from problems ;)

I can get you up to the step fo 'shrink /'.  changing a partition size is something that I have never cared to get into because every time I read about it there are a ton of warnings saying 'you will loose all memory, including your childhood, if this goes wrong'.  (well, maybe I'm paraphrasing ;) )

1. Format the free space for the /usr partition.
2. Use cp to copy all of the files from /usr to the new partion.
```

cp -Rp /usr/ (mount point of new usr partition)

```
3.  Edit your /etc/fstab so that it mounts the new partition to /usr.

This part will get the new partition mounted as /usr, and you shouldn't loose any data.  If your system works fine, you can mount your root partition with the livecd and delete the contents of /usr (from the root partition) to reclaim the space.

Although, if you have enough space, you might be better off just resizing the root partition in order to accept the larger home directory.

Cheers! :D

---

### Post by LadyDoor on 2006-03-11
Interesting, thanks...

But are there any options if I don't have a live CD? And if anyone has any suggestions for the rest...that would also be much appreciated.

--Door

---

### Post by KansasJoe on 2006-03-11
May not be the perfect answer but if you just installed ubuntu why not just reinstall and then the partitioner will come up again and you can make all of your changes there?  I believe gparted will also do the job

---

### Post by LadyDoor on 2006-03-11
Well, I did not just install Ubuntu; I did it months ago, and only just now have had occasion (i.e., an undersized /home partition) to see the error of my partitioning ways--I don't want to lose all my data and installed programs. Also:  I was using gparted, but as I said in my first post, it says that to do anything to a partition it must first be unmounted--but I think unmounting, say, / would be a very bad idea while my computer's running. But thanks.

However, if anyone has any information regarding a way any of the stuff stated in the first post can be down without losing all my data, it would be much appreciated...

--Door.

---

### Post by LadyDoor on 2006-03-11
*Or how anything from the first post can be *done*, even.

---

### Post by plors on 2006-03-12
without reading your problem thoroughly i guess you need to run gparted from a [livecd]("http://gparted.sourceforge.net/livecd.php")

---

