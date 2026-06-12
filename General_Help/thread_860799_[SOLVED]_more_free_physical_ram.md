---
title: "[SOLVED] more free physical ram?"
date: 2008-07-15
forum: General Help
---

### Post by chris4585 on 2008-07-15
lately i've seen my computer's ram usage go up to about 50% out of 2GB.  how can i change my system to use a little more swap than physical ram?

---

### Post by p_quarles on 2008-07-15
The short answer is that you don't want to. Doing so would just make your computer overall more sluggish. 

The preference for swap usage is the "wm.swappiness=X" line in /etc/sysctl.conf. By default it is set to 60, which is moderate swap usage. Normally those of us with 1 GB of RAM or more change this to 0, which minimizes swap usage aggressively. I've never heard of anyone with a modern computer increasing the value of this setting.

---

### Post by iaculallad on 2008-07-15
> **chris4585 said:**
> lately i've seen my computer's ram usage go up to about 50% out of 2GB.  how can i change my system to use a little more swap than physical ram?

You're Ubuntu system will automatically do that task for you, of using/accessing the SWAP when it detects that you are running out of RAM when using applications.

Using the RAM is much better than using SWAP (SWAP is slower, actually).

You can view what processes are using your resources:

```
top
```

---

### Post by chris4585 on 2008-07-15
> **p_quarles said:**
> The short answer is that you don't want to. Doing so would just make your computer overall more sluggish. 

The preference for swap usage is the "wm.swappiness=X" line in /etc/sysctl.conf. By default it is set to 60, which is moderate swap usage. Normally those of us with 1 GB of RAM or more change this to 0, which minimizes swap usage aggressively. I've never heard of anyone with a modern computer increasing the value of this setting.

alright.  I understand most things about swap.  One thing that puzzles me is why does ubuntu give me 5gbs of swap space when i never use no more than 32mbs... thats dumb if you ask me but meh.  I was just really curious

---

### Post by chris4585 on 2008-07-15
> **iaculallad said:**
> You're Ubuntu system will automatically do that task for you, of using/accessing the SWAP when it detects that you are running out of RAM when using applications.

Using the RAM is much better than using SWAP (SWAP is slower, actually).

You can view what processes are using your resources:

```
top
```

thanks for the comments friend.  also htop is better IMO, i understand top comes with ubuntu is probably why you said that. :)

---

### Post by p_quarles on 2008-07-15
> **chris4585 said:**
> alright.  I understand most things about swap.  One thing that puzzles me is why does ubuntu give me 5gbs of swap space when i never use no more than 32mbs... thats dumb if you ask me but meh.  I was just really curious
I agree -- it is dumb. I manually partition my drive and give it about 700 MB for the swap partition. 

The default is to dedicate hard drive space equal to twice the size of the available memory. For systems with more than 512 MB of RAM, this ends up being overkill. 

The one instance where swap > memory is inherently useful is with hibernate: if you rely on that feature, you'll want slightly more swap than you have memory (because everything in memory is dumped to swap).

---

### Post by chris4585 on 2008-07-15
ah, ok, thanks for the info.  I might possibly make my swap partition smaller, this is a desktop and i never use hibernate.

---

### Post by Canis familiaris on 2008-07-16
I always keep my SWAP size to be = RAM size + 256MB
I do so that I can hibernate.

---

