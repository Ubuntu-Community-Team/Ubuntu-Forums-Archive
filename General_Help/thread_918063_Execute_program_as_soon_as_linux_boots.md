---
title: "Execute program as soon as linux boots"
date: 2008-09-12
forum: General Help
---

### Post by piousp on 2008-09-12
HI!
First of all, i'm not sure where to post this, so move as you see fit.
Now, the issue:
I need to start a java program as soon as linux boots. I dont know if one can get that with cron so thats why i'm asking.
I think i may have seen something about editing something in /etc, but thats as far as i can remember.
Is there a way to start a program once linux boots up?
Thanks for your help

---

### Post by BlackLLama on 2008-09-12
system>preferences>sessions, make a new session with the command that starts X program, X program is run at startup\

edit: example Name: screenlets Command: screenlets --replace

---

### Post by piousp on 2008-09-12
Thanks for your answer;
and if i dont have a GUI?

---

### Post by BlackLLama on 2008-09-12
what distro are you running?

---

### Post by piousp on 2008-09-12
RHEL 5, it's for a server i'm working right now

---

### Post by bingoUV on 2008-09-12
Put the command to start your program in /etc/rc.local, before 'exit 0'. It will be run at boot time, even before you login.

EDIT: there won't be any stupid 'exit 0' in /etc/rc.local of RHEL 5. Just add your command in /etc/rc.local

---

### Post by BlackLLama on 2008-09-12
sorry i can't help you there, i asumed you where using ubuntu. Is there any out there that can help this lad.

---

### Post by piousp on 2008-09-12
> **bingoUV said:**
> Put the command to start your program in /etc/rc.local, before 'exit 0'. It will be run at boot time, even before you login.

Nice! And thanks!
I'm gonna try it right now!

---

