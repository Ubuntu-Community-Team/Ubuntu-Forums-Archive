---
title: "[SOLVED] Easy script - I thought"
date: 2008-09-27
forum: General Help
---

### Post by jamesdcarroll on 2008-09-27
I'd like to create a little script to run three commands in order. So I did this:

```
#!/bin/sh

/home/jim/oracle/product/10.2.0/db_1/bin/lsnrctl start
/home/jim/oracle/product/10.2.0/db_1/bin/dbstart
/home/jim/oracle/product/10.2.0/db_1/bin/emctl start dbconsole
```

The commands work when I just enter them at the command line and they do admittedly take a few momemts each to run.  I was hopeful when I ran it and my mouse did that 'circly' thing indicating that something was running, but alas I was not to be.

Any help would be appreciated.

Thanks!!

---

### Post by aysiu on 2008-09-28
Did you make the script executable? ```
cd *directorythathasscriptinit*
chmod +x *scriptname*
```

---

### Post by jamesdcarroll on 2008-09-28
That was it but I did it as:

```
chmod 750 orastart.sh
```

I'll get the hang of this eventually! 

Thanks!

---

