---
title: "Uninstall GRUB..."
date: 2008-10-13
forum: General Help
---

### Post by DivinityX on 2008-10-13
I deleted UBUNTU off my brother's desktop computer via formating the HDD...but i have a problem as you may have guessed...I get Error 17 before the GRUB menu even shows up, i looked at my past threads of having Error 15 & 17, i retried them, but it isn't working. in the terminal on the live cd, i type in...

```

sudo grub

grub> find /boot/grub/stage1

Error 15: File not found
```

i want to just get rid of Grub, how can i do this with only UBUNTU Live CD.

---

### Post by Hyper Tails on 2008-10-13
you can't get into an other operating system if you use the grub loader

the only way to get it back is to reinstall ubuntu

---

### Post by WWSmith36 on 2008-10-13
You can´t really uninstall grub.  You can overwrite it though.  I am assuming that you have removed ubuntu and now just want to boot only windows.

If that is the case, you will have to reinstall windows bootloader. Boot rom windows install CD, choose ´R´ at first menu to go to Recovery Console, and when you get to the command prompt enter the command fixmbr.

Hope that helps

---

### Post by DivinityX on 2008-10-13
Thanks a lot! ^_^ it worked

[SOLVED]

---

### Post by PhatKnacker on 2008-10-15
Hi I have the exact same problem, but this fix dos't seem to work with vista, when I enter fixmbr in the comand prompit gives 'fixmbr' is not recognized as an internal or external command.
Any help would be most appreciated.

I have reinstalled Ubuntu to get Vista working again, but I really need to reinstall vista bootloader somehow.

---

### Post by Aero-Z on 2008-10-15
> **PhatKnacker said:**
> Hi I have the exact same problem, but this fix dos't seem to work with vista, when I enter fixmbr in the comand prompit gives 'fixmbr' is not recognized as an internal or external command.
Any help would be most appreciated.

I have reinstalled Ubuntu to get Vista working again, but I really need to reinstall vista bootloader somehow.
[http://www.lancelhoff.com/2008/09/07/how-to-fix-vista-mbr-repair-broken-vista/](http://www.lancelhoff.com/2008/09/07/how-to-fix-vista-mbr-repair-broken-vista/)

---

### Post by PhatKnacker on 2008-10-15
Thanks a lot Aero, I will try that when I get into work in the morning.

Yep worked a treat once again Thank you.

---

