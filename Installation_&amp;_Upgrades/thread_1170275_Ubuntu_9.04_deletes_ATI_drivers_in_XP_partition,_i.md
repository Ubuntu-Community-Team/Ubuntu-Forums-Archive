---
title: "Ubuntu 9.04 deletes ATI drivers in XP partition, inter alia"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by t54 on 2009-05-26
Subject: Ubuntu 9.04 deletes ATI drivers in XP partition, inter alia  

System: Lenovo T500 ThinkPad laptop  brand new. ATI Radeon 3650 discrete graphics w/256MB video memory. card, 4GB RAM etc.  

The system came with win XP pre installed. I installed Ubuntu v9.04 to create a dual boot laptop. 

Prior to Ubuntu install, XP worked flawlessly. After Ubuntu install, Ubuntu worked fine.  

*However after quitting Ubuntu and booting into XP, problems appeared* :(  

All ATI discrete video/graphic drivers and ATI's Catalyst Control Centre had vanished and needed to be reinstalled.  Other device drivers disappeared  too, eg, the Lenovo integrated camera and others. XP still functions without them but Device Manager reports missing drivers or 'unable to load' installed driver errors. 

If the subject device drivers are reinstalled, XP works perfectly -provided you do not ever boot into Ubuntu again!  This problem only happens when you boot into Ubuntu, close it and then boot into XP. 

Any insight into a cure for this? I would very much like to have dual boot T500 with these 2 OS.  Thanks to all who provide assistance.

---

### Post by Bartender on 2009-05-26
Once it's installed, Ubuntu doesn't reach over into the Windows installation and mess with it.
My only guess is that for whatever reason, Windows was not sufficiently defragged.  Parts of it had to be shoved out of the way by the Ubuntu installer.  Installing Ubuntu to a chunk of hard drive that's devoid of data is much less risky than asking the installer to get Windows data out of the way.
If you haven't burned your recovery DVD's yet, do so.

---

### Post by Mark Phelps on 2009-05-26
Did you shrink the XP partition to make room for Ubuntu and install it that way? Or did you install inside XP using Wubi? Or did you let the Ubuntu installer do the side-by-side installation on its own?

Are you mounting the XP partition when in Ubuntu?  If you do that and shutdown without cleanly unmounting the partition, you run the risk of corrupting the partition table in the XP partition -- which when, the table is repaired, could easily result in the loss of files and directories?

---

### Post by t54 on 2009-05-26
Thank you for your kind reply.

> **Mark Phelps said:**
> Did you shrink the XP partition to make room for Ubuntu and install it that way? Or did you install inside XP using Wubi? Or did you let the Ubuntu installer do the side-by-side installation on its own?

[b]Answer: I booted and let Ubuntu install on its own from the CD.

This is a virtually new client machine, factory XP install with only a few prgs and configurations added by me. I do not think there would be much disc frangmentation in this case.

Delivery of this computer is quite overdue and I am now faced with either solving the Ubuntu/XP conflict or deleting the Ubuntu partitions and resetting the MBR to kill GRUB. Keeping Ubuntu would be nice; we all want to encourage its use. But....

There are 2 XP partitions on the drive, one for XP OS files, user files, software etc and a 'restore files' partition where all factory drivers, XP etc are kept for recovery use. I am trying to attach  a jpg of the HD partitioning layout.[/b]

>  Are you mounting the XP partition when in Ubuntu? If you do that and shutdown without cleanly unmounting the partition, you run the risk of corrupting the partition table in the XP partition -- which when, the table is repaired, could easily result in the loss of files and directories?

[b]Answer: I mount Ubuntu and XP only using the GRUB boot mgr, not from within each other. Ergo, XP and Ubuntu are started from clean boots.

It is imortant to note that if after the ATI XP drivers (and others) are replaced AND Ubuntu is NOT ever started again, XP will load time after time and run perfectly. This suggests to me that Ubuntu is messing about with files or the registry in the XP partition when Ubuntu is being loaded and/ when it is shut down.[/b]

PS I am running Firefox 3 with jscript and cookies enabled for this forum. Yet none of the post composition 'features' such as file attachments, bold font, etc will work. (I am coding font qualities by hand).  Also, NO carriage returns are retained when submitting preview requests or edits.  Hence my posts frustratingly have zero paragraphs within them and thus are difficult to read. Sorry for that. I would like to know how to enable posting features and retain paragraphs.  I have tried switching between the 3 options in user CP -to no avail.

---

### Post by Mark Phelps on 2009-05-27
Do you by any chance have the drivers in a shared partition?

The only way I can think that Ubuntu is corrupting your driver files is if the partition containing the files is being mounted in Ubuntu and not being cleanly unmounted later.  

Since you're not mounting it manually, you need to check your /etc/fstab to ensure that it's not being automounted at startup.

---

### Post by t54 on 2009-05-27
> **Mark Phelps said:**
> Do you by any chance have the drivers in a shared partition?

The only way I can think that Ubuntu is corrupting your driver files is if the partition containing the files is being mounted in Ubuntu and not being cleanly unmounted later.  

Since you're not mounting it manually, you need to check your /etc/fstab to ensure that it's not being automounted at startup.

**Thanks to all who have so kindly given advice on this issue, especially Mark Phelps**

I can say that I did not knowingly create any shared partition.

Please see the jpg image above, in my earlier post, of the drive's partitioning. There is plenty of free space available. Why would there be any need for partition sharing by the Ubuntu installer?  I presume Ubuntu's auto install on the live CD takes all this into account and would not overwrite or merge partitions without permission.

But, I must confess ignorance of Ubuntu's inner workings. 

When installed, or when booted, does Ubuntu scan the computer's drives for existing drivers usable by Ubuntu?  How could such a scan for drivers produce any destructive effect, unless the drivers were being moved instead of copied? Why would they need to be copied more than once? *Could an XP ATI driver even be used by Ubuntu?*  I remain mystified.

It is noteworthy that there is regularity present here. If Ubuntu never runs, the XP drivers remain in good order and XP runs happily. But when Ubuntu is loaded and then exited, it is always the same set of XP drivers, eg, ATI graphics/video, that are deleted or corrupted by Ubuntu. 

These drivers are resident in the XP partition along with thousands of other XP OS files. *Why are only the ATI and a few other drivers affected by Ubuntu? Why are all other OS files never affected?* 

I wish I had more time and knowledge of Ubuntu to deal with this vexing problem, but this is a client computer at issue and I must have it in good working order for delivery this Friday. (It is already long overdue.)

*However, it would still seem important to the Ubuntu community to know that the live CD automated installer (or some other process) in Ubuntu v9.04 is capable of creating this bizarre problem -and to create a cure.*

Given that presently there appears to be no simple means of eliminating Ubuntu's corruption/deletion of XP's ATI drivers on this computer,  I fear that my next step must be to delete Ubuntu and GRUB. I would be grateful for advice on the proper way to do that *without harming the integrity of the existing XP installation*.

I have several partition managers in WinXP, eg, Paragon. Is this the best procedure from within XP?

1. Delete both Linux partitions; *Will this eliminate the GRUB bootloader?*
2. then, make winXP the active partition. *Will this restore the XP MBR? Or must I run the equvalent of mbrfix to do that?*

---

### Post by Mark Phelps on 2009-05-27
> **t54 said:**
> 
I can say that I did not knowingly create any shared partition.
I'm not asking about creating shared partitions, I'm asking about mounting a partition to share it between Ubuntu and XP.  If you added the NTFS partition to your /etc/fstab file, it would automatically be mounted on startup, and unless you made the specific effort to mount it read-only, it would be mounted read-write -- which then, if Ubuntu didn't cleanly unmount it, could cause partition table corruption when you next used it in XP.

> 
When installed, or when booted, does Ubuntu scan the computer's drives for existing drivers usable by Ubuntu?  
No scanning for driver files is done (that I'm aware of).Besides, since (apart from NDISWrapper) Linux doesn't even use MS Windows drivers, such scanning would be useless.
>  Could an XP ATI driver even be used by Ubuntu?
No -- not an MS Windows driver.  Would have to be a Linux driver.
> 
It is noteworthy that there is regularity present here. If Ubuntu never runs, the XP drivers remain in good order and XP runs happily. But when Ubuntu is loaded and then exited, it is always the same set of XP drivers, eg, ATI graphics/video, that are deleted or corrupted by Ubuntu. 

Yeah -- read that the first time and still don't have an explanation for the specificity of the corruption.

> 
Given that presently there appears to be no simple means of eliminating Ubuntu's corruption/deletion of XP's ATI drivers on this computer,  I fear that my next step must be to delete Ubuntu and GRUB. I would be grateful for advice on the proper way to do that without harming the integrity of the existing XP installation.

I have several partition managers in WinXP, eg, Paragon. Is this the best procedure from within XP?


Understand, really do -- you need a working machine and don't have the time to keep messing around.

OK  - recommend the following:
1) Fix the MBR first. Link below provides the details:

[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm]("http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm")

2) Boot into XP and use Paragon to remove the Ubuntu partition(s).

