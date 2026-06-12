---
title: "Grep expert needed"
date: 2005-11-25
forum: General Help
---

### Post by Randy Sparks on 2005-11-25
Does anybody now how to make grep search for several different words at once?

I want to search for several module names in the output from dmesg but I can't make it work. Something like this:

dmesg ¦grep word1 word2 word3

---

### Post by buldir on 2005-11-25
Just use egrep...
```
dmesg | egrep 'word1|word2|word3'
```

---

### Post by Randy Sparks on 2005-11-26
I thought it might be one of the grep variants I needed. Many thanks.

---

### Post by Dooglus on 2005-11-26
[QUOTE=Randy Sparks]I thought it might be one of the grep variants I needed. Many thanks.[/QUOTE]

You can use basic regular expressions and still have grep match multiple patterns by specifying multiple -e flags:

```
dmesg | grep -e word1 -e word2 -e word3
```

---

