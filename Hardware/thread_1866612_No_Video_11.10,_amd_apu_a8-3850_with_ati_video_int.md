---
title: "No Video 11.10, amd apu a8-3850 with ati video integrated"
date: 2011-10-21
forum: Hardware
---

### Post by efpc2003 on 2011-10-21
amd apu a8-3850 with ati video integrated.
 the same.... amd unsupported hardware on my led screen (on 11.04)
 ubuntu live cd amd64 11.10 doesn't launch live sesion, no desktop, just black screen, so... i will not upgrade to 11.10

---

### Post by german_ch90 on 2011-10-29
The same happens to me, but I tried using the live USB instead, same results.

---

### Post by metersales on 2012-01-08
I'm having the same problem with my new build.

AMD A8-3850 Llano 2.9GHz Socket FM1 100W Quad-Core Desktop APU with DirectX 11 Graphic AMD Radeon HD 6550D AD3850WNGXBOX

ASRock A75 PRO4 FM1 AMD A75 (Hudson D3) HDMI SATA 6Gb/s USB 3.0 ATX AMD Motherboard with UEFI BIOS

G.SKILL Ripjaws X Series 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Desktop Memory Model F3-12800CL9D-8GBXL

The Live USB gets to one of two screens depending on the boot option that I pick (UEFI Flash Drive or USB Flash Drive).  

UEFI Flash Drive gets me to the grub boot loader on the flash drive.  I can get to the command line and that is about it.  Selecting one of the three options listed gets me a curser on a black screen for a few seconds, and then the screen just turns off.  Typing, "e", or "c" take me to the different command prompts.

USB Flash Drive gets me the purple-ish screen with the, "computer = humanity" logo.  At this point it generally gives me the black screen with the curser for a few seconds, and then the screen just turns off.  Alternately, if I press the Ctrl button at just the right time, I get the list of languages to select from.  I choose, "English".  I then get the Ubuntu Logo followed by five options (try, install, check disk for defects, test memory, and boot from first hard disk).  the first four of these five options gets to the curser, followed by the monitor turning off.  

There is also a list of options across the bottom of the screen that are selected by typing F1-F6.  According to the Ubuntu troubleshooting guide for the live CD, selecting, "linux acpi=off" might help.  Doing this and attempting install still gets the curser, but stays at that stage and the monitor does NOT turn off.

At this point, I am considering doing an install on another system and transferring the hard disk.

I should mention that I have tried multiple flash drives and multiple ISO's and multiple source computers creating the startup drives (all ubuntu using the startup disk creator).

---

### Post by Antisocialworker on 2012-01-09
[QUOTE=metersales;11597308]I'm having the same problem with my new build.
  
At this point, I am considering doing an install on another system and transferring the hard disk.

This will work however it will not solve your problem. If you have a second monitor (so far it has only worked with hdmi though i have yet to try dvi) and you should get video feed. I assume the problem has something to do with plymouth (Understand my knowledge of this is limited to the name and that it has something to do with graphics). Potentially reinstalling plymouth, Xorg might fix the problem.

---

### Post by metersales on 2012-01-11
I have not come to a solution yet, but I feel that I am much closer to one.  The problem with the LiveCD/USB seems to be with the UEFI BIOS I have.  I have done a lot of searching, and found some good information in this thread.
[http://ubuntuforums.org/showthread.php?t=1901748&highlight=uefi]("http://ubuntuforums.org/showthread.php?t=1901748&highlight=uefi")

So far, these are the things that have helped:
[LIST]
[*]Boot using a Live CD and NOT a Live USB
[*]Partition the Disk drive beforehand on another computer with a FAT16 EFI partition (approx 200MB) first, and then your preferred partitioning configuration
[*]Select to boot from UEFI CD and not ATAPI CD
[*]Edit the, "Install Ubuntu" GRUB otpion and change, "--", to  "nomodeset --"
[*]Install Ubuntu to the Partition you set aside beforehand (you may need to assign the mount points)
[/LIST]

So far, this gets me through the install, but then upon reboot the system says that the disk is not bootable. :(

---

### Post by metersales on 2012-01-12
Well I feel quite silly. :lolflag:

Turns out that the HDMI is apparently set as the default display port with the VGA being some sort of secondary display.  During bootup, apparently all three displays had the same signal, but then once in the installer, the VGA monitor was being assigned as a secondary display or being otherwise deactivated.  My UEFI BIOS has a selection for the DVI port to be the same as the HDMI or a secondary display.  I had to borrow another monitor as mine only had VGA input.

Also turns out that the standard install works just fine.  I didn't even need to boot to the UEFI GRUB installer.  I don't know about the other people on this thread, but my problem is solved.  

Try your other video outputs if you are having similar symptoms.

---

