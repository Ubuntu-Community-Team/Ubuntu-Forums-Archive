---
title: "Installing Ubuntu Studio 12.04 on Lenovo Edge E540"
date: 2014-09-03
forum: Hardware
---

### Post by newholm1 on 2014-09-03
[COLOR=#333333][FONT=Arial]Hi there. I have just purchased a Lenovo Edge E540 and I am attempting to install Ubuntu Studio 12.04 on it. However I am having some teething troubles. If I try and do it within Windows, although it says it has been successful, I am not offered an Ubuntu option at boot, and there is no evidence of its existence on my hard drive (ie no new partition for it). When I try and install it at boot, it does not succeed as there is not a sufficiently large partition, and it does not seem to want to resize any of the existing partitions. What I would ideally like would be Ubuntu and Windows dual boot, with the hard drive evenly split between ext4 and NTFS file systems respectively. Can anyone talk me through the process?[/FONT][/COLOR]

---

### Post by yancek on 2014-09-03
Which version of windows are you using?  If you have windows 8, wubi is not expected to work with it.  If an earlier version of windows, it might.  Wubi is no longer supported by Ubuntu/Canonical.  This would be the option to install within windows and there would be no partition for it.  You should be able to remove it from Program Files under windows. 

You would need to resize/shrink one of your windows partitions to create space for Ubuntu.  Boot the Ubuntu installation medium and select the "Try Ubuntu" option which will take you to a Desktop.  Open a terminal by holding down the Ctrl+Allt+t keys simultaneously and type:  sudo fdisk -l(Lower Case Letter L in the command) and post the output here.  Also post the output of:  df -h

This should provide enough information so someone can help.

---

### Post by Vladlenin5000 on 2014-09-03
Complementing the above and before you try anything else, please use Windows tools (in your normal Windows session) to shrink any Windows partitions and rebbot more than once in order to give Windows the opportunity to do its *chkdsk* thing and get confortable with the new partitions size(s). Then - and only then - is safe to to proceed to the dual boot installation of Ubuntu. This is valid for any atandard Windows installation up to Windows 7. You need a few more steps for newer UEFI based systems with Windows 8.x preinstalled.

Please post the results of the commands mentioned about so we know what we're dealing with.

---

### Post by newholm1 on 2014-09-03
It's Windows 8.1 I'm using. I should say that I did attempt the "Try Ubuntu" option, but instead of taking me to a desktop it took me to a command line. In this case I guess it will still be okay, but I thought it was worth mentioning. I shall be sure to try these suggestions when I am with my laptop in a couple of hours. Mine is a [COLOR=#000000]UEFI based system - I already managed to alter the security settings to allow booting other operating systems - is this the only extra step?[/COLOR]

---

### Post by yancek on 2014-09-03
I don't use windows 8 or uefi but from what I have read here and at other sites, you should fully shutdown windows 8 rather than hibernate.

---

### Post by newholm1 on 2014-09-03
Okay ... so I managed to resize the partition with the windows partition manager, and successfully installed Ubuntu. However, when I switch on the laptop I am not offered any opportunity to run Ubuntu; it just goes directly to Windows. However, when I look at the partition manager, it shows the change that has occurred due to installing Ubuntu, although it does list the disk as RAW rather than ext4. When creating the new partition, it did not give me an ext4 option, so I chose not to format it, assuming that the Ubuntu installer would do that itself. Could this be the problem?

---

### Post by yancek on 2014-09-03
Are you looking at the disk from windows?  Windows default isn't capable of reading a Linux filesystem and won't be able to indicate if it is ext4 or some other filesystem.
If you used the manual (Something Else) option when installing Ubuntu, you would have needed to select a previously created partition or free/unallocated space and then click the Change tab and you should have seen a new window which gave you an option to format, set the size and Mount point.  If you didn't format you don't have a filesystem and I would not expect much.  Probably need to reinstall unless someone comes up with an alternative.

---

### Post by newholm1 on 2014-09-04
Sounds like a good plan - I'll try that later. I was surprised not to get a format option on install, but I assumed it would do it automatically. Apparently not! Can't post the command line stuff - when I run the live disc, I get ONLY a command line, not a desktop, and although I get an output from those commands, I have no way of quickly copying it to here. If all else fails, I'll post it then.

---

### Post by yancek on 2014-09-04
I always use the manual option, with the current Ubuntu that would be something else.  If you select an Alongside option it will probably format and usually does it right without user input.  If you use the LVM option, I understand it will overwrite everything.  If you select the Something Else option, you need to select format.

---

### Post by newholm1 on 2014-09-04
I have now tried with the manual option (Something Else), selecting ext4 as the filesystem and / as the mount point. However it did exactly the same thing as installing from within windows, installing successfully but offering no boot option. Incidentally, the previous install from within Windows did show up as an ext4. Am I getting the Mount Point wrong?

---

### Post by newholm1 on 2014-09-08
Solved! It turned out not to be an installation issue, but a boot issue. Once I'd sorted the partitions, it installed successfully, but I had to edit the BIOS to prioritise Legacy boot over UEFI. Then it worked fine, apart from the Wireless .... but that's another story.

---

