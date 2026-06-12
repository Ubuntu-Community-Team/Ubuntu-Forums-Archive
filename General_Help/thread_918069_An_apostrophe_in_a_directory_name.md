---
title: "An apostrophe in a directory name"
date: 2008-09-12
forum: General Help
---

### Post by matthewboh on 2008-09-12
I created a directory with a file name from the command prompt, noticed that I misspelled it, now I can't delete it or access it through the file browser or the command line.

I'm running Ubuntu 8.04, and here's what I've tried to do with the directory

```
ls Let\s\ Hear\ If\ For\ The\ Boy\ Vol.\ 3\ (disc\ 2)?
-bash: syntax error near unexpected token `('
```

```
ls "Let's Hear If For The Boy Vol. 3 (disc 2)?"
ls: cannot access Let's Hear If For The Boy Vol. 3 (disc 2)?: No such file or directory
```

```
 ls Let?s?Hear?If2?For?The?Boy?Vol.?3?(disc?2)?
ls: cannot access Let?s?Hear?If2?For?The?Boy?Vol.?3?(disc?2)?: No such file or directory
```

Solved

just typed in 

```
rm -R Let\'s*
```

---

### Post by Predator106 on 2008-09-12
Please mark it as solved.

---

