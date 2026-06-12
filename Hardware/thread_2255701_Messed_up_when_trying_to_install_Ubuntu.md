---
title: "Messed up when trying to install Ubuntu"
date: 2014-12-06
forum: Hardware
---

### Post by milo9 on 2014-12-06
I've installed Ubuntu a couple of times in the past and this time I wasn't not able to install ubuntu as I usually did. I had to use unetbootin as the main installer wouldn't work for me. I was attempting to dual boot ubuntu with windows 7 to see if I could run CSGO better, as some people have told me about it ubuntu using Open GL. When I restarted to launch the computer with ubuntu, I was able to open an installation wizard in which I went on to where I had to partition my hard drive for unbuntu. As I used to be able to install ubuntu on windows without having to do it within Ubuntu, I didn't know what to do about partitioning, because the windows wizard would give me an option to select the amount of space for unbuntu, which I would select 30 gigs. I decided I didn't know what to do without potentially messing up my computer, so I restarted, went to windows and looked it up. Now I launched unbuntu again and was going to mess with the partitioning, when I decided it was not worth it. I restarted to go back to windows, and now I get past the Dell logo image on start up, in which it shows a blinking underscore on the top left of my computer like a console of sorts. I've been trying to fix my computer for the last couple of hours and couldn't figure out how to fix it. I came up with an idea to try to boot ubuntu with a usb, and I thought you could just stick the files onto the flash drive, in which I realized wasn't the case. Is there anyway to revert the partitioning and not lose any of my important documents and photos? I'm not able to launch either dual booted OS, so I'm stuck trying to figure out what to do. Thanks for reading and or thank for attempting to help me out!

---

### Post by oldfred on 2014-12-07
You should always resize Windows from its own partition tools and reboot immediately as it has to run chkdsk and make repairs for its new size.
If you still have Windows booting but with errors you may be able to use f8 to get into Windows repair console. But always better to have a Windows repair flash drive or CD, so you know you can run Windows repairs. 

You make this for free, but if you have to download it from Internet it can cost $20 to $40.
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Did you install Ubuntu. If so then grub should be booting. 
But better if errors to boot installer in live mode and add Boot-Repair.
Post link to the summary report that Boot-Repair creates. Boot repair can only do minor fixes to Windows as you usually need the Windows repair disk.


        Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by milo9 on 2014-12-07
Hey, thanks for the solutions , but I was a bit confused by the information so I tried to see what I could about it. I was able to get my spare hard drive plugged in, and booting the OS off the 2nd hard drive, in which I was able to boot a Live Usb to boot Ubuntu with. I restarted and was able to properly launch Ubuntu with the live usb. However I switched my hard drives back, and when trying to boot, it gives me a message of missing operating system. I can't launch either Windows 7 or Ubuntu installed, or via live usb. How would I go about being able to launch the Ubuntu with Live usb through the Bios if it says this error? Grub? I don't know how to exactly go about doing that. And when I get it to work, should I try Testdisk to remove the accidental partitioning, to be able to completely solve the problem and to be able to launch Win 7 again?

---

### Post by oldfred on 2014-12-07
I am confused. Are you not installing Ubuntu from a flash drive or DVD?
You should just be able to boot that in live mode and install boot repair.

Until we can review what is where, I would not start deleting stuff.
Windows does not correctly see Linux partitions and often essential partitions get deleted.

---

### Post by Mark Phelps on 2014-12-07
> However I switched my hard drives back, and when trying to boot, it gives me a message of missing operating system. This means that your PC is trying to boot from the hard drive, not the USB stick.  When you reconnected the drives, it now sees the hard drive first, instead of the USB stick.  You have to reverse the order of the two in the boot sequence, or, if F12 gives you a one-time-boot menu, use that and select the USB stick, usually something like USB-HDD.

---

### Post by milo9 on 2014-12-07
I was able to fix it randomly and now I'm able to run Ubuntu (I think the demo) through the USB. Basically, I want to revert back to the point where I had my original Win 7 boot which takes up around 8 gigs on my 1 tb hd, and my files, like photos, games, and etc, taking up around 700gigs, but the ubuntu wizard partitioned the hard drive, in which both OS weren't not able to boot. What steps should I take to undo the partitioning of the ubuntu install wizard and in what steps can I go about to saving my original files? Sorry if I'm being unclear.
My situation is similar to this [http://askubuntu.com/questions/450128/accidentally-deleted-all-my-partitions-after-ubuntu-14-04-installation](http://askubuntu.com/questions/450128/accidentally-deleted-all-my-partitions-after-ubuntu-14-04-installation) however when I try to do sudo testdisk is gives me an error of "command not found." Do I have to completely install Ubuntu to be able to get to the point in which I should install a program similar to testdisk to recover the deleted partitions of my hard drive?

Edit: to make it more clear, I tried to install ubuntu with unetbootin, and when I restarted my computer to get to the demo version of ubuntu, I went through the installation wizard of ubuntu, and accidentally deleted a partition table. So should I use testdisk to recover the partition table to get my files back? Do I need to completely install ubuntu to be able to do so? This is on Ubuntu 14.04.1 LTS demo.

---

### Post by oldfred on 2014-12-07
STOP using hard drive.
All activity is overwriting more data, so less is recoverable.

Test disk is best case if its search or deeper search can find old partitions or files.
If not then you have to use photorec. Which is a long slow process. It scans drive for anything that looks like a file and copies it to another drive which you must have enough room on for all the recovered files.
Some suggest Windows tools if a NTFS partition as sometimes they work better but may cost.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)


 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

      
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.


 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by milo9 on 2014-12-08
So I should use testdisk and or Recuva? Am I able to install and use both programs on 14.04.1 LTS?

---

### Post by oldfred on 2014-12-08
Test disk is in Ubuntu repository, so you can install to live installer version. And most Linux repairCD have it automatically.
I think all the Windows suggestions require you to boot with Windows, or move drive to another working Windows system, either internally or in a USB caddy.

---

### Post by milo9 on 2014-12-25
I was able to fix my hard drive by booting from an ubuntu live usb, and I installed from there. I went and installed testdisk and followed instructions to fix it. I ran into an error in which when I tried to restart, grub had an error of not detecting files(no such partition grub rescue), in which I needed to launch via the usb, in which the usb wouldn't work as it gave me an error on booting ubuntu (&#8220;No root file system defined"), in which it gave me another error with not being able to find a file or two. I fixed the os via startup repair for windows, and finally using the cmd to fix it, and finally everything works! I seem to have the majority of my photos and files. I haven't found a single file that has been corrupted. Thanks for all the help! I just now fixed my computer as I have been busy with school, so I saved until the break to fix my comp.

---

### Post by oldfred on 2014-12-26
Glad you got it working. Not everyone has as good success. 

And best to make good backups now.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

