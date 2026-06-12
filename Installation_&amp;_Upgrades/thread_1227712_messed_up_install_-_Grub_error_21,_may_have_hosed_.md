---
title: "messed up install - Grub error 21, may have hosed existing install"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by bluepowder7 on 2009-07-31
ok, sorry for the newbie question, but here's what i did:

have 8.04 and win2k and winxp on existing hard drive
installed 8.04 onto a USB drive for experimenting
MISTAKENLY the last option during install setup is something about writing something to hd(0,0) or something like that.  i left it checked!

now i can't boot back into my regular 8.04 that's on the hard drive, i get the usual Grub Error 21.

i THINK that the installer wrote over some info on the hard drive.

what do i do to fix it?  if i use the livecd, i can see the grub menu file, and i think it LOOKS like i last had it, but i'm not 100% sure what to look for - or if that's even where the change was made.

help!

---

### Post by louieb on 2009-07-31
Probable the install changed the MBR of the boot drive to load GRUB from the external drive. Does it boot with the external plugged in? 

To use GRUB on the internal drive - the fix is the same as if you had reinstalled windows. 
[How to install Grub from a live Ubuntu cd. - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub") 
[Recovering Ubuntu after installing Windows - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by bluepowder7 on 2009-07-31
wow that was great!  thanks!  the process worked perfectly with the only change being "/grub/stage1" instead of "/boot/grub/stage1"

thanks!!!

---

