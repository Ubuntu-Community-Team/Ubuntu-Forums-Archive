---
title: "Changing Terminal default directory"
date: 2008-09-11
forum: General Help
---

### Post by patsymcox on 2008-09-11
Hi,

The default directory location when opening the Terminal is Desktop(/home/<username>/Desktop) in Hardy. Is there a way to change that to USER(/home/<username>)?

Thanks

---

### Post by mb_webguy on 2008-09-11
:confused:

The terminal should already open to /home/<username>, not ~/Desktop...

Open a terminal, and type "gnome-terminal".  Does the new terminal start you in the Desktop directory?

---

### Post by iaculallad on 2008-09-11
Open a terminal (Applications->Accessories->Terminal) and issue the command below:

```
pwd
```

it's output should be:

> /home/your_username

EDIT: Unless you installed the nautilus-open-terminal package, that the path should equal to the folder your in when you right clicked and choose "Open In Terminal".

---

### Post by mb_webguy on 2008-09-11
> **iaculallad said:**
> EDIT: Unless you installed the nautilus-open-terminal package, that the path should equal to the folder your in when you right clicked and choose "Open In Terminal".
:nod:

That's more likely than my first thought.  I was thinking that he might have somehow changed the terminal launcher to start him in the Desktop directory.  But after a bit of consideration, I realized that he would have had to change the launcher command to something like:```
gnome-terminal -x bash -c "cd ./Desktop;bash"
```...I think he'd probably know if he did that.  It's not something you'd do by accident.

---

### Post by patsymcox on 2008-09-11
> **mb_webguy said:**
> :nod:

That's more likely than my first thought.  I was thinking that he might have somehow changed the terminal launcher to start him in the Desktop directory.  But after a bit of consideration, I realized that he would have had to change the launcher command to something like:```
gnome-terminal -x bash -c "cd ./Desktop;bash"
```...I think he'd probably know if he did that.  It's not something you'd do by accident.

You diagnosed it right webguy, My friend created a launcher in the panel and he did the changes in the properties. Anyhow I reverted it.

Thanks to all.

Ubuntu!

---

