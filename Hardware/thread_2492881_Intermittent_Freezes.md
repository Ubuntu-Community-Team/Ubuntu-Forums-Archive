---
title: "Intermittent Freezes"
date: 2023-11-26
forum: Hardware
---

### Post by daniell59 on 2023-11-26
After a few hours of use, my computer freezes necessitating a reboot. I am wonder if the following explains it.

After running a while
```

daniel@daniel-P5Q-PRO:~$ free -h
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.5Gi       145Mi        68Mi       1.2Gi       1.0Gi
Swap:          2.0Gi       174Mi       1.8Gi
daniel@daniel-P5Q-PRO:~$ free -h
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       3.4Gi       104Mi        58Mi       322Mi       128Mi
Swap:          2.0Gi       2.0Gi       0.0Ki
daniel@daniel-P5Q-PRO:~$ 
```

Immediately after Booting

```
daniel@daniel-P5Q-PRO:~$ free -h
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       761Mi       1.7Gi        39Mi       1.4Gi       2.8Gi
Swap:          2.0Gi          0B       2.0Gi
daniel@daniel-P5Q-PRO:~$
```

---

### Post by TheFu on 2023-11-27
When posting terminal output, please, please, please, use forum code tags, so columns are maintained.  Too hard to read without correct columns. Please make it easy for others to help you.  Just edit the first post to wrap in code-tags.

```
$ free -h
               total        used        free      shared  buff/cache   available
Mem:           5.7Gi       4.8Gi       329Mi        10Mi       665Mi       608Mi
Swap:          1.8Gi       0.0Ki       1.8Gi
```
see how much easier that is to read than yours? The system I took that from isn't a desktop.

Low memory can cause instability, but there are lots of other issues, usually in the system logs, which need to be checked too.  I'd look for warnings and errors in those logs.

For a desktop, I consider 4.1GB to only size for swap. Less isn't enough unless you have more than 64GB of RAM.

---

### Post by daniell59 on 2023-11-27
> **TheFu said:**
> When posting terminal output, please, please, please, use forum code tags, so columns are maintained.  Too hard to read without correct columns. Please make it easy for others to help you.  Just edit the first post to wrap in code-tags.

```
$ free -h
               total        used        free      shared  buff/cache   available
Mem:           5.7Gi       4.8Gi       329Mi        10Mi       665Mi       608Mi
Swap:          1.8Gi       0.0Ki       1.8Gi
```
see how much easier that is to read than yours? The system I took that from isn't a desktop.

Low memory can cause instability, but there are lots of other issues, usually in the system logs, which need to be checked too.  I'd look for warnings and errors in those logs.

For a desktop, I consider 4.1GB to only size for swap. Less isn't enough unless you have more than 64GB of RAM.
I must apologize for my ignorance. I know nothing about forum code tags. I will read about them, and then utilize them.

---

