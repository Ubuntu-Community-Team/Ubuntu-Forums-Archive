---
title: "Can you upgrade an (K)Ubuntu install you're not currently running?"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by Ubuntiac on 2009-09-03
I have two installs of Kubuntu. A 9.04 one which works perfectly, and a 9.10 one which had wireless stop working. Without wireless I'm having trouble updating it to fix the problem.

So is there a way to upgrade my 9.10 install from my install of 9.04?

Prize: 1 bag of virtual :popcorn: to the first correct answer! ;)

---

### Post by lykwydchykyn on 2009-09-03
Yes.

 - mount the root partition of the non-functional install in a folder on the functional one.
 - change to that directory in Konsole
 - mount proc and sys:
```

mount --bind /proc proc
mount --bind /sys sys

```
 - chroot into the current directory
```

sudo chroot .

```
 - run your favorite command-line update utility (apt-get/aptitude)
 - Exit by typing 'exit'

Now, where's my can'o'corn?

---

### Post by Ubuntiac on 2009-09-03
Mindblowing. I honestly wasn't expecting to get any reasonably sane answer to this question. Is it likely to be a problem that 9.10 is running on EXT4 and 9.04 is running on EXT3?


Oh, and by the way....


:popcorn:


Enjoy! ;)

---

### Post by lykwydchykyn on 2009-09-03
> **Ubuntiac said:**
> Mindblowing. I honestly wasn't expecting to get any reasonably sane answer to this question. Is it likely to be a problem that 9.10 is running on EXT4 and 9.04 is running on EXT3?

shouldn't matter; as long as 9.04 can mount the filesystem (9.04 supports ext4, so that shouldn't be a problem).

> 
Oh, and by the way....


:popcorn:


Enjoy! ;)

Yummy!

By the way, you can also do this from a liveCD.  I had to do this once or twice back in the day when an upgrade went wrong.

---

### Post by Ubuntiac on 2009-09-04
> **lykwydchykyn said:**
> By the way, you can also do this from a liveCD.  I had to do this once or twice back in the day when an upgrade went wrong.

Nice! Thanks again.

---

