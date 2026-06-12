---
title: "Making a boot floppy"
date: 2005-01-23
forum: Installation &amp; Upgrades
---

### Post by shewhoguards on 2005-01-23
I've a suspiscion I'm being very stupid and missing something here, but what it is I just can't seem to work out.

I've got an old computer I'm restoring that I figured I'd try out Ubuntu on. So, nice new clean hard disk, and I need to create a floppy boot disk to get things started. I settle down and read the help files and from what I understand to create a boot disk I copy sbm.bin to a floppy disk, yes?

Problem. sbm.bin is 1.40 MB in size, and my clean formatted floppies are 1.38MB. So, copying it across gets me the message that the disk isn't big enough.

What am I doing wrong?

---

### Post by shewhoguards on 2005-01-23
Okay. Update. I Googled a bit, came up with instructions at [http://www.ubuntulinux.org/support/documentation/howto/SmartBootManagerHowto/](http://www.ubuntulinux.org/support/documentation/howto/SmartBootManagerHowto/) and now have a floppy.I can now get to a screen that says "Boot Menu" and gives me a choice of "Quit to BIOS" "Power Off" "Reboot" "Floppy" "Harddisk" and "CD-ROM" Picking "Floppy" just makes the screen blink and then return. Picking CD-ROM gets "Disk Error! 0x0C"

Again, what am I doing wrong? Do I have the wrong thing on the floppy, the wrong thing on the CD-ROM, or what?

---

### Post by Seazzy on 2005-04-09
I am having the same problems, but my floppies have 1.44 Mb of space and the damned thing still says there's no room. I'm going to check out that how-to guide, if I figure anything out I'll let you know

---

### Post by mikeymouse on 2005-04-10
To make a boot floppy out of the sbm.bin file.
 Now this is the way I make boot floppies for any linux distribution so dont hate me.
 Get rawwrite for windows, put the sbm.bin file in a directory in windows.
 Then run rawwrite it will ask you for the file and for the destination floppy which is usuall A.. thats all there is to it you will find the file now fits on a floppy.
I hope this helps its has kept me from beating my head agains a wall many times.
 mikeymouse

---

### Post by occy8 on 2005-04-10
there is a thread here. I had the same issue, but didn't notice it. I haven't used my floppy for a while...
[http://www.ubuntuforums.org/showthread.php?t=22801&highlight=floppy](http://www.ubuntuforums.org/showthread.php?t=22801&highlight=floppy)

---

### Post by Stone Cold n00b on 2008-03-30
I have a similar problem, except I'm trying to install Ubuntu on an Acer Aspire 3003 laptop.

What do I do?  Do I need to buy an external floppy drive?

SOS. Please help.

---

### Post by Herman on 2008-03-30
How old is your Acer 3003 laptop?

I'm typing to you from an Acer Aspire 3003WLMi laptop and I can tell you for sure I have never needed a floppy disc for booting it, ever.
My Acer laptop isn't very old though, maybe it's about three years old already.

I just finished fixing an old Windows 95 computer for an old guy, I had to download a boot floppy disk file for it from bootdisk.Com and run fdisk /mbr and sys c: and I also ran scandisk just to make sure.
Unfortunately it only had 32MB of RAM and a 2.0 GB hard disk so I couldn't install Ubuntu in it yet.  We have another old computer we might be able to get parts from to upgrade it with though.

Even Windows 95 computers will boot by themselves, the only reason I needed a boot disc was to fix the automatic booting for it, (fix the master boot record and the partition boot sector), so I don't know how old the computers the earlier posters in this thread have. Maybe they're old DOS ones I guess.

If you're trying to install Ubuntu in a modern computer, (I mean less than ten or fifteen years old), and it won't boot a Live CD, one of the first things to do is go into your CMOS (BIOS), and make sure you have the BIOS boot order set to look at the CD-ROM drive first before it looks at the hard disk drive for a bootable MBR.
Here's a link about that, [BIOS Page]("http://www.users.bigpond.net.au/hermanzone/p1.htm") . I realize your BIOS will be quite different from the one I used to illustrate what to do there, but it should give you the basic idea anyway.

Ubuntu works very well in my Acer Aspire 3003WLMi laptop and also in my wife's Acer Aspire 1642ZWLMi.
The only thing that I would need to work at to get working would be my Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02), but I don't really care too much about that. I rarely if ever, need to use wireless networking.
Everything else works fine. -no floppy disc required- :)

Regards, Herman :)

EDIT: Windows 95 and earlier need a boot floppy with a CD-ROM driver in it to boot a Windows 95 installation CD.

---

### Post by Stone Cold n00b on 2008-03-31
The boot order was set correctly.  I downloaded 7.10 from Ubuntu's website and I think I burnt the CD incorrectly.

