---
title: "GRUB and EasyBCD and problems booting."
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by MrCool0760 on 2009-11-06
Hello all, my computer setup looks like this. It originally had Windows 7 and then i later installed XP on the 2nd partition. I got it all booting fine with EasyBCD, giving me the option to boot into either.

Now i just installed Ubuntu last night and it looks like GRUB might have messed some things up. I decided to try to fix it on my own so i went into EasyBCD and reinstalled the original bootloader. Now it looks like this when i boot up..

1) Windows 7
2) WinXP
3) Ubuntu 9.10

BUT, for some reason, the only one that actually works now is windows 7! i will post the error messaged below if they provide any help. i obviously screwed something up when i installed Ubuntu and erased GRUB, so simply enough, how can i make my boot up menu look like the above with working operating systems?





Here are my errors when i enter each boot option

2)WinXP - "windows could not start because the following file is missing or corrupt:
<Windows root>\system32\ntoskrel.exe. Please reinstall a copy of the above file
3) Ubuntu- "Try (hd0,0): EXT2

---

### Post by Mark Phelps on 2009-11-06
You would do better going to the NeoSmart Technology forum and checking the EasyBCD support forum for details and tutorials.

---

