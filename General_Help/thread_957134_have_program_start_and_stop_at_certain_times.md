---
title: "have program start and stop at certain times"
date: 2008-10-24
forum: General Help
---

### Post by canabal on 2008-10-24
Hey guys,

I just picked up an old laptop that I want to turn into a digital picture frame.

I have some details sorted out, but I want to turn on a weather app at certain times, say 7:50-8 (just before I leave for class) some days, and other times other days.

I downloaded a screenlet that can take up most of the screen and should go on top. I just want a way to turn it on and off at certain times.

any ideas?

---

### Post by MaxIBoy on 2008-10-24
You can schedule things with cron, but I'm not exactly sure how. Try googling "cron."

---

### Post by canabal on 2008-10-24
great idea, i looked and there is a gui for cron called "scheduled tasks" in add/remove.

now if I can only find a way to close the thing after.

is there a way to end currently running programs in the terminal, because I think that may do it.

---

### Post by canabal on 2008-10-24
Anyone else have an idea?

---

### Post by jespdj on 2008-10-24
If there's no way to have the program close itself down, you can kill it:
```
kill <processid>
```
When you don't know the process ID (which you can find with ps -ef, note that each process gets a new process ID when you start it), you can kill all instances of a certain program by name:
```
killall <name>
```
See "man kill" and "man killall".

---

