---
title: "HAL crashes on Dell D820 because there is no"
date: 2008-08-22
forum: Hardware
---

### Post by obitori on 2008-08-22
My D820 mysteriously started booting up with a "HAL Failed" error.  Without HAL, my laptop does not recognize the built-in ETH0 NIC.  I tried booting HAL by hand and got this error:

```

obitori@moosilauk:~$ sudo /etc/init.d/hal restart
[sudo] password for obitori: 

 * Restarting Hardware abstraction layer hald  [FAILED]

Error: File /usr/share/hal/fdi/policy/gparted-disable-automount.fdi 
- No such file or directory

```

I figured I'd "add" the missing file and re-try:

```

obitori@moosilauk:~$ sudo touch /usr/share/hal/fdi/policy/gparted-disable-automount.fdi

obitori@moosilauk:~$ sudo /etc/init.d/hal restart 

 * Restarting Hardware abstraction layer hald   [OK]

```

The fix worked!  I am unsure of the cause and this concerns me.  Also, if others start experiencing the same, the fix may not be readily apparent.  

Any ideas/suggestions welcome...

Obitori

---

