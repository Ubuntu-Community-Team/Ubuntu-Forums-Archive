---
title: "There is a file in my trash that wont delete"
date: 2008-09-07
forum: General Help
---

### Post by PsychedelicWonders on 2008-09-07
Alright I have a file stuck in my trash can that wont delete.

It totals 7.5g, so I def want to get rid of it.

How or why is it not emptying it?

It gets rid of everything else?

---

### Post by drs305 on 2008-09-07
Read the tutorial in my signature line about Trash Bins for a complete solution. 

Essentially, you probalby have ended up with trash owned by root which a normal user can't delete. You will need to use the command line with administrative powers or open your file browser with "gksu" or "gksudo".

```

gksu nautilus ~/.local/share/Trash/files

```

---

### Post by PsychedelicWonders on 2008-09-07
I'll run that code you just gave me, it will allow me to fully delete?

This should probably just be a one time deal, so I wont need to change any main settings.

---

### Post by PsychedelicWonders on 2008-09-07
alright, that seemed to have worked, thanks.

My trash icon doesnt seem to be working.

It shows it being empty, and even gives me a message of not having any trash in there, but when I open it up, there are obviously files in there.

Why wouldnt this be registering properly?

---

### Post by PsychedelicWonders on 2008-09-07
also, there is now an icon for my 80g hdd that has my OS's on it.

How can I delete the icon with out affecting any of the data?

I tried to right click and move to trash, but that area is now invisable.

---

### Post by drs305 on 2008-09-07
> **PsychedelicWonders said:**
> alright, that seemed to have worked, thanks.

My trash icon doesnt seem to be working.

It shows it being empty, and even gives me a message of not having any trash in there, but when I open it up, there are obviously files in there.

Why wouldnt this be registering properly?

It *may* be because you deleted the files but not the subfolders. Try deleting (SHIFT-del) the entire Trash folder - it will be recreated the next time you delete something. The trash shows empty because there probably aren't any files in the 'files' folder. The 'files' and 'info' subfolders are the ways ubuntu stores the trash, and those may be the folders you are seeing. (They don't really count as 'trash'.) 

I don't really understand your HD icon question. If it is on your desktop there is a 'volumes visible' option that can hide all your partitions but I'd need more information on this before rendering any advice.

---

