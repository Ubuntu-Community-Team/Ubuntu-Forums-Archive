---
title: "create a directory named by the current date"
date: 2008-07-15
forum: General Help
---

### Post by goodtimes200 on 2008-07-15
I cannot get this to work. Any help is appreciated. 
Tried mkdir 'date +%y%m%d%H' but that just created the directory --
date +%y%m%d%H

Thanks.

---

### Post by fyo on 2008-07-15
You are quoting out of context ;-)

Replace your single quotes with ` quotes:

```
mkdir `date +%y%m%d%H`
```

and it should work just fine.

---