I extraced the files for the ISO file into a folder.  Burnt all the folders and files within the folder with Nero.  I believe I may need to make the CD bootable.  I've only made one or two bootable discs, so I can't say for sure I did everything correctly.

Any advice?

---

### Post by Stone Cold n00b on 2008-03-31
The boot order was set correctly. I downloaded 7.10 from Ubuntu's website and I think I burnt the CD incorrectly.

I extraced the files for the ISO file into a folder. Burnt all the folders and files within the folder with Nero. I believe I may need to make the CD bootable. I've only made one or two bootable discs, so I can't say for sure I did everything correctly.

Any advice?

---

### Post by Herman on 2008-03-31
> I extraced the files for the ISO file into a folder. Burnt all the folders and files within the folder with Nero. I believe I may need to make the CD bootable. I've only made one or two bootable discs, so I can't say for sure I did everything correctly. It sounds like you're doing something wrong there alright, you should be downloading an .iso file, (already made). There shouldn't be any need to combine files into a folder, are you sure you have the correct download? 
If you want Gutsy Gibbon 'Desktop' CD from Ubuntu's website, try this link, [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
When you have received the complete .iso file, just be sure to burn it as an .iso, not as a data disk and it should boot and run for you.

Regards, Herman :)

---

### Post by Stone Cold n00b on 2008-03-31
Ah ok.  I thought the ISO file needed to be uncompressed.  I will try it and let you know.  Thanks!

---

### Post by Stone Cold n00b on 2008-03-31
Ok, it worked!  I burned  an image file CD and the installation went smoothly...  But now I have another problem.

After I got an internet connection and downloaded the updates, my computer crashed during update installation and now when I try to boot my computer, after I log in, my computer freezes at the peach colored screen.

SOS!  Please help...

---

### Post by Stone Cold n00b on 2008-03-31
BTW, my mouse still moves and I am able to ctrl+alt+backspace to reboot.

---

### Post by Herman on 2008-04-01
:) Okay, probably you just have a file system problem.
Exactly the same thing happened to me not so long ago.
I booted up my Ubuntu Live CD and opened up a terminal and ran 'fdisk -lu' to check on my partition numbers,
```
sudo fdisk -lu
```
Another good one is 'sudo parted /dev/hda p'
```
sudo parted /dev/hda p
```Where: your hard drive is IDE (PATA), if SATA or scsi, replace the 'hda' part with 'sda' instead.
Or, just look with Gnome Partition Editor to see what your partitions are.

Now, when you know which partition number is Ubuntu's, run the e2fsck file system checl like this,
```
sudo e2fsck -C0 -p -f -v /dev/hda2
```Where: your Ubuntu partition is 'dev/hda2' or whatever you just found out from the previous commands I just showed, (above).

That should repair your file system almost every time.

In my case it didn't, but it gave me an error message telling me what else to do next. That was something like 'the superblock can not be read or it isn't a correct ext3 superblock, if this really is an ext3 file system please run sudo e2fsck -b 32768  to replace the superblock with a backup', (or something like that).

To see where all my backups of the superblock were, I ran, ```
sudo dumpe2fs /dev/hda2 | grep -i superblock
```
Then I ran ```
sudo e2fsck -b 32768 /dev/hda2
```, and my file system was fixed and Ubuntu worked normally again.

Probably you'll only need the first command, 'sudo e2fsck -C0 -p -f -v /dev/hda2'. 

Regards, Herman :)

---

### Post by Stone Cold n00b on 2008-04-02
Ok, I used the Gnome Partion Editor and discovered my Ubuntu partion is sda1 and then I used your code like so:

sudo e2fsck -CO -p -f -v /dev/sda1

The terminal went through some sort of system check for six things/areas, which took a little time.  I rebooted and my computer still stalled.  So, I re-installed Ubuntu (went great), downloaded 202 updates and while they were aproximately 70% installed, my comp crashed again.  I rebooted and the stall occurs again.

I should mention, the reason I switched to Ubuntu was because my computer kept crashing within five minutes of any game I played.  However, I was planning on switching to Ubuntu at some point.  The reason I mention this is because the update install crash and the previous gameplay crashes seem to be very similar; my computer just crashes with no error message or bluescreen.  It just crashes to power off.

I hope this isn't a hardware issue.  Please advise.

---

### Post by Stone Cold n00b on 2008-04-02
BTW, the games my computer used to crash on ranged from Age of Empires (very low specs required) II to Star Wars: Empire at War (average specs required).

These are not my dxdiag specs, but mine would be very similar:
------------------ 
System Information 
------------------ 
Time of this report: 6/4/2007, 17:30:29 
Operating System: Windows XP Home Edition (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.070227-2254) 
Language: English (Regional Setting: English) 
System Manufacturer: Acer, inc . 
System Model: Aspire 3000 
BIOS: Phoenix NoteBIOS 4.0 Release 6.0 
Processor: Mobile AMD Sempron(tm) Processor 3000+, MMX, 3DNow, ~1.8GHz 
Memory: 1.4GB RAM 
Page File: 451MB used, 1862MB available 
Windows Dir: C:\WINDOWS 
DirectX Version: DirectX 9.0c (4.09.0000.0904) 
DX Setup Parameters: Not found 
DxDiag Version: 5.03.2600.2180 32bit Unicode 

