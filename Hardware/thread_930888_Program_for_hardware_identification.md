---
title: "Program for hardware identification"
date: 2008-09-26
forum: Hardware
---

### Post by gimmejimmy on 2008-09-26
I've tried both lshw and gnome-device-manager and they both can't identify my motherboard model, processor socket type and the type of memory installed.  I could open the case but it would be much better if there were something like Everest I could use.  Thank you.

---

### Post by kdcoetzee on 2008-09-26
Ok.

for CPU info.

```
 cat /proc/cpuinfo 
```

For memory

```
 cat /proc/meminfo 
```


And Hardware Info

```
 lspci 
```


To see what memory you installed. try the BIOS settings. it usally has a info page. And to see what CPU socket you have. use the info of "cat /proc/cpuinfo"and  google it.

---

### Post by gimmejimmy on 2008-09-28
The processor is a Pentium III Coppermine, so it's either slot 1 or socket 370.  It's probably socket 370.  Not much info on the mems, just says 128MB SDRAM.  Can't tell if it's PC100 or PC133.  If I got Wine and ran Everest would that work?
I tried the advice here:
[http://ubuntuforums.org/showthread.php?t=634729]("http://ubuntuforums.org/showthread.php?t=634729")
but the system returned "No SMBIOS nor DMI entry point found, sorry."
At least it was polite.

---

