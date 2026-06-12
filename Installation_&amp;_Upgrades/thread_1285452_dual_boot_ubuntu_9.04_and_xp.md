---
title: "dual boot ubuntu 9.04 and xp"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by adavis on 2009-10-07
Hello,

I am relatively new to linux (ubuntu 9.04)and want to install windows on my laptop to run microsoft sql server. I have chosen windows xp sp2.

I read that it is cleaner to install windows first (NTFS format) then install Ubuntu. I have setup an unpartitioned portion of my hard drive for the windows installation. When I boot from the windows cd, I am receiving the following error right after Setup is starting Windows:

"
A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this stop error screen, restart your computer. If this screen appears again, follow these steps:

Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it is properly configured and terminated. Run CHKDSK /F to check for hard drive corruption, and then restart your computer.

Technical information:

***STOP: 0x0000007B (0xF78D2524,0xC0000034,0x00000000,0x00000000)
"

I have used my ubuntu install cd to confirm that my hard drive has no viruses and no corruption. If I bypass the cd rom, I am able to boot and run Ubuntu with no problems.

Do you have any suggestions on how to get past this blue stop screen from the windows setup?

I appreciate your help in advance.

Thanks.

---

### Post by lindsay7 on 2009-10-07
Here is a guide that may help,

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by adavis on 2009-10-07
Thank you for the link. I also came across this how-to earlier today. I am able to complete page 1,2, and 3 successfully. I receive the blue stop screen before getting the first screen shot of the list of existing partitioned drives on page 4.

---

### Post by lindsay7 on 2009-10-07
After reading this,  [http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103)

It looks like you may need to install windows on a clean drive and then install Ubuntu.

---

### Post by adavis on 2009-10-07
How do I make a clean drive? I'm having challenges with fdisk and gParted to get the drive completely clean.

---

### Post by lindsay7 on 2009-10-07
Use the Ubuntu install cd to get to Gparted. Make sure the drive is unmounted, then format the drive to ntsf. Then you can install windows on a clean drive.

---

### Post by adavis on 2009-10-07
My apologies for the newbie question: How do I get to gParted from the install disk?

My install CD gives me the following choices:

Try Ubuntu without any change to your computer
Install Ubuntu
Check disc for defects
Test memory
Boot from first hard disk

---

### Post by lindsay7 on 2009-10-07
You choose this option. It will load Ubuntu but does not install it. It is like a trial version.  Then go to the top menu bar and choose Systems/Administration/Partition Editor (same as Gparted). When you are in Gparted, right click the drive and make sure it is unmounted.  Then you can format the drive.

---

### Post by adavis on 2009-10-08
I have been able to get to GParted so that it has NTFS file format available, thru the trial version. I have tried these scenarios...all ending with the blue stop screen.
 
1. format 40 GB as ntfs, unmounted. leave remainder unpartitioned.
2. format 70GB as ntfs, unmounted; 40GB at ext3, unmounted; 10GB as linux-swap, unmounted; remainder formatted as fat32, unmounted.
 
I have been able to confirm that my windows xp disk works as expected on a windows laptop.
 
Other suggestions?

---

### Post by dstew on 2009-10-08
Maybe try this. Delete all the partitions so that the whole drive is unallocated space. Then create a single partition that encompasses the whole drive, but **do not format it**. That will tell the Windows install CD that it has a clear drive to install to. You could also create three partitions, one for Windows, one for Linux and one for swap. Again, leave them unformatted. The installers can format the partitions.

---

### Post by adavis on 2009-10-08
Same result...blue stop screen...with single unformatted partition.
 
My laptop was purchased with ubuntu installed on it. Is there a bios setting that is different when using linux os vs windows os? Or maybe a boot setting?

---

### Post by dstew on 2009-10-08
I am kind of stumped. You get an error after the message "Setup is starting Windows:" I don't know much about Windows installation, but that message seems odd. Aren't you trying to *install* Windows? I don't think it's a problem with your BIOS, and I think your hard disk is OK. Are you sure that that Windows CD will install on that computer? Maybe there are different kinds of Windows installers for different kinds of computers, so the disk will work on some computers, but not others. As I said, I don't know much about Windows installation, and I have never done it.

---

### Post by QIII on 2009-10-08
Try formatting the drive as NTFS.

