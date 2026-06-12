---
title: "Partitioning"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by crazlunatic on 2006-01-14
Can anyone give me a link to a guide where I can dual-OS my Windows XP Pro and Ubuntu Linux.

Also, I have 20 GB free space on my C Drive. When I go to my Linux partitioner wizard while installng, it displays that I only have 5.2 MB space left!

Why is that?

Thank you for your help.

Also if you can find like, a step to step guide to installing, that would also be great.

---

### Post by aysiu on 2006-01-14
[QUOTE=crazlunatic]Can anyone give me a link to a guide where I can dual-OS my Windows XP Pro and Ubuntu Linux.[/QUOTE] The fifth link of my signature is a great place to start.

---

### Post by crazlunatic on 2006-01-14
Yea, but can anyone please explain the extremly low free space?

---

### Post by SilentCacophony on 2006-01-14
What do you mean by 'free space'?

If you've already got ubuntu running, and you're speaking of the **free RAM**, then it's because linux *dynamically* uses free RAM for buffers/cache to improve system performance. It in no way reduces the actual free RAM.

For instance, if I open a terminal-emulator and issue the **free** command:

```
brian@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:        451680     423864      27816          0      64556     143104
-/+ buffers/cache:     216204     235476
Swap:      1020088          0    1020088
```

The top line shows 423864 bytes used and 27816 bytes free, but the second line explains that 216204 bytes are all that are actually used if you discount the buffers/cache usage, so 235476 are available for use if needed.

Note that the swap is not used at all. :)

Otherwise, if you're speaking of harddisk space, then that's entirely up to how you partition your drive.

---

