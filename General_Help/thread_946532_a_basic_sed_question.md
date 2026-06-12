---
title: "a basic sed question"
date: 2008-10-13
forum: General Help
---

### Post by heluani on 2008-10-13
Hello all, I apologize if this is not the right question for this forum, couldn't find anything that would say so.

I am trying to replace the string "*****" appearing in file1 by a string "AAAAA" and write in file2. I was expecting

```
sed 's/\*\*\*\*\*/AAAAA/ <file1 > file2
```

would work, but it spits an "Invalid preceding regular expression" how do I escape the "*" character?

Thanks.

R.

---

### Post by Uchiha_madara on 2008-10-13
in which language this Syntax from???

---

### Post by Sam on 2008-10-13
```
sed 's/\*\*\*\*\*/AAAAA/' file1 > file2
```

---

### Post by bodhi.zazen on 2008-10-13
Well your expression syntax is off.

First you can use characters other then "/" in you expressions, and in fact / is confusing.

try 's_\*\*\*_AAA_g'

---

### Post by heluani on 2008-10-13
Wow, thanks for all the quick answers. First Sam, what you propose is equivalent to what I propose, the order of redirecting is the same.

bodhi.zazen: what you propose is also the same, just that you used a different delimiter for the commands... (plus the global character that I don't care for now) it does spit the same answer.

I think the issue is with * expanding in the shell to the directory contents...

R.

[Edit] just to make things more confusing, I just tried
```
 cat file1 | sed 's/\*\*\*/AAA/' > file2
``` and that does work!

R.

---

### Post by bodhi.zazen on 2008-10-13
no it is not the same, there are subtle differences, mainly closing the expression (with a tailing ').

---

### Post by heluani on 2008-10-13
Ooops sorry, that was my bad in my first post forgot to close it...

R.

---

### Post by geirha on 2008-10-13
* is not expanded inside single or double quotes in bash, so the single quotes protects them on that. Also, some different ways of using sed
```

# -r makes it take extended regular expressions
sed -r 's/\*{5}/AAAAA/' file1 > file2
# requires more escaping without
sed 's/\*\{5\}/AAAAA/' file1 > file2
# you can also do the change directly on the file with -i (--in-place)
sed -r -i 's/\*{5}/AAAAA/' file1
# In case you go wrong, make a backup (file1~)
sed -r -i~ 's/\*{5}/AAAAA/' file1

```

---

