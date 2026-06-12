---
title: "Move .gvfs?"
date: 2008-07-14
forum: General Help
---

### Post by inselaffe on 2008-07-14
That there .gvfs may be doing some fancy useful things, but it is becoming a bit of a pain being located in my home directory.

For instance I just tried listing all the shell scripts in my home folder using [FONT="Courier New"]find ~ | grep \\.sh$[/FONT], but it started searching through the SMB shares I have connected to, which takes time. I had cancel and unmount them all.

These mounted shares have no logical connection to my home directory and I don't wish them to be there at all. I also don't want to lose the functionality of mounting shares through the gui, so can .gvfs be moved elsewhere and be made to work there?

---

### Post by sdennie on 2008-07-14
Rather than moving .gvfs (which, I'm not sure will work), you could just use find with "-xdev".  Using "-xdev" prevents find from traversing outside the filesystem it's run on and, because ~/.gvfs is listed in the output of "df" as it's own filesystem, it should prevent find from traversing it.

---

