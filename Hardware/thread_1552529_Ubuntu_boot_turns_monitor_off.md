---
title: "Ubuntu boot turns monitor off"
date: 2010-08-13
forum: Hardware
---

### Post by mysteryword on 2010-08-13
Hey guys.  I need help with the Ubuntu 10.04 installed with wubi.  I installed it on the computer but now when I want to boot up Ubuntu on start up my monitor goes to sleep.  I couldn't even get to the Ubuntu logo and couldn't finalize the installation.  I'm really frustrated because I installed it on my laptop which Ubuntu worked perfectly on except wireless wouldn't work.  I tried all that madwifi and ndiswrapper but nothing worked.  So I thought that on my desktop it would work without much problems.  Instead now I don't even get a screen.  It's pretty annoying and I really like Ubuntu.  Please help!

---

### Post by mysteryword on 2010-08-13
I forgot to mention specifications.  I'm running an HP Pavilion AMD Athlon 64 X2 Dual Core Processor 3800+.

_Display Adapter_
NVIDIA GeForce 6150 LE

_Monitor_
HPvs15 Flat panel monitor

I'm also not really familiar with the Ubuntu terminal codes and such so if someone can explain the process of the solution, it would be much appreciated.

---

### Post by bcbc on 2010-08-13
> **mysteryword said:**
> Hey guys.  I need help with the Ubuntu 10.04 installed with wubi.  I installed it on the computer but now when I want to boot up Ubuntu on start up my monitor goes to sleep.  I couldn't even get to the Ubuntu logo and couldn't finalize the installation.  I'm really frustrated because I installed it on my laptop which Ubuntu worked perfectly on except wireless wouldn't work.  I tried all that madwifi and ndiswrapper but nothing worked.  So I thought that on my desktop it would work without much problems.  Instead now I don't even get a screen.  It's pretty annoying and I really like Ubuntu.  Please help!

After selecting Ubuntu, you see the grub menu. Hit 'e' to edit the entry. Find where it says "quiet splash" and add "nomodeset" so it says (without quotes) "quiet splash nomodeset".
Then hit CTRL-X to boot.

Once booted, and online you'll need to check for specific drivers for your nvidia card. (System, Administration, Hardware Drivers).

---

### Post by bashologist on 2010-08-15
I have the same graphics card and I'm having problems after installation and after using nomodeset. After installing nvidia drivers I reboot and it says there's like an error and it asks me to reconfigure graphics.

So I go though the maze of options and reset it back to "default". I'm not able to get the nvidia drivers installed. Only difference is I'm using Ubuntu 10.10 Alpha 2 Desktop.

---

