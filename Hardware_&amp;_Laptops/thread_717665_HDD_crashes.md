---
title: "HDD crashes"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by Gouz on 2008-03-07
Greeting

I formated my external HDD into NTFS
And now that I am trying to copy files from an other HDD the first one crashes and then it can't be mounted again.
i have all ready tried to format it even in windows but with out any success.
it just crashes without any error msg or anything..

Ideas?

---

### Post by {BzF}~JOKesTER on 2008-03-07
If Your Talking About The External HDD Crashing The Primary - From Ubuntu {I Assume}

I Would Personally Recommend Formatting The External HDD To FAT - Which Both Windows And Ubuntu Support Quite Well.

However If Your Using An External HDD In NTFS - Make Sure That You Have The:

libntfs-3g12

Package On Your Ubuntu.

You Can Get It In Synaptic Package Manager.

Hope This Helps - Keep Me Updated

:popcorn:

---

### Post by Gouz on 2008-03-07
hmm no

maybe i explained it poorly i am sorry
I have an external that runs on nfts.
with windows it runs just fine and I can read and write from it.
when I am trying to perform any action in ubuntu the external crashes not the primary hdd which holes the OS.

libntfs-3g12 I all ready have this one
I don't wanna use FAT.
I am trying to test it with ext3 and see if it will work.
I will keep you update and if you have any idea how to solve it tell me

cheers

---

### Post by {BzF}~JOKesTER on 2008-03-07
What Do You Mean By :

The External Drive "Crashes" - Does It Unmount - Give You An Error Code What?

I May Be Able To Figure This One Out If You Can Give Me More Info On The Problem.

---

### Post by Gouz on 2008-03-07
/dev/sdb1 acts as it is uplugged
i get the msg that say that I should use umount to avoid damage or datalose.
and this happened only when I am trying to write something on the hdd.
the only "extra" msg I get is 

-Error "File not found" while copying "/media/Helix/music

EDIT: and I know that there is data, I can see it.

---

