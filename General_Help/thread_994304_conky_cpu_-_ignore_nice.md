---
title: "conky cpu - ignore nice"
date: 2008-11-26
forum: General Help
---

### Post by squaregoldfish on 2008-11-26
Does anyone know of a way to get conky to report CPU usage but exclude nice processes? If conky can't do it properly, is there somewhere in /proc or /sys that holds this info?

This seems to be the sort of thing that's easy to solve, but googling hasn't got me very far.

Thanks,
Steve.

---

### Post by cdtech on 2008-11-26
Sounds like a little scripting work for ya ahead. lol

Your probably looking for "CPU utilization". You can use the "mpstat" command to find this information but you need to install the "sysstat" utility. Once you have the information its just a process of grep-ing the information.

You can check out this site to help you better understand the outputs:
[http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html](http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html)

Hope this helps ya.....

---

### Post by squaregoldfish on 2008-11-28
Thanks, I'll check those out. If I come up with anything useful I'll post it back up here.

---

### Post by squaregoldfish on 2008-12-06
OK, I've got something working with the sar command. exec/execgraph with the following command works for a single processor (or combination of all processors):

```
sar 1|grep Average |awk '{ sum += $3; sum += $5; sum += $6; sum += $7; sum += $8; print sum }'
```

Unfortunately I have to wait a second for sar to do its stuff, as it has to sample the CPU activity to get its figures. mpstat suffers the same problem.

Is there a command I can use that will give me instantaneous CPU usage info?

Steve.

---

