---
title: "Mount is denied on second hard drive"
date: 2014-12-22
forum: Hardware
---

### Post by trevis2 on 2014-12-22
Ok.  Long story short.  I have two internal hard drives in PC, totally separate (no raids or weird stuff).  I just put Ubuntu on one, which seemed to break the bootloader so I cannot access Windows on the other.  I am trying to recover some files on the Windows drive before I wipe that drive completely.  When I go to mount the drive, I get the following:

"Mount is denied because the NTFS volume is already exclusively opened.The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command."

I am guessing that something in Windows is still trying to lock down that drive.  I cannot boot into Windows to see what the issue is, nor do I really want to if it can be avoided.  All the files are media files that can be recovered easily (although time-consuming) if necessary.  If there is a fix to this issue, I have yet to find it.  Most of what I see deals with external or USB drives with solutions that don't really seem to apply to my situation.  Please help!  This is the last step to getting my media server up and going!  Thank you.

---

### Post by ajgreeny on 2014-12-22
Windows of some versions does not totally shutdown when you close it down but goes into a hybrid-like suspend state, and if you have then started Ubuntu you may have messed up your Windows installation.

What Windows do you have?
It this a BIOS or UEFI machine, and if UEFI did you use UEFI or the CSM (BIOS compatibility) way to install Ubuntu?

I assume you can boot to Ubuntu and it is just Windows that will not boot: correct?

Go to Boot-Repair in my signature and run that, then show us the pastebin link it provides with a report of your system.

---

### Post by trevis2 on 2014-12-23
Hi, sorry for the slow reply.  I was using Windows 7.  I do have a BIOS machine.  I can get into Ubuntu just fine, just cannot boot to Windows.  Unfortunately, I won't be able to work on this issue until after Christmas.  But, as soon as I can, I will be trying your Boot-Repair.  Thank you for the quick reply!

---

### Post by weatherman2 on 2014-12-23
If your BIOS has the ability to choose a boot device upon startup (typically you can hit F12 as you startup to get a boot menu), then you could use that to choose which drive to boot.  

And then, you could run Windows boot repair on the Windows 7 drive that now won't boot.  (To be safe, I'd also unplug the Ubuntu drive while you do this operation.)  You need a Windows 7 boot disk to do this, but there are legal, free ones online at DigitalRiver.  (And then you can use a flash drive instead of a DVD to create the boot disk if you want.)

It's also possible to boot Ubuntu using the Windows boot manager but it's more tricky - you have to grab a Grub boot sector and save it in a file so Windows will be able to boot it.  But the BIOS boot menu method is less complicated if that's an option.

---

### Post by trevis2 on 2014-12-24
That is the option I would have preferred to avoid.  Interesting thing happened, though.  I swapped the hard drives around (as my second one was operating as a slave), and rebooted back into Ubuntu.  Just out of curiosity, I tried mounting the other drive again, and it worked this time!  I am copying everything now, and will be reformatting once that's complete.  So glad to be rid of Windows.

---

