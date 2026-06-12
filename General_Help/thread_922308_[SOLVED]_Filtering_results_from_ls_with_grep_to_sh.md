---
title: "[SOLVED] Filtering results from ls with grep to show file location"
date: 2008-09-17
forum: General Help
---

### Post by davidryder on 2008-09-17
I'm trying to show the directories that the files from this command reside in. 

```
ls -R /mnt/media/Music/ | grep wma
```

This only shows me the names of the files, but I would like to see what directories they are in also. 

Thanks!

---

### Post by justleen on 2008-09-17
use find instead of ls to get the full path:
```

find /mnt/media/Music/  -name "*.wma"

```

---

### Post by davidryder on 2008-09-17
Thanks, worked perfectly!

---

### Post by justleen on 2008-09-17
(then mark post as solved, would you please?)

---

### Post by NoReflex on 2008-09-17
You can do it with ls as well : 
```
ls -dR /mnt/media/Music/* | grep wma
```

Best wishes,
NoReflex

---

