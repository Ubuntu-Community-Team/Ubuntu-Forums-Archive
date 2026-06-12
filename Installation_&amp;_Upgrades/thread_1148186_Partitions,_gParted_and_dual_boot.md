---
title: "Partitions, gParted and dual boot"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by NlCK on 2009-05-04
Hello everyone, thought I would come here for some advice as I am having some trouble. Hope this is the right section for this question!

Anyway, basically I had a dual boot configuration on my computer (Ubuntu and Windows XP). 

I only used 20GB of my 250GB hard drive for XP (for Windows games). However, I soon realised this was not enough space for all my games. So I need a bigger XP partition. 

What I did was format my 20gb C drive and I used gParted to shrink my Linux partition by 80gb (leaving 100gb unpartitioned for XP). 

However, this did not do what I expected it to do. I ended up having two seperate chunks of unpartitioned space, one 20gb and one 80gb and I can't find a way to combine them.

So now, what I want to do is find a way to merge all of my unpartitioned space into one 100gb partition and install XP on that.

I have included this screenshot to show you what my partitions look like in gParted:

[img]http://img25.imageshack.us/img25/1714/partitionsq.jpg[/img]

Any help would be much appreciated!

Cheers,
Nick

---

### Post by NlCK on 2009-05-04
Also, why does it say my HDD is 233gb total when it should be a 250gb HDD?

---

### Post by Mark Phelps on 2009-05-04
You can't combine separate unallocated spaces if there are partitions between them.  You have to move the partitions so all the unallocated space is together.  In this case, you would have to move all the partitions to the left so that all the unallocated space is on the right.

If you use GParted to do this, be aware that it can take HOURS to do this.  So, Don't get impatient and interrupt it or you are likely to trash your machine in the process.

---

### Post by Mountaineer on 2009-05-04
I've just done almost exactly this on my drive.
Boot a live cd and then use gParted to move the linux partition across to the right.
This actually failed for me, luckily I had backed up the contents of the partition to another drive so I'd suggest you do that too if possible. ;)

After you reinstall windows in the empty space at the start of the drive, you'll need to reinstall grub so you can actually boot into linux.
You can do this from the live cd as well.

In the end, it'll be a lot easier to backup your data and start again from scratch, it took me a lot of fiddling to get grub to work because the UUID's no longer matched the partitions...

If you're feeling adventurous, I'd be happy to give more detailed direction. :)

---

### Post by NlCK on 2009-05-05
Thanks guys, problem solved!

If anyone else is still having trouble with this issue there is more advice about it here:
[http://gparted-forum.surf4.info/viewtopic.php?pid=20246#p20246](http://gparted-forum.surf4.info/viewtopic.php?pid=20246#p20246)

---

