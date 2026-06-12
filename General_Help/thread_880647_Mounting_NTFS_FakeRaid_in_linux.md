---
title: "Mounting NTFS FakeRaid in linux?"
date: 2008-08-05
forum: General Help
---

### Post by Sprax on 2008-08-05
How do I mount and access a FakeRaid" array running on two NTFS drivers from xubuntu?

In this case xubuntu runs on a regular ide / pata drive.

---

### Post by Sprax on 2008-08-05
Nevermind

apt-get install dmraid
dmraid -ay
then mount /dev/mapper/<name of partition>

I have no idea why it works or if I've mounted the array or just one disk, but it's read only so I'm not too worried right now...

---

### Post by cKats on 2008-11-16
I just tried it and I noticed that when you install dmraid it removes a lot of existing packages and replaces them with the dmraid ones. Also after you activate dmraid on your fakeraid disk it sets up all the raid drivers and mounts etc.. for you that is why it 'just magically works'.

The correct device to mount if your raid decide is called new_fakeraid and you need to mount the first partition on it is /dev/mapper/new_fakeraid1

But I think mounting just one of the images will work because dmraid handles the mapping automatically.

---

