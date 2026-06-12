---
title: "Deleted Wubi - what now?"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by suerachel on 2009-08-21
Hi, we run Ubuntu parallel with Windows XP on a laptop. My husband's writing files are under  the Ubuntu installation - and I UNintentionally UNinstalled Wubi today in the process of checking a new Ubuntu Boot CD.

Is there any way to access Ubuntu environment and rescue these files?
Thanks for any help. Husband is stressed!

---

### Post by suerachel on 2009-08-21
BTW, Ubuntu now longer offers as a boot option on Reboot, laptop jumps straight to Windows, and I can see no way to access files that were saved under Ubuntu.

---

### Post by JOHNNYG713 on 2009-08-21
Hi run a live ubuntu to access your files and retrieve them for back up, Then reboot ubuntu live and try repair mode, or reboot into windows, and try to reinstall wubi, OR after retrieving your files do a fresh install of ububntu

---

### Post by howefield on 2009-08-21
> **suerachel said:**
> Hi, we run Ubuntu parallel with Windows XP on a laptop. My husband's writing files are under  the Ubuntu installation - and I UNintentionally UNinstalled Wubi today in the process of checking a new Ubuntu Boot CD.

Is there any way to access Ubuntu environment and rescue these files?
Thanks for any help. Husband is stressed!

Have you simply removed the boot options with the Wubi folder still in windows ? 

Exactly what did you do ?

PS. He can always use his backup... he does have a backup of his files, yes ????

---

### Post by suerachel on 2009-08-21
Can you explain what you mean by 

" run a **live ubuntu** to access your files and retrieve them for back up,"?

This sounds like a hopeful option!

We have an Ubuntu image disk.

---

### Post by suerachel on 2009-08-21
PS if we had a backup of all the files this would be a non issue.... but thanks for the thought

---

### Post by howefield on 2009-08-21
> **suerachel said:**
> PS if we had a backup of all the files this would be a non issue.... but thanks for the thought

I was joking... 

You still haven't told us exactly what you have done, if it is only the boot options that you have screwed, try this page..

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Scroll down to "How can I access my Wubi install and repair my install if it won't boot?"  very near the bottom of the page.

---

### Post by suerachel on 2009-08-21
There is still a file called [file:///C:/WINDOWS/Prefetch/WUBI.EXE-14717AF8.pf](file:///C:/WINDOWS/Prefetch/WUBI.EXE-14717AF8.pf) and one called [file:///C:/WINDOWS/Prefetch/WUBI.EXE-3AB3BFC5.pf](file:///C:/WINDOWS/Prefetch/WUBI.EXE-3AB3BFC5.pf) in the WINDOWS folder. no idea what these are. 

Process: I had burned a new Ubuntu 8.04 image disk to load Ubuntu onto another laptop soon. In trying to verify it, as per the Ubuntu download site, I was offered the option of removing the existing Wubi, which I took, and it began the Uninstall wizard. That looked worrying... Then no more Ubuntu boot option on rebooting the computer.

---

### Post by howefield on 2009-08-21
That sounds bad, much worse than screwing the boot loader, I'd stop using the machine in question and try some file recovery utilities to restore your deleted Ubuntu folder.

You might still get your files back, but the more you use that hard disk, the higher the risk of over writing the files you want.

I use a commercial program called Easy Recovery (usually for getting deleted .jpgs from SD cards) but there are several free programs available, none of which I know about so can't recommend.

---

### Post by suerachel on 2009-08-21
Sadly the computer has already been through several reboots before we knew there was a problem. I suspect that there is little chance of recovering files. Windows Recovery won't help at the moment either. Guess we are done for.

Thanks for your help guys!

---

### Post by wojox on 2009-08-21
Try recuva. I've used it on xp before and it's free:

[http://www.recuva.com/](http://www.recuva.com/)

---

### Post by Jon Monreal on 2009-08-21
> **suerachel said:**
> Sadly the computer has already been through several reboots before we knew there was a problem. I suspect that there is little chance of recovering files. Windows Recovery won't help at the moment either. Guess we are done for.

Thanks for your help guys!

I wouldn't give up that easily. There are plenty of programs, some free and some not, that can [restore deleted files]("http://www.google.com/#hl=en&source=hp&q=windows+file+recovery&aq=f&aqi=g10&fp=35e5f905b5e4329b"). Your rebooting several times isn't nearly as bad as downloading files and the like. It would be worth it to at least give one of these programs a try. If you can, use another computer to browse this thread and download the program on to a flash drive and run it from there.

---

### Post by JOHNNYG713 on 2009-08-22
Once again download and burn a ubuntu live cd and retrieve your files, then refer to my first post, a ubuntu live cd will more than likely see your ubuntu partition and you my copy those files to a flash drive, external hard drive and even to your your windows partition !

---

### Post by 999terry on 2009-08-23
Please let me know how you go as I have the same problem. My email: [email]dialogue_quest@hotmail.com[/email] - thanks - 999terry

---

### Post by 999terry on 2009-08-24
one other possibility is to go to the windows xp system manager and to 'system restore' which should have a number of restore dates to return the system to which may then show up wubi before it was damaged!

---

### Post by psonar on 2009-11-09
> **JOHNNYG713 said:**
> Once again download and burn a ubuntu live cd and retrieve your files, then refer to my first post, a ubuntu live cd will more than likely see your ubuntu partition and you my copy those files to a flash drive, external hard drive and even to your your windows partition !
Your suggestion does not apply to a wubi install of linux.  With wubi, Linux lives inside a disk image within the Windows file system.  Wubi adds an option to the Windows boot manager that allows the disk image to be mounted and booted into if Ubuntu is selected at the boot menu.  One of the main advantages of wubi is that it does not require partitioning, which makes trying Linux a much lower risk proposition for Windows users.

Deleted file recovery is most likely the best option at this point.

---

