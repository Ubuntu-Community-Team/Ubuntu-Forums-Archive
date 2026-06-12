---
title: "[SOLVED] How to cut and display first 250 chars from some file?"
date: 2008-09-19
forum: General Help
---

### Post by jakonj on 2008-09-19
example: i created one file in ~/ named text (so ~/text). 
Q: How can i cut first 250 chars from ~/text and display them  in terminal using 
cut?

tnx

---

### Post by NoReflex on 2008-09-19
I don't really understand your question. You want to create a program that does this? If yes you can use "fread". You can find more information here : 
[http://www.cplusplus.com/reference/clibrary/cstdio/fread.html](http://www.cplusplus.com/reference/clibrary/cstdio/fread.html)
If you want to use bash for this you can use read and then echo.
Hope this helps.

Best wishes,
NoReflex

---

### Post by Pro-reason on 2008-09-19
> **jakonj said:**
> example: i created one file in ~/ named text (so ~/text). 
Q: How can i cut first 250 chars from ~/text and display them  in terminal using 
cut?

tnx
I believe that “cut” only works on lines.  For multi-line files, something else will be required, perhaps “gawk”.

---

### Post by ghostdog74 on 2008-09-19
> **jakonj said:**
> example: i created one file in ~/ named text (so ~/text). 
Q: How can i cut first 250 chars from ~/text and display them  in terminal using 
cut?

tnx

if you want to cut 250 chars from every line
```

awk '{print substr($0,1,250)}' file
cut -b1-250 file

```

if you want to cut only the first 250 and ignore the rest of the lines
```

head -1 file | cut -b1-250

```

---

### Post by mali2297 on 2008-09-19
> **jakonj said:**
> example: i created one file in ~/ named text (so ~/text). 
Q: How can i cut first 250 chars from ~/text and display them  in terminal using 
cut?

tnx

Use your head. ;-)
```

head -c 250 ~/text

```

---

### Post by jakonj on 2008-09-19
> **mali2297 said:**
> Use your head. ;-)
```

head -c 250 ~/text

```

This works. Arigato for help :)

---

