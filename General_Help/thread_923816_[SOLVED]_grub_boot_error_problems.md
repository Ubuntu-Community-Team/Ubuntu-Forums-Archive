---
title: "[SOLVED] grub boot error problems"
date: 2008-09-18
forum: General Help
---

### Post by phread59 on 2008-09-18
I'm having a boot issue.  I let my machine run through post and it goes to my Grub boot screen.  I select ubuntu and it returns an error 17.  Now if I F-8 and load from the Ubuntu hard drive I get the same screen and it runs through fine and boots normally.  I do have the machine selecting the ubuntu drive as the primary hard drive in the boot priority's.  In bios the order is floppy then hard drive.  I just have the Ubuntu drive set as the first hard drive to boot from.  There are 3 hard drives.  One with Ubuntu on it.  One with Windughs on it.  And 1 with nothing on it yet.  The Ubuntu is on a Sata and the others are IDE.  Any help fixing this would be nice.  Would save a lot of wear on the F-8 key:).

Mark Shuman

---

### Post by oilchangeguy on 2008-09-18
grub is probably on a hard drive that the bios is not set to boot from. if you can change your hard drive boot order that should work. if not, you'll need to install grub on the first hard drive set to boot.

---

### Post by caljohnsmith on 2008-09-18
> **phread59 said:**
> I'm having a boot issue.  I let my machine run through post and it goes to my Grub boot screen.  I select ubuntu and it returns an error 17.  Now if I F-8 and load from the Ubuntu hard drive I get the same screen and it runs through fine and boots normally.  I do have the machine selecting the ubuntu drive as the primary hard drive in the boot priority's.  In bios the order is floppy then hard drive.  I just have the Ubuntu drive set as the first hard drive to boot from.  There are 3 hard drives.  One with Ubuntu on it.  One with Windughs on it.  And 1 with nothing on it yet.  The Ubuntu is on a Sata and the others are IDE.  Any help fixing this would be nice.  Would save a lot of wear on the F-8 key:).

Mark Shuman
The behavior you describe typically happens when you install Grub to the master boot record (MBR) of a HDD other than the HDD where Grub's system files reside (like menu.lst). Right now your menu.lst is set up so you can correctly boot Ubuntu when you boot from the Ubuntu HDD on start up. That would mean the menu.lst entries for Ubuntu would be of the form (hd0,X), or stated another way, Ubuntu is on the boot drive (hd0). But if you boot from your other HDD, which also has Grub in the MBR, it still loads up the same menu.lst, but now Ubuntu is not on the boot drive (hd0) but instead on (hd1) or (hd2); thus Ubuntu doesn't boot.

So, can you simply go into your BIOS and change the boot order so that the Ubuntu HDD is first? Or do you want to boot from your other HDD, and still get Grub's menu like you do now? Because if you want to do that, all you would need to do is change your Ubuntu entries in menu.lst to use the correct drive, either (hd1) or (hd2).

---

### Post by phread59 on 2008-09-20
Maybe I'm not being clear enough.  Lemme see if I can say it better this time:).  I have Grub on only 1 drive (I hope).  I installed Ubuntu 64 bit on the Sata drive and did a standard install.  Grub should be on that drive.  The files should be on that drive.

If I allow the machine to boot unchanged.  I mean with no input at all from me it goes to a Grub screen.  It is the same screen as if I go into the boot order with F-8 and highlighting the Sata drive and selecting it.

However on the untouched boot to Grub it throws the error 17.  If I go into the boot order with F-8 and manually select the Sata drive it works just fine.

Is there any way to search my hard drives and see where grub is?  Can I search to see if Grub is actually on 2 or more drives and this is why I get the error 17.  Maybe there is a Grub file on another of the IDE drives that got there by mistake?

I haven't booted into Woindows in ages.  Windows is on the primary IDE drive.  Maybe Grub got stuck on there by accident.  If there is a way to search for Grub and report on which drives it is found.  That would be a big step forward on solving this problem.

I'm going to log out and try to boot windows and see what I get.

Mark Shuman

---

### Post by phread59 on 2008-09-20
OK John you hit that one outta the park.  I tried to boot the Windows drive and I get Grub instead of the Windows boot loader.  I have Grub on my primary IDE drive as well somehow.

The Question is do I go in and try to edit that Grub list and add the other drives.  Or try to reinstall the Windows boot loader?

If I can how do I work with Grub to add the other Op systems to the one on my Ide drive.  I would love to leave it there and just boot from it without having to resort to the F-8 route.  Any help to configure Grub from within Grub would be a big help.  Thank you for all the help so far.

Mark Shuman

---

### Post by caljohnsmith on 2008-09-20
Try this the next time you boot from your Windows drive (your normal start up): select the Grub menu entry for Ubuntu, press "e" to edit it, select the line that says "root (hd0,X)" where X is some number, press "e" to edit it, change it to "root (hd1,X)", return to save the change, then press "b" to boot it. If that works, great, if not, change the (hd0,X) to (hd2,X), and try and boot again. If I'm understanding your setup correctly, one of those changes should work.

If you are then able to boot into Ubuntu successfully that way, when you get into Ubuntu, open up your Grub's menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And find all the Ubuntu entries, and change all the (hd0,X) references to whatever worked for you. Also, if you are truly booting from the Windows drive, add the following menu entry at the bottom of menu.lst for Windows, and it should work:
```
title Windows
root (hd0,0)
makeactive
chainloader +1
```
If you have any problems, then please post the output of:
```
sudo fdisk -lu
```
Otherwise, let me know how it goes. If it all works, I will be happy to explain it all to you if you like, but until we get it working, then I can't be sure I know your setup correctly. :)

---

### Post by phread59 on 2008-09-24
John, you were absolutely right on the money.  All is well.  I have Grub fully edited and working just fine.  Thank you for your help.  You're instructions were absolutely perfect.

Mark Shuman

---

### Post by caljohnsmith on 2008-09-24
> **phread59 said:**
> John, you were absolutely right on the money.  All is well.  I have Grub fully edited and working just fine.  Thank you for your help.  You're instructions were absolutely perfect.

Mark Shuman
You're welcome, Mark; I'm glad you can boot Ubuntu and Windows OK now. Cheers and have fun. :)

---

