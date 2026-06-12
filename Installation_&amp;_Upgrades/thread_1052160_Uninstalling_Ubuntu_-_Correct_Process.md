---
title: "Uninstalling Ubuntu - Correct Process?"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by Mahinva on 2009-01-27
I've read many threads on the issue, but wanted to ask if I have the process right for my system; many threads were regarding a dual-boot setup.

My goal is to uninstall Ubuntu and reinstall Windows XP while leaving my secondary HD untouched. Ideally, I will return to Ubuntu but not at this time.

Ubuntu is the only OS I have installed; it overrode XP in Ubuntu's installation. I have a secondary hard drive that was never formatted for Ubuntu and am backing up all my necessary files from my master to this slave. I have a licensed copy of Windows XP and though I have upgraded to Ubuntu 8.10, I have a 8.04 install CD which I hope can be of use if required.

I have read that I should do the following so I may reinstall Windows XP:

1) Downloaded and burn GParted Live to a CD. I am in the process of downloading now.

2) Run GParted Live and delete the disc's (master hard drive) contents.

3) I've also read that Windows MBR can be fixed by loading the Windows XP CD and then typing "fixmbr" at the prompt. (Alternatively, I've read of using supergrub figured I'd use the XP CD to save on another download.)

Are these steps correct? Am I missing anything?

[_THIS_]("http://ubuntuforums.org/showpost.php?p=5978093&postcount=4") post makes it seems I only need to run GParted Live. However, I've also read [_HERE_]("http://ubuntuforums.org/showpost.php?p=5849180&postcount=2") that fixing Windows MBR is a step too. For MBR, I've read [_THIS_]("http://ubuntuforums.org/showpost.php?p=6546490&postcount=2").

---

### Post by sancho panza on 2009-01-27
If you wish to completely remove ubuntu and install winxp on the entire primary drive, you can do that via the winxp install cd. When the winxp installer runs ask it to completely reformat your primary drive as ntfs and install winxp there. You do not need to necessarily use gparted or worry about mbr either.

If you wish to retain ubuntu on the primary drive, its more complicated.

---

### Post by Mahinva on 2009-01-27
Thank you very much, sancho panza! I am glad that the process is not as complicated as I thought it would be.

---

