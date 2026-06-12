---
title: "listing all pdf files by command line?"
date: 2008-10-28
forum: General Help
---

### Post by mfrag on 2008-10-28
From the command line, how do I list all .pdf files in whichever directory I'm working in?
Shouldn't 

ls *.pdf

do the trick?

---

### Post by sdennie on 2008-10-28
That would probably do it, yes.  However, if you are working with files coming from Windows, the .pdf extension may be uppercase (or even mixed case).  Try:

```

ls *.pdf *.PDF

```

Or, more perverse but completely case insensitive:

```

ls *.[pP][dD][fF]

```

---

### Post by mfrag on 2008-10-29
Thanks for the response, vor.


When I type

```

ls *.pdf

```

I get

```

ls: invalid option --  
Try `ls --help' for more information.

```

However, when I try some like

```

ls *.iso

```

it works just fine.

Also, if I recall, I've used ls *.pdf in the past and it has worked just fine.  It works just fine on my computer at home.

What could be giving ls *.pdf trouble?

---

### Post by geirha on 2008-10-29
If one of the pdf files start with a - it will be treated as an option, which it doesn't understand in this case. To avoid the filenames being treated as options, even though they start with a -, use the special -- option.

```
ls -- *.pdf
```

---

### Post by Titan8990 on 2008-10-29
disregard

---

### Post by mfrag on 2008-10-29
geirha, 

Thanks, that did the trick.  Someone sent me a pdf file recently which started with a dash.  Makes perfect sense about ls not understanding the option.  I've since renamed the file so it won't be a problem in the future.

---

