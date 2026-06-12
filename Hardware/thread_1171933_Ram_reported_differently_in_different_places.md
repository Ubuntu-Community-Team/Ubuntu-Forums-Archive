---
title: "Ram reported differently in different places"
date: 2009-05-27
forum: Hardware
---

### Post by vonedaddy on 2009-05-27
I just got a new hp mini 1030NR with Ubuntu Netbook Remix and bought a new 2GB stick of ram from crucial.  OK... so when i use the free command this is reported:

$ free -g
             total       used       free     shared    buffers     cached
Mem:             1          0          1          0          0          0
-/+ buffers/cache:          0          1
Swap:            0          0          0


When I use the system monitor which comes with UNR it says X of 2.0 GiB of RAM.

I am just wondering which is more valid, or is the computer actually using the extra gig of ram.

---

### Post by x33a on 2009-05-27
try
```
free
```

without the -g option.

---

