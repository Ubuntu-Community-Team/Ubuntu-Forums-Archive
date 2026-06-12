---
title: "[URGENT] - Ubuntu installed - XP: Autochk not found then BSOD"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by TheProblemMaker on 2009-09-18
[COLOR=Red]**[URGENT] **- ALL HELP GIVEN IS APPRECIATED[/COLOR]
**[COLOR=DarkOrange]IMPORTANT QUESTION: [/COLOR]**Will I be able to use an XP home CD to recover XP Media Centre?
Hey,
I've just installed Ubuntu desktop edition 9.04 on a desktop computer.
The installation was a success, and Ubuntu can now be used as a fully working operating system.
BUT, when I try to load Windows XP (Media centre edition) from the GRUB option (I'm choosing the right option) it goes to the loading screen but then says something along the lines of "autochk not found - SKIPPING AUTOCHECK" followed by a Blue Screen of Death 

[STOP c000021a{Fatal System Error} … 0xC000003a the system has been shut down] 

The system is manufactured by Packard Bell, it's a good few years old.
(I would love to go in depth with its specs, but I'm not sure how on Ubuntu)

It has ~512mb RAM, a nVidia graphics card and an Intel Pentium 4 (I highly doubt that means quad core) processor from what I can find.

To modify the partitions, I used the ubuntu installer.

Thanks so much in advance!

Just to go over again in short, Ubuntu works, XP doesn't.
Oh, and half of the  XP documents and settings files seem to have *vanished*

~Andy

P.S. I believe the version of Ubuntu I have installed and working uses GNOME.
I've tried using gedit to change a file in the grub folder to add a line 'unhide (hd0,1)' just above the root line. -Didn't solve the problem. I think it's to do with windows itself.

---

### Post by stlsaint on 2009-09-19
Yes sounds like windows has gone bad as ubuntu does not alter windows boot files in anyway! try running recovery on windows...but as we all no the BSOD usually means its not looking good for the OS!
all hope is not lost tho as ubuntu can access your windows partition and you could start pulling important files off of there! go to add/remove programs under Applications and install the NTFS tool from there just to help in the ntfs handling. then go to <Places> you should see your windows partition...select that partition and it should mount to your desktop. from there you can enter into the partition and start transferring files over to ubuntu or ext. hdd!

hope this helps

---

### Post by Bucky Ball on 2009-09-19
Don't panic yet! As suggested, IF you have a install CD of windows you can run repair. That will put you at a prompt. First type 'help' and you will get a list of commands. Check that I have the spelling right for the code here:

```
chkdsk
fixmbr
fixboot
```

Type these one at a time and let it go through the motions. That should give you a working Windows: BUT, if you have grub installed on the first part of your Windows partition you will have wiped it with the process and will need to re-install grub.

Easiest way to get a working grub is to do it with Super Grub Disk. Download and burn the iso then boot from it:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I think you will need to get the boot sector in order before using it but you could give it a try first. 

It shouldn't be major; grub has probably just fiddled with your Windows boot.

* The Ubuntu Grub boot loader broke the Windows MBR so kind of about Windows. You will find once the MBR is fixed it should work as was. In other words, it shouldn't have effected the actual Windows install in anyway. :)

---

### Post by TheProblemMaker on 2009-09-19
Sorry to say this, but I strongly believe Ubuntu has done something, I am certain that it was the partition manager in Ubuntu.

The next Mega-Scary thing is when I try to access my XP partition... I can get into Documents and settings, but I CAN NOT see my My Documents folder or ANYTHING.

To confirm,
Ubuntu installation has meddled with windows booting, and this has directly affected the AUTOCHK file?
Also, do any of you have MSN Messenger? If yes, and you would be happy to assist me on there, PM me.

The computer is not mine, so the whole installation of Ubuntu, it wrecking XP and stopping the OS from starting came as a complete shock to me as it had worked on every other computer I've installed it on.

I can not find an XP installation CD for the computer. (Media centre edition)

Thanks.

---

### Post by onehit on 2009-09-19
I am going through a very similar situation.

I messed with the partitions on my already dual booting machine with WinXP + Vista on it so that I could add Ubuntu

I used 

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

to repair the Windows MBR and now it looks like Vista is booting fine. I'm not sure if a Vista Recovery disk will work for you because you only have XP but you should try booting with an XP CD into the recovery console and fixmbr and then fixboot like the previous poster suggested.

---

### Post by TheProblemMaker on 2009-09-19
Onehit,
Thanks for your comments.
Searching the net, I have found that it may be an issue of a hidden NTFS partition OR I need to change the partition types from Primary to Logical. I have no idea as to how I fix that without booting into windows. (An Ubuntu application? DOS startup disk?)

MORE RESEARCH:
The autochk problem may be related to the system wanting to check my disk on startup, but it cannot find the file causing it to canibalise itself.

~Andy

---

