---
title: "attempt to boot from USB flash drive failed"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by THinDC on 2009-10-30
[FONT=Arial][SIZE=2]I am trying to boot a windows machine using a USB flash drive, but have been unable to do so.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]I am a complete novice interested in running Ubuntu off of a 4 GB flash drive plugged into my Dell Latitude D630 USB drive. To accomplish this, I did the following (I have questions about each step, but bottom line, I just want to figure out what to do so that I can boot off of the USB drive):[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]**1) I downloaded ubuntu-9.04-desktop-i386.iso onto my Windows machine from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)**[/SIZE][/FONT]

[FONT=Arial][SIZE=2]My understanding is that this is the correct version (9.04, desktop) for a PC like mine.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Questions: did I download the correct version? Was there some sort of check I should have run after the download to confirm there were no errors in the downloading process?[/SIZE][/FONT]
 
**2) following the instructions at **[**https://help.ubuntu.com/community/Installation/FromUSBStick**]("https://help.ubuntu.com/community/Installation/FromUSBStick")**, I ran UNetbootin with the iso file on my windows machine as the image and the USB drive as the target.**
 
[FONT=Arial][SIZE=2]various files were copied to the drive. "So far, so good," I thought.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]**3) I rebooted my Windows machine, then pressed F12 and entered the BIOS menu. I selected the USB drive as the drive from which to boot. I then continued the start up process.**[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]At this point, my expectation was that I should see a DOS-esque screen for me to select a languge. But that never happened ...[/SIZE][/FONT][FONT=Arial][SIZE=2]my screen just showed a blinking cursor in the top left for several minutes, I gave up and rebooted back to windows.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]**4) Ok, so then I read the page that I cited above and saw this:**[/SIZE][/FONT]
[INDENT][FONT=Arial][SIZE=2]"If you need to activate the original Ubuntu livecd boot menu, for example if you want to disable the framebuffer or read the Ubuntu livecd HELP screens and cheatcodes, please make these changes to your USB drive after your UNetbootin installation is completed: [/SIZE][/FONT]
 
[SIZE=2][FONT=Arial]1) Delete the SYSLINUX.CFG file or rename it to be SYSLINUX.OLD [/FONT][/SIZE]
[SIZE=2][FONT=Arial]2) Enter the ISOLINUX folder and rename the ISOLINUX.CFG file to be SYSLINUX.CFG. You may or may not need to rename ISOLINUX.BIN to SYSLINUX.BIN, but it won't hurt. 3) Move up to the top level and rename the ISOLINUX folder to be SYSLINUX [/FONT][/SIZE]
[/INDENT][FONT=Arial][SIZE=2]**5) ...so I made those changes, and re-attempted the reboot (i.e., Step 3 above)--but got the same result.**[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]**_Questions:_**[/SIZE][/FONT]
[INDENT][FONT=Arial][SIZE=2]1) um, what am I doing wrong?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]2) did I make a mistake in downloading the ISO files? should I have downloaded IMG (?) files instead?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]3) Do I need to reformat/add files to the USB drive using Make the USB flash drive bootable using SYSLINUX? (again, see [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) under the section "Creating bootable USB manually")[/SIZE][/FONT]
[/INDENT][FONT=Arial][SIZE=2]I am very eager to try ubuntu via a USB drive, so I am very disappointed at my failed attempt(s) thus far--yet eager to understand what to do to make this work. I would be grateful for any advice.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Thanks in advance for your help!![/SIZE][/FONT]

---

