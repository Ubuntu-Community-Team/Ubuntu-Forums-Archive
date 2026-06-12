---
title: "Neither Wubi nor Windows working"
date: 2008-08-29
forum: General Help
---

### Post by phearsome on 2008-08-29
Hello.
I decided to install Wubi on my laptop that is (was) running Windows XP Professional SP2. It worked fine for several days, but today it ceased working. I was booting up Ubuntu, and recieved an error.

```
Try (hd0,0): NTFS5: No wubildr
Try (hd0,1): FAT32: No WUBILDR
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (fd0): invalid or null
Cannot find GRLDR.
Press space bar to hold the screen, any other key to boot previous MBR ...
Timeout : 5 
```

I read a few threads here on ubuntuforums, and read a post about removing the wubildr and grldr-files from C:\ to see if it would boot into grub. It didn't. Now I got another error. 
"<system path>/system32/hal.dll is either missing or corrupt. Press any key to reboot"

I decided to try to reinstall Wubi. I got the GRDLR error again. I removed them yet again, and got the hal.dll error.
I booted into windows, and replaced the hal.dll in system32 (which was really stupid by me I noticed after googling), and now Windows won't work either. 

I obviously need to reinstall Windows now, but I'd like to know what caused the GRLDR problem, and how to solve it in case it happens again?

Thanks in advance.

---

### Post by Gabt on 2008-08-29
you could try use windows cd, use R to select recovery console. Type fixboot, ok it, type fixmbr, ok it.

---

### Post by phearsome on 2008-08-30
I used Rescue and Recovery, as I have a Thinkpad, and I got windows working. However, I've still got the GRLDR problem. I'll try doing the recovery console thing as soon as I get my hands on a Windows CD. Is it possible to do this from Windows?

---

