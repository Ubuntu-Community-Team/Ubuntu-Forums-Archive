---
title: "BIOS Upgrade on Tyan Thunder n3600B (S2927-E) NEED HELP"
date: 2009-01-15
forum: Hardware
---

### Post by Sean4000 on 2009-01-15
Hello everyone,

I have a Tyan Thunder n3600B (S2927-E) server board in my workstation and I want to upgrade the BIOS to version 2.03 from xubuntu Linux 8.10 x64. Any thought on how to go about doing this? Tyan's site is of little help when it comes to documenting this, even under the "How to" section.

[http://www.tyan.com/support_download_bios.aspx?model=S.S2927-E](http://www.tyan.com/support_download_bios.aspx?model=S.S2927-E)

---

### Post by electrogeist on 2009-01-15
While it may be technically possible to flash it within linux, IMHO it is probably best to just use the AFUDOS.EXE utility they provide for MS-DOS.  If something goes wrong with the flash process you can find yourself up a creek without a paddle, until you buy/install a new BIOS chip.  

Create a bootable, minimal DOS/Win98 disk on CD or USB flash drive.  Minimal is the key, you don't want any memory managers. Google will point you towards lots of help doing this, and you can try [http://www.bootdisk.com/](http://www.bootdisk.com/) just avoid their self-extracting EXE images meant for windows.

---

### Post by Sean4000 on 2009-01-18
I'm not going to risk it. I have purchased and new BIOS chip from BIOSMAN, Inc!

---

### Post by electrogeist on 2009-01-18
Um that should work too I guess... but that is normally what one would do in the worst case scenario when a flash goes bad.

---

### Post by librarian on 2009-01-18
I'm in the same boat as Sean4000 - confused by Tyan's instructions, mainly not being able to determine which flash utility to use since s2927-e doesn't show up at [http://www.tyan.com/tech/flash_utilities.aspx](http://www.tyan.com/tech/flash_utilities.aspx) . I wrote TYAN support a few days ago and they said:

[INDENT]The BIOS package includes the appropriate flashing utility. Simply unzip the BIOS package onto a floppy disk and execute the &#8242;FLASH&#8242; batch file from within a DOS environment and it will call the flash utility and load the BIOS file automatically. Please note that you may not update the BIOS from within Windows, you must use a DOS boot disk of some sort.[/INDENT]

Thanks, electrogeist, for pointing us to AFUDOS.EXE - which is mentioned at [http://www.tyan.com/tech/matrix_flashUtility.aspx](http://www.tyan.com/tech/matrix_flashUtility.aspx) , and closeby are the Linux utilities at [http://www.tyan.com/tech/matrix_LinuxflashUtility.aspx](http://www.tyan.com/tech/matrix_LinuxflashUtility.aspx) .

Sean, I'll let you know how my adventure goes if you let me know how your new $30 chip worked :)

'Course, my real question is whether the BIOS flash will cure a problem I'm having with creating a VirtualBox XP virtual machine...

---

### Post by electrogeist on 2009-01-18
librarian - grab that zip archive from the link in Sean4000's original post.  That should have everything you need (except a DOS boot disk).  Running the batch file (a simplistic script) should call the included AFUDOS utility and do everything for you.  It is a simple process.

---

### Post by librarian on 2009-01-19
Thanks, electrogeist. That's exactly what I did (well, minus the really boring story about spending an hour trying to find a floppy disk drive and another hour not getting it to work and finally using the flashcd from [http://www.bootdisk.com/plan40/flashcd.zip](http://www.bootdisk.com/plan40/flashcd.zip) to build a boot CD with the BIOS flash - which I had to do on a Windows machine :( - but the CD not mounting on my TYAN's box 'cause I'm using SATA optical drives and the CD needs IDE and, well...)

The good news: the BIOS flash did eventually run without a hitch (after I hooked up an IDE CD-ROM drive to use the flashcd), and lo and behold it has fixed the problem I had while installing WindowsXP as a virtual machine with VirtualBox.

---

### Post by Sean4000 on 2009-01-20
I have received my chip in the mail and will post an update to see if that option worked for me. 

Glad to see you had success too! I just cannot risk my rig to a risky option.

---

