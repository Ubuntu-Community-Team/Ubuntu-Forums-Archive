---
title: "what's accessing my hard drive?"
date: 2006-02-27
forum: Hardware &amp; Laptops
---

### Post by Ndlovu on 2006-02-27
Are there any tools to check what process is accessing the hard drive (like top for hard drive access)? For about a week now my hard drive is making a lot of noise, and during hard drive access the computer becomes frustratingly slow. This access usually has no clear reason, or seems excessive for the task (like switching between active applications).

I'd suspect an imminent crash, but smartctl doesn't report any errors. It could be that the swap partition is being used more than it used to, but I can't point to any configuration changes that would cause this or anything running that would eat up memory. Any thoughts?

---

### Post by taurus on 2006-02-27
Sounds like the swap partition problem to me!!!  How much RAM do you have and what is your swap partition, size?  Also, what window manager do you run right now?

---

### Post by Ndlovu on 2006-02-27
I'm running Gnome (Ubuntu 5.10 Breezy), on 256MB RAM. My swap partition is around 600MB. 

$ free -m
                  total       used       free     shared    buffers     cached
Mem:           242         236          6          0         14         87
-/+ buffers/cache:        134        108
Swap:          619         213        406

---

### Post by taurus on 2006-02-27
I find that running Gnome on a 256MB of RAM is pushing it to the limit!!!  It's still functional but extremely slow so you either have to upgrade your RAM, go with a lighter window manager like xfce4 or fluxbox/blackbox, or just live with it...

```

sudo apt-get install xubuntu-desktop fluxbox

```

---

