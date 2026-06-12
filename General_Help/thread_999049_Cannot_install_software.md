---
title: "Cannot install software"
date: 2008-12-01
forum: General Help
---

### Post by 62no on 2008-12-01
Whenever I try to open a package manager up or install something I get this error message
.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So when I run that, I get this...

alex@alex-desktop:~$ sudo dpkg --configure -a
[sudo] password for alex: 
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted


Help?

---

### Post by 62no on 2008-12-01
bump

---

### Post by 62no on 2008-12-01
bump

---

### Post by 62no on 2008-12-02
> **62no said:**
> bump

[COLOR="Silver"][SIZE="1"].[/SIZE][/COLOR]

---

### Post by 62no on 2008-12-04
bump

---

### Post by 62no on 2008-12-06
anyone?

---

### Post by 62no on 2008-12-07
bump

---

### Post by 62no on 2008-12-07
bump

---

### Post by Kevbert on 2008-12-07
Please try the following
```
sudo apt-get install -f
```

---

### Post by 62no on 2008-12-08
Doesn't work, I get this.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by 62no on 2008-12-09
bump

---

### Post by Ayuthia on 2008-12-09
Can you see if system-tools-backends exists in /etc/init.d:
```
ls /etc/init.d/system-tools-backends
```

If it does, try:
```
sudo /etc/init.d/system-tools-backends stop
sudo dpkg --configure -a
```

---

### Post by 62no on 2008-12-09
It exists and the second part didn't work.

```
alex@alex-desktop:~$ ls /etc/init.d/system-tools-backends
/etc/init.d/system-tools-backends
alex@alex-desktop:~$ ls /etc/init.d/system-tools-backendsda
ls: cannot access /etc/init.d/system-tools-backendsda: No such file or directory
alex@alex-desktop:~$ sudo /etc/init.d/system-tools-backends stop
[sudo] password for alex: 
Sorry, try again.
[sudo] password for alex: 
 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
alex@alex-desktop:~$ sudo dpkg --configure -a
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting System Tools Backends system-tools-backends                  [ OK ] 

dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
alex@alex-desktop:~$

```

Anyone else got any other suggestions?

---

### Post by Ayuthia on 2008-12-09
You might want to look into /var/log/dpkg.log to see what package is getting stuck.  It should be the last item in the file.  You will need to use sudo to view the file.

I am unable to find a package.c file in my system so I can't tell what is failing.

---

