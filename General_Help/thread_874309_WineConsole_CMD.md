---
title: "WineConsole CMD"
date: 2008-07-29
forum: General Help
---

### Post by Zer0noise on 2008-07-29
Ok. I want to run a file called fixmbr.bat so i can restore my Laptop to manufacture condition. My model is an Acer Aspire 5100. And in order to restore my laptop i have to first restore its MBR. So, now i ran fixmbr.bat with wineconsole cmd. The batch file has the command:


> 
Mbrwrwin.exe install Rtmbr.bin

ok, it runs ok, but at the end, it says:

> Installing MBR ... Error while writting to Rtmbr.bin

Does Wineconsole cmd have all the ability of Windows Command line? Cause ive done this on another Acer Laptop with windows xp as the OS and it worked fine. :confused: What could be the problem? Why cant it finish writing? I really need this fix. :(


[email]Zer0noise@yahoo.com[/email]

---

### Post by ibuclaw on 2008-07-29
I sincerely doubt WINE even has the ability to even touch the MBR with windows scripts...and god forbid :)

WINE can only change settings from within it's little cocoon, it does not touch hardware directly, but translates signals into ones that the Linux kernel can understand. But from the looks of the minimal output you gave, perhaps its because it a expecting a file to exist that simply isn't there...

What is the contents of the script?

Perhaps someone can convert it into a Linux Bash script for you?

Regards
Iain

---

### Post by Zer0noise on 2008-07-29
Im not sure about the scripting seeing how it was sent to me by the Acer support team. It was part of a utility to repair my MBR. It contained those two files i mentioned earlier Mbrwrwin.exe and Rtmbr.bin and fixmbr.bat. Can Wineconsole write to .bin files? And, like you said, its only limited to its own setting? Is there a program i can download in the repository that can allow wine to write on .bin?

---

### Post by raab on 2008-07-29
Just make a bootable usb key and run it off that?

---

### Post by ibuclaw on 2008-07-29
What is wrong with your MBR?

There is almost nothing that the forums can't help you fix.

Regards
Iain

---

### Post by Zer0noise on 2008-07-29
> **raab said:**
> Just make a bootable usb key and run it off that?

I need to install it in my C: drive. How can i use a UBS key to open run fixmbr.bat? 

[QUOTE=tinivole]What is wrong with your MBR?[/QUOTE]

My MBR was replace by the grub loader, but i got rid of grub, then i used ms-sys to reinstall the Windows Xp MBR.(but, im still unable to boot for some reason :confused:) but, that still wouldn't do me any good, seeing that i need my custom Acer MBR in order to run the eRecovery console(which appears when i boot the Laptop) Anyways, i need to successfully run Fixmbr.bat so i can reinstall the Acer MBR back to its original place. How can i fix this problem?

---

### Post by ibuclaw on 2008-07-29
Are you in the UBuntu LiveCD now?

To save yourself alot of hassle, I recommend just reinstalling Ubuntu to get back grub, to allow you to boot into windows and run the script.

You can then reload the LiveCD and kill Ubuntu altogether if you have no need for it.

Regards
Iain

---

### Post by Zer0noise on 2008-07-30
Yea, im using the Ubuntu Live CD. I already have Grub Loader removed and Windows Xp MBR on my /dev/hda. My question is, why isnt it booting XP? I have the system files setup in my C:\. When i go to Gparted, it shows me all the partitions. And i created 3 partitions, one for my PQSERVICE (recovery), second for D:, third for C:. Heres the set up:



Drive:   |   MountedPoint    |  Size:   | Used:  | Filesystem: | Flags:
----------------------------------------------------------------------------------------------------
The "D"  | "/Media/Disk"     |  0.00 MB | 0.0 MB |  NTFS/07    |
The "C"  | "/Media/Disk-1"   | 26.09 MB | 4.6MB  |  Fat32/0C   | Hidden
The "PQ" | "/Media/Disk-2"   |  4.66 MB | 0.0 MB |  Fat32/0C   | 

(Note: In "/Media/Disk-1" its being used by invisible files, probably the Original C:\ Directory. But, i do not see the files in the GUI, when i actually go to "/media/disk-1")




I see all of the Partitions mounted on z:/media. How can i get my original C:\ (the one with the system folders)to show up in the GUI? Also, if you see an error with the the type of filesystem i assigned to each drive,(cause im not sure which filesystem goes with which) just let me know.

---

### Post by Zer0noise on 2008-07-30
Ok, since my question above went unanswered for a while ^ :mad:... i would like this second question answered, How do you convert .bat to shell script then execute it?

Heres the following .bat code: 

```
Mbrwrwin.exe install Rtmbr.bin
```

How will i be able to convert that into Shell? I tried rename the extension from .bat to .sh, but all i get when i run it is access denied. And i read on  some other forum that the shell script are, by default, read-only. I tried to  use Chmod to change the file permission, but was unsuccessful. If anyone here could convert it and give me the code to running it, (Also where i must run it, eg..Terminal or Wineconsole CMD) I would REALLY appreciate it.

---

