---
title: "GParted during install: accidentally moving Windows partition?"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by skullmunky on 2009-10-15
I'm using GParted to partition a hard drive before installing Ubuntu.  I resized the Windows partition to free up space, created a new ext4, and hit apply.  Now I see it's also "Moving the partition to the right", creating a 7.85 MB bit of free space before sda1 (windows).  This is taking forever and I don't think I told it to do that.

- is that normal?
- will it cause problems?
- when this happens, can you cancel it or will that bork the whole drive?

---

### Post by phillw on 2009-10-15
> **skullmunky said:**
> i'm using gparted to partition a hard drive before installing ubuntu.  I resized the windows partition to free up space, created a new ext4, and hit apply.  Now i see it's also "moving the partition to the right", creating a 7.85 mb bit of free space before sda1 (windows).  This is taking forever and i don't think i told it to do that.

- is that normal?
- will it cause problems?
- when this happens, can you cancel it or will that bork the whole drive?

let it finish !!!!

---

### Post by phillw on 2009-10-15
Hi,

Not quite sure what you did, it usually creates the linux partition after the windows partition. Although I seem to recall you do have an option to create before or after - I'm guessing you selected before.

The most important thing is to leave it be whilst it is moving partitions around.

Once it is done, you should be able to install as per usual.

Phill.

---

### Post by Mark Phelps on 2009-10-17
For your sake, I hope the answer to the question "was this Vista you are messing with" is a NO, otherwise, if you DID move it, you  most likely corrupted the OS, rendering it unbootable.

---

### Post by skullmunky on 2009-11-15
thanks ... everything worked fine, it just took a long time :)

---

### Post by efflandt on 2009-11-15
You have to be careful with those little scroll arrows when setting partition sizes because if you press the wrong one, on the wrong number, it might shrink the partition from the wrong end.  It took so long because it had to move all files the same distance into the new partition.

So you probably created some dead space  on your hard drive.  Some day when you feel bold and have time to kill, you could expand the partition to fill the void.

---

