---
title: "Upgrade problem(s)"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by jazzfan1 on 2009-04-25
I upgraded last night from 8.10 to 9.04. Everything seemed to go OK until it asked me to restart the system. Then at boot up I get the following:
Bug: Int 14: CR2 c1000000 EDI c1000000 ESI 00000000 EBP c0731f50
     ESP c0731f14 EBX ff78f000 EDX 000000e ECX 3f004000 EAX 00000000

err 0000002 EIP c073e3OD cs 00000060 f1g00010016

can anyone help before I go back to 8.10?
Thanks in advance
Armando

---

### Post by lemmof on 2009-05-07
I'm having the same error message.

I am trying to install Xubuntu 9.04 and I tried the desktop disk and the alternate install disk.  No matter what I do at the boot manager screen, I get that error message when I select install or check disk.

The machine works, because the old installation of Red Hat that is currently on the drive boots fine.

The only thing that I have found suggested by searching is to upgrade the motherboard BIOS.  The only software I can find to do that runs in Windows, which I don't have.  So what can I do?

I guess I can try 8.10 in the meantime but I'm running out of CDs!

---

### Post by rMatey on 2009-05-07
Hi!  I guess I'm not alone in this.  Tried to use Update Manager to go to 9.04 from 8.10   Hosed the system, which I had all data backed up.  Couldn't do anykind of install of 9.04, and tried them all.  And  updating the board is out... no updates out there as its unsupported now.  Built my own computers, and used an Abit board.
  I've been with Ubuntu since warty.  Is this the end, and now I'm a relic??  I thought we made these versions to run on less than ideal equipment??

:confused::confused::confused:

---

### Post by lemmof on 2009-05-07
8.10 is installing just fine.

I can't find a bug in launchpad that matches this very error.  I don't want to enter it myself because it seems to be a very technical thing, and it would just be "not enough information, closed!"  But I'd at least like to know when this issue is fixed and then I can know when to upgrade this machine.

---

### Post by rMatey on 2009-05-09
I posted elsewhere on the forums after I got mine fixed.  You can find more about the problem here :
[http://ubuntuforums.org/showthread.php?p=7232155#post7232155](http://ubuntuforums.org/showthread.php?p=7232155#post7232155)

  It just seems to affect the 9.04 upgrade.  Something about rolling back as patch or two.

---

