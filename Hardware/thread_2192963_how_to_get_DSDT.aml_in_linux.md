---
title: "how to get DSDT.aml in linux?"
date: 2013-12-10
forum: Hardware
---

### Post by C0NFU53D2 on 2013-12-10
Hello all,
so i have a laptop (Toshiba L755D-S5171) and all is well except the battery doesn't work.  now i found a site for making it appear and work for the L640 series ([here]("http://techinterplay.com/fix-toshiba-battery-issue-linux.html")) and i went though all the steps, and there seems to be no change.  but in a comment someone said to try ([this]("http://blog.michael.kuron-germany.de/2011/03/patching-dsdt-in-recent-linux-kernels-without-recompiling/")) and i would love to, except that 
```
iasl -tc dsdt.dsl
``` 
does not give me a DSDT.aml file, it gives me a DSDT.hex file.  iv scouered the internet looking for how to make a DSDT.aml or even a .aml file in general and have come up with nothing for linux except the code above, and alot of mac solutions.  

so how do i get a DSDT.aml file?  i appreciate your answers.
Thanks!:D

---

