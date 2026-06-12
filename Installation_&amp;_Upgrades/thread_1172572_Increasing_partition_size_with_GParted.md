---
title: "Increasing partition size with GParted"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by yaroslavvb on 2009-05-28
I booted from GParted LiveCD and I'm trying to increase size of my main partition, sda1. GParted is letting me increase size of /dev/sda2, but not of /dev/sda1, possibly because it's blocked in by /dev/sda1.
Currently partitions look like this

11GB  /dev/sda1
.5 GB /dev/sda2, inside it is /dev/sda5 (linux-swap)
39 GB unallocated space

What's the best way to increase /dev/sda1 size to 50GB?

---

### Post by drs305 on 2009-05-28
Since you say sda5 is inside sda2, sda2 is the extended partition. You must first unmount sda5 (swapoff) and move it to the right. Might as well put it all the way to the far right edge.

Next shrink sda2, leaving space to the left.

Finally, expand sda1 to the right.

It's often helpful to include a snapshot to let us see things more clearly. If what I've surmised isn't the correct situation, that would help.

---

### Post by yaroslavvb on 2009-05-29
Still no luck, here's what I'm doing

Booting up from GParted LiveCD
[img]http://yaroslavvb.com/upload/gparted-troubleshooting/Picture%201.png[/img]

sda5 (linux-swap is unmounted)
[img]http://yaroslavvb.com/upload/gparted-troubleshooting/Picture%202.png[/img]

but, I can't move it anywhere
[img]http://yaroslavvb.com/upload/gparted-troubleshooting/Picture%203.png[/img]

the enclosing partition (sda2) can be increased in size, but only from the right, and I can't move it either (the left slider doesn't respond)
[img]http://yaroslavvb.com/upload/gparted-troubleshooting/Picture%205.png[/img]

My guess is that I can't move them because there's data in linux-swap partition.

---

### Post by merlinus on 2009-05-29
Might the problem be that sda2 is an extended partition?  If so, you can try deleting it entirely, starting with swap, and then you may be able to enlarge sda1.

---

### Post by drs305 on 2009-05-29
My original instructions assumed the sda2 extended partition took up the rest of the disk, which isn't the case. Now that you have provided pictures...

You could simply delete the swap and extended partitions and recreate them but we would have to then deal with the changed UUID of the swap partition. Not a big deal but this method will stay entirely within gparted without editing several system files along the way.

Back up any important data before doing this.

LiveCD
Again, make sure the swap (sda5) is off (swapoff).

Expand sda2:
Select sda2 from the bottom section of gparted.
From the top menu, Resize/Move and slide the right edge it all the way to the right. It should now take up all the free space on the drive (everything but sda1).

Move sda5:
Highlight sda5 (swap).
Resize/Move and drag it to the far right. You don't have to change the size.

Shrink sda2:
Select sda2 (extended partition), Resize/Move.
Drag the left edge of sda2 to the right as far as you want. The "space before" window will show how much space you will be giving to sda1. The right edge of sda1 should now be touching the left edge of sda2.

Expand sda1:
Select sda1, Resize/Move, and drag the right edge to the right to include the new free space. 

Now you should see a larger sda1, sda2 taking up all the remaining space, and at the far right (and still inside sda2) sda5.

---

### Post by yaroslavvb on 2009-06-01
Thanks drs, I followed the instructions, and it worked

---

