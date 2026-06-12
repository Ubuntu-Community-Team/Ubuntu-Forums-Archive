---
title: "a problem with my dual boot system"
date: 2011-03-28
forum: Hardware
---

### Post by danielsender on 2011-03-28
Hi,

I have a Dell Precision M50 laptop with 2 disks. In the main disk I have XP installed and in the bay I have ubuntu 10.10. The bios points to the main disk for first priority in the booting. I have legacy grub installed. Everything was working fine until a few days ago when my ubuntu system starting freezing randomly, even when it was idling. It wasn't doing it when I was booting XP. But last night, when I wanted to boot XP, after clicking on the grub menu, the screen shows "starting up ...." but does not go beyond that. On the other hand, ubuntu boots fine. I starting to think that it was some hardware malfunction, maybe the main disk but when I mount it under ubuntu (ntfs) I can read the whole thing fine. Also, would such a potential malfunction in the main disk (XP) affect ubuntu? Mounting the XP disk is always done automatically in the fstab file.

After reading other postings I realized that the freezing of ubuntu could be related to my nvidia driver and not the XP disk

Is there any diagnostics that I could run to troubleshoot the problem? I'll appreciate any inputs.

Cheers,

Daniel

---

### Post by danielsender on 2011-03-29
Anybody there?

At least I would like to know whether this is a grub problem, a windows problem or some kind of hardware failure. One more thing, I re-installed grub but it didn't make any difference. In other words, when I choose to start XP from the grub menu, it just writes "Starting up ..." without any other message and gets stuck there. I hope some guru can help me. Thanks.

Daniel

---

### Post by oldfred on 2011-03-29
While my XP continued to work, Ubuntu & gparted started having problems with seeing the entire drive. I ran chkdsk on the NTFS partition and then everything was ok. That might be one thing to try. If chkdsk finds errors you have to rerun it until there are no errors. It does not fix everything on one pass.

XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

Also what does System, Administration, Disk Utility click on XP drive. It should show a overall smart status. It also has lots of detail on errors but I do not know what makes too many errors by type.

---

### Post by danielsender on 2011-03-29
I guess that i would have to run chkdsk from a live CD right? Remember that I cannot boot XP.

Daniel

---

### Post by oldfred on 2011-03-29
You have to run it from a windows CD. You should have your original XP install disk.

You can use a Vista/7 repair disk to run chkdsk. It just will not do much for other XP repairs.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You can try this from Ubuntu but it is not a full chkdsk.
In windows run "chkdsk /f". Although you can also use "ntfsfix" in Ubuntu:
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdXY x- drive y - partition

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
ntfsfix is able to repair some minor errors and it will flag the volume as dirty. So the next time you try to boot Windows XP, XP should run "chkdsk".

---

### Post by danielsender on 2011-03-29
OK. I got ntfsfix, ran it and unfortunately it didn't solve the problem. Do I have to get the original XP CD to run chkdsk or could be another CD, I cannot find the original one.

---

### Post by oldfred on 2011-03-29
Any windows disk or the Vista/7 cd's I posted above.

---

### Post by danielsender on 2011-03-30
I succesfully ran CHKDSK from an XP CD. However it didn't solve the problem, that is, if I choose to boot XP, it writes on the screen "Starting up ..." and it gets stuck there. If I press Ctrl+Alt+Delete it goes back to the grub menu. As I said before, Ubuntu boots fine. Any ideas what I could try next?

Many thanks again.

Cheers,

Daniel

---

### Post by oldfred on 2011-03-30
It seems grub is working ok if you get to a windows error.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\.

---

### Post by danielsender on 2011-03-31
I followed all the steps you indicated and according to what these programs display everything ran ok, but the problem remains. Indeed I can boot into ubuntu, but not XP.
What else could be wrong here? It seems that grub is working because it boots ubuntu and it appears to go ok to where XP is sitting...

Thanks again,

