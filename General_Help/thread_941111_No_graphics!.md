---
title: "No graphics!"
date: 2008-10-07
forum: General Help
---

### Post by DonZabu on 2008-10-07
I installed Ubuntu through Wubi, and now I don't have any GUI! All I have is a command prompt that I don't know jack about.

Help please?

---

### Post by Sealbhach on 2008-10-07
You may have installed the no graphics version (called the alternate version).

Try this command and see what happens:

```
Xorg -configure
```

.

---

### Post by ago on 2008-10-07
> **DonZabu said:**
> I installed Ubuntu through Wubi, and now I don't have any GUI! All I have is a command prompt that I don't know jack about.

Help please?

What exactly do you see on the screen?

---

### Post by DonZabu on 2008-10-19
> **ago said:**
> What exactly do you see on the screen?

Something about a BusyBox.
The freaky thing is, the previous time I had turned it on, I had graphics and everything!

---

### Post by peril62 on 2008-10-19
Had same problem! Have just installed wubi, and when rebooting and selecting ubuntu, rather than a graphic environment, a black page kind of MS Dos console appears with a Groub> or some similar word on the screen. I installed in an external USB disk and installation seemed all OK (through Windows i can see the disk with an Ubuntu folder). What should I do from that black page with the Groub>?
thanks

---

### Post by anhvu2875 on 2008-10-19
> **DonZabu said:**
> Something about a BusyBox.
The freaky thing is, the previous time I had turned it on, I had graphics and everything!

log in Wins , go to the disk u installed Ubuntu on , then click right mouse button > Properties > Tools > Error checking > press ''check now'' > tick to choose ''automatically fix the system errors'' > Start > it will ask u to restart the PC > press Ok ( dont restart pc by pressing restart button on PC ) . after that u can choose Ubuntu when the PC restarts into BL screen ! hope that will work !

---

### Post by DonZabu on 2008-10-27
> **Sealbhach said:**
> You may have installed the no graphics version (called the alternate version).

Try this command and see what happens:

```
Xorg -configure
```

.
Didn't work.

---

### Post by ago on 2008-10-28
> **DonZabu said:**
> Something about a BusyBox.
The freaky thing is, the previous time I had turned it on, I had graphics and everything!

boot in windows and run chkdsk /r

---

### Post by ago on 2008-10-28
> **peril62 said:**
> Had same problem! Have just installed wubi, and when rebooting and selecting ubuntu, rather than a graphic environment, a black page kind of MS Dos console appears with a Groub> or some similar word on the screen. I installed in an external USB disk and installation seemed all OK (through Windows i can see the disk with an Ubuntu folder). What should I do from that black page with the Groub>?
thanks

It is possible that your USB disk is not accessible at boot time. So it is not possible to launch ubuntu from there. Either install to hard disk or use a more recent grub4dos version (see the sticky thread on grub).

---

