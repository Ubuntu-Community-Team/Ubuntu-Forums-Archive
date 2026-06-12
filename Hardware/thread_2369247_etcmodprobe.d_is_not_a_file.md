---
title: "/etc/modprobe.d is not a file"
date: 2017-08-20
forum: Hardware
---

### Post by tmccaffery on 2017-08-20
Getting this error in syslog

---

### Post by vocx on 2017-08-20
> **tmccaffery said:**
> Getting this error in syslog
Correct.

The path "/etc/modprobe.d" is a directory, not a file.
```

ls -ld /etc/modprobe.d

```
```

drwxr-xr-x  2 root root     4096 Aug 19 20:55 /etc/modprobe.d

```
The first "d" in the permission string indicates it's a directory.

Now. What is the problem? If there is no problem, then you should not worry. We cannot guess if there is a problem, if you don't tell us.

---

### Post by Yellow Pasque on 2017-08-21
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1452610](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1452610)

---

