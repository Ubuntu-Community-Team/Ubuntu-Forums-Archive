---
title: "man Page Question"
date: 2008-10-24
forum: General Help
---

### Post by Chewie RFC on 2008-10-24
Hello,

I'm new to Ubuntu (as of a month ago), a recent convert from Windows XP. I have to say... I love it. I've used Linux off and on in the past (Slackware, Red Hat, and Fedora), but I've finally taken the plunge. I'm somewhat familiar with the system, however I'm having an issue with man pages. I'm reading "A Practical Guide to Linux Commands, Editors, and Shell Programming" and one of the Advanced Exercises they have is as follows:

"How many man pages are in the Devices subsection of the system manual? (Hint: Devices is a subsection of Special Files.)"

I can't for the life of me figure out how to get the man command to list the required information. Any tips?

---

### Post by fjgaude on 2008-10-24
It's just man <program>, with program being the name of the file you wish to review.

---

### Post by Chewie RFC on 2008-10-24
> **fjgaude said:**
> It's just man <program>, with program being the name of the file you wish to review.

Yes, I know how to display a man page. However, I'm trying to list the man pages under a subsection.

---

### Post by Yellow Pasque on 2008-10-24
```
man man
``` :P

---

### Post by fjgaude on 2008-10-24
Wow, learn something new everyday.

---

### Post by Chewie RFC on 2008-10-24
> **Temüjin said:**
> ```
man man
``` :P

Thanks, but I tried that a while ago and that's not cutting it.

---

### Post by Iowan on 2008-10-24
Perhaps it's not a **man** command option, but a location to be checked.  For MY info (FMI?), where is the system manual located?

---

### Post by Yellow Pasque on 2008-10-24
```
cd /usr/share/man/man4
ls
```

---

### Post by Ayuthia on 2008-10-24
The more painful way would be to count them through xman(The X version of man).  You can select the Manual Page button which will open up another window and then you can select Options->Display Directory.  You can then count the number of items in each section (which you can select from the Section dropdown).

Actually, Temüjin's option is better.  I just wanted to show you the graphical version of man.

---

### Post by Chewie RFC on 2008-10-25
> **Temüjin said:**
> ```
cd /usr/share/man/man4
ls
```

It probably is just that simple... thanks.

---

### Post by Iowan on 2008-10-27
```
ls  /usr/share/man/man4/ |grep --count .4
```

---

### Post by Sam on 2008-10-27
```
apropos --section 4 * |wc -l
```

---

