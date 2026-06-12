---
title: "System Description Tables not loading"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by TriadDraykin on 2009-02-10
Hiya. This'll be my fifth time going back to trying ubuntu... I keep on having to sell my systems for food and rent! Can't resist Ubuntu, though. No 'you just can't do that' with Linux!

Trying to install Ubuntu Intrepid Ibex.
Got a 2.6 ghz processor, 1GB RAM, 128MB PCI graphics card, able to boot the CD. CD checks out for defects, even ran a memory test overnight! Burnt a new CD, had a winmd5sum ran on the image, checks out just fine, and tried one burnt with PowerISO, and when that didn't work, InfraReader. Same problem every time.
I get a brief message displayed, Unable to Load System Description Tables, after selecting either Install or Run without Changes, then the bar runs back and forth, da-de-da... It loads the first two sections and most of the third, and freezes. I even tried to let it run for a couple hours... Nope, stayed frozen. 

What I want to have set up is a dual-boot, I have a separate 16-gig internal drive set aside for Ubuntu, and the other drive for XP. And an external 160-gig for storage. 

Help?

---

### Post by TriadDraykin on 2009-02-12
I'm guessing from [http://ubuntuforums.org/showthread.php?p=6724446&posted=1#post6724446](http://ubuntuforums.org/showthread.php?p=6724446&posted=1#post6724446) that I can bump... So here's my first self-serving bump!

Bump!

---

### Post by TriadDraykin on 2009-02-16
PLACEHOLDER POST:

Normal:ACPI Unable to load System Description Tables

Display and Verbose:
[69.927187] [<c0370000>] ? Default_Device_exit +0x70/0xb0
[69.927187] ====================
[69.927187] Code: (a lot of hex here)
[69.927187] EIP [<f8a34dpp>] squashfs_get_cached_block +00x3b9/0x4c0 [squashfs] SS: ESP 0068:f1359c50
[69.927187] ---- [ end trace 92415d 158c5ea60c ] ----
init: rcS main process (####) Killed by SEGV signal
init: unable to execture bin/sh for RC-default: No such file or directory
init: rc-default main process (####) terminated w/ status 255

---

### Post by Matrix7 on 2009-03-25
I seem t be having a similar problem.  Same "Unable to load the System Description Tables".  I have yet to find an answer for my problem but when I do I will make sure to post a response here.  Just out of curiosity i don't suppose your computer is a Compaq Presario is it?  That is what mine is and it doesn't want to run ANY version of Linux that I have found. I am wanting Ubuntu Studio for media creation, Kubuntu for everyday use and my current XP Home for some things that Linux will not do such as a few specific games - at least until I can get better with WINE and try to get them over to Linux.

From other posts sprinkled around the net on this problem I fear it may be an issue between the hardware and the kernel o.O

I will bookmark this post and report back if I have any luck tracking the problem down.

Regards,

::[Matrix7]::
[http://matrix7.deviantart.com](http://matrix7.deviantart.com)

*Looks at your location*  Maybe it's an Ohio thing :-)

---

### Post by Matrix7 on 2009-03-25
Okay!  I may have some hope for you.  I searched the forums pretty thoroughly and found this post by another user with the exact same problem and system as I have.  Not sure if yours is a Compaq as well, but try the steps detailed here and see if it works.  Good Luck!

[http://ubuntuforums.org/showthread.php?t=1037909&highlight=Unable+load+System+Description+Tables](http://ubuntuforums.org/showthread.php?t=1037909&highlight=Unable+load+System+Description+Tables)

---

