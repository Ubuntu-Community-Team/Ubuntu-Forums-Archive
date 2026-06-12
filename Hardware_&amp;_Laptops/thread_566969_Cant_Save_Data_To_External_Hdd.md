---
title: "Cant Save Data To External Hdd"
date: 2007-10-04
forum: Hardware &amp; Laptops
---

### Post by godwin on 2007-10-04
hello everyone, yes i am a newbie to ubuntu.
well my win xp partition seemed to have died on me, pc wont boot anymore...think either hdd partition is courrupt or damaged by virus or the hdd is physically damaged.
however when i use the ubuntu live cd i can actually access all my files.
tried to copy what i need to an external harddrive but it says i do not have permission..
i tried to give permission by right clicking on properties but nothing..
can anyone please help me... either to fix the hdd or be able to back up my files..
thank you very much

---

### Post by dabl on 2007-10-04
It's been too long for me to be real crisp on this, but I think "fixmbr" or "fixboot" are the Win commands that are relevant to your boot problem.  These would be issued on the command line after you have booted the Win installation CD and chosen "recovery mode".

If you Google those commands, you should find more specifics.

An undesired (by you) consequence of fixing the Windows booting may be that it will bork the Grub bootloader, and so Job #2 will be to fix that so you can back to dual-booting.  Here's guidance:

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

:)

---

### Post by godwin on 2007-10-05
thanks for your reply
already tried all the win commands.. but no luck
is there a way to access as an admin using the live cd.
with the ubuntu live cd i am able to access all my files on the hdd
however if i try to copy to external hdd it says i do not have permission
and wheni try to change permission it does not allow me
please help

---

