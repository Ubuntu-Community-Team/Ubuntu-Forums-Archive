---
title: "CD drive not working"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by danip on 2007-08-17
When i put data cds into my computer nothing happens.  I open up the file viewer and try to mount it manually and it says unable to mount drive under special details it says 
'mount: special device /dev/scd0/ does not exist'
a few days ago everything worked perfectly so im not sure why all of a sudden i cant look at my cds

---

### Post by heimo on 2007-08-17
> **danip said:**
> When i put data cds into my computer nothing happens.  I open up the file viewer and try to mount it manually and it says unable to mount drive under special details it says 
'mount: special device /dev/scd0/ does not exist'
a few days ago everything worked perfectly so im not sure why all of a sudden i cant look at my cds

First thing I'd do is list those devices:
```
ls -l /dev/scd*
```

Reboot and at the very beginning of boot, or by entering BIOS, check that CD drive is detected. It may be hardware failure. Do you dual boot? Does it work there?

---

### Post by danip on 2007-08-20
ok well i ran that command and it says no such file or directory.  i went into my bios it lists it in the boot process although after that im not really sure what im looking for.  I havent done any bios work in about 2 years so im not as fimiliar with it as i used to.  I dont do any dual booting, i just run straight linux.  I do have a couple windows boxs though and i have tested all the cds i have tried to run on there and i know that they do work so the problem is with the computer.  when i put the cd in it revs up the light blinks like its trying to read and does everything normal its just that the OS doesnt do anything.

---

### Post by danip on 2007-08-23
> **danip said:**
> ok well i ran that command and it says no such file or directory.  i went into my bios it lists it in the boot process although after that im not really sure what im looking for.  I havent done any bios work in about 2 years so im not as fimiliar with it as i used to.  I dont do any dual booting, i just run straight linux.  I do have a couple windows boxs though and i have tested all the cds i have tried to run on there and i know that they do work so the problem is with the computer.  when i put the cd in it revs up the light blinks like its trying to read and does everything normal its just that the OS doesnt do anything.

bump

---

