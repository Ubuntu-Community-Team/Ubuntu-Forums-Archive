---
title: "Copy a whole directory with variable in copy name"
date: 2008-11-01
forum: General Help
---

### Post by aeriph on 2008-11-01
I've been googling and searching for some time and still can't find a solution to what I assume is a very simple problem.

I want to copy a directory (including subfolders) and I want the copy's name to include the date formatted in particular way.

I'm currently trying to use:

```
cp -r ~/original ~/Private/Backups/`date +%e-%m-%y@%R`-new
```

I've also tried setting the variable first:

```
new_name=`date +%e-%m-%y@%R`-new
cp -r ~/original ~/Private/Backups/$new_name
```

Each of these gives the same result:
```
cp: target `1-11-08@13:50-new' is not a directory
```

Which is quite frustrating as I'm aware it's not a directory - I want to create it.

I'd be really grateful for any advice on this.

---

### Post by Alaric on 2008-11-01
So why not try this?

mkdir ~/Private/Backups/`date +%e-%m-%y@%R` && cp -r ~/original ~/Private/Backups/`date +%e-%m-%y@%R`

---

### Post by aeriph on 2008-11-01
That gives:

```
mkdir: cannot create directory `/home/myname/Private/Backups/': File exists
```

---

### Post by Alaric on 2008-11-01
Alright, try this then.  It's a bit messy, but it's the best I can come up with.  

```
cd ~/Private/Backups && cp -r ~/.gnome `date +%e-%m-%y@%R`
```

---

### Post by aeriph on 2008-11-01
Success! Thank you so much

---

