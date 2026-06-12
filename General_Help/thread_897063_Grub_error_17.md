---
title: "Grub error 17"
date: 2008-08-21
forum: General Help
---

### Post by decoy26517 on 2008-08-21
Hey there ubuntu forum goers,

A long time ago I installed ubuntu and windows XP on an older machine that I don't use a lot. Everything worked ok for awhile but recently I've gotten a GRUB error 17 every time I boot it up. 

Now I've gone to: [http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945) and [http://ubuntuforums.org/showthread.php?t=1669](http://ubuntuforums.org/showthread.php?t=1669) and nothing that they've suggested works. probably the biggest problem is that the old computer doesn't have an optical drive installed anymore. So I tried to get a thumb drive of Super Grub going, but even that gave me errors and didn't fix the problem. 

So did Ubuntu completely brick my two hard drives or is there a way to bypass GRUB completely just so I can delete the thing?

---

### Post by Diabolis on 2008-08-21
It can be fixed: [http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by pauper on 2008-08-21
You might have already tried every possible solution, mentioned in the link
below, but check it out anyway.

[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

I type too slow, Diabolis :(.

---

### Post by decoy26517 on 2008-08-21
thanks for the replies!

Changing the boot order of the drives: Did not work, got a different error saying: NTLDR is missing, press Ctrl + alt + del to restart.

using GRUBs command line interface: I have no idea why they suggest this because you can't even get into GRUBs menu system to start with. 

Checked both drives jumpers and cables.


Unfortunately the link didn't help correct the problem. Does anyone else know of a way to fix this?

---

### Post by caljohnsmith on 2008-08-21
> **decoy26517 said:**
> So I tried to get a thumb drive of Super Grub going, but even that gave me errors and didn't fix the problem. 

So did you actually get Super Grub to boot off your USB, but then got errors when you tried to use Super Grub, or could you not boot Super Grub at all?

---

### Post by decoy26517 on 2008-08-21
I don't think SuperGrub loaded up at all. I got some error about cylinders.

---

### Post by adrian15 on 2008-08-22
> **decoy26517 said:**
> I don't think SuperGrub loaded up at all. I got some error about cylinders.

Did you follow this [guide to make your SGD usb](http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB.) ?

What was the exact error?

About the error 17 I suggest an fsck from a live cd.

adrian15

---

### Post by decoy26517 on 2008-09-05
Ok, I'm done with this. Can anyone point me in the direction to figure out how to uninstall ubuntu, GRUB and all of the other crap that ubuntu installed on my system without having to format my windows partition? 

Thanks.

---

### Post by Herman on 2008-09-05
Sorry things didn't work out for you. Here's a whole page full of ways to uninstall Ubuntu, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm"). Just pick whichever method you think will be the easiest for you.

Regards, Herman :)

---

### Post by chiefgeargrinder on 2008-09-05
> **decoy26517 said:**
> Ok, I'm done with this. Can anyone point me in the direction to figure out how to uninstall ubuntu, GRUB and all of the other crap that ubuntu installed on my system without having to format my windows partition? 

Thanks.

to remove grub you have to boot off the xp disk choose recovery console then when you see the c prompt you have to type fixmrb then it will ask for a administrator password you have to have a password assigned to the default administrator account in xp for this to work.
when i had the grub boot error the cause was I have xp pro install 32bit. I installed ubuntu 64 bit and it work for a little while but was getting grub boot 17 errors. I switched to ubuntu 32 bit then everything worked out fine so 32 bit xp and 64bit ubuntu didnt play nice togeather.

---

### Post by decoy26517 on 2008-09-05
> **chiefgeargrinder said:**
> to remove grub you have to boot off the xp disk choose recovery console then when you see the c prompt you have to type fixmrb then it will ask for a administrator password you have to have a password assigned to the default administrator account in xp for this to work.
when i had the grub boot error the cause was I have xp pro install 32bit. I installed ubuntu 64 bit and it work for a little while but was getting grub boot 17 errors. I switched to ubuntu 32 bit then everything worked out fine so 32 bit xp and 64bit ubuntu didnt play nice togeather.

Well on that computer, I'm using both 32bit XP and 32bit ubuntu because it doesn't have a 64bit CPU. I honestly have no idea what caused this but its been nothing but frustrating.

---

### Post by chiefgeargrinder on 2008-09-05
> **decoy26517 said:**
> Well on that computer, I'm using both 32bit XP and 32bit ubuntu because it doesn't have a 64bit CPU. I honestly have no idea what caused this but its been nothing but frustrating.

you can also boot off the ubuntu disk and reinstall the grub boot loader that way.

---

