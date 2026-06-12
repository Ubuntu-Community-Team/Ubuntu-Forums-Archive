---
title: "Problem mounting NTFS partitons"
date: 2008-07-22
forum: General Help
---

### Post by Gjoko on 2008-07-22
I run a dual boot XP/Ubuntu and recently my brother messed up XP with a ton of viruses and stuff so it just boots and then nothing. I've been trying to a cces the partitons but since then they can't seem to open untill now they opened just fine might it be the messed up Xp is doing something to them? It says unable to mount volume altho i entered the corect pasword both usr and root paswords are set the same so i don't confuse them.

---

### Post by bodhi.zazen on 2008-07-22
Boot a live CD

```
sudo mount /dev/sda1 /mnt
```

Assuming window is on sda1.

Post any error messages

You will now have mounted windows ro on /mnt -> data recovery. Just be careful how you go about it.

---

