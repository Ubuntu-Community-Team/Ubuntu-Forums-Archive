---
title: "Computer halts with an old hard disk"
date: 2013-04-13
forum: Hardware
---

### Post by ruwan2 on 2013-04-13
Hi, I have a hard disk (250 GB, 7200 RPM) which is from a 2005 HP computer. I would like to use it running Linux/WinXP on a compatible ZT Systems AMD A8-3850 computer. Almost after XP installation (it restarts and configure the application), the desktop PC crashes. Even it is reboot, I check the BIOS settings, it will crash again. The hard drive does not look bad as it still runs on the old computer. What can cause this problem? I suspect some settings are different from the new hard disk although I do not know which are. Thanks,

---

### Post by ahallubuntu on 2013-04-13
~

---

### Post by ruwan2 on 2013-04-13
Hi,
When I build the gsmartcontrol, it has errors:
.............
checking for target thread support flags... configure: WARNING: Cannot detect compiler thread support. Set CFLAGS, CXXFLAGS and LIBS manually.
checking for target system extension flags... CFLAGS: -D_GNU_SOURCE;  CXXFLAGS: -D_GNU_SOURCE;  LIBS: 
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... unknown
checking for _LARGE_FILES value needed for large files... unknown
checking how to run the C++ preprocessor... /lib/cpp
configure: error: in `/home/ruwan2/gsmartcontrol-0.8.7':
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details
root@ruwan2-MS-7696:/home/ruwan2/gsmartcontrol-0.8.7# edit config.log
Warning: unknown mime-type for "config.log" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"

............

I have tried to upload config.log, but it shows this file is invalid file. I do not know why.

Thanks,

---

### Post by ahallubuntu on 2013-04-13
~

---

### Post by Sef on 2013-04-13
> [COLOR=#000000]sudo apt-get install gsmartcontrol[/COLOR]

Do not forget to update the repositories:

```
Sudo apt-get update && sudo apt-get install gsmartcontrol
```

---

### Post by ruwan2 on 2013-04-13
Your are right! I change to another new hard drive. Both old and new machine run without problem now.

---

