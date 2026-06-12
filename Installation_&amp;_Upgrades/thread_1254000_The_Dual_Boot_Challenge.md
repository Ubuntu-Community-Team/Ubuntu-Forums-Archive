---
title: "The Dual Boot Challenge"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by SnarlSlayer on 2009-08-30
I read two pages of different posts on dual booting, however none of them really answered my question. If I missed something please point me to the link.

What I want to do is install Ubuntu on one internal HD and Windows 7 on a second internal HD.

BUT-- I do not want ANY bootloader to give me a choice. When I want to boot a different OS, I want to do it by adjusting the Boot Order in the BIOS.

So the goal is to have the machine boot right into Ubunut with no hesitation-- the same as if were the only OS on the computer.

When I have to use Windows (ugh), I want to do it by telling the BIOS to boot that disk first.

Is this even possible? If so, how?

SS

---

### Post by running_rabbit07 on 2009-08-30
The only option that comes to mind is loading the grub boot loading and then setting it to boot Ubuntu in the startupmanager. 

Then when you want to boot MS you just hit escape at startup and select Windows 7 from the bootloader menu.

---

### Post by ad_267 on 2009-08-30
It might be possible. When you install Ubuntu there's an "advanced" option near the end that allows you to select where to install the boot loader (GRUB). So you could install it to the second hard drive instead of the master boot record of the other drive. 

I'm just not sure that your BIOS will let you boot from two different drives though, someone else will need to clear that up. I was under the impression that you have only one primary drive that contains the master boot record.

Is there a reason why you want this though? You can just set the boot loader to boot directly into Ubuntu instead with only a 1 second delay (a 0 second delay isn't recommended) so you have to press Esc to bring up the boot menu.

---

### Post by ronparent on 2009-08-30
It is possible and easy if you know how to chage boot order in bios. The main thing you want to remember is you should set the ubuntu drive 1st in boot order when you install ubuntu. That way only the MBR of that one drive will find the boot loader. The MBR of the windows drive will be left alone so that when that drive is set as 1st in bios win 7 will boot automatically.

A bonus is that if installed second the grub bootloader installed with ubuntu will probably automatically include win7 as a boot choice. Who knows, you may find that more convenient than switching boot order.

To recap - you would install win 7 first on its own disk set first in boot order. You would then switch boot order to the second disk and install ubuntu on that disk. You can also edit /etc/fstab to mount automount any partition you would assecibly to both systems. Any partition you want commont to both would have to be formatted fat32 of ntfs. Have fun.

---

### Post by presence1960 on 2009-08-30
> **ronparent said:**
> It is possible and easy if you know how to chage boot order in bios. The main thing you want to remember is you should set the ubuntu drive 1st in boot order when you install ubuntu. That way only the MBR of that one drive will find the boot loader. The MBR of the windows drive will be left alone so that when that drive is set as 1st in bios win 7 will boot automatically.

A bonus is that if installed second the grub bootloader installed with ubuntu will probably automatically include win7 as a boot choice. Who knows, you may find that more convenient than switching boot order.

To recap - you would install win 7 first on its own disk set first in boot order. You would then switch boot order to the second disk and install ubuntu on that disk. You can also edit /etc/fstab to mount automount any partition you would assecibly to both systems. Any partition you want commont to both would have to be formatted fat32 of ntfs. Have fun.

+1

It can't get any simpler than that. I think you will like the GRUB bootloader with the option of booting into ubuntu or windows. I know you said you don't want that, but the prospect of changing my disk boot order in BIOS to choose OSs is not something I would like to have to do. But it is your machine and can do as you see fit. Good Luck, it not only is doable but is easy to set up.

---

### Post by SnarlSlayer on 2009-08-31
Thanks, folks-- I already knew most of the options listed. I wanted to see if I could do it another way.

In the end, I just blew the Windows Installation away and I'm going to use that disk for storage...

SS

---

### Post by cascade9 on 2009-08-31
> **ad_267 said:**
> I'm just not sure that your BIOS will let you boot from two different drives though, someone else will need to clear that up. I was under the impression that you have only one primary drive that contains the master boot record.

Yes, booting from 2 different drives is totally possible. I was doing just that for a while. 

Even in the 'old' days, you could normally set up 1 drive as C: and another as D: (there was some way to do this with linux, 'd:' was just the bios setting). Then change boot sequence- you normally had options like "a, c, CDrom", "CDrom, C, SCSI". One of them is normally "C, D, SCSI" or something like that depending on your BIOS. With newer PCs you can normally set any attached drive to boot 1st, and then load whatever OS you have ion that drive.

---

### Post by Bartender on 2009-08-31
Most BIOS'es allow you to tap on a key during startup that takes you to a page asking which device you want to boot.  That's quicker than going into BIOS and changing the boot priority.

---

### Post by Swagman on 2009-09-01
I would just simply pull the power on the drives that you are **NOT** installing on.

Do this in turn until all installations have completed .. then plug all the drives back in.

**NOW** your'll HAVE to use BIOS to select boot drive.

btw... don't forget to turn the machine OFF at the mains before fiddling around inside. ( If you power down via O/s then the board stays live. This wont hurt you but may well bugger something else)

---

### Post by presence1960 on 2009-09-01
> **ad_267 said:**
> 
I'm just not sure that your BIOS will let you boot from two different drives though, someone else will need to clear that up. I was under the impression that you have only one primary drive that contains the master boot record.



Each hard disk has an MBR. If you change the disk that boots first in BIOS as long as the new disk has a bootloader on MBR the computer will boot into that OS. If it has no bootloader you will get an error message since whatever disk boots first must have a bootloader on it's MBR. 

Example: sda has Ubuntu installed and GRUB is in MBR and sdb has windows installed and windows is on the MBR of that disk. Whichever disk boots first will use whatever is on that MBR. If sda boots first GRUB will take over, if sdb boots first the machine will boot directly into windows.

---

### Post by ad_267 on 2009-09-02
Ok thanks I wasn't sure about that. I just thought I recalled that when I changed my boot order in my BIOS I could only see one of my drives, but I must have been mistaken. :)

---

