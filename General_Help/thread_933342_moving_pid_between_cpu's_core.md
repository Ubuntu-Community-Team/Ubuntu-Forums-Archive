---
title: "moving pid between cpu's core"
date: 2008-09-29
forum: General Help
---

### Post by rperrones on 2008-09-29
Hi,

i have few questions for the experts here ;)

1-How to identify the cpu core where the process are running? The "taskset command" show me only by PID process individualy, and i need something like a report that show me for all process (i.e. ps -ec).

2-Is it possible to migrate all process to run in one specific cpu core via cpuset (CFS scheduler), including kernel's tasks. I need isolate one process from all others to run in the first cpu core. At the same time i want to block scheduler load balance between cores. Does anybody knows how to do that?

Thanks a lot
Ricardo

---

### Post by Endless_Nameless on 2009-05-29
Hi rperrones!

My first post in this great Forum! (the first time we never forgot!)

I don't know if you already found the answer, but here are my guesses:

1) As fair as I know, there is no way in Linux to find out what core are running some process. I am searching this feature for a long time, and I never saw anything like it. The only thing you can do is see each cpu usage, with "gnome-system-monitor", or "htop", or pressing "1" inside "top".

2) One way you can isolate all the kernel in one processor is to use the "isolcpus" function in the kernel boot option. Edit "/boot/grub/menu.lst", and, for example, if you want to isolate the second core from the kernel, write "isolcpus=1" at the end of the line of the kernel, with the other options (for example, "splash" and "ro"). When you boot with this kernel, it will not run anything in the isolated core. The isolate core can only be acessed with the "taskset" command.

But now I have a question:

I have 2 quad-cores, and I isolate one of them. With taskset, I assigned a process to run from cores 5-7. But all of them are running in the core number 5! 

taskset -pc 5-7 <program pid>

If I write 7-5, it will use only the core number 7. I already-tried to write "5,6,7".

When the taskset is used it, it shows that the new program affinity is 5,6,7, in both cases. Anyone have a clue? Thanks for any information...

---

### Post by Pakia on 2009-06-19
monit

---

