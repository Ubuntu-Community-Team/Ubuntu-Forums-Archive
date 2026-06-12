---
title: "exit status of terminal commands"
date: 2008-10-01
forum: General Help
---

### Post by alphaniner on 2008-10-01
Is it possible to use the exit status of a command in an if-then conditional?  If so, how?  For example, grep exits with "0 if selected lines are found and 1 otherwise" and I want some commands to be run only if a match is found.  Thanks.

---

### Post by GrouchoMarx on 2008-10-01
> **alphaniner said:**
> Is it possible to use the exit status of a command in an if-then conditional?  If so, how?  For example, grep exits with "0 if selected lines are found and 1 otherwise" and I want some commands to be run only if a match is found.  Thanks.

Yes, you can, for instance in:

```
command1 && command2
```


command2 is only executed if command1 returns 0 (true).

---

### Post by alphaniner on 2008-10-01
Thank you!

---

### Post by llebegue on 2008-10-01
If you want more advanced behavior you can retreive the latest return code in $? variable

Example :
```


#!/bin/sh
#launches dosomething.sh which is a pure fictional process 
~/bin/dosomething.sh
retCode=$?

if [ $retCode -eq 0 ]
  then
     echo "Ok this was a big success, congratulations !"
fi
if [ $retCode -gt 0 -a $retCode -lt 4 ]
  then
     echo "Something weird happened"
fi
if [ $retCode -gt 4 ]
  then
     echo "Unknown value, please call admin !!"
fi


```

---

### Post by alphaniner on 2008-10-01
```
~/bin/dosomething.sh
retCode=$?
```

That's probably more practical for what I'm trying to do.  I also figured out how to do it with if-then, just used parenthesis instead of brackets which is what I was trying at first.  Thanks.

---

