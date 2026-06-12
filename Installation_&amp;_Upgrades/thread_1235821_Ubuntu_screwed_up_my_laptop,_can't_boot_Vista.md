---
title: "Ubuntu screwed up my laptop, can't boot Vista"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by pipesville on 2009-08-09
I used my laptop to install Ubuntu onto a flash drive.  After I removed the flash the laptop will no longer boot up to Vista.  I get the error "GRUB loading, please wait.... Error 21".  I tried to go into system restore while the laptop is booting but still got the same message.  My laptop didn't come with any system disks (I wish they wouldn't do that) so I can't restore from them.  I read in another forum that the boot program probably got installed onto the hard drive and not the flash.  I never saw that option in the install process, did I miss it?  I can boot into Vista if the flash is installed but I don't want to have to keep the flash plugged in all the time.

MAIN QUESTION:  How do I get this boot program off my laptop so it will boot normally (the way it used to)?

---

### Post by adempewolff on 2009-08-09
well you have two options.  find a vista disk and use its startup repair option.  or configure grub to load vista.  to do that however you would need to move your GRUB stage 2 files somewhere where GRUB could find them (I suspect they are on the flash drive right now).  I don't know if GRUB will read stage 2 files from NTFS, also I think it needs a linux kernel image to run.  So you would need to create a partition on your main hardrive with the stage 2 files and a kernel image.

You would be much better off using Vista's startup repair if you are not planning on dual/multibooting.  I don't think you need a product key to do startup repair so maybe you could borrow a friend's Vista DVD or something.

good luck.

---

### Post by ibutho on 2009-08-09
Hi. It does indeed seem like the GRUB bootloader was installed on your hard rive. There is an option to install it elsewhere, but you need to click the Advanced tab in order for this to show up during install time. You could use a small live disc like [Super Grub Disk]("http://www.supergrubdisk.org") to restore the Windows bootloader. Another option would be to use a [FreeDOS]("http://www.freedos.org") disc and enter something like "fdisk /mbr" to rewrite the MBR. There are other options available such as Various Windows discs and from within Linux itself. Take a look at this [link]("http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/") for more info.

---

### Post by chaosx9 on 2009-08-09
I actually had this exact same problem when i first uninstalled kubuntu from my laptop.

Basically, the problem is that ubuntu, by default, always installs GRUB (it's bootloader) into the MBR, or something like that, so it always comes up first. Basically, as it works with ubuntu, when you uninstall/format it's partition, some support files are deleted and you get the error.

Mainly, if you have a vista installatio cd, then use that, and boot into the cd. After that, choose language settings, then click "Repair your computer", click your installation of vista, then click "next", then open a command prompt then type and execute this:

Bootrec.exe /FixMbr

This restores Vista's original bootloader.

Now, you might get a problem where the repair mode won't work with ur installation cd for whatever reason, in which case you'll need to install ubuntu again, just to do a few things:

1) get an iso of the Windows Vista Recovery CD, these are avaliable from torrents, so using ubuntu, transmission will handle them - there are two separate torrents

For 64-bit Vista installations:
[http://neosmart.net:6969/torrent.html?info_hash=fbf47dd7d63708ea2e7acac1709747c5f7eb94b5](http://neosmart.net:6969/torrent.html?info_hash=fbf47dd7d63708ea2e7acac1709747c5f7eb94b5)

For 32-bit Vista installations:
[http://neosmart.net:6969/torrent.html?info_hash=c7411cffb5b0c27b28d0ec080af55ea0016f7b7b](http://neosmart.net:6969/torrent.html?info_hash=c7411cffb5b0c27b28d0ec080af55ea0016f7b7b)

2) burn that onto a blank CD (not dvd, unless ur willing to lose about 4.6GB of space for aroundabout 100MB of data)

3) use that to boot into the repair mode, and use the command prompt to use the same code: Bootrec.exe /FixMbr

Either way, once you do the FixMBR command, then it'll fix it. Therefore, in theory, you could install ubuntu to allow yourself to acces vista, run an elevated command prompt inside vista, then use the same command (Bootrec.exe /FixMbr)

This will defo help you fixing it. To prevent this problem again, you might want to look at this page:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

It explains installing linux distributions so that you can install grub onto the linux partition, then use easybcd to enter grub. Counts as a safeguard to this problem. It defo works, because i use it myself.

---

### Post by stlsaint on 2009-08-09
Type "DaRT for vista" into google!!

---

### Post by pipesville on 2009-08-09
Thanks chaosx9!  The Vista Recovery CD did it.  I'll be more careful next time.

---

