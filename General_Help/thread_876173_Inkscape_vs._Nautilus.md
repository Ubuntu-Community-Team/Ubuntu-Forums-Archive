---
title: "Inkscape vs. Nautilus"
date: 2008-07-31
forum: General Help
---

### Post by lyceum on 2008-07-31
So, when I try to use Nautilus to open files while having Inkscape open and I get to a folder with svg files I made in Inkscape in it, Nautilus freezes then crashes. My CPS spikes almost off the chart. I have a 1.6 gigahertz dual core processor. This does not happen if I close Inkscape first. Any ideas as to why this might be happening? :confused:

---

### Post by damis648 on 2008-07-31
You could check the output in /var/log and see if anything sticks out at you.

---

### Post by lyceum on 2008-07-31
> **damis648 said:**
> You could check the output in /var/log and see if anything sticks out at you.

I would not even know what I was looking at, but how do I do that?

---

### Post by decoherence on 2008-07-31
When checking logs for a reproducible error, it's often easier to watch the log as it is updated.

In a terminal type
```

sudo tail -f /var/log/syslog
```

then try to reproduce the crash. When nautilus dies, see if anything has been output in the terminal.

if you don't see anything relating to nautilus, try substituting 'syslog' with 'messages' in the above command.

if you still get nothing, do this

```
sudo grep -r nautilus /var/log | awk -F: '{print $1}' | uniq

```

to get a list of logs nautilus has written to. then re-do the process for the first command, substituting each name. you probably won't have to go this far.

---

