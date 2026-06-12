---
title: "Dual booting."
date: 2008-07-14
forum: General Help
---

### Post by thegnarlypanda on 2008-07-14
Hi, I have just this second downloaded Ubuntu because I fancy a change from Windows. However, I have a question about dual booting. At the moment I dual boot Vista and XP and I was wondering that if I were to install Ubuntu whether I would still be able to boot to Vista or XP. 

I've read some instructions on how to dual boot and I can see no reason why it shouldn't work but I just want someone who has got it working to let me know.

Thanks.

---

### Post by geeth on 2008-07-14
As long as you select them in the boot loader setup when installing ubuntu there should be no issue.

---

### Post by WRDN on 2008-07-14
Its perfectly possible to tri-boot with XP, Vista and Ubuntu, and its even possible to quad- boot :)

Theres a guide [here]("http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php") on how to do it.

EDIT: I'm currently dual booting XP and Ubuntu. Ubuntu is my primary OS, while my brother uses Windows, as he has become accustomed to it and is resistant to change. I only use Windows now for a couple of games and some programming.

---

### Post by ChameleonDave on 2008-07-14
> **thegnarlypanda said:**
> XP. 

I've read some instructions on how to dual boot and I can see no reason why it shouldn't work but I just want someone who has got it working to let me know.

You'll probably find that something like half of the people here are dual booting.

---

### Post by Jim! on 2008-07-14
You should have no trouble with accessing the Windows partitions with Ubuntu installed along side them.

---

### Post by stolich on 2008-07-14
You can triple boot and even quad boot as long as you still have the necessary disk space, not only for required Ubuntu diskspace but also to other programs and softwares like updates and etc.

---

### Post by CatKiller on 2008-07-14
Just as a quick description so that you can read up on it, when you install Ubuntu, it will install [GRUB]("http://en.wikipedia.org/wiki/GRUB") into the [Master Boot Record]("http://en.wikipedia.org/wiki/Master_boot_record") of your hard drive. GRUB is able to [chain load]("http://en.wikipedia.org/wiki/Chainload") the Windows bootloader (which you are currently using to dual boot) to then carry on booting either version of Windows.

---

