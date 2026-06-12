---
title: "core 2 duo and top command?"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by hp22s on 2007-08-20
hi all,
is it normal that feisty fawn' s 'top' command only shows one cpu.
the bios says, that i have 2 cores...

regards
guido

---

### Post by newlinux on 2007-08-20
It's normal on my dual cores. I use htop instead which shows both cpus (it's in the repos).

---

### Post by ozgurcakmak on 2007-08-20
could very well be like that because top was written in the good old days when computers had one cpu and they had to watch it like crown jewels...

For seeing whether distro had supported your dualcore, go to System->Administration->System Monitor and look for 2 cpu graphs...

---

### Post by Golyadkin on 2007-08-20
I use htop as well on my dual-core (AMD Athlon 64 X2). If you want something with a graphical interface, try the System Monitor that comes by default in Ubuntu.

---

### Post by Golyadkin on 2007-08-20
> **ozgurcakmak said:**
> could very well be like that because top was written in the good old days when computers had one cpu and they had to watch it like crown jewels...


Not quite ozgurcakmak :D SMP (symmetric multiprocessing, also knowns as dual processors) was first implemented on the Burroughs B5500 in 1961, which is a bit older than the top program :). The first implementation of top was in April of 1984... more than 23 years later :)

---

