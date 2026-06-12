---
title: "BIOS Freezes, Motherboard Failure? Dell Dimension E521"
date: 2010-09-23
forum: Hardware
---

### Post by lbrty on 2010-09-23
My friend is having trouble with his Dell Dimension E521 desktop. He asked me if I could reinstall Windows XP MCE (Media Center Edition) 2005 and install Ubuntu along side Windows.  
 
 When I initially booted the machine, it displayed the Dell logo, then the Phoenix BIOS screen with the following errors: 'Diskette drive 0 seek failure' and 'Keyboard Failure'. And at the very bottom 'Press F1 to continue, F2 to enter setup'. So I pressed F1 to continue. Nothing happened -- the screen turned black (no OS loaded, etc).  
 
 I did a hard reboot and the same info posted as stated above but this time I pressed F1 to enter setup. After pressing F1 it brings me to the BIOS menu but it immediately freezes. It does not allow navigation or any other action (must do a hard reboot). 

I turned off the machine and test the Dell USB keyboard on my laptop and it works fine. I then detach all cables to the tower and remove the casing. Once I remove the casing, I removed CMOS battery and check all the cables to make sure nothing is loose. I waited 5 minutes and placed the CMOS battery back in the motherboard, plug in the keyboard and the power cable. I then boot the machine and do the same procedure as above with the same results. 
 
I turned off the machine and replace the CMOS battery with a brand new battery to see if that would make a difference and it did not. BIOS still reports the same errors and freezes once entering BIOS setup.

I disconnected everything as stated above again but now I remove the RAM and hard drive. I tested the hard drive with a USB to SATA/IDE adapter to my laptop and it works fine. I copy the personal data and place the hard drive and RAM back in the machine. I then boot the machine and same results occur again.

I now only remove the NVIDIA video card and use the on-board/integrated video and the same results occur.
 
 I replace the SATA cable from the hard drive to motherboard with a new SATA cable and check the power supply and the power supply connectors to ensure that each connector is providing power to the hard drive and optical hard drives (power supply works).
 
 I disconnected all non-essential hardware but left one optical drive (DVD) attached and the SATA hard drive attached and booted the machine with the Windows XP MCE 2005 OS disc and received this message:
 NO BOOT DEVICE DETECTED, INSERT SYSTEM DISK AND PRESS F1 TO CONTINUE OR PRESS F2 TO SETUP MENU
 
I disconnected the SATA cable from the optical drive to motherboard and attached the USB to SATA/IDE cable to the SATA optical drive and inserted the USB end (of the USB to SATA/IDE adapter) to back of the tower to USB slots but left the power connector intact (to give the optical drive power). I then booted the machine again with Windows XP MCE 2005 OS disc in the optical drive and I received this message:
 BOOTMGR is missing
 
 I removed the Windows XP MCE 2005 OS disc and inserted Ubuntu 10.04.1 OS disc and booted the machine. Something finally worked! Ubuntu takes about 1 minute to load into live desktop environment and once it does I begin installing Ubuntu (typical install with all the usual prompts, questions, etc). It prompts me stating it successfully installed Ubuntu and I restart the machine. The optical drive automatically ejects the disc before rebooting. After the machine reboots, I receive the following message:  
 NO BOOT DEVICE DETECTED, INSERT SYSTEM DISK AND PRESS F1 TO CONTINUE OR PRESS F2 TO SETUP MENU
 
 I researched the Dell desktop model on the internet and it seems that some others have success with updating BIOS from a Windows environment, however I cannot get to the Windows desktop environment or reinstall the OS. The desktop is out of warranty.
 
 Copied the hardware configuration from dell.com
 Dell Dimension E521
 Card, NVIDIA Graphics, 128MB
 Dual In-line Memory Module 512MB 
 Compact Disk Read Write/digital Video Disk DriveCombo, 48, Sony, Serial Ata, Black 
 Processor, AMD X2, 3800, 2.0, 512K, 2.5" FORM FACTOR... 
 Hard Drive, 160GB, S2, 7.2K, 8M Lead Free, Samsung 
 Digital Video Disk Drive, 16X, Serial Ata, Half Height, Philips, Black 
 Modem, V.92, Data Fax, Internal SON4, Lead Free, Dell Americas Organization
 
 I believe that the BIOS is either corrupt/damaged and/or the motherboard is bad. I found the motherboard on ebay.com for $65 with shipping included.
 
 Thank you for reading this long thread and any help/suggestions would be greatly appreciated.

---

### Post by PRC09 on 2010-09-23
If you go to the dell download website (attached link) the original bios release is available for use in a dos environment with a bootable floppy.Maybe try that and if you can boot windows then update to the latest bios.....




[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R133985&SystemID=DIM_P4_E521&servicetag=&os=WW1&osl=en&deviceid=308&devlib=0&typecnt=0&vercnt=5&catid=-1&impid=-1&formatcnt=0&libid=1&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=178463#3DOS](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R133985&SystemID=DIM_P4_E521&servicetag=&os=WW1&osl=en&deviceid=308&devlib=0&typecnt=0&vercnt=5&catid=-1&impid=-1&formatcnt=0&libid=1&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=178463#3DOS)

---

### Post by lbrty on 2010-09-25
Thanks for reply.

I looked into doing that prior to posting here, however all I could find on dell.com was the .exe file without the instructions that dell.com (universal BIOS) gives in regards to booting with a floppy with an .exe file. How do I make a bootable DOS diskette? The desktop does not have a floppy drive and I do not have USB floppy drive. Is there a way to flash BIOS with a USB flash drive and somehow convert/extract an .exe file and make it bootable? Please let me know. :)

From dell.com
> Run the BIOS update utility from DOS environment (Non-Windows users)
NOTE: You will need to provide a bootable DOS diskette. This executable file does not create the DOS system files.
1. Copy the file DME521-010000.EXE to a bootable floppy.
2. Boot from the floppy to the DOS prompt.
3. Run the file by typing Y:\DME521-010000.EXE (where y is the drive letter where the executable is located).

---

### Post by PRC09 on 2010-09-26
I have never tried to do this but here are some links for you......

[http://www.bootdisk.com/pendrive.htm](http://www.bootdisk.com/pendrive.htm)


And the boot disks are here...

[http://www.bootdisk.com/](http://www.bootdisk.com/)

---

### Post by lbrty on 2010-09-26
Thanks again for the info! I used Method 8 (UNetbootin). The machine recognized and booted from the flash drive, however during the Loading period for flashing BIOS it would hang (not freeze just hang). Thanks again for all your help. I will recommend that he just buy a new motherboard.

---

