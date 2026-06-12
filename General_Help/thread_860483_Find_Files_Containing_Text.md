---
title: "Find Files Containing Text"
date: 2008-07-15
forum: General Help
---

### Post by solarwind on 2008-07-15
How do I find files containing certain text?

---

### Post by meatpan on 2008-07-15
> **solarwind said:**
> How do I find files containing certain text?

The unix filters, such as sed, awk, and grep, are useful for matching text.  For example, to find the string 'somestr' in all '.cpp' files in the current directory, you could run:

```
grep 'somestr' *.cpp
```

Output the matching line number with the '-n' flag.  Search recursively through directories with the 'r' flag.

Does this help?

---

### Post by solarwind on 2008-07-15
> **meatpan said:**
> The unix filters, such as sed, awk, and grep, are useful for matching text.  For example, to find the string 'somestr' in all '.cpp' files in the current directory, you could run:

```
grep 'somestr' *.cpp
```

Output the matching line number with the '-n' flag.  Search recursively through directories with the 'r' flag.

Does this help?

That's what I use along with a host of other tools and pipes and so on, but I actually posted this for a friend who isn't too good with the terminal yet. Are there any GUI apps that do this?

---

### Post by jocko on 2008-07-15
Using gnome's search function (Places --> Search for files...), it is possible under "More Options". Just type the text in the field labelled "contains the text:"

---

### Post by solarwind on 2008-07-15
> **jocko said:**
> Using gnome's search function (Places --> Search for files...), it is possible under "More Options". Just type the text in the field labelled "contains the text:"

Thanks!

---

### Post by meatpan on 2008-07-16
> **solarwind said:**
> That's what I use along with a host of other tools and pipes and so on, but I actually posted this for a friend who isn't too good with the terminal yet. Are there any GUI apps that do this?


Gotcha,  wasn't clear from your post that you wanted a gui app for a non-command-line user.

---

