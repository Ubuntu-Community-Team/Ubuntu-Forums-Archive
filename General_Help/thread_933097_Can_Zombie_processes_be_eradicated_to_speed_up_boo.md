---
title: "Can Zombie processes be eradicated to speed up boot time?"
date: 2008-09-29
forum: General Help
---

### Post by the8thstar on 2008-09-29
Hello,

I'm looking for a way to get rid of zombie processes that appear in bootchart when I turn on my computer. How can I do that?

Aside from that, I was wondering if removing these could speed up the boot time, or if this is a completely unrelated issue. Any ideas?

---

### Post by frankleeee on 2008-09-29
> **the8thstar said:**
> Hello,

I'm looking for a way to get rid of zombie processes that appear in bootchart when I turn on my computer. How can I do that?

Aside from that, I was wondering if removing these could speed up the boot time, or if this is a completely unrelated issue. Any ideas?

Zombies are not a problem they will go away shortly, if you go to system preferences sessions 1st tab you can turn off processes that are not needed.

---

### Post by the8thstar on 2008-09-29
> **frankleeee said:**
> Zombies are not a problem they will go away shortly, if you go to system preferences sessions 1st tab you can turn off processes that are not needed.

Thanks. How do I control that for processes at start up?

---

### Post by frankleeee on 2008-09-29
> **the8thstar said:**
> Thanks. How do I control that for processes at start up?

I am not quite sure of what you mean by boot chart. Are you looking at the system monitor to see the zombie. Zombies are actually stopped processes. As far as I know which is not a whole lot the zombies are not removable but disappear after a couple of restarts or days I'm not sure of the whole process of them leaving.

---

### Post by nsche on 2008-09-29
A zombie is just a process which has exited but has not yet been harvested by init.  It will get harvested and all resources will be returned shortly.

---

### Post by rbmorse on 2008-09-29
Frankleeee:  Bootchart is an application that records the start/stop times of processes during the IPL (Initial Program Load) and presents them in the form of a Gantt chart. It's in repository. 

I've never been able to decide if its really useful or not, but I had a couple of the charts printed out on an inkjet roll printer and then matted and framed the print for office decor. 

I know a couple of Gentoo users who are having a contest to see who can get have a bootable system with the shortest bootchart display, but beyonf that...

---

