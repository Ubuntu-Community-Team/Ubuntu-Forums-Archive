---
title: "parse CPU info with BASH"
date: 2008-11-03
forum: General Help
---

### Post by very_japi on 2008-11-03
SO im monitoring some ubuntu servers (... like a million of them) using SNMP, and i need to send an SNMP trap periodically with information about the top 20 processes that are hogging most of the CPU.

I've already worked out a custom command which throws the snmp trap, it looks like this:

throwPStrap -p [name of the command that spawned the process] -c [ammount of CPU beeing used]

And i have a command that gets the info about processes which is roughly like this.

```
 ps -e -o pcpu,comm|sort -r|grep -v '%CPU COMMAND'| awk '{if($1>1.0){print $1 "-->" $2}}'
```


So i was just thinking of a way to pipe the output of the second command on to the first command... kinda like:


```
 ps -e -o pcpu,comm|sort -r|grep -v '%CPU COMMAND'| awk '{if($1>1.0){print "Process " $2 " is taking " $1 "% of CPU for node BLA"}}'
| throwPStrap  
```

Any ideas on how to accomplish this? an idea of a better/simpler approach?

PS.- can anyone think of a better name for this thread?

Thanks guys.

---

### Post by tatsuno on 2008-11-04
```
ps -e -o pcpu,comm|sort -r|grep -v '%CPU COMMAND'| awk '($1>1.0)' | while read a b; do throwPStrap $b -c $a; done
```

---

