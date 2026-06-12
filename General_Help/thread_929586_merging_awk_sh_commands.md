---
title: "merging awk sh commands"
date: 2008-09-25
forum: General Help
---

### Post by BloodRedSandman on 2008-09-25
How can I use bash command in awk script?
Lets say that I want to display 3rd column from ```
la -la
```

---

### Post by spin2cool on 2008-09-25
Like this?

```
ls -al | awk '{print $3}'
```

do a search for 'awk tutorial' and you'll find many pages with explanations of awk syntax.

---

### Post by ghostdog74 on 2008-09-25
you can use bash 
```

ls -l | while read a b c dummy;do echo $c;done 

```

---

