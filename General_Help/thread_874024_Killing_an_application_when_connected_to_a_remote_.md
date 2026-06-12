---
title: "Killing an application when connected to a remote computer."
date: 2008-07-29
forum: General Help
---

### Post by MidnightJulia on 2008-07-29
Hi! 

I've been messing around with netcat and found a little problem that I haven't been able to workaround.  I've connected to a port (where I have another netcat listening for incoming traffic) and got a shell. So far everything is great - I can run programs without any problems but I haven't figured out how to kill  applications running on the remote computer. When using ctrl c I kill my connection to the computer – but all I want to kill is that application that is running. 

/MJ

---

### Post by cdtech on 2008-07-29
If you know the name you could kill the process by using "killall" followed by the process name.

example:
killall gnome-panel

if you know the **id**, or **pid** for example, in the terminal you could type ps -aef. And you'll get a list of processes running. Then you can use the command kill to kill the process.

example:
for the pid 2893
kill -9 2893

Hope this helps......

---

### Post by MidnightJulia on 2008-07-29
I think that I wasn't clear enough. Sorry about that...

What I am referring to is when I'm stuck in a program on the system I'm connecting to. On my local computer I would escape by using ctrl + c but on the remote computer using ctrl + c will kill my connection to that computer. I'm not out to kill a process but to kill the program that I am running at the moment on that computer that I can't escape from.

---

