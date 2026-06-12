---
title: "[SOLVED] Wubi need some info"
date: 2008-10-05
forum: General Help
---

### Post by coolguy2000 on 2008-10-05
Hi All,

I would like to try **Wubi** installer for Ubuntu. I have following queries before installing it

[LIST=1]
[*]does it replace the boot loader with grub
[*]or ubuntu runs as a seperate window inside my OS
[/LIST]

Thanks,
sur

---

### Post by Sef on 2008-10-05
> 
[LIST=1]
[*]does it replace the boot loader with grub
[*]or ubuntu runs as a seperate window inside my OS
[/LIST]
1) Yes,  Windows boot loader will only boot into Window's oses.

2) It's a separate os.  The default is Windows, but you can choose Ubuntu.

3) Moved to Wubi forum.

---

### Post by coolguy2000 on 2008-10-06
Thanks Sef for the information.

But what happens when I uninstall Wubi from windows.

Will my boot loader gets restored to orgianal state.


sur

---

### Post by ago on 2008-10-06
The windows bootloader is not in fact replaced
What happens is that Wubi adds an option to your existing windows bootloader to load grub4dos which in turns is capable of loading the Linux kernel.
Once uninstalled the system is restored to its previous state and the extra boot menu option is removed.
You need to reboot to choose between Ubuntu and Wubi.

---

### Post by coolguy2000 on 2008-10-06
thanks ago,

going to try kubunutu today :D

---

### Post by Orlsend on 2008-10-06
OK seems like the Question is Solved, So maybe we can mark it as solved?

---