3) Optionally, resize the XP partition to fill the unallocated space or create a new partition (NTFS) for that space.

Yeah, I know EVERYONE ELSE will tell you to use GParted to do the partitioning, but I prefer to use MS Windows tools to mess with MS Windows partitions, and Linux tools to mess with Linux partitions -- have avoided LOTS of problems using this approach.

---

### Post by t54 on 2009-05-28
Subsequent to the adverse events described above, Ubuntu 9.04 was removed by deleting its partitions and restoring the XP MBR.

XP then loaded and ran perfectly every time **UNTIL** I decided to see if a ***live session*** run on the Ubuntu CD would function for emergency internet access, etc. 

I ran the live session, quit it, removed the CD and rebooted into XP. **To my astonishment, the ATI graphics/video drivers had been deleted again -even though Ubuntu was not installed on this computer!** (See ATI pop-up error msg on attached jpg.)

It was my understanding, that in a live Ubuntu CD session, no data is supposed to be written to the host computer's hard drive. My understanding apparently was wrong.  

I am wondering if this ATI driver deletion phenomenon is peculiar to: Ubuntu 9.04? All Linux distros? A bizarre, perhaps unique, interaction between the Lenovo Thinkpad T500 running XP and Ubuntu?


PS Mark Phelps instructions on deleting the Ubuntu partitions and restoring the XP MBR worked perfectly. Thank you, Mark.

