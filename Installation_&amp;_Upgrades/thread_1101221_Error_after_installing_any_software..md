---
title: "Error after installing any software."
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by kcode on 2009-03-20
This is what I get after installing any software, after installing updates : 

```

Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks

---

### Post by Partyboi2 on 2009-03-20
Open a terminal and try

```
sudo dpkg --configure -a
```

and post the output.

---

### Post by kcode on 2009-03-20
Heres the output:

[CODE}
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 system-tools-backends
[/CODE]

---

### Post by Partyboi2 on 2009-03-20
Try
```
sudo invoke-rc.d system-tools-backends stop
```
then
```
sudo dpkg --configure -a
```

[[COLOR=Blue]Bugreport[/COLOR]]("https://bugs.launchpad.net/ubuntu/intrepid/+source/system-tools-backends/+bug/294389")

---

