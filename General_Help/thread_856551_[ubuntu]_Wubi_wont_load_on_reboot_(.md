---
title: "[ubuntu] Wubi wont load on reboot :("
date: 2008-07-11
forum: General Help
---

### Post by Ubuntox on 2008-07-11
I love ubuntu more than Vista, i had it on my old computer so when i bought my new HP G7000 laptop id thought id put it on here, but as with linux there are always problems (Best thing about linux lol :P a good challenge).

Ok, when i restarted i got the option:

----------
MS Vista
Ubuntu
----------

So i selected ubuntu and pressed Enter
It had the Ubuntu logo and a proccess bar!
Once finished it went through lots of files/things (Black background white text)

Then stopped, and just left me with a CMD PROMPT (Terminal) and i don't know what to do.

Any help is great :D


----Computer Spec----
This may help...

30g Partion for Ubuntu [NTFS]
2gb RAM
INTEL Cor Due (1.47 GhZ x2)

---

### Post by MyBrainReallyHurts on 2008-07-11
I had the same problem. 

1. Verify if you have the Windows 32 or 64 bit version. 
2. Check the Ubuntu\Install folder. Make sure the correct version downloaded when you installed Wubi. 

I created a new folder UbuntuInstall, placed both files in the same folder and then ran Wubi. 

You have to make sure you have the 8.04.1 Wubi, and then the 8.04.1 ubunto with either the i386 or amd64, depending on which Vista version you have. 

Once I had everything correct, it installed correctly.

---

### Post by plastichero on 2008-07-15
Do you stuck at some point with this prompt?

[COLOR="DarkOrange"]Busybox v1.1.3 (Debian 1.1.1.3-5ubunu7) Bult-in shell (ash)
Enter help for a list of built in commands.
(initramfs)[/COLOR]

I also got the same thing and was astonished. The solution is simple: From windows, after running the WUBI installer, replce "quiet splash" with "all_generic_ide" in the file g:\ubuntu\disks\boot\grub\menu.lst and reboot. Hope it works. (Here G: was the drive that is selected for Ubuntu installation, it may be different for you)

also, is your drive FAT32 formatted? make it NTFS.

---