---

### Post by Bartender on 2009-05-28
t54 -
If there was a "Stump the Experts" game show, I would nominate your situation.
Linux uses Linux drivers, except for odd instances like ndiswrapper, as mentioned previously.  So, no, Ubuntu doesn't go foraging for drivers in the NTFS partition.  Your LiveCD experience is even weirder!  A good example of trouble-shooting creativity.
There are a couple of questions I have after looking at the partition table you attached.
First off, that FAT 32 partition inside the extended; you said that's the recovery partition, right?
Reason why I ask is because Ubuntu picked out a tiny amount of space for itself.  Only 2 GB.  And the swap is miniscule.  Here's what I think happened.  There can only be one extended partition.  It looks to me like Ubuntu tried to install to the extended partition instead of moving aside the main NTFS partition and creating more primary partitions.  I believe the Ubuntu installer is set up to choose an extended partition over creating primary partitions because there is often no room for more primary partitions. 
If I were you, I'd burn a copy of the recovery partition to DVD and delete the recovery partition.  XP should still boot without any problems.  Defrag the dickens out of XP.  Then use whatever partitioner you want (I've never heard of Paragon before) to move XP over far enough so you have 20 or 30 GB for Ubuntu.  Check to see that XP still runs.  If it doesn't, you can try to fix it or just re-install from recovery discs.
Then use GParted LiveCD to create an extended partition for Ubuntu and install to that partition.
As to why the ATI drivers keep getting screwed up, I have no idea, but that is a weird partition table and if I'm right about Ubuntu trying to find some space on the recovery partition that may have something to do with the odd behavior.  How I don't know exactly.
There is the possibility that Ubuntu has ruined the recovery partition if it tried to cohabitate with the existing data.  If that's the case, you may need to contact the manufacturer and see if you can order a copy.

