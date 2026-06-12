---
title: "[SOLVED] View system info"
date: 2008-07-18
forum: General Help
---

### Post by agaudio on 2008-07-18
This seems like a simple question, but I cannot seem to find the answer. How do I view information about the system processor, amount of memory, etc in my Ubuntu system? In other words, the equivalent of right clicking on My Computer in Windows and selecting Properties.

---

### Post by Mister.Vash on 2008-07-18
go System -> System Administration -> System Monitor

Click on the System tab

---

### Post by andrewc6l on 2008-07-18
A lot of those things can be found in the /proc directory. For example,

```
cat /proc/cpuinfo
```

will tell you about the CPU, while

```
cat /proc/meminfo
```

will tell you about memory.

---

### Post by agaudio on 2008-07-18
Many thanks to both of you!. I knew it had to be something simple :-)

---

