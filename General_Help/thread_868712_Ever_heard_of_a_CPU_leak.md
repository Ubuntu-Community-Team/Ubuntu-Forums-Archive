---
title: "Ever heard of a CPU leak?"
date: 2008-07-24
forum: General Help
---

### Post by MaddMatt on 2008-07-24
Hello!

I've never heard of a CPU leak, but maybe someone else has. Recently, after performing large tasks with Nautilus (like deleting many gb of files), and sometimes even closing a misbehaving firefox, there is ghost CPU usage - Gnome system monitor reports 100% usage and the system starts being VERY slow, but there are no processes using more than 2% or so, and plenty of RAM left. Is there another way of discovering what's eating away my CPU? I usually have to restart, or at the least restart gnome with a ctrl-alt-backspace command. Doesn't happen frequently, but when it does it's extremely annoying and puzzling, given that I can't find where the problem is. Sounds like a bug, but I don't know where the error is - any ideas? 

Thanks, 
Matt

---

### Post by mcduck on 2008-07-24
Are you sure you are looking at the CPU usage of _all_ processes, not just the ones owned by your user?

Run "top" in a terminal to check what's using the CPU.

---

### Post by soxs on 2008-07-24
When this will happen again, change into terminal <control><alt><F1> and type:
```
cp -vf ~/.xsession-errors ~/Desktop/xsession-errors.txt
``` and post/attach it here

---

### Post by MaddMatt on 2008-07-24
I'm assuming that ~/.xsession-errors gets replaced when a new session opens? I just looked at it because I had one of these "CPU leak" type crashes not more than 30mins ago, and it seems to have all new information - all of the messages are startup type messages. I'll post one when I have another, which might be soon. Is there anything in particular I should be looking for in it? Would you like to see the other one anyway?

Thanks, 
Matt

---

### Post by soxs on 2008-07-24
> **MaddMatt said:**
> I'm assuming that ~/.xsession-errors gets replaced when a new session opens? I just looked at it because I had one of these "CPU leak" type crashes not more than 30mins ago, and it seems to have all new information - all of the messages are startup type messages. I'll post one when I have another, which might be soon. Is there anything in particular I should be looking for in it? Would you like to see the other one anyway?

Thanks, 
Matt

On xrestart the log gets reset :-S that's the reason you only saw startup messages

---

### Post by MaddMatt on 2008-07-24
I ran top and no dice - right now I've got 40% cpu usage, and only 4 programs with usage in the 1-4% range. So what's with the missing 20%? I feel like this is a reflection of the big problems in a small bit. No anomalous .xsession-errors yet.

---

### Post by evets25 on 2008-07-24
well there's cpu usage, and then there's cpu usage. Programs use your cpu in different ways, and one of these is just I/O - pumping information in and out. Different cpu moniters may or may not count this as real cpu usage, because it's basically negligible, but perhaps that's the CPU usage you're seeing? if so, then don't worry about it. I have gnome's system moniter applet running in my panel, and it shows CPU usage. If I right click on it, go to preferences, then click on the processor tab, there's a bunch of different kinds of CPU usage there, and you can set a different color for each. By default, they are shades of blue, with I/Owait being an almost-black shade of blue, but I set this to the lightest shade of blue, closer to white, so I can see it more clearly. This kind of cpu usage isn't registered by top, or at least there's probably an option to enable showing it.

sreenshot:

---

