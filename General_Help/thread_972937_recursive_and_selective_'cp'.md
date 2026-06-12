---
title: "recursive and selective 'cp'"
date: 2008-11-06
forum: General Help
---

### Post by martin_legion on 2008-11-06
Hello. Here's the situation.
I want to create a script to make backups of some files:

I have a directory with lots of mixed files. I only want to backup the .prg files in that directory. But inside that dir there are also other sub-dirs containing mixed files. I want to back up the .prg files in those dirs too.
I need to make a copy of the directory structure and copy each .prg file in the corresponding dir or sub-dir.
Got the idea?
The best solution would be that the script automatically creates the directories each time it runs, because in the future the structure might change, and I need the script to adapt to those changes.
Any ideas?...

Thanks!

---

### Post by squaregoldfish on 2008-11-06
I don't have time to go into details right now, but check out rsync with the --include option - that should get you what you want.

Steve.

---

### Post by martin_legion on 2008-11-06
> **squaregoldfish said:**
> I don't have time to go into details right now, but check out rsync with the --include option - that should get you what you want.

Steve.

I'll check it out. Thanks!

---

