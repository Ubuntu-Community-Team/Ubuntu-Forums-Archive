---
title: "How to check memory usage?"
date: 2008-07-31
forum: General Help
---

### Post by Disastorm on 2008-07-31
I was just wondering how to check memory usage? The Gnome System Monitor shows a list of processes and some kind of memory usage there, but then when u add them up, it doens't equal what it says the total memory usage is??

---

### Post by Joeb454 on 2008-07-31
In a terminal type ```
free -m
```

You want to look at the middle line (where it says "+/- buffers")

---

### Post by OutOfReach on 2008-07-31
In the System Monitor there is a tab called 'Resources' there it tells you how much Memory your using.

Or you can open up the terminal (Applications>Accessories>Terminal) and type in 'top' (with out the quotes). And it'll tell you at the memory usage, CPU usage, etc...

---

### Post by Disastorm on 2008-07-31
Well, I'm just wondering why is the memory usage under Resources alot more than the memory usage (of each process added together) under Processes?

---

### Post by Cactus Sediento on 2009-05-19
same question here

---

### Post by Cheesemill on 2009-05-19
Are you sure that System Monitor is showing you all of the processes?
Click on View and make sure that All Processes is selected.

Cheesemill

---

### Post by pesho318i on 2009-11-05
@Disastorms: Because the memory usage under Resourses also includes the swap memory that you have allocated when installing linux. It might be that none of this memory is in use at some point. Therefore the difference.

---

### Post by aminalid on 2011-03-25
The swap memory is displayed separately under Resources...

I also see the memory usage under Resources much more that the sum of separate running process under Processes.
And yes I am displaying all processes.

I encountered this when my system was consuming almost all available memory, so went to processes to check the responsible process, but there everything looks normal, and the sum didn't match.

Anybody have an idea how to correctly figure this out.

---

