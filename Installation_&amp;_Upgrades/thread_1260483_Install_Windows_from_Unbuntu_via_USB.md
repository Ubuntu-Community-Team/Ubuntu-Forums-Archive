---
title: "Install Windows from Unbuntu via USB"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by jman2232 on 2009-09-07
I have an Acer Aspire One Netbook, came with XP, got a virus and wiped it, installed Ubuntu... Long story, but I need to get XP back or Windows 7 (please don't ask why, just need to do it). I've searched for 2 weeks trying to go from Linux to Windows via a USB stick and the few tutorials I've found do not work.  I've tried Unetbootin as well.  Virtualbox is too slow.

I'd like to Dual boot Windows 7/XP with Ubuntu.  95% of the tutorials out there describe Windows to Linux, I need the opposite using only a USB Stick.

Newish to Linux, would love a simple set of instructions. Thanks

---

### Post by pastalavista on 2009-09-07
Boot Ubuntu from the live USB and go to System > Administration > Partition Editor. Right-click on the Ubuntu partition and select 'resize' and then shrink the partition to leave enough room for Windows. Then format the empty space to NTFS or fat 32. Reboot to the WindowsXP install USB stick and install. Afterwards you'll need to reinstall grub to dual boot. Just run through the Ubuntu installation again in the MANUAL mode and UNCHECK all the 'format' boxes.

---

### Post by presence1960 on 2009-09-07
I just looked at the documentation for Acer Aspire Netbooks. Hopefully you made bootable CDs/DVDs of your recovery partition from an external USB CD/DVD RW drive. If you just wiped the recovery partition then you are not going to be able to restore the factory image unless you made those bootable CDs/DVDs.

Or if you had the foresight to make an image of the Acer Recovery partition to an external media you can restore that image back to the hard disk. If you did neither of these you may be out of luck and will have to contact Acer to purchase recovery media from them.

If your recovery partition is still in tact then read your documentation to see how to restore the factory image.

If you don't have the recovery partition in tact on your hard disk, didn't make an image of or a set of bootable recovery CDs/DVDs this will be a lesson learned: never wipe anything without backing up. You never know when you will need it again.

I really hope you did one of the options that will allow you to restore the factory image.

P.S. my mistake, I didn't see you have a bootable USB XP install stick.

---

### Post by gagagoogoo on 2009-09-07
am in the same boat as the original author. got Ubuntu LiveCD working via USB but would now like to install XP or VISTA via the USB. lot of info about doing that from Windows but need to do this while in Ubuntu.

going along the lines of the Windows users then the steps would be:

> create bootable USB 
> prep the Windows CD/DVD and copy to USB
> boot from USB
> choose TEXT install then, barring any problems, go onto the GUI install phase

tried this in various forms in Windows but didn't work. maybe/probably 'cause my current Windows is screwed (that's actually why i'm here!)

so what i would like to know is how do i do the above in Ubuntu. i think i'm going to try Wine... but hoping there's a more direct method.

---

### Post by jman2232 on 2009-09-08
> **presence1960 said:**
> I just looked at the documentation for Acer Aspire Netbooks. Hopefully you made bootable CDs/DVDs of your recovery partition from an external USB CD/DVD RW drive. If you just wiped the recovery partition then you are not going to be able to restore the factory image unless you made those bootable CDs/DVDs.

Or if you had the foresight to make an image of the Acer Recovery partition to an external media you can restore that image back to the hard disk. If you did neither of these you may be out of luck and will have to contact Acer to purchase recovery media from them.

If your recovery partition is still in tact then read your documentation to see how to restore the factory image.

If you don't have the recovery partition in tact on your hard disk, didn't make an image of or a set of bootable recovery CDs/DVDs this will be a lesson learned: never wipe anything without backing up. You never know when you will need it again.

I really hope you did one of the options that will allow you to restore the factory image.

P.S. my mistake, I didn't see you have a bootable USB XP install stick.

Thanks, that is helpful. 

I really find it hard to believe that you can't wipe a machine, install linux and then from there simply install Windows!?  Is there any other version of Linux I can go to from Ubuntu to Linux Version to Windows?  

This should be easier...

---

### Post by pastalavista on 2009-09-08
> **jman2232 said:**
> Thanks, that is helpful. 

I really find it hard to believe that you can't wipe a machine, install linux and then from there simply install Windows!?  Is there any other version of Linux I can go to from Ubuntu to Linux Version to Windows?  

This should be easier...The Windows installer can't manipulate Linux filesystems the way Linux can with Windows NTFS or Fat32. It needs either blank space or it's own format. If you had thought to leave some blank space when you installed Ubuntu, you could have done it the way you want to. But you'd still have to add Windows to grub.

---

### Post by presence1960 on 2009-09-08
> **jman2232 said:**
> Thanks, that is helpful. 

I really find it hard to believe that you can't wipe a machine, install linux and then from there simply install Windows!?  Is there any other version of Linux I can go to from Ubuntu to Linux Version to Windows?  

This should be easier...

I thought you wiped your machine and didn't have a windows install media. I also thought you want to get rid of Ubuntu and go back to windows. Either way pastalavista is correct. The windows installer needs either free space or a windows filesystem (FAT or NTFS) to install onto. if you have Ubuntu now and want to add windows to dual boot you must use gparted to shrink Ubuntu and create space for Windows. You can then leave it as free space or further use gparted to create an NTFS primary partition for Windows. Then proceed with the windows install.

If you want to get rid of Ubuntu and go only Windows you must use gparted to remove all partitions. You can leave it as free space or create one big NTFS partition. You can then proceed with the install of windows.

---

### Post by jman2232 on 2009-09-08
I understand what you mean about the blank space, can I not install Windows to my USB stick, then once run from the USB wipe the hard drive and install from the USB?

If that's not an option, I'll do the gparted to create some free space, but what is the next step?  I have a Windows ISO, but how do I install it to the free the space from there?  Can/How do I  use a USB stick to do this?

---

### Post by presence1960 on 2009-09-08
> **jman2232 said:**
> I understand what you mean about the blank space, can I not install Windows to my USB stick, then once run from the USB wipe the hard drive and install from the USB?

If that's not an option, I'll do the gparted to create some free space, but what is the next step?  I have a Windows ISO, but how do I install it to the free the space from there?  Can/How do I  use a USB stick to do this?

I am not aware that Microsoft has isos of their windows installation disks except in one case. You aren't using pirated Windows are you?

Don't take this the wrong way, but I refuse to support anything to do with pirated software, even if it pertains to Microsoft whom I can lose no love for.

---

### Post by stlsaint on 2009-09-08
sorry presence but it seems you are correct...quote:"except in one case!" unless im wrong i dont think that windows does give iso's unless you made one from a direct xp cd and in this case (netbook) it is unlikely. To install xp onto a usb with no cd your getting into virtual drive images, bartPE and some formatting like stated earlier. A quick google search will give all your looking for.

---

### Post by alexanderbow on 2009-09-22
> **stlsaint said:**
> sorry presence but it seems you are correct...quote:"except in one case!" To install xp onto a usb with no cd your getting into virtual drive images, bartPE and some formatting like stated earlier. A quick google search will give all your looking for.
I would also have to agree with the both of you, but it seems the "quick google search" is the stuff of fantasy. So, if you were to be stuck with only Ubuntu, and this "one case" was the ISO you were legally trying to boot, 
(< [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) > to be exact)
and for some reason your cd drive was acting like a loser, would you think it to be possible to use any sort of Ubuntu program to make a boot-able USB with this ISO on it?

---

### Post by presence1960 on 2009-09-22
> **alexanderbow said:**
> I would also have to agree with the both of you, but it seems the "quick google search" is the stuff of fantasy. So, if you were to be stuck with only Ubuntu, and this "one case" was the ISO you were legally trying to boot, 
(< [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) > to be exact)
and for some reason your cd drive was acting like a loser, would you think it to be possible to use any sort of Ubuntu program to make a boot-able USB with this ISO on it?

That is not a windows install image that you linked. It is an iso for Windows Vista recovery console, for those who have a recovery partition and don't have access to Vista's recovery console. You can not install Vista with that.

Except in one case Microsoft does not sell Windows in the form of an iso. Of course I will not say what that one case is, because those who use pirated windows will be on here saying they purchased it that way. I refuse to support or help anyone I am aware of using pirated software.

---

### Post by Kougaiji on 2009-09-22
> **presence1960 said:**
> That is not a windows install image that you linked. It is an iso for Windows Vista recovery console, for those who have a recovery partition and don't have access to Vista's recovery console. You can not install Vista with that.

Except in one case Microsoft does not sell Windows in the form of an iso. Of course I will not say what that one case is, because those who use pirated windows will be on here saying they purchased it that way. I refuse to support or help anyone I am aware of using pirated software.

Well then help ME out! I have attempted to use various .iso and to copy their contents to a USB stick via ubuntu, and it has failed because the usb stick is "not a bootable drive" according to windows. I legitimately have disk images from MSDNAA (university EE and compsci program) and the most recent install of ubuntu somehow broke the Windows [7] boot manager.

In other words, grub works, gets to the windows bootloader, I select windows 7 (the bootloader is identical to vista) and it will not boot and suggests to a recovery disk.

Unfortunately for me I wiped the recovery partition without realizing it on my Acer laptop, and they do not supply any external recovery media.

Now, will you stop being anal and accusative and actually help someone out?!


MY GOAL: Make a working Windows Vista/7 Recovery USB stick via Ubuntu. I just need to run software on my win partition that not only doesn't work in linux, but there is not even a linux alternative attempted (Serato Scratch).


PS: Yay for searching for a solution for 4 hours only to find someone keeping secrets because they don't believe in using backups or copied recovery disks or generic windows installation isos with genuine software keys!!</sarcasm>

---

### Post by the_orator on 2009-11-03
Sorry if the reply is a bit late, but I found this link, which may be helpful:
[http://serverfault.com/questions/6714/how-to-make-a-windows-7-usb-flash-install-media-from-linux](http://serverfault.com/questions/6714/how-to-make-a-windows-7-usb-flash-install-media-from-linux)

And presence, legitimately installing Windows from ISO isn't very uncommon. A lot of people have accounts on MSDN, or can probably use the MSDN partnership with their company/university.

---

