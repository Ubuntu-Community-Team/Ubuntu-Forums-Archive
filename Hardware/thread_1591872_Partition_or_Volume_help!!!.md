---
title: "Partition or Volume help!!!"
date: 2010-10-10
forum: Hardware
---

### Post by requimrar on 2010-10-10
HELP!!! I have a problem: I run a Dual-Boot with Windows 7 and Ubuntu 10.04 Long-Term Support. Anyways, I remember creating a 95GB Partition/Volume thingy (Sounds stupid I know, I didn't know Linux was supposed to be lightweight at that time ](*,)) with another 5GB for Swap. Anyways, now I reclaimed 45GB from the main Ubuntu thingy (Lets call them thingys, I get confused with partitions and volumes) with GParted on a Live CD and I have 45GB FREE SPACE left if I go back into the Windows disk management. Now, when I use a 3rd party program to try to add the 45GB of space to the Windows partition, [IMG]http://img840.imageshack.us/i/57731605.jpg/[/IMG]Image attached) the Windows thingy is in a separate "box" from the 45GB free space and the 50GB linux thingy which are in the same "box". Now, when I try to extend the Windows thingy, it can't detect the 45GB thingy. NOW WHAT??? PLEASE HELP!!!

Note: the 49.9 Linux EXT4 is obviously Ubuntu, the 49.9 UNALLOCATED is the one I'm trying to extend the Windows thingy with. PLEASE HELP!!!

---

### Post by Quackers on 2010-10-10
You can only extend a partition into free space if they are physically next to each other on the disc. Is this the case?

---

### Post by requimrar on 2010-10-10
Thats what I am trying to ask.

---

### Post by Martyn Thompson on 2010-10-10
Can you do a screenshot of the disk when using gparted?

If they are next to each other you might be able to shrink that partition then extend the Windows one into the space left. 

It may take a while for the software to make the changes. 

Additionally, like all processes like this, please take care to back up all your work from both OSes before you begin. I have used gparted many times and although this has never fouled up if you chose an unsuitable option you would be at risk of losing work.

---

### Post by Quackers on 2010-10-10
You say in your first post "image attached"  - it isn't. If we can see your partitions we may be able to help :-)

---

### Post by requimrar on 2010-10-10
> **Quackers said:**
> You say in your first post "image attached"  - it isn't. If we can see your partitions we may be able to help :-)

If you see a question mark before "Image Attached", click it. Else 

[http://img840.imageshack.us/i/57731605.jpg/]("http://img840.imageshack.us/i/57731605.jpg/")

---

