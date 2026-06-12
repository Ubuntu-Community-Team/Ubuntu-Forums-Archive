---
title: "Uninstalling, Grub and booting problems"
date: 2008-10-04
forum: General Help
---

### Post by nick334 on 2008-10-04
I had Ubuntu 8.04 installed but it was causing too many problems with drivers and other things so I decided to uninstall it. I did a google search and found that all you had to do was format and use your XP disc to do a fixmbr or something.

I formatted it fine but when I restarted it comes up with this error:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 22.

I've found that this basically means that this grub is still installed and it can't find the files needed to work because the hard drive partition they were on was formatted. I read that the way to fix this is to use your XP disc to boot into recovery and type fixmbr and fixboot (or something similar to that).

I've tried to boot my XP disc but nothing happens - it says something like "No bootable media in tray". My computer has had problems with booting from CDs before (see [http://ubuntuforums.org/showthread.php?t=868147](http://ubuntuforums.org/showthread.php?t=868147)).

Is this a problem with my CD-drive? It's the only thing I can think of. I can't boot CDs and I've checked the CDs and the BIOS settings.

---

### Post by Idefix82 on 2008-10-04
Can you check on some other computer whether your windows disk is bootable? If it is then it's probably a problem with either the cd-rom drive or ith the bios. In this case you could try creating a bootable USB stick provided that your bios supports booting from usb devices.

---

### Post by nick334 on 2008-10-04
Just checked it on my mums laptop and it's fine. I have a 1GB USB pen that I had to use to install Ubuntu in the first place. I'll try copying the files from the disc onto the pen and see how it goes.

I'm almost completely sure that it's a problem with the CD drive now.

---

### Post by nick334 on 2008-10-04
That didn't work. Just comes up with boot error.

I think it may be that I didn't burn it to the USB drive, I just copied it. I remember with Ubuntu I had to extract it to the pen. 

I've heard you can download a copy of Windows 98 legally and use it to get the Recovery Console. Is this possible?

---

### Post by Neo_The_User on 2008-10-04
Grub error 22 means it can't find Ubuntu. I used to have the same problem. I re-installed it, worked fine (after I fixed my corrupted hard drive which took about... an hour)

Grub error 22 specifically means it cannot find the kernel therefor making it unbootable. Next time when you install Ubuntu, make sure it's on a CD or DVD and make sure that its installing it on your hard drive. You'll never receive this error again if you do that. ;)

---

### Post by nick334 on 2008-10-04
I don't want to reinstall Ubuntu though - I want to be able to boot into Windows again. The formatting of the partition ubuntu was on has messed with Grub.

I think I may buy a new CD drive tomorrow.

---

### Post by ajgreeny on 2008-10-04
If by chance you have a floppy drive and can find or download a win98 startup disk, you can restore the windows MBR with that.  I think a quick google may help, but I must admit, it sounds like a good idea to get a new CD/DVD drive.

---

### Post by Herman on 2008-10-04
> I've heard you can download a copy of Windows 98 legally and use it to get the Recovery Console. Is this possible?     :D I agree with ajgreeny.
If your computer has a working floppy disk drive you should be able to use a Windows 98 floppy disk which you can download for free.
You can restore your Windows XP boot with a Windows 98 floppy disk but do not use it for Vista becuase it changes the 'disc signature' in the MBR. Windows 98 or XP dosn't depend on the 'disk signature', but Vista does.

Here is an illustrated link which will show you what to do,  [Windows 98 Floppy Disk Method]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method")...also works for XP.

Regards, Herman :D

---

### Post by nick334 on 2008-10-05
Thanks for all the help everybody I've managed to fix it. I removed the CD drive from an old computer that was lying around and tried to replace the one in mine. I couldn't figure out how to get it out but then realised I could just plug it in with the wires and leads I unplugged from the drive inside the computer. I everntually set it all up right and managed to get into the Recovery Console with my XP disc. I ran the fixmbr and fixboot commands and everythingf is fine now :D

Just need to buy a new drive now :(

---

### Post by TeXtonyx on 2008-10-05
[http://aumha.net/viewtopic.php?f=62&t=31844](http://aumha.net/viewtopic.php?f=62&t=31844)

If you install this before a problem, it puts the Recovery Console on the menu at the 
XP boot.ini generated boot to screen. Works for people with no XP install cds best.

---

