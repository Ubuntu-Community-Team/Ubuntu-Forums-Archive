---
title: "compaq laptop won't boot after clean install"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by pehrlabel on 2009-03-06
hello, i have a compaq v2000 laptop. i can't get it to boot since i installed ubuntu 8.10. i have no other installations, no xp, just ubuntu.

i installed from the live cd. when it asked me where to install the bootloader, i put it on /sda.

now when i turn the computer on, i just get a black screen with the cursor (nothing else) after the bios splash.

i can still run linux off of a live cd just fine. the live cd can also see the hard drive.

when i put a vista cd in just to see what the problem was, vista installer told me that the bios might not be able to see the drive.

i also tried to use super grub disk, but it said "error 15"

any help would be much appreciated. thanks!

---

### Post by Mark Phelps on 2009-03-07
You should have installed GRUB to the MBR of your hard disk.

See the following link about installing GRUB from the Ubuntu LiveCD:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by pehrlabel on 2009-03-07
Thanks, I forgot to mention that I already did that Grub tutorial as my last step, and it made no difference.

i think this might have something to do with a secret partition from compaq and the bios. i remember something like this happening with a laptop before from toshiba.

this has never happened to me with desktops.

---

### Post by Dallywood on 2009-03-07
I have the same problem with my compaq when trying to use 8.10
I tried to install, and I tried to just run ubuntu off the cd but both options didn't work for me.
I am trying 8.04 now and I'll let you know if it works better

---

### Post by pehrlabel on 2009-03-08
Well I was researching the compaq angle on this problem, and I ran across something called BOMID, that says Compaq and HP had proprietary code on their drives, and if you wipe the drive with a clean install, you erase some small amount of that code and the laptop won't let you boot. I'm going to try to find out if that's the problem with this particlular laptop.

---

### Post by pehrlabel on 2009-03-11
from chatting with compaq support, i think i am stuck with xp on this laptop. i don't think the bios wants to boot anything else. i'm going to attempt to install xp again (ugh) from a restore cd, and then try a dual boot configuration and see if that will work.

anyone else know how to get xp off this compaq for good and get just ubuntu, lemme know. cheers!

---

### Post by Neo_The_User on 2009-03-11
You got a spare Desktop or something? You can take the hard drive out, put it in the desktop and put the hard drive on top of the case or something and I can tell you a command that will most likely work. Also, I've hacked an Alienware computer that locked me out of installing linux on it and it worked afterward but that was a desktop.

---

### Post by pehrlabel on 2009-03-11
Hey Neo thanks for the advice but i finally got it to work. i don't know why i couldn't get ubuntu to work on it's own but i'm going to guess it was that whole thing with BOMID (i'm still not even sure this laptop has BOMID). but once i used a restore cd to get windows back on the laptop, then i used the install cd for ubuntu, everything now works.

after the clean install of linux, the drive showed up in the bios with an exclamation mark next to it. i re-enabled my drive in the bios with shift-F1 i think, and then re-set up this computer with both OSes. cool.

grub works now!

---

### Post by Greg748 on 2009-03-12
hey check this out mate i was having trouble with my compaq presario v3000 as i had lost the restore disks so this fixed my problem and works great
```
http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/
```

---

