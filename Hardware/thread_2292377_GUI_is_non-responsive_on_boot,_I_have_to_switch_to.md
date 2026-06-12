---
title: "GUI is non-responsive on boot, I have to switch to terminal ( CTRL+SHIFT+F1 ) to fix"
date: 2015-08-27
forum: Hardware
---

### Post by dlublink2 on 2015-08-27
Hello,

I have an HP Elitebook 8530P. I've tried Ubuntu 14.04, Xubuntu 14.04, Ubuntu-Mate 15.04 and they all have the same bug.

The computer boots, when I reach the GUI, no buttons work. 9/10 I can "fix" it by switching to a terminal ( CTRL+SHIFT+F1 ) and back to the GUI. 1/10 I have to restart the GUI. Once "fixed", the computer works reasonably well until next reboot. If the computer sleeps and wakes up, windows become unresponsive.

On Ubuntu-Mate 15.04, the interface is responsive but the mouse randomly disappears. When it does, it comes back after a CTRL+SHIFT+F1.


As mentioned, this affects multiple variants and versions of Ubuntu. 

I think it may be graphics card related because the computer occassionally horribly freezes ( white dots appear on screen, and take over the screen.) I have to hard reset the computer when it happens ). magic sysrq key doesn't help.

I have openssh-server installed and therefore am able to access any logs you need without affecting the bug.

Please advise,

David

Notes : The laptop has an ATI HD 3650 card. I will post lspci in a few minutes ( I am doing a clean install for the sake of simplifying diagnostics. )

---

### Post by Bashing-om on 2015-08-27
dlublink2; Hi !

I have to wonder:
> 
The laptop has an ATI HD 3650 card. I will post lspci in a few minutes

IF you are attempting to install a proprietary graphics driver ? Be aware none exist as ATI relegated these series of cards to legacy and no longer supports them. The only option in this situation is to run the open source driver - Which I affirm on my system performs very well .

[INDENT][INDENT]mind ya, just a thought
[/INDENT][/INDENT]

---

