---
title: "BIOS upgrade only comes as Windows executable"
date: 2008-05-14
forum: Hardware
---

### Post by Sarah L on 2008-05-14
Hi,
I want to upgrade my Lenovo 3000 n100's BIOS. Only problem is, the manufacturer only provides a Windows XP installation exectuable, and I only run Ubuntu on my system. The laptop didn't come with an XP disc so I can't reinstall windows.

How can I flash my laptop's BIOS?

Thanks,
Sarah

---

### Post by 505 on 2008-05-14
Usually flashing is done in an environment where no OS is running. Most likely the Windows executable will create an bootable disk or CD which can then be used to flash the bios. If the executable if some sort of archive, you might be able to open it in file roller. Otherwise try to make the disk on another computer.

---

### Post by Sarah L on 2008-05-14
Unfortunately the executable doesn't seem to be simply an archive, and it doesn't create a boot disk either. The instructions simply say, click and run, so I'm reluctant to run it on another machine in case it goes straight to BIOS-wiping.

Are there any other alternatives?

---

### Post by Zorael on 2008-05-14
Most such programs don't dare flash when not running under a DOS/similar OS session. I recollect seeing an app named something in lieu of WinFlash that claimed to be able to do it when running XP, but no; most such .exes ask you to insert a floppy, which it'll proceed to format and make bootable with the new bios image in place.

My educated guess would be that it's Safe&#8482; to run it on another computer. Any self-respecting bios upgrading software will ask for your confirmation anyway, blaring warnings about how power outages will hose your system.

---

### Post by MemoryDump on 2008-05-14
I'd email the manufactor asking if there's any alternative methods in installing their bios updates.

---

### Post by prshah on 2008-05-14
> **Sarah L said:**
> manufacturer only provides a Windows XP installation exectuable, and I only run Ubuntu on my system. 
How can I flash my laptop's BIOS?


Get hold of a Windows Live CD (Yes, there is such an animal). Boot off it, flash your BIOS, and Bob's your uncle.

Any more details are (I think) against forum policy; i'm skating dangerously close to it anyway.

---

### Post by logos34 on 2008-05-14
> **Zorael said:**
> I recollect seeing an app named something in lieu of WinFlash

that's what I think it is too--a WinFlash .exe (Intel boards have those)...you just run them from the desktop and it completes by rebooting


Here's what I'd try (a popular thread):

HOWTO: Flash BIOS, The Ubuntu Way
[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

---

### Post by Sarah L on 2008-05-14
I took a leap of faith and ran the executable on a Windows system. Fortunately it turns out it's only a self-extracting package, and it dumped a bunch of files onto my desktop. There's a bunch of .dll's and WinPhlash, and a couple of .WPH files which I presume are the WinPhlash-formatted BIOS files.

Unfortunately this is all on another computer... how can I run it on my Kubuntu laptop (which doesn't have a floppy disk drive)? I doubt my Linux live CD's will be able to run the (Windows) BIOS update utility.

EDIT:
Ah, sorry guys, I started typing my response before I saw the new posts. I'll get to reading that forum thread right away, and as to Windows Live CDs: where can I get one? PM me or something >:)

---

### Post by Limbic on 2008-05-14
I recently updated the Bios on my Abit IP35-e and the installer actually did run completely in Windows (Vista x64 dual boot).  I installed the program, then ran it and it checked my BIO version against the most recent available, downloaded it directly within the application, then installed it.  The update went smoothly and it POSTed the most recent BIOS when I rebooted.

The program was [FlashMenu]("http://www.abit-usa.com/downloads/bios/flashmenu.php").

---

