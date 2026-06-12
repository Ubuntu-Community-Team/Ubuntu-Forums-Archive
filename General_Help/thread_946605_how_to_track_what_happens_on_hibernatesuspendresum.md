---
title: "how to track what happens on hibernate/suspend/resume/shutdown"
date: 2008-10-13
forum: General Help
---

### Post by imbuto on 2008-10-13
A newbie basic question, but I could not find a clear answer (could you suggest some good reference material?).
How can I track what happens when I hibernate or shutdown my computer? I would like to see _which_ scripts/commands are called and in _which order_?
Best would be a way to log the commands which are called together with their stdout/stderr.
My soundcard seems not to be handled correctly at shutdown (strange noise from the speakers), but correctly when I hibernate: how can I find the differences?

Thanks in advance!

---

### Post by kerry_s on 2008-10-13
you can call the commands from terminal and out put it to text.

example:

sudo hibernate > log.txt
sudo halt > log1.txt

---

