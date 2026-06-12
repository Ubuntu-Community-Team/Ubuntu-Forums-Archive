---
title: "Reinstall...sort of"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by evil elvis on 2009-07-25
Greetings.  I had been running Ubuntu 9.04 with the ability to boot into windoze as needed.  Made a wrong turn messing about with Grub 2 (my fault) and ended up having to run fixmbr from xp's recovery console.  I have used this numerous times over the past several years without a problem.  This time it took out 3 OS's on 3 hard drives.  One of those drives contained the backups.  Don't know why, can't prove it but it did.  Enough whining.

My question:  is there a sequence of options I can select during a normal Ubuntu install that will basically re-write all of the system files while leaving the user files/directories intact?

I have been rebuilding my system for the past week and this would offer me an easy finish.  I'm tired.  Speculation about why this happened probably won't help me.  Pretty sure I know since all 3 hard drives were Maxtor's.

Regardless, any suggestion will be appreciated.

evil elvis

---

### Post by philcamlin on 2009-07-25
ahh this is going to drive me nuts i cant remember the name but yes i know what your talking about. every shutdown it reloads the os but still has yur files set.

you have to have a server to load the os from and a server to hold your user acocunt and settings etc.

:popcorn:

---

### Post by presence1960 on 2009-07-25
did you boot from the ubuntu live cd and see if your OS's and files are still on your disks? I say this because it sounds like all that happened is windows overwrote GRUB when you ran fixmbr, which is the usual outcome of that command. if your files are still intact all you need to do is reinstall GRUB to MBR to get booting Linux & windows again:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

---

