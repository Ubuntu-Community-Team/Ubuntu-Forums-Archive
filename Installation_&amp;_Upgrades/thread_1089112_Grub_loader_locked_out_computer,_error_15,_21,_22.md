---
title: "Grub loader locked out computer, error 15, 21, 22"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by Bonecutter on 2009-03-06
I had Windows on my main drive, installed Ubuntu on my backup drive, installed the GRUB loader, reformatted backup drive, tried to get rid of GRUB loader by resetting to a system restore point on windows xp home edition, and now the GRUB loader is locking me out of everything with Error 21, Error 22, or Error 15. Ive tried reinstalling Ubuntu, but it still doesnt let me through the grub loader. What should I do to get back into windows or into Linux? Either one can help me resolve the issue, but I would rather use windows at this time.

---

### Post by martrn on 2009-03-07
See the following : [http://www.blogmanno.com/?q=node/9]("http://www.blogmanno.com/?q=node/9") for deatails with how to fix the MBR (Master Boot Record) with windoze system on it.

See [http://supergrub.forjamari.linex.org/?section=download]("http://supergrub.forjamari.linex.org/?section=download") for the supergrub disc pages or follow that through to boot one of your operating systems and get hold of a supergrub disc.  You should be able to get back into ubuntu or any os from the supergrub disc.

---

### Post by sotvomike on 2009-03-07
I'm having the same problem.  Error 22.  I'm using SuperGrub on usb to try to repair.  Here's the setup:

HDD 1: Windows Vista installed with a partition for "Recovery"
HDD 2: Storage drive, no partition
HDD 3: Spare drive, had Ubuntu loaded to run.  Crashed and removed.
HDD 3 (new):  Just installed, not even had the chance to use since system crash
HDD 4: External drive, had loaded Ubuntu for the time being.  

So, the GRUB was set to dual boot either Ubuntu or Vista.  After external drive (HDD 4) got disconected because of connecting new HDD 3, GRUB freaked out and gave Error 22.  Am using SuperGrub USB to boot.  Have chosen to fix MSB, fix GRUB, SWAP, start linux, all of them.  If I load easy boot, I can see the options to boot to Ubuntu or recovery and Vista.  When I click Ubuntu, it says "file not found".  When I try to boot to Vista, also says "file not found".  This is getting really frustration.  Can anyone suggest something?  I can't even get into my computer to make any changes in terminal.

---

### Post by tommcd on 2009-03-07
Super Grub Disc should be able to reinstall grub for you. You can also reinstall grub from the Ubuntu live CD. Boot the CD, open a terminal and run:
```
sudo grub
```
Follow this tutorial to use grub to find your Ubuntu root partition.
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer)
To reinstall grub, boot the live CD and run this:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