Windows tends to think it is the only OS in the universe and cries, throws a tantrum, wets its pants and generally has a very bad day when presented with anything that does not fit that world view.

(Not knocking the "other OS" per se.  It is not really bad.  I just hate Microsoft's business practices, monopoly on the market and lack of choice in "user experience" other than what Microsoft thinks your "user experience" should be.

In the immortal words of Henry Ford (may be apocryphal, but I like it):  "Any customer can have a car painted any color that he wants so long as it is black.")

---

### Post by adavis on 2009-10-08
Really good questions. 
 
When you boot up with the Windows install CD, it first prepares the files that it needs for the install questions (how to partition the drive(s), where to install, what to install, etc). This is what I see...the prep work. The next steps I'm not completely sure of the order or the exact details. I believe the next step is to check the hardware on the computer box, then start the windows installer screens. This is where I suspect is the problem with my laptop. That there is some setting that I have not set that will tell windows that it's ok to install.
 
I was under the impression that hard drives and memory were independent of operating systems. They may not be. However, there are lots of discussions about successful dual boot systems. What I'm unsure of is the starting point of those computer boxes.
 
This is frustrating. Especially since I have tried to move away from Windows to Linux, but SQL Server is a strong skillset to have and I want to learn it...but only can be installed on a Windows OS.
 
Any other ideas/suggestions that you have, please send them. They are greatly appreciated.

---

### Post by adavis on 2009-10-08
QIII,
 
I'm currently trying your suggestion of formatting the entire drive as NTFS. I will post my results.
 
thanks.

---

### Post by QIII on 2009-10-08
The hard drives themselves don't really care about what type of file system you use on them.

But Windows cares about FAT and NTFS.

If I recall correctly from the way old days, DOS and Windows started out needing disks that were preformatted.  You just bought them that way.  "Formatted for MSDOS", etc, marked on the box.

I haven't installed Windows on a bare disk for quite some time (ten or fifteen years, I'd guess) -- I take the disks with Windows pre-installed on a machine, put them lower in the boot order and put Linux on a new disk.  So I don't know how that plays now.

---

### Post by adavis on 2009-10-08
QIII,
 
A single formatted NTFS drive results in the same windows blue stop screen before the user interacted windows install screens are reached.

---

### Post by QIII on 2009-10-08
Dreck!

OK.

Check this out:

[http://support.microsoft.com/kb/330182](http://support.microsoft.com/kb/330182)

Could be BIOS or hardware -- which really surprises me!

What is the make, model, etc and specs of the machine?

(You may be reduced to running XP in a virtual machine, but that is a lot of overhead...)

---

### Post by praveenthivari on 2009-10-08
:)Hi,
    It's just the fault of cd or amd processors i suppose, I don't know. Because i hv amd athlon x64 and on this, one of the XP cd (especially the one which is customised) comes up with the same message, after the services are loaded during installation. The same cd works on my friend's system without any faults. I used another cd and it booted without any error messages
     So,I think just use another XP bootable cd (preferably a clean one):P

---

### Post by ermeyers on 2009-10-08
Install Ubuntu on it successfully, the whole disk.  Then try to install Windows XP, and for-sure they'll jump all over that disk with their OS. :)

---

### Post by adavis on 2009-10-08
Hello All!
 
I am currently in the Windows XP setup screens...farther than I have gotten. Below are the notes of the settings that I changed while driving blindfolded at the computer that seem to have helped me...
 
Hard drive was formatted as NTFS using GParted under the trial version.
Restart the computer.
Go into System settings...for me, it's F2 right after the first signs of the computer booting up.
Under the Advanced tab, I noted that the operating system was set to Vista. I changed this to XP. F10 for save and exit.
Then boot from the CD...windows installer cd.
 
I am very early in the install/setup process. I will post if I encounter any challenges to get your advice.
 
Thank you for your help!

---

### Post by QIII on 2009-10-08
When you get Windows going, you can dowload SQL Server 2008 Express for free.

It is fully functional (for ONE user), but it limits the size of any single database to 2GB.

For $50, you can get SQL Server 2008 Developer Edition, which gives you unlimited size, but, again, it is limited to one user.

Each of them also is limited to one processor, so if you have multiple cores it will only hit one.  Keep a careful eye on temperature.

---

