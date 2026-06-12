---
title: "Need some really Big Help."
date: 2008-04-11
forum: Hardware &amp; Laptops
---

### Post by Ventango on 2008-04-11
Ok so I have decided to rid my self completly of window's and now i want to know how do i remove the Window's OS Completly and Put Linux There Instead. i dont want to Dual Boot them i want to compleatly ridmyselfof window's. Also Is there a way of Using linux without a Cd.

---

### Post by kutjara on 2008-04-11
> **Ventango said:**
> Ok so I have decided to rid my self completly of window's and now i want to know how do i remove the Window's OS Completly and Put Linux There Instead. i dont want to Dual Boot them i want to compleatly ridmyselfof window's. Also Is there a way of Using linux without a Cd.

You need some device capable of booting your PC, other than the hard drive. On modern machines, that usually means the CD drive or (if you have a BIOS that supports it) a USB flash drive. There are distributions that will install from a USB drive, but I don't think Ubuntu is one of them (without a lot of manual tweaking).

When I install Ubuntu, I just set my bios to boot from CD, slap in the Ubuntu CD (I typically use the "alternate" CD that just lets me install Ubuntu, rather than running it live from the CD), and tell it to use the whole disk. Then it's bye bye Windows.

If you really can't use a CD, you should probably try one of the "light" distributions like PuppyLinux that support USB installation.

---

### Post by RTrev on 2008-04-11
> **Ventango said:**
> Ok so I have decided to rid my self completly of window's and now i want to know how do i remove the Window's OS Completly and Put Linux There Instead. i dont want to Dual Boot them i want to compleatly ridmyselfof window's. Also Is there a way of Using linux without a Cd.

Hmm, I'm not entirely sure I understand your question.. but I'll try.

First, to get rid of windows is as simple as installing Ubuntu and during the partitioning phase telling it to use the entire disk.  

When you ask if you can use Linux without a CD, do mean you have been booting and running it from a CD and you now wish to run it from the hard drive?  Do you mean can you install it without having a CD on the machine?

Maybe this story will help you.  When my wife got interested in Linux, she installed Ubuntu as a dual boot with XP.  She made a list of everything she needed the machine to do, and she went through that list, in Linux, until she'd found a way to do everything she needed without booting Windows at all.  At that point, she simply did a fresh install of Ubuntu, told it to use the entire disk, and Windows was history.  From then on it was a Linux-only machine, and has been ever since.

HTH,
Bob

---

### Post by Afkpuz on 2008-04-11
To overwrite windows, just download a live CD from ubuntu.com and put that in and reboot.  Boot from the CD and pick the top choice.  Then, once the live environment has booted, select the "Install con on the desktop.  Then, during the parition stage, choose "Use entire disk".  That will install ubuntu over XP and XP will be gone.  Simple as that.  Then, you can reboot and take out the CD and ubuntu will boot on its own.  Enjoy!

---

### Post by aquinashub on 2008-04-11
Check the Ubuntu Community documentation for sure. Ubuntu supports several ways of installation: USB, netboot, CD/DVD, you can do it from Windows if you like, etc... Each different way will have different requirements and a different level of knowledge, but give it a shot!

[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

You'll have to look at your BIOS (at the very first screen while booting, it's usually an F-1 thru F-12 or delete key - but it will tell you at the bottom of the screen) to see what kind of boot options it has, so you can choose the most effective way to install Ubuntu. When you know this, and you've made your decision as to the best (or easiest) way to install, check it out on that site, and if you have any questions about the process before you begin, just post'em up here!

Either way, Windows will no longer exist if you choose to install Ubuntu on the entire hard drive. So no need to wipe it clean first.

Have fun!

---

