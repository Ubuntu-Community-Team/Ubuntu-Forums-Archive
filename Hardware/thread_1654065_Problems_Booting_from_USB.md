---
title: "Problems Booting from USB"
date: 2010-12-27
forum: Hardware
---

### Post by polandee on 2010-12-27
Ok so my computer has been suffering some problems lately, causing me to have to reinstall the OS fairly often. I decided to try to fix this by replacing the motherboard, and again reinstall the OS.
 
I put the 10.10 ISO file on a usb drive, and confirmed that it worked on a seperate computer. When I tryed it on my comp, a menu popped up but I couldn't use the keyboard (it worked during BIOS). After a couple of seconds it went past the menu and attempted to run Ubuntu from the flash drive, but it got stuck at the loading screen.
 
I don't much about hardware, so I don't know what part this kind of problem points to. Would the harddrive be involved at all in booting from the USB? Or does this sound like a problem with the processor?
 
Thanks.

---

### Post by oldfred on 2010-12-27
If you installed a new motherboard you may have some BIOS settings that make a difference. I had the same issue a couple of years ago and had to go into BIOS and allow USB keyboard & mouse. Mine only defaulted to the ps/2 ports for keyboard and mouse.

There are other BIOS settings that may make a difference. I have copied comments from many, see if any apply:

Some issues on booting install:
BIOS settings need USB mouse & keyboard
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility 
BIOS should be set for IDE compatibility mode
So then I tried disabling "IDE DMA Transfer Access" which had no explanation in the BIOS as to what it did. Restarted the computer and Ubuntu booted up no problem. According to the motherboard manual "This item is used to enable or disable the DMA transfer function of the IDE hard drive."
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
BIOS setting, Keyboard response in grub really slow

---

### Post by polandee on 2010-12-27
Changing the BIOS settings got the keyboard working, but it still gets stuck on the loading screen. I looked through all the options on the menu and couldn't find anything useful. Is there anything I can do besides trying an older version of Ubuntu?

---

### Post by Fafler on 2010-12-27
Now you got the keyboard working, try this. Edit the kernel options from the boot menu, there should be onscreen directions on how to do that. Remove the words "quiet splash" and boot. This should make it boot in textmode without the splash screen and allow you too see whats wrong. Also, what board did you buy?

---

### Post by oldfred on 2010-12-27
Also what video card. 

I had to add nomodeset in place of the quiet spash on a boot and use f6 on CD boot to add nomodeset as a parameter.

---

### Post by polandee on 2010-12-27
The board's a Gigabyte GA-G41M-ES2L. 
 
I couldn't find kernel options, but the boot menu help showed some options I could type in at the prompt. "Cli" was supposed to be the text-based install but it gave me the error, "Could not find kernel image: cli". Other options I tried were install, expert, and memtest. Out of those the only one that worked was memtest, the other gave similar errors.
 
The video card is native.
 
Edit: If I press escape while on the loading screen I get a screen showing this message repeated over and over.
 
-----------------------------------------
stdin: error 0
/init: can't open /dev/sr0: No medium found
/init: can't open /dev/sr0: No medium found
Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin Running /scripts/casper-premount ... done.
done.
Killed
-------------------
 
The final line on the  screen, after that block has looped over and over is:
 
unable to open 'dva/sda'

---

### Post by oldfred on 2010-12-28
If you have verified that the ISO is correct.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

There have been some issues with USBs.

syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
Install Ubuntu Server.Work around the CD-ROM detection issue
[http://www.revouser.com/forum/viewtopic.php?f=7&t=794](http://www.revouser.com/forum/viewtopic.php?f=7&t=794)

---

### Post by polandee on 2010-12-28
The USB stick itself worked on a separate computer. I never figured out the problem, but the 10.04 ISO worked fine. Thanks everybody.

---

