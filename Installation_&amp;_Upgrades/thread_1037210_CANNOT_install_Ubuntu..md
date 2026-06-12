---
title: "CANNOT install Ubuntu."
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by codfishy on 2009-01-11
Hello.  I have a MAJOR problem. I **cannot** install Ubuntu.  I have tried everything.  I used the Alternate/Text Based Installer, and the normal Desktop installer, but NOTHING works!

I checked the checksum and everything, everything is correct.

I'll tell you what happens when I boot up the Dekstop CD:
Everything is all fine and dandy until I get to the main menu(Be aware this isn't the Live CD screen). I select my language(English) then I select "Install Ubuntu", and away I go. It stays on the Ubuntu Loading screen(with the orange bar from side to side) for about 2 minutes. After that is up, a "BusyBox" screen pops up. It says this exactly:

"Loading, please wait...
BusyBox v1.10.2 (ubuntu1:10.2-1ubuntu6) built in shell (ash)

Enter 'help' for alist of built in commands.

(itinramfs) _"

What do I do there so that I can get to the Live CD screen/Installer Screen?

Now I will tell you what happens when I use the Alternate/Text Based installer:
Everything again is all fine and dandy until I hit the menu. I again select English, then "Install Ubuntu" After a long wait, I am brought to the Text Based Installer. I again choose my language and my country, and I select my keyboard. At the "Detect CDRom and mount"(or something like that) selection screen, I am told that "No common cd rom drive was detected".

LIKE what! My CD rom is inserted, and that's how I got to this screen! I already tried the ctrl+alt+F2 and modprobe ide-scsi thing, but that didn't work!

WHAT DO I DO?!

My specs are:
-AMD Athlon 64 X2 Dual Core 6000+
-ASUS M2A-MVp Motherboard
-2 GB of RAM
-125 GB Hard Drive(IDE, and it has XP on it)
-500 GB Hard Drive(Sata, and I want to partition it so that only 125 GB on it has Ubuntu)

But I can't DO THAT BECAUSE I CAN'T EVER GET TO THE ACTUAL INSTALLER!

---

### Post by avtolle on 2009-01-11
The error you are describing with the alternate install iso occurs on the ppc alternate iso, too; the work around there has been to get to a terminal and do ```
modprobe ide-scsi
```I've no idea if this will work on your system, but is offered as something to try.

Been thinking; instead of doing the above, see [https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20During%20Install]("https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20During%20Install") for how to change boot options during installation, and after pressing F6 to get to the boot line, try "all generic ide" (without the quotes, of course) there to see if this works.

EDIT: sorry, was going from memory. On checking some resources, that boot parameter shoud be "all_generic_ide" (again without the quotes). See if that helps.

---

### Post by avtolle on 2009-01-11
Also, see post #9 in this thread: [http://ubuntuforums.org/showthread.php?t=1035271](http://ubuntuforums.org/showthread.php?t=1035271) with the attendant information contained therein. I don't know if this will help you, but it is something to try.

---

### Post by codfishy on 2009-01-11
Darn it. It didn't work.

---

