---
title: "Can't update BIOS"
date: 2011-12-10
forum: Hardware
---

### Post by lumalav on 2011-12-10
Hi, I am totally new to Linux, and I just recently did a clean installation over my HP DV4-1155SE laptop with the last Ubuntu version (11.10)

I am experiencing heating problems. I don't know how to check the temperature, but I think it is way to high.

I've been researching for the last couple of days on the forum, and I've found out that HP has always had overheating problems with their laptops due to a poor design.

I tried to update my BIOS, but I don't know how to do it.

I tried to follow this tutorial using the CD method: 

[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

But, I don't know how to mount the BIOS last version (.exe) on DOS. 

Can someone help me with this? I also tried to download the last version of the BIOS for vista x86 (that was the original OS)

Thanks in advance

---

### Post by Mark Phelps on 2011-12-12
Are you trying to trash your PC?  Because, messing around with BIOS udpates, especially when (in this case) that will do nothing to fix the underlying problem, is a very simple way to turn your PC into an "electric brick".

The BIOS installed on laptops is written to work with the OS's installed on the laptops by the OEMs -- in nearly all cases, MS Windows.  There is no reason to suspect that upgrading the BIOS will suddenly make the laptop more compatible with "other" OSs (i.e., Linux).

This overheating is a known kernel problem, not a BIOS problem, so even if you did flash the BIOS, and managed NOT to "brick" your PC in the process, that would not fix it.

---

### Post by devansh.j2007 on 2011-12-12
Well if You just want to check hardware temprature... install acpi some 13 kB i guess then run 

```
acpi -t
```

u know ur temp if its around 60 its normal

---

