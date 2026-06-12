---
title: "[SOLVED] Reassign process parent / PPID"
date: 2008-09-10
forum: General Help
---

### Post by jon.mithe on 2008-09-10
Hi,

Is it possible to reassign the PPID / parent process ID of a process (i.e. shift it to a different node in the process tree).

For example, I can open a terminal (process PPID=1) and execute a program in it (process PPID = terminal PID). Later I want to reassign the PPID to that of the GUI apps or something else (another application) - is that possible?

I can execute programs in the terminal using nohup command, which assigns the process a PPID of 1 - but that does not apply to already running processes or shifting to a different process.  Also I can use screen to get applications running when the terminal closes, but again not useful for running processes / creating that process tree relationship when things get killed.

Thanks for any help, Jon

---

### Post by Yannick Le Saint kyncani on 2008-09-10
> **jon.mithe said:**
> Is it possible to reassign the PPID / parent process ID of a process (i.e. shift it to a different node in the process tree).

Nope, a process will get adopted by init if its parent die/exit, other than that, nothing can change a ppid (AFAIK).

---

### Post by sdennie on 2008-09-10
I'm not sure if it's possible to reassign a process to a new parent however, you can disassociate it while it's running using "disown".  For example:

```

gcalctool &
exit

```

The calculator closes.

```

gcalctool &
disown
exit

```

The calculator stays open.  You can also use "disown -a" to disown all background child processes of the currently shell.

---

### Post by jon.mithe on 2008-09-11
Thats worked great thanks

---

