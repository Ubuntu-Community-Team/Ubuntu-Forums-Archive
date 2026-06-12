---
title: "date in shell script, this format 0720108"
date: 2008-07-20
forum: General Help
---

### Post by dapim on 2008-07-20
i would like to retrive date in shell script,
in this format  0720108 , month day and year, how can i do that?

---

### Post by sisco311 on 2008-07-20
???
```
date +%m%d%y
```???

---

### Post by ghostdog74 on 2008-07-20
check the date man page
```

date +%d%m #this is for day and month.

```

---

### Post by iaculallad on 2008-07-20
That would be:

> #!/bin/bash
echo "`date +%m%d%y`"
exit 0

---

### Post by Dr Small on 2008-07-20
> **iaculallad said:**
> That would be:
Or:
```
#!/bin/bash
date=`date +%m%d%y`
echo $date
exit 0
```

---

