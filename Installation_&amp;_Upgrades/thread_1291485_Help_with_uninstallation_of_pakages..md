---
title: "Help with uninstallation of pakages."
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by yo2boy on 2009-10-14
_[ Ubuntu 9.10 Karmic Koala BETA ]_

I went on terminal and entered "sudo apt-get install ubuntustudio-desktop".

After that, it was successfully installed. But when I did "sudo apt-get remove ubuntustudio-desktop" some stuff wasn't going away and was giving me errors like:
```

yo2boy@ubuntu:~$ sudo apt-get remove ubuntustudio-default-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntustudio-default-settings
0 upgraded, 0 newly installed, 1 to remove and 437 not upgraded.
1 not fully installed or removed.
After this operation, 73.7kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 137956 files and directories currently installed.)
Removing ubuntustudio-default-settings ...
dpkg: error processing ubuntustudio-default-settings (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 ubuntustudio-default-settings
E: Sub-process /usr/bin/dpkg returned an error code (1)
yo2boy@ubuntu:~$ 

```And also, I'm trying to "sudo apt-get install mailserver" but it's not installing all becuase of the ubunutstudio-default-settings error.

HELP

---

### Post by yo2boy on 2009-10-14
bump

---