Daniel :(

---

### Post by oldfred on 2011-03-31
Post this, so we can see where you are at. If everything was run, I would think it should be ok.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by danielsender on 2011-04-01
I ran the script. I really appreciate your help. I'm attaching the file RESULTS.txt.

Regards,

Daniel

---

### Post by oldfred on 2011-04-01
It may be just that you have two copies of this:

/boot.ini /ntldr [COLOR=Red]/NTDETECT.COM /ntdetect.com
[/COLOR]

Delete either one. Windows is not case sensitive so it thinks they are the same and then gets confused.

You have two drives, and are booting Ubuntu in sdb with grub legacy in sda.

I prefer to keep each drive independant if possible. Does your BIOS let you choose boot drive? If so I would install grub to sdb and change BIOS to boot sdb. Then you can install a windows boot loader to sda. That way if either drive does not work at least in BIOS you can choose the other.

In Ubuntu:

sudo fdisk -l
#confirm drive with Linux is sdb
grub-install /dev/sdb

Try booting from sdb. If it works then you can install a windows boot loader to sda.

---

### Post by danielsender on 2011-04-01
The two copies of the same file are there because when I copied them according to your instructions I didn't check that there was one already in upper case. I just deleted one (the lower case) but it didn't solve the problem.

I agree with you that I should install grub in sdb to separate the systems, but I would like first to know and perhaps fix whatever was functional before. I am very puzzled about the problem, it appears that grub and XP are ok, so...

Regards,

Daniel

---

### Post by oldfred on 2011-04-01
Boot script is showing all the files & what structures it parses as ok. Sometime something in the boot sector or other just requires repair and then it works.

Boot.ini has a first blank entry. That may be an issue, not sure.

multi(0)disk(0)rdisk(0)partition(1)\[COLOR=Red]WINDOWS="" [/COLOR]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

When you ran the repairs it should have auto rebuilt boot.ini. You can manually edit it but have to be careful with Linux due to different line endings.
I used to just recommend nano, but gedit now has a combo box where you can choose line endings. You must choose windows.

If editing windows files like boot.ini
(Using nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.

---

### Post by danielsender on 2011-04-01
boot.ini was repaired, I see the time stamp being from yesterday. I deleted that blank line you mentioned making sure that the line endings were ok by using unix2dos/dos2unix and vi. Again it does the same thing. Frustrating, isn't?...

Cheers,

Daniel

---

### Post by oldfred on 2011-04-01
I am about out of ideas. Usually the fixes solve boot issues. I might try installing grub to the sdb drive and confirm you can boot.

Then rerun the fixes for windows including the fixMBR command that will write the windows boot loader to sda. Then you can with one time boot key directly boot windows and see if that works. You should still be able to boot Ubuntu from sdb then.

---

### Post by danielsender on 2011-04-01
I ran grub-install after confirming that should be on /dev/sdb. There was a little glitch in terms of having the change the name of hd0 to hd1 to boot XP, but still it does not want to start. Ubuntu starts as usual. If I set in the bios the priority to sda it just hangs as when I use grub. I did follow all the steps but maybe I didn't run bootcfg properly. It asked a few questions that I just pressed return, but perhaps I should have done otherwise. The questions are:

Add installation to boot list? (Yes/No/All):
Enter Load Identifier:
Enter OS Load Options:

What are the proper answers to these? And also how should I fix the issue of the names of hd0, hd1? When I boot it I just did a temporary editing on the boot options: 'e' followed by 'b'.

Daniel

---

### Post by oldfred on 2011-04-01
That must be why you got the blank entry. It should not even be asking (I think). Why is it now hd1. It should be hd0 and that should not change. 

Or do you have a BIOS that is not booting both drives in the same order every time. We have seen that occasionally and it creates huge problems for windows. Ubuntu will use UUID so it finds correct partition to boot either way. Not sure if it is low power, inconsistent drive startups or what may change drive order.

[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)

---

### Post by danielsender on 2011-04-02
I re-ran bootcfg, fixboot and chkdsk but this time I answer 'n' to the question "Add installation to boot list?". Again, it just refuses to boot. The new grub installation displays (hd0, 0) as the disk where ubuntu is, but when it attempts to boot XP doesn't display from what disk it will attempt, I think that can be easily changed in the configuration file. I know that this is getting old, but do you have any other suggestions on what should I attempt?
Thanks.

Daniel

---

### Post by oldfred on 2011-04-02
Did you do anything in BIOS or hardware to get drives to change order? 

Windows was set as hd0 and if it is now hd1 it will have problems. That must be why it keeps asking to add it as windows now thinks another install is on hd1?

But windows works best if it is hd0. Ubuntu does not care.

Are these IDE/PATA drives, SATA or mixed?

---

### Post by danielsender on 2011-04-02
In order to run the grub bootloader, now in the disk in the bay together with ubuntu 10.10 I had to change the boot order in the bios. Otherwise will only attempt to boot XP.

These are pata disks (320G WD for the XP and 160G Seagate for 10.10). One more thing, I just re-ran chkdsk and I get a message that I don't remember seeing it before, something like: "the volume appears to contain an unrecoverable error",. Does this mean that the hardware is bad or something else went south?

Daniel

---

### Post by oldfred on 2011-04-02
Often with PATA you can only boot the first drive. Old system always only booted primary master. New SATA drives are totally defined in BIOS, but BIOS' with early SATA capability did not always convert IDE drives. You may only be able to install grub to which ever drive is first which should probably be the windows drive. You can have grub in the Ubuntu drive but it would only ever be used if you removed the first drive. And if the Ubuntu drive fails the grub in the windows drive would not work, but you could install a windows boot loader from a Windows repair CD or Lilo from Ubuntu to be able to boot windows. Or have a SuperGrub disk handy. 

It sounds like a partition has an error. If it is NTFS then you need to run chkdsk from the XP CD. If it is Linux partition you should run e2fsck from the Ubuntu liveCD.

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

be sure swapoff completed so swap is not mounted also.

---

### Post by danielsender on 2011-04-03
The bios in my laptop allows the secondary hard drive, where now I have grup and ubuntu to be first in the boot order. Trying to boot XP acts the same way, whether I use the XP bootloader (re-installed the other day) or grub, it just gets stuck. I ran 2 times more chkdsk and in both instances comes out without errors.

Based on a past experience with another machine, although unrelated to this problem, I resetted the bios (ALT-F), but it didn't fix the problem. I also restored the autochk.exe file from the CD, but it didn't fix it.

I wouldn't like to re-install XP because I learnt that some applications won't run any more and also it may not solve the problem.

Daniel

---

### Post by oldfred on 2011-04-03
If you are directly booting windows and you ran the windows fixes, I do not know why it should not boot.

Rerun boot script to see if I can see anything, but I am not hopeful at this point.

---

### Post by techunit on 2011-04-03
have you tryed setting the bios to choose Ubuntu as the primary disk? sometimes there is a boot problem. It sounds like you have grub installed on the XP disk so you may not want to do that.

Nvidia drivers can do that but not likely. ATI graphics have a worse history.

Good Luck.

---

### Post by danielsender on 2011-04-03
Please see the attached new RESULTS1.TXT.

To answer TECHUNIT question, at this point grub and ubuntu are on the secondary disk, XP is in the primary together with the XP loader. I used to have grub in the same disk as XP, but I changed it. The problem persists in both cases.

Thanks,

Daniel

---

### Post by oldfred on 2011-04-03
I still do not see anything obvious out of place.

How full is XP partition?

Did I ask what Disk Utility, click on windows partition show. Does drive show green/good?

(Note I am grasping at straws, if anyone has any idea please chime in.)

---

### Post by danielsender on 2011-04-04
The XP system is on a separate drive. It's using about 60GB and the disk is 320G, so is pretty much empty.

You mention a disk utility that shows the partitions in colors, what utility is that?

Thanks,

Daniel

---

### Post by oldfred on 2011-04-04
I do not know all the details as it gives lots of detailed info on a drive. Minor errors as considered ok.

System, Administration, Disk Utility. then click on drive and/or click on partition for additional info. You can also do some disk changes like you do in gparted but partitions must be unmounted for much to work. I have used it to relabel partitions as I like each partition to have a label.

---

### Post by danielsender on 2011-04-04
Looking into some windows forums I read that windows has a program called sfc (system file checker) that it said to repair corrupted files and the likes. However, this program is not part of the CD repair menu. It appears that you run it once you're logged on the system, which is something I still can't do.

Daniel

---

### Post by danielsender on 2011-04-04
I know next to nothing about windows XP, but I got an idea that perhaps will tell me what's going on. What is in windows the equivalent of the linux kernel file? I suspect that for some reason is not even attempting to load that kernel. So I was thinking if I can attempt to boot windows and after restart the machine with linux I could read the last access time of the kernel file. If that time stamp hasn't changed from the previous reading, then it would imply that the boot loader is not even attempting to load XP. Would something like this work? I would need to know what is the file to check.

Thanks,

Daniel

---

### Post by danielsender on 2011-04-04
I recorded the time of the last access to "boot.ini" using "ls -lastu boot.ini" and attempted booting into XP. Of course, nothing happened, so I booted 10.10 and ran the same "ls" command and saw that the file was apparently not read. Does this mean anything?

Thanks,

Daniel

---

### Post by oldfred on 2011-04-04
I do not know all the files it boots. It starts with the MBR (or grub) jumping to the partition boot sector (PBR) and loading ntldr and reading boot.ini on what partition/version to use. I do not know if it even has any date stamps on that. 

All of the above were what we tried to repair, boot sector, ntldr, boot.ini. Also chkdsk so it can read partition. That should get you started and then windows may give blue screen & error numbers.

Did you at any point change BIOS to have drives not be in IDE mode? XP requires special drivers to be in AHCI or a SATA mode.

Discusses Vista & XP dual boot. And how booting works for all MBR(msdos) type systems.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by danielsender on 2011-04-05
As you said, boot.ini is one of the files involved in the booting process, therefore if there was an attempt to read it, then "ls -lastu" should have given the time of that event, that is any time younger than the preceding reading. Furthermore, neither ntldr and ntdetect.com do not show as having been read at the time of the attempted boot.

I didn't modify anything in the bios, furthermore, as I said before I did a reset to default factory values "ALT-f".

Regards,

Daniel

---

### Post by oldfred on 2011-04-05
Depending on BIOS that may not be correct. Check BIOS for anything related to IDE.

I copied comments from others, different BIOS all use different terminology.

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> &#8220;Large&#8221;, did the trick.
I
t was the SATA Native IDE setting that hosed Grub. I had to set the OnChip SATA Type to AHCI in order to boot using Grub. As for the OnChip SATA Port 4/5 Type setting it doesn't have any affect on Grub, it can be set to IDE or as SATA Type. My MB BIOS doesn't have a Compatibility or LBA setting so I have to find the AHCI XP drivers if I want to Multi-Boot XP and Ubuntu.

---

### Post by danielsender on 2011-04-05
This machine is a vintage Dell made circa 2002 (M50). The bios does not have anything related to sata disks since there were not in existence at that time. The menu in the bios does not have any instructions on how the reset to default values, I just found on a web site that alt-f does the job. Indeed it appears to reset since the boot order changes, the clock goes back to epoch and probably something else that I didn't observe. However I sense that you are looking at the bios as the culprit and the fact that those files that I indicated above are not being read seem to confirm this. I don't know if is possible to check when the mbr has been last read.

Don't forget that this was a perfectly working system until a few days ago, and I didn't change any settings before the time that it didn't work. Today, out of desperation I removed the HD and cleaned the contacts to no avail. Also what is really surprising is that all the recovery programs in the XP CD return success and I can perfectly read the disk when mounted under 10.10. I'm sure that it must be something very stupid...

Cheers,

Daniel

---

### Post by oldfred on 2011-04-05
After the windows repairs, you did try directly booting from a windows boot loader in the MBR, I forgot?

All grub does is skip MBR and jump to the same partition as the windows MBR does, so it should not matter.

---

### Post by danielsender on 2011-04-05
yes, i tried many times booting directly from the xp disk without going through grub, in fact I even disabled the ubuntu disk in the bios.

Daniel

---

### Post by oldfred on 2011-04-05
How many times have you run the fixboot & fixMBR commands. Sometimes more  than once or it fixes something else the second time?

I am literally out of ideas.

---

### Post by danielsender on 2011-04-05
I ran these programs quite a few times, I just ran them again twice. It's hard to tell, but if you look at the little green light that is the indicator for disk activity, it blinks very briefly as it leaves the bios program. I was thinking that if there would be some software problem it will show a more steady and longer light, wouldn't it?

Daniel

---

### Post by oldfred on 2011-04-05
Usually it flickers as it reads, so yes maybe it is not reading much or as much as it should??

---

### Post by danielsender on 2011-04-05
It blinks only once and very, very briefly.

A guy in the Microsoft forum suggested to press F8 after the bios stage to go to the advanced boot page, but it doesn't get anywhere.
I wonder if there is something in the hardware other than the disk itself that would keep the system from being loaded, but without restricting other operations, such as the XP CD recovery programs or ubuntu mounting them and reading them.

---

### Post by oldfred on 2011-04-06
We were experimenting with setting the Ubuntu drive as the boot drive, but with your system and IDE drives, jumpers on hard drives have to be correct or if you are using cable select you have to have the jumpers set for that and have the newer 80 conductor cable.

Do you have the windows drive set /jumpered as master? Or master with slave on a few systems. And the Ubuntu drive set as slave.

---

### Post by danielsender on 2011-04-06
I don't have any jumpers. I remember when I replaced the main disk 2 years ago I experimented but the only functional solution was not to have any jumper. Plus the bios does not give any options in that regard. But again, remember that this was a perfectly functional system until a week ago with the hardware as is.

Daniel

---

### Post by oldfred on 2011-04-06
Old IDE BIOS relies on the drive having jumpers or on  a cable select cable and jumpered cable select.

If we did not change anything I do not know what the problem is then.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by danielsender on 2011-04-06
This is a laptop, thus there are no ribbon cables available to the user. I don't know how the system handles the interaction with both disks and the bios does not provide any options in that regard. My next experiment will be to swap disks, that is to place the one currently in the bay (secondary) as the main one, and viceversa.

Daniel

---

### Post by danielsender on 2011-04-07
This is very strange. I ran the complete hardware diagnostics from the Dell CD "Drivers and Utilities" that came with the machine. It took probably 8 hours (nighttime) and the response was "your hardware performs optimally". Then I took the the XP CD and follow the instructions on [http://support.microsoft.com/kb/314503](http://support.microsoft.com/kb/314503) (Method 2) to repair the system. It also finished correctly. But guess what:... it still refuses to boot or do anything.
I'm about the get a hammer!

Cheers,

Daniel

---

### Post by oldfred on 2011-04-07
I have seen issues with Vista & 7, but repairs to XP almost always work. I do not understand why do are not booting.

---

### Post by danielsender on 2011-04-08
I reached a conclusion that the HD is defective although it does not show in the hardware testing. I ran the extensive hardware test of Dell, the repair option of the XP CD and swapped  disks between the main location and the bay. So I contacted Western Digital for a warranty replacement.

Oldfred, I really appreciate the time you spent on this.

Regards,

Daniel

---

### Post by danielsender on 2011-04-26
I think that I finally nailed the problem. And most probably it wasn't a hardware problem with my disk. Here is a summary of the issues.

1. One day XP refused to boot, while Ubuntu was fine. I swapped the disks, that is placed the ubuntu disk in the main slot and the XP disk in the secondary bay. Same result, XP would not boot while Ubuntu was fine.

2. I said the XP disk is bad, so I got an identical disk, re-installed XP and booted fine. After installation, I ran the XP update and again it refused to boot!!!

3. I took another smaller disk (20G vs 320G) and installed XP, ran an update and booted fine. So I copied the image from that one into the 320G. It booted fine again.

4. Simultaneously I inquired in one of the Dell forums and I was told that this machine should be configured as cable select, which for these IDE disks implies to place jumpers in both disks according to the manufacturers diagrams, which for most 2.5in disks is in horizontal position.

5. After a week of these modifications, XP is running fine (well... is a nice way to talk about windows).

6. Now that I think of it, before all these issues came about, once every while either system use to freeze randomly. Now I suspect that could have been due to not having the jumpers set for cable select. So far, there weren't any issues, but I keep my fingers crossed.

Thank you oldfred, the ubuntu forums are great!

Daniel[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by oldfred on 2011-04-26
Glad you got it working.:)

Hopefully it is permanently resolved, as if anything ever is. I seem to keep breaking my system and have to do something to make it correct.

---

