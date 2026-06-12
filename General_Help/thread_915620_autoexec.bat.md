---
title: "autoexec.bat"
date: 2008-09-10
forum: General Help
---

### Post by sulekha on 2008-09-10
Hi,

which file in ubuntu 8.04 does the same purpose as, autoexec.bat file in windows ?

---

### Post by iaculallad on 2008-09-10
> **sulekha said:**
> Hi,

which file in ubuntu 8.04 does the same purpose as, autoexec.bat file in windows ?

Any script file (with executable attribute) could be equivalent to autoexec, and you have to place it in the init.d directory for it to execute after boot process.

---

### Post by amo-ej1 on 2008-09-10
Actually within ubuntu you can use the file /etc/rc.local for this 

```

edb@lapedb:/etc/init.d$ cat /etc/rc.local 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```

This gets called from /etc/init.d/rc.local

---

### Post by kpkeerthi on 2008-09-10
Also look in System -> Sessions -> Startup Programs

---

### Post by hyper_ch on 2008-09-10
what do you want to do?

---

