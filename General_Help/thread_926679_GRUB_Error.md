---
title: "GRUB Error"
date: 2008-09-22
forum: General Help
---

### Post by arefem on 2008-09-22
:confused:  Hi.  I'm new to Linux, so please be gentle.

I installed Ubuntu on an old machine so I could play around with it.  I'm now giving the machine away and have had to re-install Windows Me from the manufacturers (Systemax) recovery disc. (Please don't ask me why)

I re-installed over the Ubuntu installation and let the program wipe the hard disk.

The re-install seems to have completed. However, when I re-boot I am presented with a GRUB error (I think it's Error 17).

I have run Fdisk on the drive, which reports only a primary DOS partition; manually deleted all partitions and run the recovery disk again, but I still get the same problem.

So just where is this GRUB file(?) hiding, and how can I get rid of any Obuntu stuff still hiding on the hard-drive and get it back to Windows Me?

Any help will be appreciated.

---

### Post by mike1821 on 2008-09-22
If you are not going to use Linux anymore you do not need GRUB either.

Try to boot with the installation CD of windows xp or something similar and enter the rescue console.

Type the following in order to create a new MBR partition

```
fixmbr
```

---

### Post by prshah on 2008-09-22
> **arefem said:**
> 
So just where is this GRUB file(?) hiding, and how can I get rid of any Obuntu stuff still hiding on the hard-drive and get it back to Windows Me?


> **mike1821 said:**
> 
```
fixmbr
```

the command "fixmbr" only appears in Win XP and higher's recovery console. For Windows ME, boot off the installation CD, then give the command ```
fdisk c: /mbr
```

This will remove GRUB and (re)place Windows bootup code.

---

### Post by arefem on 2008-09-28
Thanks to both of you.  The mbr option is so obvious, can't think why I didn't think of it. Duh!!

---

