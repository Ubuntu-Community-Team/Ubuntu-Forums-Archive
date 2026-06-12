---
title: "[SOLVED] how do i reinstall ubuntu?"
date: 2008-11-03
forum: General Help
---

### Post by reinaldistic on 2008-11-03
i wanna uninstall ubuntu to install it again from scratch, this is because i installed ubuntu8.4 on top of kbuntu and now a bunch of device errors apear on my loading page after i upgraded to ubuntu 8.10
if i reinstall it and it comes back the same ill live with it, my ubuntu still loads to some extent, but i need to try it...
(this is also because in loading the kbuntu apears and not ubuntu ad i think it's screwing with my wine and some of my internet drivers)

---

### Post by bodhi.zazen on 2008-11-03
Boot the live CD and fire up the installer :)

---

### Post by reinaldistic on 2008-11-03
i tried alredy, the linux partition doesnt show up

---

### Post by reinaldistic on 2008-11-03
i wanna uninstall ubuntu to install it again from scratch, this is because i installed ubuntu8.4 on top of kbuntu and now a bunch of device errors apear on my loading page after i upgraded to ubuntu 8.10
if i reinstall it and it comes back the same ill live with it, my ubuntu still loads to some extent, but i need to try it...
(this is also because in loading the kbuntu apears and not ubuntu ad i think it's screwing with my wine and some of my internet drivers)

i have alredy tried to install from live cd, the new partition doesnt include the old partition, is like it wants to partition the win partition

---

### Post by Partyboi2 on 2008-11-03
When you get to the partitioning stage of the install choose manual and make sure the box to format your / is ticked. This should format and install ubuntu again.

edit: 
If you have your /home folder on its own partition make sure you do not tick the format box for /home and reset the mount point to /home.

---

### Post by cariboo on 2008-11-03
When you get to the partitoning section choose manual partitoning and right click on the partition and select edit, select the files system and then put a check mark in format the patition, do this  for all partitions except for swap as it gets formatted automatically.

Jim

---

### Post by sspletttstoeszer on 2008-11-03
I just had to reinstall Ubuntu 8.10 64 bit and every thing is working great now. First off I reformated my HD  and then did the install. It went like it was the first time it was install. O ya I'm doing dualboot with 2 HDs 1 for windows vista and the other for Ubuntu. You could try it just a thought.

Scott

---

### Post by reinaldistic on 2008-11-03
or my entire ubuntu os? i e i installed ubuntu in top of kbuntu, and some ppl tell me its the cause of my problems, so i wanna do that, noone seems to be able to reinstall ubuntu without messing with my xp partition

---

### Post by reinaldistic on 2008-11-03
i need to make it accessable to overwrite it in order to reinstall ubuntu

---

### Post by liferules on 2008-11-03
> **reinaldistic said:**
> i need to make it accessable to overwrite it in order to reinstall ubuntu

Try this driver:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

worked fine for me.

---

### Post by Monotoko on 2008-11-03
Watch it! If your duel-booting using GRUB, take head of the following (trust me, its hapened to me -.-)

Doing that will kill GRUB entirly, making you not even be able to get into windows (error 23 i think?)
What you want to do is just shove the LiveCD in the drive and install over the top of the ubuntu partition

thatl work :)

---

### Post by reinaldistic on 2008-11-03
i cant acces linux partition from live cd install it asks me to split up my old win partition thats why i need to do it!!!

---

### Post by mempman on 2008-11-03
you can reinstall ubuntu linux without messing up your xp parition.  Do this, by :

-boot off live cd
-select install
-select "manual partition"
-do not select formating of xp parition.

---

### Post by reinaldistic on 2008-11-03
so i got a problem and i have asked how to reinstall ubuntu, but they tell me to install over the ubuntu partition, the problem is the live cd just doesnt see my linux partition!!! windows partition has 146 gb and linux partition has 30gb but livecd wants me to partition a driver the size of 146 gb so i know its only the windows partition, all the attempts i have made various threads and everyone tells me the same thing please help!!!

---

### Post by Monotoko on 2008-11-03
Hmm, well, the method your thinking of here wont work unless you do the following:

1: Delete Ubuntu from windows then close windows down (you will now be unable to access windows until we do the other steps)

2: Insert LiveCD and install on the old ubuntu partition

3: Edit GRUB so that it can once again boot both Windows and Ubuntu

Im not responsible if your windows partition goes byebyes, as i have never tried this method myself, only i assume it would work.

---

### Post by LateNiteTV on 2008-11-03
how many damn threads are you going to make about this?

---

### Post by reinaldistic on 2008-11-03
i cant, live cd only sees 146 gb which is my current windows partition...

---

### Post by LateNiteTV on 2008-11-03
lol @ all your threads. relax dude.

[http://ubuntuforums.org/showthread.php?t=969882](http://ubuntuforums.org/showthread.php?t=969882)
[http://ubuntuforums.org/showthread.php?t=969863](http://ubuntuforums.org/showthread.php?t=969863)
[http://ubuntuforums.org/showthread.php?t=969816](http://ubuntuforums.org/showthread.php?t=969816)
[http://ubuntuforums.org/showthread.php?t=969708](http://ubuntuforums.org/showthread.php?t=969708)
[http://ubuntuforums.org/showthread.php?t=969730](http://ubuntuforums.org/showthread.php?t=969730)
[http://ubuntuforums.org/showthread.php?t=969791](http://ubuntuforums.org/showthread.php?t=969791)

---

### Post by Monotoko on 2008-11-03
please stop making seperate topics, its hard to follow what you have and havent tried, im trying to help you here, but its hard if theres 5 topics floating around of yours on the same issue

---

### Post by reinaldistic on 2008-11-03
well, in a lot of them ppl say install over the other and stop reading it...

---

### Post by Monotoko on 2008-11-03
I have given you a solution:
[http://ubuntuforums.org/showthread.php?t=969863](http://ubuntuforums.org/showthread.php?t=969863)

---

### Post by reinaldistic on 2008-11-03
if you dont like it give me an answer

---

### Post by louieb on 2008-11-03
Is this a WUBI install? Answer depends on your answer to this question. 

Your new but duplicate post are not the best way to get help. You will just get confused. I've notified the moderator. My guess is that the duplicate threads will get merged.

---

### Post by reinaldistic on 2008-11-03
no need i done it, the "manual partition" was the good answer... now 1 last question how do you mark as solved?

---

### Post by oldos2er on 2008-11-03
> **reinaldistic said:**
> i need to make it accessable to overwrite it in order to reinstall ubuntu

 Just reinstall Ubuntu; there's no need for unnecessary steps e.g. deleting it from Windows.

---

### Post by dmizer on 2008-11-03
Don't make multiple threads for the same problem. I've merged all your threads. It's impossible for us to help you when you do this.

Thank you.

---

### Post by Partyboi2 on 2008-11-04
> **reinaldistic said:**
> no need i done it, the "manual partition" was the good answer... now 1 last question how do you mark as solved?


[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

