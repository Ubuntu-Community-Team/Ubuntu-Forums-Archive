---
title: "Can't go back to XP after 8.10?"
date: 2008-11-18
forum: General Help
---

### Post by generalpurpose on 2008-11-18
I didn't know where else to post this and I Googled and searched and I can't seem to find it. The XP disk is fine and did a media check and works on other machines. When I try to boot it up:
Press any key to boot from CD...
Detecting Hardware...
Then a black screen, the hard drive light stays on and the CD spins down.
I walked away for 5 minutes and still the same thing. I tried rebooting it several times and still the same thing. I tried the disk in 3 other computers and it boots just fine on those.

I have an NTFS partition that GRUB sees as "Windows XP" and it is obviously not. It has a lot of information on it, which I am backing up now. Any thoughts on how to fix this would be hugely appreciated!

---

### Post by quazi on 2008-11-18
In your bios, double-check that your PC is set to try to boot from the CD-ROM first (although it sounds like it is).  Ubuntu shouldn't impact your ability to boot from your CD-ROM at all (as far as I know) because GRUB doesn't start until you boot from a harddrive.

---

### Post by generalpurpose on 2008-11-18
It does boot from the cd then goes black... I can boot up to Ubuntu just fine but for some odd reason it doesnt like XP Maybe I will try a Vista disk and swap oever to XP...

---

### Post by TeXtonyx on 2008-11-18
You say you tested the cd on other computers. Did they have mixed
OS? I would make space for the XP installation first by deleting a 
partition and installing (or trying) XP into the unallocated space.

The computers you tested on, did they have grub written to the MBR?
It seems like it has to do with the content of the drive. I've had
this problem and deleted the whole drive, installed XP first, and
then Ubuntu. But, I've seen guides or Howtos which tell how to
install Ubuntu first and XP second (google). They were written for
8.04 or before so 8.10 is an unknown factor-> not a likely cause.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
A Howto using Ubuntu with pictures and links to various variations.
Page 3 describes how to shrink the Ubuntu partition in order to 
make free space so that XP can be installed into it. 
Deleting an existing partition in order to install XP into the 
unallocated space is the same idea.

---

### Post by generalpurpose on 2008-11-18
Thank you TeXtonyx it worked after I backed up all my junk on the NTFS partition. Now I have XP back it looked as if Grub broke the boot tables of NTFS and the XP disk could not locate the 0 block due to Microsoft being ignorant of other operating systems.

---

### Post by TeXtonyx on 2008-11-18
> **generalpurpose said:**
> Thank you TeXtonyx it worked after I backed up all my junk on the NTFS partition. Now I have XP back it looked as if Grub broke the boot tables of NTFS and the XP disk could not locate the 0 block due to Microsoft being ignorant of other operating systems.

Well, sometimes it happens that grub damages part of Windows boot
sector code. There is a tool called TestDisk that fixes this error
sometimes. Here is some information on how to run it.
[http://georgia.ubuntuforums.org/showpost.php?p=6107798&postcount=3](http://georgia.ubuntuforums.org/showpost.php?p=6107798&postcount=3)

Actually proceeding through the initial steps you want to see if
Rebuild boot sector will fix your problem. There is a backup of
the boot sector and if it is not "identical" with the current
boot sector, you can rebuild the boot sector from the backup.

Some pictures with this very clear explanation, a very handy tool
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

If this problem didn't develop after you reinstalled grub to get
dual booting, then I'm not sure what you mean.

I use a different method to dual boot XP and Ubuntu. Bootpart
is free and makes a 512 byte .bin segment, puts it in the C:\ 
root and writes to boot.ini, making another boot menu option. 
If you resize a partition then you have to run bootpart again.
You will need to fixmbr and fixboot if Testdisk doesn't work,
from the XP install cd. Grub is installed to the /boot partition 
not the MBR so Ubuntu and XP boot can be booted independently.
[http://forums.majorgeeks.com/showthread.php?t=108021](http://forums.majorgeeks.com/showthread.php?t=108021)

If you are partial to grub, after XP Recovery Console -> fixmbr
and fixboot, you can reinstall grub again, it might work out OK.
One reason I like Bootpart is less typing, it takes about 12 sec
after the program (1mb) is first downloaded and unzipped. I think 
this problem you now have is likely very fixable.

---

