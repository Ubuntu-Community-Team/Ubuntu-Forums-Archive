---
title: "Dual Boot Linux+Windows"
date: 2015-03-22
forum: Hardware
---

### Post by mayagrafix on 2015-03-22
How can I temporarily bypass GRUB2? Ubuntu on sda and Windows on sdb. Want to disable GRUB2 temporarily so I can boot directly to Windows HDD during a Win10 upgrade, and enable GRUB2 to work as before when upgrade finished. If I physically disable the sda (by disconnecting the HDD), I get an GRUB error message and PC will not boot from sdb as primary HDD.

---

### Post by yancek on 2015-03-22
That would be explained if you have previously installed Grub to the mbr of both drives pointing to the Ubuntu Grub files on sda.  Not sure why you would have done that or if that is the case but that would explain the behavior.  If you are using windows 8 now then your probably have UEFI/GPT and the above would not apply.  If that is the case, where is the EFI partition?  Use boot repair and just select the option to Create Boot Info Summary and post that output here.  Someone familiar with UEFI/GPT should then be able to advise you.  The link to boot repair below:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ajgreeny on 2015-03-22
If for some reason you have had to use Boot-Repair before, and you chose to accept the default repair, that can sometimes put grub on all hard drives, I believe, as a failsafe to make sure that the system will boot whichever disk is the first boot priority device, but it can be a pain in the a..e if you wanted to keep the Windows MBR on the Windows disk and put grub on the Ubuntu disk.

This could explain why grub is on both disks, but I would like to know if you can still boot from sdb when that is first boot device when sda is disconnected..If so then you must have grub on both disk's MBRs.

---

### Post by mayagrafix on 2015-03-22
> **ajgreeny said:**
> This could explain why grub is on both disks, but **I would like to know if you can still boot from sdb when that is first boot device when sda is disconnected**..If so then you must have grub on both disk's MBRs.

with sba disconnected, PC will not boot, GRUB error message appears on screen.

---

### Post by mayagrafix on 2015-03-22
> **yancek said:**
> That would be explained if you have previously installed Grub to the mbr of both drives pointing to the Ubuntu Grub files on sda.]

Yes, boot-repair was used the last time I re-installed Windows 7 on sdb. No UEFI/GPT on this PC.

---

### Post by yancek on 2015-03-22
Since you have Grub installed to the MBR of both drives, you would need to use your windows installation medium to reinstall its bootloader to the mbr of the drive on which you have installed windows.  Probably the repair option would work.  If you don't have the installation medium, you might be able to download a repair disk somewhere but I don't use windows so don't have any idea where you would get that.  

If you can boot windows, why can't you run the upgrade from windows after you boot it?

---

### Post by mayagrafix on 2015-03-23
> **yancek said:**
> If you can boot windows, why can't you run the upgrade from windows after you boot it?

Windows installer gets confused when other than C:\ is the operating path. It is funny that way. Initially I downloaded and ran the Windows 10 Technical Preview upgrade but when reboot is required to complete install, it has to be just like MS decided it was supposed to be back in Redmond. After rebooting twice and nothing happening, I tried to make a one HDD PC so Windows installer will not get confused but GRUB2 will not allow me to boot from sdb.

Here is the BootRepair report you requested: [http://paste.ubuntu.com/10658026/](http://paste.ubuntu.com/10658026/)

OK, so the plan is to use Win7 install DVD to "repair" boot sector of sdb then after Win10 is successfully installed I will use BootRepair CD to make GRUB2 work again with sda + sdb.

Thanks for all the good help. You guys ROCK :)

---

### Post by yancek on 2015-03-23
Since windows 10 is just beta and available for testing, one option would be to install it in VirtualBox.  If you don't want to do that, I would dis-connect the Ubuntu drive and boot with the windows Installation medium to repair the bootloader on the windows drive, boot windows and then try the windows 10 upgrade.

I notice that on sda (the Ubuntu drive) you have a partition with windows boot files:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 

On the windows drive you have two different partitions with boot files, sdb2:  /bootmgr /Boot/BCD

and on sdb3:  /Windows/System32/winload.exe

Son on the windows drive, sdb, you have two separate partitions which contain the same boot files that you have on one partition,  sda1 which seems odd to me.

---

### Post by mayagrafix on 2015-03-23
> **yancek said:**
> Son on the windows drive, sdb, you have two separate partitions which contain the same boot files that you have on one partition,  sda1 which seems odd to me.

Yeah, previous installs of XP, Vista, etc. Past Windows have a tendency to corrupt and require complete re installation (version 7 however, is very stable). I let BootRepair take care of MBR for me.

Windows 10 as so far as I know, is only available via update program, no stand alone ISO version available to download for Vbox.

FYI: if you have Windows 7 installed, it is easy to create a System Recovery Disc.  

Click Start menu > All Programs > Maintenance > **Create a System Repair Disc** and Insert a blank CD or DVD.

Thanxs!

---

### Post by oldfred on 2015-03-23
Where grub normally installs boot loader to drive seen by BIOS as sda, Windows installs its boot partition to the drive set in BIOS as boot drive. 
So make sure you have changed BIOS to boot from sdb before installing Windows or it will put its boot files on sda. In some cases it has forced install of its 100MB partition on another drive corrupting the partition table and causing major issues.

---

### Post by yancek on 2015-03-23
> Windows 10 as so far as I know, is only available via update program, no stand alone ISO version available to download for Vbox.

No true.  Downloaded it and installed it in VirtualBox several months ago just to see what it was like.  Link below to microsoft site:

[http://windows.microsoft.com/en-us/windows/preview-iso](http://windows.microsoft.com/en-us/windows/preview-iso)

I created the Recovery CD when I first got the computer with windows 7 on it, if I remember correctly I was prompted to do so on the first boot.  Knowing windows, I figured it would be a good idea.

You can also put the extracted windows 10 iso on a flash drive and boot it from Grub, another option.

---

### Post by mayagrafix on 2015-03-23
Thanks for news. In hindsight, this would have been a better option:-( However, I got the thing installed and working and GRUB2 back to the way it was before. WinX TP9926 has a long way to go. Right out of the box, it has a weak network connection to the internet, and I get a lot of 0x80240438 errors. Rebooting to Ubuntu I get the normal connect without any problems. 
> I created the Recovery CD when I first got the computer with windows 7 on it, if I remember correctly I was prompted to do so on the first boot. Knowing windows, I figured it would be a good idea.
You're instincts were right.

Thanks for your help.

---

