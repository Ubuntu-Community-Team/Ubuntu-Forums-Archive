---
title: "drop characters from each line of 'tail'ed log file"
date: 2008-11-11
forum: General Help
---

### Post by anystupidname on 2008-11-11
I'm working on a conky config and when I tail /var/log/messages (for example) I get 'long date' 'hostname' 'source' 'goodstuff'
I'd like to omit everything before 'source'. Could one of you guys that knows awk or sed or something like that gimme a hand please?

---

### Post by anystupidname on 2008-11-14
It turns out the tail option in conky is not the same as the native linux tail command. It won't accept manipulation/piping I guess?!? Anyway, using > execi tail something | cut c-1-2 instead (for example) works.

---

