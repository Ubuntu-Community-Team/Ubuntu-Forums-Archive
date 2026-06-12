---
title: "[SOLVED] Need help with new installation"
date: 2008-10-19
forum: General Help
---

### Post by Ironhorse_somo on 2008-10-19
Background info:
I have installed Ubuntu 8.04.1 LTS Desktop edition 32 bit as my only OS (the disc was received from Ubuntu via snail mail - not burned on my computer.) My computer was built for me by a local shop and is not any name brand. After playing with Ubuntu a little on the disc, I installed it over my existing Windows, and have no Windows any more.

The problem:
After it goes through the ubuntu startup screen, and I watch the little bar go back and forth under the ubuntu logo, it kicks up the following error:

Busybox v1.13 (Debian 1:1.1.3-5ubuntu12)Built-in shell (ash) Enter 'help' for a list of built-in commands.
(Initframs)

And I am unable to proceed any further. Yes, I am a complete newbie to Ubuntu. Help?

---

### Post by anhvu2875 on 2008-10-19
**Ironhorse_somo**
take a look at this : [http://ubuntuforums.org/showthread.php?t=941111](http://ubuntuforums.org/showthread.php?t=941111)

---

### Post by jmszr on 2008-10-20
This has worked for me:

This is from the Wubi Wiki-lots of good information there:

The Ubuntu splash screen loads for awhile then exits to a BusyBox/(initramfs) prompt.

Try The Following Solution: 1) Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in.Click Properties.
Select the "Tools" tab and click "check now" under error checking(On Vista, You might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After The checking is done, restart the pc by using the start menu(Do not hard reboot) and try using ubuntu now.

---

### Post by Ironhorse_somo on 2008-10-23
oops

---

