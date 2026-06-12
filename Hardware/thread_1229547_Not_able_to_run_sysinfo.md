---
title: "Not able to run sysinfo"
date: 2009-08-02
forum: Hardware
---

### Post by gemini6 on 2009-08-02
When I start sysinfo following messages were shown.
```
start@up:~$ sudo sysinfo

** (Sysinfo.exe:11377): WARNING **: The following assembly referenced from /usr/lib/sysinfo/Sysinfo.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=2)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/sysinfo/).


** (Sysinfo.exe:11377): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: Could not load type 'Sysinfo.Sysinfo' from assembly 'Sysinfo, Version=1.0.3293.37466, Culture=neutral, PublicKeyToken=null'.

```
May someone help? Thanks.

---

