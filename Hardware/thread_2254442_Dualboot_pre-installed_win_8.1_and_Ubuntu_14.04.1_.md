---
title: "Dualboot pre-installed win 8.1 and Ubuntu 14.04.1 on Fujitsu Lifebook A512"
date: 2014-11-27
forum: Hardware
---

### Post by cderson on 2014-11-27
Hi,

It's taken me a few attepts to get this working, so I thought I'd share my success with the rest of the community.  I don't want to re-write the very excellect guides that exist, so I'll just run through the major steps that worked (or did not work) for me.

I would advise opening the [Everyday Linux user "install-ubuntu-1404-alongside-windows"]("http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html") guide.  It's not really any better or worse than the others, but it does have the one crucial command I needed to get things working.  Please note - I didn't follow all of this (or any other) guide.

[B]What worked:
[/B]
[LIST]
[*]Disable 'Fast boot' in BIOS and Windows 
[*]Disable 'Secure boot' in BIOS - For the Lifebook series you have to set an admin password and reboot before you can change these options. 
[*]Resize partitions in Windows, not Linux 
[*]Use the 'Do something else' partitioning option, and manually create root and swap partitions.  I set swap to be about the same size as the installed memory. 
[*]Important: From Windows, run: 
[/LIST]
bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi
[FONT=arial]From a windows admin command prompt.  Very clear instructions on doing this are in step 8 of the Everyday Linux User guide.
[/FONT][FONT=arial]
That's it!  I now have a working dual boot Linux/Windows laptop.   If I do this again, I may try re-sizing the partition from the Ubuntu Live desktop, as I think this gives better (but
riskier) control over partition sizes - Windows would not let me shrink the existing volume quite as much as I would have liked.

**What didn't work:**
[/FONT]* Running boot-repair.  Didn't really cause any problems, but it didn't help either
* Manually fiddling with the EFI volume - Windows just undid everything, use the command above instead
* Running fsck the try and 'fix' problems boot-repair seemed to be reporting - don't do this.
* Removing Windows entirely - not what I wanted to do, but it looks like the Lifebook 'A' series requires a Windows EFI boot loader to boot ata all.

**What was just plain odd:**
* Part way through this process, just about all boot options vanished from the boot menu and BIOS boot order screen.
 The laptop was repaired quickly by the Fujitsu service team, and the report suggested a broken MB - but it may have been my
 ill-advised 'fix NTFS' attempt.
* Part way through my second attempt, boot from USB dropped off the list.  In the end I bought a DVD-R and booted from that.
* A re-install of Windows 8.1 from the supplied 'rescue' disk (Yay! An actual disk, not a wierd, hidden, easy-to-accidentally-delete
 recovery partition) means that Windows now drops straight to the 'Desktop', not the it's-not-metro 'Start' screen menu thing.


So, I hope this helps somebody.  Sorry about the odd formatting - in browser editors hate me ;-)

---

