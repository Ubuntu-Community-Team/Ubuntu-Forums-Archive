---
title: "Cannot install Ubuntu 22.04 on new PC"
date: 2023-04-03
forum: Hardware
---

### Post by jacek.gajek on 2023-04-03
I've got a new PC on which I've installed Windows 10 and obviously everything works fine. Games especially, since it's Geforce 4070ti. Whole setup:

CPU AMD Ryzen 9 7900X 
Motherboard Asus TUF GAMING B650M-PLUS
GPU MSI GeForce RTX 4070 Ti
Memory: Kingston Fury Beast, DDR5, 32 GB, 5600MHz, CL40
SSD Disk: Lexar SSD NM620 1TB

I'm used to Ubuntu and worked with it for years, so to install Linux I used Windows partition manager to shrink a C: partition to get unallocated space, download the latest **LTS 22.04.02 **and run setup with 'nomodeset', otherwise it wouldn't start (noaveau chipset unknown).

Setup seemed to run with nothing suspicious happening. I tried the default "Install along Windows" option. After setup completed, Ubuntu froze with a** black screen **with a (non-blinking) underscore character in a top-left corner. Couldn't get out, so I did magic shortcut for **emergency remount & reboot**.

After reboot, the menu to choose OS appeared, so I chose to run ubuntu, again with **nomodeset** to install Nvidia drivers.

Then, the following sequence happens:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292010&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292011&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292012&stc=1[/IMG]

Just before (2) there is the same screen but with rotating circle indication system loading, but then the circle disappears.

The (3) is an **unending stream** of IO errors. So I couldn't do anything but again use the** magic remount and reboot**.

After that the **PC reboot straight to BIOS and the SSD cannot be detected** so I cannot boot neither to Windows nor Ubunt, even after reboot triggered from BIOS.

However, if I completely shut down my PC with Power button and start it again, it boots **straight to Windows**. In BIOS, the Ubuntu bootloader **does **appear, but if I try to run it, it goes to a **"Minimal Grub console" **or sth like that.

This is **reproducible**, I tried several times, also with 22.10 and "do something different" option. Not sure which attept that was, but at one point I was able to boot to Ubuntu and run apt update upgrade and install Nvidia drivers, but after that it **wouldn't boot anymore**. Errors were also about file system, but interchanged with GPU failing, and it was in color:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292014&stc=1[/IMG]

At other time I** was able to run** it for some time, but after **two reboots** it started to fail.

The disk should be fine, it's new and I checked it with chkdsk with **no errors**. Also I run the PC with Windows use it everyday for **two months** and didn't encounter any problems. I've also downloaded and installed the **latest BIOS version.** chkdsk result:

```
[SIZE=1][FONT=comic sans ms]Checking file system on C:
The type of the file system is NTFS.


A disk check has been scheduled.
Windows will now check the disk.                         


Stage 1: Examining basic file system structure ...
  897280 file records processed.                                                         
File verification completed.
 Phase duration (File record verification): 4.27 seconds.
  9088 large file records processed.                                    
 Phase duration (Orphan file record recovery): 0.00 milliseconds.
  0 bad file records processed.                                      
 Phase duration (Bad file record checking): 1.46 milliseconds.


Stage 2: Examining file name linkage ...
  299 reparse records processed.                                       
  1322298 index entries processed.                                                        
Index verification completed.
 Phase duration (Index verification): 13.19 seconds.
  0 unindexed files scanned.                                         
 Phase duration (Orphan reconnection): 1.51 seconds.
  0 unindexed files recovered to lost and found.                     
 Phase duration (Orphan recovery to lost and found): 1.55 seconds.
  299 reparse records processed.                                       
 Phase duration (Reparse point and Object ID verification): 5.20 milliseconds.


Stage 3: Examining security descriptors ...
Cleaning up 1717 unused index entries from index $SII of file 0x9.
Cleaning up 1717 unused index entries from index $SDH of file 0x9.
Cleaning up 1717 unused security descriptors.
Security descriptor verification completed.
 Phase duration (Security descriptor verification): 17.14 milliseconds.
  212510 data files processed.                                            
 Phase duration (Data attribute verification): 1.57 milliseconds.
CHKDSK is verifying Usn Journal...
  41157112 USN bytes processed.                                                            
Usn Journal verification completed.
 Phase duration (USN journal verification): 82.51 milliseconds.


Stage 4: Looking for bad clusters in user file data ...
  897264 files processed.                                                                
File data verification completed.
 Phase duration (User file recovery): 2.53 minutes.


Stage 5: Looking for bad, free clusters ...
  142061916 free clusters processed.                                                        
Free space verification is complete.
 Phase duration (Free space recovery): 0.00 milliseconds.


Windows has scanned the file system and found no problems.
No further action is required.


 685495315 KB total disk space.
 115827664 KB in 675358 files.
    389908 KB in 212511 indexes.
         0 KB in bad sectors.
   1030075 KB in use by the system.
     65536 KB occupied by the log file.
 568247668 KB available on disk.


      4096 bytes in each allocation unit.
 171373828 total allocation units on disk.
 142061917 allocation units available on disk.
Total duration: 2.88 minutes (172980 ms).


Internal Info:
00 b1 0d 00 47 8c 0d 00 3c ee 18 00 00 00 00 00  ....G...<.......
ac 00 00 00 7f 00 00 00 00 00 00 00 00 00 00 00  ................[/FONT][/SIZE]
```

