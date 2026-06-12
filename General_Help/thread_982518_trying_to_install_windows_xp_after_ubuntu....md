---
title: "trying to install windows xp after ubuntu..."
date: 2008-11-14
forum: General Help
---

### Post by EnGorDiaz on 2008-11-14
ok i have fiddle around with the grub it works the windows partition does boot to a certain degree but now it says the BOOTMGR file is missing i need the file so i can complete the installation of windows

any help will be appreciated :)

---

### Post by TeXtonyx on 2008-11-14
[http://lifehacker.com/software/troubleshooting/vista-tip--repair-bootmgr-is-missing-error-251733.php](http://lifehacker.com/software/troubleshooting/vista-tip--repair-bootmgr-is-missing-error-251733.php)

There is a picture and you choose the first option, Startup Repair.
The OEM cd will not work, you need a standard Vista install cd/dvd.

If you don't have the a standard Vista install disk, read this url
"[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Replacing bootmgr might work, but the error message is usually a symptom.
"xcopy /h bootmgr C:" to copy the BOOTMGR file to the C drive, or whichever 
drive you need to copy them too.  
The "/h" switch makes sure that it sees hidden files.

"The partition boot record found the critical system file bootmgr, 
located in the root C:\ directory, but the file is compressed and can't 
be used. Windows cannot begin without loading the uncompressed version 
of this file. The bootmgr file is stored in the C:\ root directory as 
a hidden system file."

Here you would have your Vista install cd inserted and xcopy from it.
The cdrom drive might be D: for instance. If you have a usb stick then
you could xcopy bootmgr from its drive letter F: for instance if you
have previously place bootmgr there first. I presented the Starup Repair
method first because it is much more reliable. bootmgr can be "missing"
because it isn't uncompressed, which is why replacing the file may not
work, it doesn't guarantee that it will be uncompressed, or processed properly.

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

This is properly the best help and includes a manual recovery section.

You should probably look first to see if the file is actually missing,
remember it is hidden. In the past I've received similar error messages
about missing files and the file is actually there. The error messages 
are short not very accurately descriptive. The error message can mean
that the process the bootmgr is supposed to provide is missing not the
actual file.

---