---

### Post by t54 on 2009-05-30
I posted this earlier in this thread:
*"I am wondering if this ATI driver deletion phenomenon is peculiar to: Ubuntu 9.04? All Linux distros? A bizarre, perhaps unique, interaction between the Lenovo Thinkpad T500 running XP and Ubuntu?"*

Here is a partial answer. Today I installed Acronis Trueimage 2009 v12 (a Windows drive imaging/restore utility) and burned a recovery CD. Though Trueimage is a Windows application, the CD is based on Linux. After testing the recovery CD features, I rebooted and -you guessed it- the ATI graphics drivers were gone from XP.

The ATI drivers were reinstalled and the computer was booted and rebooted several times into win XP without incident.

For the avoidance of doubt, Ubuntu was completely removed from this machine yesterday; XP is the only resident OS.

I remain completely mystified.  There must be an explanation for this computer's adverse, very specific reaction to any form of contact with Linux. I would be most grateful for an understanding of the how and why of it.

---

### Post by harlekin65 on 2009-06-02
I have had exactly the same experience that t54. 

Last week I received my brand new Lenovo T500 with a Windows XP totally functional and all the drivers installed. I installed Ubuntu 9.04 in a dual boot configuration without problemas ... until I boot in Windows. As t54, my ATI drivers were gone!

So the issue seems reproducible and maybe related some way to our particulap laptop (Lenovo T500).

Any ideas?

---

### Post by harlekin65 on 2009-06-04
I think I have found the origin of the problem. The Lenovo T500 has TWO graphical card: the ATI one and another one integrated in the mainnboard.

For some reason when Ubuntu boots it switch the graphic card to the integrated one. This switch is the reason of the "corruption" of the ATI drivers on Windows. If in the laptop BIOS you disabled the "OS Detection for Switchable Graphics" option the issue disappears.

---

### Post by t54 on 2009-06-05
> **harlekin65 said:**
> I think I have found the origin of the problem. The Lenovo T500 has TWO graphical card: the ATI one and another one integrated in the mainnboard.

For some reason when Ubuntu boots it switch the graphic card to the integrated one. This switch is the reason of the "corruption" of the ATI drivers on Windows. If in the laptop BIOS you disabled the "OS Detection for Switchable Graphics" option the issue disappears.

**Thank you Harlekin65! **I can confirm that your solution works on my T500 too.  Apparently, the Lenovo factory default for the culprit BIOS setting 'OS Detection for Switchable Graphics' is ENABLED on all T500s. Changing it to DISABLED cures the T500's 'Linux contact allergy' in every form reported in this thread. :)

---

### Post by vollmond on 2009-06-30
Just to chime in, I saw the same symptoms on my T400, and the same BIOS setting fixed it for me.

---

### Post by Vikdal on 2009-07-22
Finally!! I've been having this problem for some months now. I can confirm that the live cd also removes the ATI driver. Even the CloneZilla backup cd does it :(

I'll try the solution to edit the BIOS settings, I just need to reinstall the ATI driver first, so that I don't reboot for nothing.

BTW, my first post :D
Been a reader for a long time though:popcorn:

---

