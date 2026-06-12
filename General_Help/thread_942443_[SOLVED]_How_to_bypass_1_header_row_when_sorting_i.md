---
title: "[SOLVED] How to bypass 1 header row when sorting in bash"
date: 2008-10-09
forum: General Help
---

### Post by abcuser on 2008-10-09
Hi,
I would like to get processes that occupy the CPU the most. I would like to sort processes by using bellow command header is also sorted. ```
ps -eo pcpu,pid,user,args | sort -n -k 1 -r | head -n 10 
```

How to skip first header row when sorting?

Thanks,
Abcuser

---

### Post by jfsylvain on 2008-10-09
> **abcuser said:**
> Hi,
I would like to get processes that occupy the CPU the most. I would like to sort processes by using bellow command header is also sorted. ```
ps -eo pcpu,pid,user,args | sort -n -k 1 -r | head -n 10 
```

How to skip first header row when sorting?

Thanks,
Abcuser

Suppress the header in the ps command
```
ps -e -o pcpu= -o pid= -o user= -o args= | sort -n -k 1 -r | head -n 10
```

or remove the header with grep -v
```
ps -eo pcpu,pid,user,args | grep -v COMMAND | sort -n -k 1 -r | head -n 10
```

---

### Post by ymo on 2008-10-09
Or remove the header with tail -n +2
```
ps -eo pcpu,pid,user,args | tail -n +2 | sort -n -k 1 -r | head -n 10
```

---

### Post by abcuser on 2008-10-10
Hi,
I know I can remove header by I don't want to remove header I would like it to be displayed! I would just like to omit it from being sorted.
Regards,
Abcuser

---

### Post by abcuser on 2008-10-10
Hi,
I have found out one solution:
```
ps -eo pcpu,pid,user,args | grep "%CPU" | grep -v "grep %CPU" && ps -eo pcpu,pid,user,args | grep -v "%CPU" | sort -n -k 1 -r | head -n 10 

```
Regards,
Abcuser

---

