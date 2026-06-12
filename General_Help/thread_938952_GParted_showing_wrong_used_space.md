---
title: "GParted showing wrong used space"
date: 2008-10-05
forum: General Help
---

### Post by GriFF3n on 2008-10-05
Hello everyone,

I have a dual boot with Vista and Ubuntu. My original Ubuntu partition was smaller than i wanted so i booted the live CD and increased the size of the partition with ubuntu on it. Now when i load back into my Ubuntu partition, GParted shows that i have the same about of unused space as i did before i increased the partition. For some reason it is telling me that the increased part of the partition is all used. Any ideas on how to fix this? Thanks,

GriFF

---

### Post by unutbu on 2008-10-05
If your Ubuntu partition is /dev/sda3, try this:```

sudo resize2fs /dev/sda3
```
(Change sda3 to the correct name for your Ubuntu partition).

This command resizes the filesystem on sda3 to make it  the same size as the enclosing partition.

---

### Post by GriFF3n on 2008-10-05
> **unutbu said:**
> If your Ubuntu partition is /dev/sda3, try this:```

sudo resize2fs /dev/sda3
```
(Change sda3 to the correct name for your Ubuntu partition).

This command resizes the filesystem on sda3 to make it  the same size as the enclosing partition.

You my friend...are a genius. That command worked perfectly. Heres a question for you though, how did you know to do that? I keep seeing everyone on these forums asking for help, and then someone presenting a magic code to fix their problems. Is it the fact that you've been using Linux for so long that you remember this stuff or did you have a magic elf tell you what to type? :) Thanks again for the help!

GriFF

---

### Post by unutbu on 2008-10-05
GriFF3n, thanks for the kind words. 

I think you guessed the answer -- I've been using Linux for a long time. The problem you faced has come up in the forums before, and I just happened to recall the solution.

Sometimes I'm lucky and can remember things, more often I can't remember what I had for lunch :)

---

### Post by GriFF3n on 2008-10-05
> **unutbu said:**
> GriFF3n, thanks for the kind words. 

I think you guessed the answer -- I've been using Linux for a long time. The problem you faced has come up in the forums before, and I just happened to recall the solution.

Sometimes I'm lucky and can remember things, more often I can't remember what I had for lunch :)

Haha, I guess when you work with something long enough it just becomes second nature. I love this user community, it really makes switching over from M$ a pleasure. Thanks again for your help unutbu, I'm sure you'll solve another one of my problems later down the road. Until then take care :)

GriFF

---

