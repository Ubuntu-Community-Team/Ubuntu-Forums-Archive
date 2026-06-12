---
title: "Ubuntu disc won't start"
date: 2008-09-06
forum: General Help
---

### Post by erorr404 on 2008-09-06
I have a copy of the latest version of Ubuntu on CD, and I get an error whenever I choose an action (I have tried Demo and Check Disk for Errors actions, and I assume I'll get the same error if I choose to install Linux). Here is what happens:

After I select a language and an action it says,

```
Kernel active
Kernel direct mapping table...
```

Then the Ubuntu loading screen appears.

Then I get a console window that later shows an error:

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [    83.099993] ata6.00: revalidation failed (errno=-5)
[    83.151477] ata6: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0 t4
[    83.151527] ata6: irq_stat 0x40000008
[    101.806626] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    101.808371] sd 6:0:0:0: [sdb] Assuming drive cache: write through
```


I need to get Ubuntu installed on this computer (to dual boot with Windows Vista), so any help would be appreciated. The computer is a Gateway P-7811FX laptop with 4GB RAM, an SATA hard drive, and a Core 2 Duo P8400 processor. The Ubuntu version is 8.04.1.

Thanks in advance.

---

### Post by Predator106 on 2008-09-06
I have to be honest, I'm basically clueless when it comes to the CD, but lets see if I can help.

First of all, how many times did you try the Live CD (with the demo option)?

Did you/is it possible to try it with multiple drives?? i.e. 2 or more?

---

### Post by MaxIBoy on 2008-09-06
Only thing I can think of is to burn another CD at a slower write speed.

---

### Post by erorr404 on 2008-09-06
> **Predator106 said:**
> I have to be honest, I'm basically clueless when it comes to the CD, but lets see if I can help.

First of all, how many times did you try the Live CD (with the demo option)?

Did you/is it possible to try it with multiple drives?? i.e. 2 or more?

I tried the demo maybe 5 or 6 times, each time I get that error.

I only have one dvd drive in this laptop, and I don't have another one to replace it with (if that's even possible).


I am redownloading the Ubuntu CD and I'm gonna burn it at a slower speed to see if it works (although my last CD worked flawlessly on my old laptop when I installed Linux on it a couple of weeks ago).

---

### Post by erorr404 on 2008-09-06
I tried burning a new disk at 10x, but the result is exactly the same. Trying the demo gives the same error (except it says "[    101.808371] sd 6:0:0:0: [sdb] Assuming drive cache: write through" a few more times).

Could it be an issue with the hard drive? The first couple of lines say 'ata6' and the last lines are clearly about a drive. Does Ubuntu support SATA?

Any other ideas, or advice about where to get help? I will really need Linux installed on here when school starts. :(

---

### Post by erorr404 on 2008-09-07
I tried using the "Alternate" Ubuntu CD and although I did get the error, it went straight past it and onto the installation. I was able to successfully install Linux from there.

The only problem I encountered was it wouldn't let me change the size of a partition, so I couldn't shave a few GB off my empty partition for some Swap space. I probably won't need it, since I have 4GB of physical memory.. right?

Anyway, thanks for the help.

---

### Post by tangibleorange on 2008-09-07
> **erorr404 said:**
> I tried using the "Alternate" Ubuntu CD and although I did get the error, it went straight past it and onto the installation. I was able to successfully install Linux from there.

The only problem I encountered was it wouldn't let me change the size of a partition, so I couldn't shave a few GB off my empty partition for some Swap space. I probably won't need it, since I have 4GB of physical memory.. right?

Anyway, thanks for the help.

unless you use hibernate, you don't need swap at 4GB (lucky) :)! well not unless you plan on opening 20 copies of open office...

---

### Post by MaxIBoy on 2008-09-07
I have 4 gigs of RAM, I use swap anyway for hibernate and also in case I ever feel the need to show off.

If you ever want to hibernate, try booting from the CD of another distro (PuppyLinux comes to mind,) create the swap partition. That will be safe because EXT3 isn't prone to fragmentation as bad as NTFS. If the swap partition isn't recognized, reinstall Ubuntu and tell it to "use as" swap.

---

### Post by Predator106 on 2008-09-09
This is random but something that I had happen with Firefox yesterday, when I was using OpenOffice to do a school project. I was worried it was OpenOffice, because suddenly my music skipped (never ever does), and the desktop was getting laggy (never does either), and it was acting like... well, it felt like using a Mac, to be honest, even a dual core CPU-d Mac feels really really laggy, and bottles up after every program runs. Anyways, it used all 2 GB of memory, and went into my swap space. I think it's 2 or 4 gigs of swap space. But yeah, it maxxed out the whole thing heh, my hard drive was running like crazy, was really really weird. Never had it happen before.

</random thought>

---