---

### Post by oldfred on 2023-04-03
Please use Code Tags with any code.
If using Quick Reply then[noparse] ```
 at the beginning and 
``` at the end. [/noparse]
Easy to add in Forum's advanced editor with # icon.
How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

Also remove in line screen shots/photos, they only need to be the attachments.
Not all users have high speed Internet & in line photo can be then slow downloading.

When you installed, did you also choose the optional restricted drivers so correct nVidia driver is installed?

Do not know AMD, but many older AMD needed UEFI updates and latest kernel and IOMMU settings.

Was it 22.04.2 that you installed?

Asus ROG Strix B450 E motherboard UEFI update worked
[https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679](https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679)
Asus Rog Strix B550 Disable IOMMU
[https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-lts-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397](https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-lts-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397)

---

### Post by jacek.gajek on 2023-04-03
There was no option for to install "optional restricted drivers". There was something like "3-rd party libraries". For one attempt I checked it, for another I didn't. This didn't help at all.

As I've written yes it was 22.04.2. No offence, but I think reading a post is a good idea before answering.

As you probably have noticed, the posts you've linked describe completely different issues. Also I don't want change/disable anything in BIOS just to make OS work since Windows runs perfectly fine.

---

### Post by tea for one on 2023-04-03
Did you install Ubuntu in UEFI mode?

In one of the screen shots, I can see [COLOR="#0000FF"]Ext4 fs error (/dev/nvmeon1p6[/COLOR])
Have you tried to fsck your Ubuntu partition in a live session?

---

### Post by oldfred on 2023-04-03
Ok, exact wording is 
Install third party software for graphics 
Some is proprietary (Which is referring to nVidia and possibly others).
[https://ubuntu.com/tutorials/install-ubuntu-desktop#5-installation-setup](https://ubuntu.com/tutorials/install-ubuntu-desktop#5-installation-setup)

Have you updated UEFI to latest version?
That is required whether running just Windows or not.

A lot of this was in 2022, but new versions are regularly found. 
Spectre virus, repoline, RETBleed -  firmware update needed as well as maintaining updates of operating system. 
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.

---

### Post by TheFu on 2023-04-03
Really new CPU, really new motherboard = bleeding edge.  This is one of the times when running the 23.04 beta might be needed to get support.

I have older Asus B450 STRIX motherboards with older Ryzen 5600G CPUs.  Remove the nVidia GPU to avoid all the hassles it causes under Linux, but I'm not a gamer.  AMD GPU drivers are built-into the kernel.

One of my Ryzens boots with BIOS and the other boots with UEFI.  The UEFI system has problems with the keyboard and mouse, which makes little sense. Besides that, the systems are identical. Same MB, version, RAM, PSU. The UEFI has a Samsung NVMe SSD, while the BIOS boot one has a Micron SATA SSD.

I specifically wanted Intel GigE NICs and the B550 had Intel 2.5Gbps which were having driver issues at the time, so I avoided them.  I always avoid Realtek NICs. Learned that lesson the hard way (bad performance, more overhead, and dead onboard NICs).  My reasoning is that paying $20 more to get Intel NICs that "just work" work is well worth my sanity.

But we all have different needs.

If an SSD goes read-only, that usually means it is failing or the drivers somewhere in the chain aren't right.  I'd boot into a "Try Ubuntu" environment using whatever Desktop ISO you have for installation, install smartmontools, then run a short SMART test.  Wait however long it says will be needed, then run a SMART report on that specific device.  SSDs sometimes fail when they are brand new, even well-regarded brands have this issue.  A buddy had a Samsung PRO 980 die within 1 month, as an example.  They replaced it with little hassle.  My credit cards will replace anything bought within the last 90 days that fails. Takes about 20 minutes to file the forms.

---

### Post by jacek.gajek on 2023-04-25
Thanks for answering. Disk errors on my Windows SSD were scary so I bought a separate disk just for Linux. Successfuly installed Ubuntu with erase disk option.

After booting with nomodeset was able to install 525 driver which was recently added to Ubuntu and it works.

With 530 it didn't boot .

---

### Post by jacek.gajek on 2023-04-25
^^ That was written on phone, this post is from working Ubuntu!

There is a weird thing though &#8211; sometimes PC boots to a "Minimal GRUB", where I need to type "exit" and press enter... then it goes to normal grub menu. What gives?

---

### Post by oldfred on 2023-04-25
Did you install in UEFI boot mode?
IS then default boot mode in UEFI settings BIOS, not UEFI? Or some other setting?
Review UEFI settings.

---

### Post by jacek.gajek on 2023-04-28
Yes it's UEFI.

---

### Post by jacek.gajek on 2023-08-07
Just to finish the topic:

I was able to fix "Minimal Grub" menu by disabling fast boot in BIOS. I don't think it's much faster because the booting itself takes a bit more time, but it requires one interaction less (typing "exit" in the Minimal Grub console).

Disabling fast boot in Windows is necessary only if you want to access Windows drives from Linux.

---