--------------- 
Display Devices 
--------------- 
Card name: SiS M760GX 
Manufacturer: SiS 
Chip type: SiS 760 Rev 00 
DAC type: Internal 
Device Key: Enum\PCI\VEN_1039&DEV_6330&SUBSYS_00831025&REV_00 
Display Memory: 64.0 MB 
Current Mode: 1024 x 768 (32 bit) (60Hz) 
Monitor: Plug and Play Monitor 
Monitor Max Res: 1600,1200 
Driver Name: SiSGRV.dll 
Driver Version: 6.14.0010.3654 (English) 
DDI Version: 9 (or higher) 
Driver Attributes: Final Retail 
Driver Date/Size: 3/1/2005 23:47:32, 862208 bytes 
WHQL Logo'd: Yes 
WHQL Date Stamp: n/a 
VDD: n/a 
Mini VDD: sisgrp.sys 
Mini VDD Date: 3/2/2005 00:09:02, 240640 bytes 
Device Identifier: {D7B71ED9-2070-11CF-D37D-8920A1C2CB35} 
Vendor ID: 0x1039 
Device ID: 0x6330 
SubSys ID: 0x00831025 
Revision ID: 0x0000 
Revision ID: 0x0000 
Video Accel: 
Deinterlace Caps: n/a 
Registry: OK 
DDraw Status: Enabled 
D3D Status: Enabled 
AGP Status: Enabled 
DDraw Test Result: Not run 
D3D7 Test Result: Not run 
D3D8 Test Result: Not run 
D3D9 Test Result: Not run

Additional specs:
[http://reviews.cnet.com/laptops/acer-aspire-3000/4507-3121_7-31532504.html](http://reviews.cnet.com/laptops/acer-aspire-3000/4507-3121_7-31532504.html)

---

### Post by Aim9b on 2008-04-03
Stone Cold, Sounds like a heat problem I had a while back. 
I was told (on a diff forum) that my Acer was notoriously "under fanned".
I installed a heat sink & additional fan & the system ran [windows] flawlessly.  Good Luck.

---

### Post by Herman on 2008-04-03
> Stone Cold, Sounds like a heat problem I had a while back. 
I was told (on a diff forum) that my Acer was notoriously "under fanned".
I installed a heat sink & additional fan & the system ran [windows] flawlessly.  Good Luck.      I agree with Aim9b,
If you have your computer repaired professionally, it's time to have it serviced, it might just need cleaning.

If you do your own work, remove your CPU fan and clean your heat sink and fans, and then of course put the fan back on. Run your PC without the case cover on for a while and watch the case fan and CPU fan. Make sure they are working okay.
I have one computer that has a CPU fan with a bad bearing and it stops from time to time, then the computer shuts down just about the same as you described yours doing. It I keep an eye on it and tap it the CPU fan with a ballpoint pen when it stops and the fans starts again and the computer keeps working fine. (LOL).
I plan on buying a new CPU fan sometime soon.

I also replaced a power supply in a computer and while I was doing that I noticed the CPU heat sink and fan were clogged with dust, so I cleaned them. The when I was putting the cover back on I saw a dust filter behind the air vent that lets air into the CPU duct. That was blocked too. It was kind of like a lint filter for a clothes dryer or air conditioner, like a plastic screen that was easy to slide out and clean with a vacuum cleaner. 

The power supply is another thing that can make a PC turm off randomly too. Power supplies are not too expensive. 

Try going into your computer's BIOS and looking at what it says in this link, [System Health Check]("http://www.users.bigpond.net.au/hermanzone/p1.htm#System_Health_Check").

---

### Post by Stone Cold n00b on 2008-04-04
So, last night I took a can of air and took apart my laptop to find hardly any dust.  I blew it out anyway, especially the fan, and took a cake pan, filled it with ice and set my laptop on top of it while I re-installed Ubuntu 7.10 and updates.  However, I limited my updates from unstable updates and... whatever the last checkbox is in the update setup tab.

The computer still crashed during update installation, but I was able to boot it back up normally.  When the computer loaded I recieved a message stating that I had to configure the updates manually, which wasn't that hard.  It turned out successful.

I've started playing with preferences and installing all the software I think I'll need, before I start using the computer, to ensure I won't received too many defragmented files.

On another note, I'm pretty sure my battery is need of replacement, which I will, hopefully, take care of soon.

Thanks for your help everyone.  On to Ubuntu home servers after this... :)

---

