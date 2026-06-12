---
title: "No EFI boot on Dell Inspiron One 2330"
date: 2012-11-21
forum: Hardware
---

### Post by cboling on 2012-11-21
I just bought this machine, and found that Quantal Quetzal seems to run fine on it -- as long as I configure the machine for "Legacy Boot Mode" (thus not allowing me to access Dell's Windows 8 installation).

Note that you actually have to be in full legacy mode (No EFI allowed); if you specify a legacy boot while in UEFI mode, you're told that there are no boot devices available.   Manually specifying a UEFI boot when in Legacy mode fails the same as when in "pure" UEFI mode (described below).

The behavior when attempting to boot via UEFI is the same whether booting from the DVD, USB, or hard drive:

GRUB comes up fine, but upon choosing any of the Linux options (Windows still loads fine), it goes to a blank screen with the same color as the menu background (black or purple, depending on whether you boot from removable or fixed drives), and hangs. When booting from a USB stick I can see about 3 seconds of additional activity (blinking R/W light) after the menu text disappears, but then no further sign of life.  Ctrl-Alt-Del does nothing.  Pressing the power button immediately turns the machine off.

Initially, I thought it was maybe only a problem when booting from removable media, so I used legacy mode to install to the hard drive, after shrinking the Windows partition to make room.  I installed GRUB to the Linux root partition, then used Boot-Repair to help me convert it to an EFI install.  I had to manually copy the EFI loader file to the appropriate directory/name (BOOT/BOOTx64.EFI) on the EFI partition, then the machine booted to GRUB fine.  As I said above, I can load Windows via GRUB, but anything involving the Linux kernel is dead.

Ideas?

---

### Post by oldfred on 2012-11-21
Did you install the 64 bit version of 12.10? That is the only one that supports secure boot with UEFI. The 12.04 will work with UEFI on non-secure boot systems and will get the new grub2 2.00 with the next point release to boot with secure boot systems.

Boot-Repair will automatically convert a BIOS install to UEFI install. You also need to edit fstab which Boot-Repair does when you uninstall grub-pc and install grub-efi.

       Post the link to the BootInfo report that this creates.

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by cboling on 2012-11-21
> **oldfred said:**
> Did you install the 64 bit version of 12.10?

Yes.

Here's the latest Boot-Repair report:
[http://paste.ubuntu.com/1375656/](http://paste.ubuntu.com/1375656/)

On the hard drive (sda), /EFI/Boot/bootx64.efi was, IIRC, originally a copy of /EFI/Microsoft/Boot/bootmgfw.efi.bkp (or, it was at least the same size & date of it -- I didn't run a checksum); I replaced it with /EFI/ubuntu/grubx64.efi, since I could find no way in the BIOS setup to tell it to boot from a different file.  On the flash drive (made from LiveCD iso), I didn't tamper with anything.

---

### Post by YannBuntu on 2012-11-21
Hello

> **cboling said:**
> /EFI/Boot/bootx64.efi was, IIRC, originally a copy of /EFI/Microsoft/Boot/bootmgfw.efi.bkp

I confirm. The presence of a *.efi.bkp file means that the corresponding *.efi file is a copy of /ubuntu/grubx64.efi file created by Boot-Repair, in order to workaround BIOS (like yours) which don't allow to boot the standard /ubuntu/grubx64.efi 

> **cboling said:**
> I replaced it with /EFI/ubuntu/grubx64.efi, since I could find no way in the BIOS setup to tell it to boot from a different file.

Thanks for the feedback, i'll modify Boot-Repair to take such case into account.

> **cboling said:**
> GRUB comes up fine, but upon choosing any of the Linux options (Windows still loads fine), it goes to a blank screen with the same color as the menu background (black or purple, depending on whether you boot from removable or fixed drives), and hangs.

This is a kernel (or graphic driver) problem. So don't change your BIOS settings any more, and let's try adding some kernel options:
run Boot-Repair --> Advanced options --> GRUB options tab --> tick "Add kernel option: nomodeset" --> Apply
Tell us the new URL that will appear.
Reboot the pc and tell us what you observe.

---

### Post by cboling on 2012-11-21
> **YannBuntu said:**
> This is a kernel (or graphic driver) problem. So don't change your BIOS settings any more, and let's try adding some kernel options:
run Boot-Repair --> Advanced options --> GRUB options tab --> tick "Add kernel option: nomodeset
I actually tried nomodeset on the LiveCD, but it made no difference.
Not that I really expected it to; since it works just fine when not booting from UEFI, I figured that it was not related to video modes.

---

### Post by YannBuntu on 2012-11-21
> **cboling said:**
> since it works just fine when not booting from UEFI

sorry, i missed that part in your 1st post.
Then i have no clue... the issue may be related to Secure Boot, have you tried to disable it? ( [https://help.ubuntu.com/community/UEFI#Enabling_.2BAC8_disabling_Secure_Boot](https://help.ubuntu.com/community/UEFI#Enabling_.2BAC8_disabling_Secure_Boot) )

---

### Post by cboling on 2012-11-21
> **YannBuntu said:**
> the issue may be related to Secure Boot, have you tried to disable it?Yes, no difference. (Sorry. Let's see, how many more things did I try that I forgot to mention?)

---

### Post by YannBuntu on 2012-11-22
Please create a bug report here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug](https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug)
and tell us the link so that we can follow-up.

---

### Post by cboling on 2012-11-22
Now filed as [Bug #1082218]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1082218").

---

### Post by YannBuntu on 2012-11-22
Thanks.
There is a "SecureBoot" option in Boot-Repair, you can try it by:
1) enabling SecureBoot in your BIOS
2) run Boot-Repair --> Advanced options --> GRUB options tab --> tick the "SecureBoot" option --> Apply
3) tell me the new URL that will appear
4) reboot the pc and tell me what you observe

---

### Post by cboling on 2012-11-23
> **YannBuntu said:**
> There is a "SecureBoot" option in Boot-Repair
Do you know offhand what version(s) that appears in?  I can't find such an option in either v3.194, which is, I believe the latest PPA version, or in whatever version came on last month's Boot-Repair LiveCD image.

Note that I'm assuming that, like the other EFI options, the SecureBoot option appears if it detects an EFI disk partition, regardless of what your BIOS settings may be.  (I only have one machine at my present location that features SecureBoot, so I can't test that assumption.)

---

### Post by YannBuntu on 2012-11-23
From version 3.195 .
See PPA packages: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)

---

### Post by cboling on 2012-11-24
That's odd -- I installed the Debian package, and it said it upgraded to 195, but I still don't see the option.

---

### Post by YannBuntu on 2012-11-24
> **cboling said:**
> That's odd -- I installed the Debian package, and it said it upgraded to 195, but I still don't see the option.

The option only appears on UEFI systems. Please update Boot-Repair, then run Boot-Repair --> Create BootInfo , and indicate the URL that will appear.

---

### Post by cboling on 2012-11-24
Here ya go! 
[http://paste.ubuntu.com/1384377/]("http://paste.ubuntu.com/1384377/")

---

### Post by YannBuntu on 2012-11-25
> **cboling said:**
> Here ya go! 
[http://paste.ubuntu.com/1384377/]("http://paste.ubuntu.com/1384377/")

ok, your system is UEFI, but you don't see the option because you only updated the boot-repair package. You need to also update the **boot-sav** package.

---

### Post by cboling on 2012-11-26
I installed nice fresh (3.195~ppa7) copies of boot-repair, boot-sav, and boot-sav-extra, and ran boot-repair.  I copied EFI/ubuntu/shimx64.efi to EFI/Boot/bootx64.efi, and booted in secure UEFI mode.  Oops!  no bootable hard drive anymore.

Looks like there was a problem -- "source_dir doesn't exist" -- setting up grub-ef-amd64.

[_HERE_]("http://paste.ubuntu.com/1389851/") is the boot-repair output.
[_HERE_]("http://paste.ubuntu.com/1389899/") is a record of the install showing the error mentioned above.

---

### Post by YannBuntu on 2012-11-26
> **cboling said:**
> I installed nice fresh (3.195~ppa7) copies of boot-repair, boot-sav, and boot-sav-extra, and ran boot-repair.

ok

> **cboling said:**
> I copied EFI/ubuntu/shimx64.efi to EFI/Boot/bootx64.efi, and booted in secure UEFI mode.  Oops!  no bootable hard drive anymore.

have you made a backup of the EFI/Boot/bootx64.efi before this?


> **cboling said:**
> [_HERE_]("http://paste.ubuntu.com/1389851/") is the boot-repair output.
[_HERE_]("http://paste.ubuntu.com/1389899/") is a record of the install showing the error mentioned above.


1. Your firmware (~BIOS) currently boots your Ubuntu liveCD in Legacy (not UEFI) mode. Please setup it in UEFI mode.
2. then update Boot-Repair, run the Recommended Repair, and indicate the new URL that will appear.

---

### Post by cboling on 2012-11-26
> **YannBuntu said:**
> have you made a backup of the EFI/Boot/bootx64.efi before this?No; I assume it was still the previously-generated one I'd copied from the Ubuntu, so if I needed to I could generate it again at some point.  I'm not horrified that it didn't boot, just noting it for info.

> **YannBuntu said:**
> 1. Your firmware (~BIOS) currently boots your Ubuntu liveCD in Legacy (not UEFI) mode.
Right -- necessary because this machine won't load Linux in UEFI mode.  The reported behavior (Grub loads, but trying to start a Linux kernel leaves you hanging on a blank screen) is the same whether you boot the hard drive or the DVD.  

So, lest we get distracted by our wanderings in this thread since the initial post, let me reiterate: The original problem has nothing to do with Boot-Repair -- the LiveCD has the same issue on this machine.  The only reason poor ol' Boot-Repair got drug into the discussion was that I used it [unsuccessfully] to try to make my installed-via-legacy-mode  Ubuntu installation UEFI-bootable.

---

### Post by oldfred on 2012-11-26
It sounds like you are booting, but the issue is a driver issue probably video, but occasionally something else that then prevents the video from loading.

What video chip does you system have?

---

### Post by YannBuntu on 2012-11-26
I agree. Maybe the nomodeset option could help...
 have you tried the Ubuntu Recovery option ?

(Memo for me)
- your firmware is setup to boot the liveCD in Legacy mode, but the HDD in UEFI mode
- GRUB appears and allows to boot Windows fine.
- "Ubuntu boots fine in Legacy mode" but there is no GRUB in MBR

---

### Post by cboling on 2012-11-26
> **oldfred said:**
> the issue is a driver issue probably video:confused: I would be suprised to learn that it ran different video based on booting via MBR vs. EFI.  (Remember, it boots and runs fine in Legacy Mode.)
> **oldfred said:**
> What video chip does you system have? Oh, let's see, Intel HD something-or-other.  Google rumors suggest B75.
lspci reports 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)".
Ubuntu GUI "system details" simply reports "Intel Sandybridge".
lsmod shows an i915 driver.

---

### Post by YannBuntu on 2012-11-26
> **cboling said:**
> (Remember, it boots and runs fine in Legacy Mode.)

There is no GRUB in your MBR and no BIOS-Boot partition, so AFAIK Ubuntu cannot boot in Legacy mode. Maybe you setup something in Legacy mode in your BIOS, but when it tries to boot on your MBR it fails then automatically switches to UEFI mode?

Just to be sure, what do you mean exactly by "in Legacy mode"?
is it when you setup your BIOS to boot the CD in Legacy mode? or is it when you setup your BIOS to boot the HDD in Legacy mode?
can you provide pictures of your BIOS please?

---

### Post by cboling on 2012-11-26
> **YannBuntu said:**
> Maybe the nomodeset option could help...I tried it early on, and it didn't.

> **YannBuntu said:**
> have you tried the Ubuntu Recovery option ?That phrase looks familiar, but I don't see it in the LiveCD options.  Can you tell me more about it?

In EFI mode, GRUB has:Install, test, OEM, and check for defects, all of which appear to instantly die.  MemTest isn't listed in EFI mode (perhaps because it's 32-bit only) so I can't try that one.

---

### Post by cboling on 2012-11-26
> **YannBuntu said:**
> There is no GRUB in your MBR and no BIOS-Boot partitionSorry for the confusion.  When I say "boots and runs fine in legacy mode", I'm referring to the LiveCD.  I have not attempted to configure the hard drive for a BIOS boot.

> **YannBuntu said:**
> what do you mean exactly by "in Legacy mode"?Good approach: some clarification is indeed in order.  I've got references to this scattered through the previous 3 pages, but there's nothing that shoes the "big picture" of the setup/boot options on this machine.  I will post another reply shortly (with pictures) that should improve this situation a little.

---

### Post by cboling on 2012-11-26
I just created [_this page_]("http://ebs.boling.us/2012-InspironOne2330-BootOpts/") that documents the boot mode configuration on this machine.

---

### Post by oldfred on 2012-11-27
From the UEFI menu that only gives a black screen, using e remove quiet splash from linux line. Does that show it booting? Normally you should see each driver & process starting by time stamp. 

Nice set of photos of UEFI menus.

---

### Post by cboling on 2012-11-27
> **oldfred said:**
> remove quiet splash from linux line. Does that show it booting?No. (I had the same thought eariler, but no joy!) It seems to be halting before that point.  Even on the "fancy" modes, I never see any sign of video mode changes or anything -- the menu text disappears as if the screen were cleared but no mode change, and the display stays rock-solid from that point on.   (Oh, for a serial debugging port!)

---

### Post by YannBuntu on 2012-11-27
> **cboling said:**
> I just created [_this page_]("http://ebs.boling.us/2012-InspironOne2330-BootOpts/") that documents the boot mode configuration on this machine.

Thanks! this makes things much clearer.

Please:
1) remove your CD/DVD/USB devices.

2) In the "Legacy" screen (screenshot below), please select "LEGACY BOOT: Hard Disk :ST5000M002", and press Enter. Does this load Ubuntu? if yes, please install and run Boot-Repair from this installed Ubuntu, click "Create BootInfo" and indicate the URL that will appear.  (goal: checking if Legacy/UEFI mode, and if live/installed session)

3) Then in the "Legacy" screen (screenshot below), please select "UEFI BOOT: UEFI ST5000M002", and press Enter. Does this load Ubuntu? if yes, please install and run Boot-Repair from this installed Ubuntu, click "Create BootInfo" and indicate the URL that will appear.

[[img]http://pix.toile-libre.org/upload/img/1354005224.jpg[/img]](http://pix.toile-libre.org/?img=1354005224.jpg)

4) In the "UEFI Mode (Non-secure) [Screenshot missing]" screen, please select "LEGACY BOOT: Hard Disk :ST5000M002", and press Enter. Does this load Ubuntu? if yes, please install and run Boot-Repair from this installed Ubuntu, click "Create BootInfo" and indicate the URL that will appear.

5) In the "UEFI Mode (Non-secure) [Screenshot missing]" screen, please select "UEFI BOOT: UEFI ST5000M002", and press Enter. Does this load Ubuntu? if yes, please install and run Boot-Repair from this installed Ubuntu, click "Create BootInfo" and indicate the URL that will appear.

6) In the "UEFI Mode (Secure)" screen (screenshot below), please select "UEFI BOOT: UEFI ST5000M002", and press Enter. Does this load Ubuntu? if yes, please install and run Boot-Repair from this installed Ubuntu, click "Create BootInfo" and indicate the URL that will appear.

[[img]http://pix.toile-libre.org/upload/img/1354006347.jpg[/img]](http://pix.toile-libre.org/?img=1354006347.jpg)

---

### Post by oldfred on 2012-11-27
A lot of systems have a setting somewhere in UEFI/BIOS called quick boot or fast boot. Make sure that is turned off.
I did not see it in the screens you showed, but you have several others in UEFI menu.

---

### Post by cboling on 2012-11-28
Yannbuntu:
> 2) "Legacy" screen - "LEGACY BOOT: Hard Disk :ST5000M002"
This has never worked, BECAUSE when I installed Ubuntu in Legacy mode (and when playing w/ boot-repair afterwards), I was careful NOT to allow it to install GRUB to the MBR, since I wasn't certain that it wouldn't mess up UEFI booting and make Windows and Dell's utilities inaccessible.

What DOES work from this mode (and this mode only) is legacy-booting the LiveCD (disc or USB).

> 4) "UEFI Mode (Non-secure)" screen - "LEGACY BOOT: Hard Disk :ST5000M002"
Trying to legacy boot anything* from UEFI on this machine always fails to find anything bootable.

*I've only tried the Ubuntu LiveCD media and a couple of other older Linux LiveCDs.  The hard drive doesn't work either, but that's expected because of consciously NOT setting up MBR boot, as mentioned above in (2).

> 3) "Legacy" screen - "UEFI BOOT: UEFI ST5000M002"
5) "UEFI Mode (Non-secure)" screen - "UEFI BOOT: UEFI ST5000M002"
6) "UEFI Mode (Non-secure)" screen - "UEFI BOOT: UEFI ST5000M002"

All 3 of these have behaved the same so far:

**AFTER upgrading Boot-repair & trying out its new Secure Boot option:**
Fails to find anything to boot on the hard drive.

**BEFORE upgrading Boot-repair, or, now, after the upgrade but using ubuntu/bootx64.efi in Boot/ instead of shimx64.efi:**
All 3 load UEFI GRUB; all 3 die after selecting any Linux option (I can still boot Windows 8 through GRUB in any of the 3 modes).

**NOW...**
For testing & temporary use, I was originally hoping to use Boot-Repair to add an option to the USB LiveCD to allow it to transfer control to the Linux partition on the hard drive, but Boot-Repair doesn't appear to have that option; the USB drive may only boot a partition on the USB drive.  My GRUB/LILO skills have rotted for a decade, so I was lost as to how to manually add such an option to the menu, or even to type in a temporary paragraph to boot sda8 once I got into USB's GRUB.

Should I try to install GRUB to the MBR on the hard drive?  I'm new to EFI, but I seem to remember that you can have a hybrid GPT/MBR that can support both modes, but I wasn't sure if Boot-Repair would do that or if it would wipe out something such that I'd never be able to boot Windows again or what.  I suppose that since the bulk of the stuff for EFI booting is in sda1 that even were I to completely wipe out the MBR including partition tables, I would have some chance of running a utility to find the partitions and rescue the drive...

> **oldfred said:**
> quick boot or fast boot I poked around everywhere in there as soon as I turned the machine on, and I didn't see anything like that.  This machine lacks quite a few "classic" CMOS Setup options.

---

### Post by oldfred on 2012-11-28
If Windows 8 boots from grub menu that is saying you are booting thru grub and the issue is with drivers after grub efi has worked. Often then kernel parameters are required for some systems.

From the grub menu can you use e and delete splash quiet, or use advanced options and boot in recovery mode?

---

### Post by cboling on 2012-11-28
> **oldfred said:**
> If Windows 8 boots from grub menu that is saying you are booting thru grubYes, indeed.> and the issue is with *drivers* after grub efi has worked.Yes, though I think I personally prefer the more generic term "*code*" since we know so little about exactly where the problem is at tha point. I don't think it's getting very far into loading of the kernel.  There is absolutely no text output before it dies.

> From the grub menu can you use e and delete splash quiet,Nope, no good.> or use advanced options and boot in recovery mode?No.  I'm sure I haven't tried all possible parameters, but I have yet to find anything that makes any sense that makes any difference at all.  Any suggestions? (other than deleting spalsh/quiet) -- anything to make more verbose logging at the very beginning, or any idea how else to get a clue as to how far it's actually getting?  (I'm picturing a device that goes in front of the actual hard drive to log what sectors are read...sign of a desperate mind)

---

### Post by oldfred on 2012-11-28
Post a picture of your grub menu. OR are you only booting Windows from the UEFI menu? From UEFI are you choosing ubuntu?

You should be able to choose the second menu item or recovery mode.

Do you have a launch UEFI shell menu item?

If you do not have a shell menu you can add one Info & links:
       Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by cboling on 2012-11-29
I'm booting Windows through GRUB. (As far as I have been able to tell, this machine has no UEFI menu -- it always boots sda1:/EFI/Boot/bootx64.efi with no way to change it.)

Menu title/contents:
[INDENT]GNU GRUB  version 2.00-7ubuntu11[LIST][*]Ubuntu
[*]Advanced Options for Ubuntu
[*]Windows UEFI loader
[*]Windows Boot UEFI bootx64.efi
[/LIST]
[/INDENT]

I lied when I said earlier that Advanced Options got me nothing -- I was mis-remembering when I'd tried it earlier.  Recovery Mode *does* give additional intelligence before it dies.
Both options:[LIST][*]Ubuntu, with Linux 3.5.0-18-generic
[*]Ubuntu, with Linux 3.5.0-18-generic (recovery mode)
[/LIST]display:
[INDENT]Loading Linux 3.5.0-18-generic ...
Loading initial ramdisk ...[/INDENT]
Sorry, I shall be more careful in my assertions.

---

### Post by YannBuntu on 2012-11-29
Just to be sure:
- currently, you cannot boot your installed Ubuntu at all?
- the only way you can access an Ubuntu session is to boot the LiveCD (disc or USB) in Legacy mode, which means that before accessing Ubuntu you always see the "Try Ubuntu" menu below?

[IMG]http://pix.toile-libre.org/upload/original/1354179916.png[/IMG]

or

[IMG]http://pix.toile-libre.org/upload/original/1354180067.png[/IMG]

?

---

### Post by oldfred on 2012-11-29
If you have grub menu you should be able to press e on Linux entry and see your boot stanza. Then on linux line remove quiet splash and/or add other boot options which in your case are probably required to get past the problem.

---

### Post by cboling on 2012-11-29
> **YannBuntu said:**
> Just to be sure:
- currently, you cannot boot your installed Ubuntu at all?
- the only way you can access an Ubuntu session is to boot the LiveCD (disc or USB) in Legacy mode, which means that before accessing Ubuntu you always see the "Try Ubuntu" menu below?
**Correct!** -- though with the additional note that I haven't *seriously* tried to boot the hard drive in Legacy mode, i.e. I didn't install GRUB to the MBR (for fear that it would mess up EFI booting).  I'm pretty sure that it would work, since it does for the LiveCD, but I've focused on trying to find the problem with the UEFI boot.

> **oldfred said:**
> If you have grub menu you should be able to press e on Linux entry and see your boot stanza. Then on linux line remove quiet splashwhich is the very first thing I did when I saw it freeze for the first time.  "Recovery mode" also does away with those two options.


_**COMPARISON OF GRUB MENU'S BOOT OPTIONS**_

I'll call them:[LIST][*]Ubuntu
[*]Advanced
[*]Recovery[/LIST](the last two being under the "advanced options" submenu)

**Advanced** is the same as the default **Ubuntu** except for the addition of informational displays ("echo") before the two commands that actually do the deed:
[INDENT]*echo	'Loading Linux 3.5.0-17-generic ...'*
linux	/boot/vmlinuz-3.5.0-17-generic root=UUID=9b6d6c36-e799-4071-97a9-6a79e0b957a2 ro   quiet splash $vt_handoff
*echo	'Loading initial ramdisk ...'*
initrd	/boot/initrd.img-3.5.0-17-generic
[/INDENT]
**Recovery** differs from **Advanced** only in the parameters:
[INDENT]Advanced:[INDENT]linux	/boot/vmlinuz-3.5.0-17-generic root=UUID=9b6d6c36-e799-4071-97a9-6a79e0b957a2 ro   *quiet splash $vt_handoff*[/INDENT]
Recovery Mode:[INDENT]linux	/boot/vmlinuz-3.5.0-17-generic root=UUID=9b6d6c36-e799-4071-97a9-6a79e0b957a2 ro *recovery nomodeset*[/INDENT] 
[/INDENT]
So the parameters are pretty much mutually exclusive between these two options.

Reminder: full text of grub config @ [http://paste.ubuntu.com/1384377/]("http://paste.ubuntu.com/1384377/")

---

### Post by YannBuntu on 2012-11-29
> **cboling said:**
> I'm pretty sure that it would work, since it does for the LiveCD, but I've focused on trying to find the problem with the UEFI boot.

That's clever. This way, there will be no mistake: if you can boot the installed Ubuntu, it will be in UEFI mode for sure.


-both you want to boot the installed Ubuntu in UEFI mode, so you have to setup the installed Ubuntu in UEFI mode.
- Boot-Repair allows to setup your installed Ubuntu either in simple UEFI mode, or in UEFI+SecureBoot mode.

You wrote you can boot Windows via this menu:
```
    Ubuntu
    Advanced Options for Ubuntu
    Windows UEFI loader
    Windows Boot UEFI bootx64.efi

```

Do you see this menu when SecureBoot is **enabled** or **disabled** or **both** ?

---

### Post by cboling on 2012-11-29
> **YannBuntu said:**
> Do you see this menu when SecureBoot is **enabled** or **disabled** or **both** ?Both.  Neither GRUB nor Windows have a problem with either mode.

---

### Post by YannBuntu on 2012-11-29
ok.
Please setup your firmware to Legacy mode, then boot you Ubuntu liveCD, choose "Try Ubuntu", open a terminal and type:
```
sudo mount /dev/sda1 /mnt
```

then open a file browser, and make a backup of the /mnt/efi folder (eg to a USB key).

then type:
```
sudo rm -r /mnt/EFI/ubuntu
```

if you confirm that EFI/Boot/bootx64.efi is a copy of EFI/ubuntu/shimx64.efi, please also type:

```
sudo rm /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootmgfw.efi.bkp
```


Then run Boot-Repair --> Advanced options --> "GRUB location" tab --> **tick** "Separate /boot/efi partition: sda1" --> "GRUB options" tab --> **untick** "SecureBoot" --> **tick** "Purge GRUB and reinstall it" --> Apply   (don't change any other option)
Indicate the new URL that will appear.
Setup the firmware in **UEFI (non-Secure)** mode.
Reboot the pc, and indicate what you observe.

---

### Post by cboling on 2012-11-29
Okay, I created a datestamped backup of EFI, blew away the ubuntu dir, and cleared the Boot dir.  Verified the options & rebuilt.
Output: [http://paste.ubuntu.com/1398020/]("http://paste.ubuntu.com/1398020/")
Nice to see the files in EFI/Boot.

Rebooted, and...same as before.  (I allowed it to default, then after 2min of blank screen I rebooted and tried recovery mode, and am still staring at those same two lines printed by GRUB.)

---

### Post by YannBuntu on 2012-11-29
> **cboling said:**
> Okay, I created a datestamped backup of EFI

i saw it in sda1 in the log. By security, please also keep a backup on a USB key.

> **cboling said:**
> Rebooted, and...same as before.  (I allowed it to default, then after 2min of blank screen I rebooted and tried recovery mode, and am still staring at those same two lines printed by GRUB.)

ok. Then I am sorry i can't help much more.
Just to confirm: the GRUB menu appears and you can boot Windows from the "Windows UEFI loader" entry ?

---

### Post by cboling on 2012-11-29
> **YannBuntu said:**
> the GRUB menu appears and you can boot Windows from the "Windows UEFI loader" entry ?Correct.

---

### Post by YannBuntu on 2012-11-30
Now your GRUB and Ubuntu are setup in "UEFI not SecureBoot" mode.

1) please setup your firmware in "UEFI + SecureBoot" mode, and tell me if that changes something. (i guess the GRUB menu should not appear as it is not signed)

2) now let's do another test (setup your GRUB + Ubuntu in SecureBoot mode):
please **delete your /EFI/ubuntu/ folder**
then run Boot-Repair --> Advanced options --> "GRUB options" tab --> **tick** "SecureBoot" --> **tick** "Purge GRUB and reinstall it" --> Apply (don't change any other option)
Indicate the new URL that will appear.
Setup the firmware in UEFI **(Secure)** mode.
Reboot the pc, and indicate what you observe. 
Then setup the firmware in UEFI **(Non-Secure)** mode.
Reboot the pc, and indicate what you observe.

---

### Post by cboling on 2012-11-30
I'm heading out of town in a few minutes, but will try this as soon as I get back late Tuesday (UTC).  Thanks.

---

### Post by hgroover on 2012-12-01
This sounds very much like the (still unsolved) problem I'm having with my Asus Q500A with AMI / Aptio BIOS. Link: [http://ubuntuforums.org/showthread.php?p=12383132](http://ubuntuforums.org/showthread.php?p=12383132)

---

### Post by cboling on 2012-12-04
> **hgroover said:**
> This sounds very much like the...problem I'm havingIndeed it does.

> **YannBuntu said:**
> firmware in "UEFI + SecureBoot" mode...GRUB menu should not appear as it is not signedYes, the BIOS showed a nice red rejection message:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=228211&stc=1&d=1354644778[/IMG]

> **YannBuntu said:**
> GRUB + Ubuntu in SecureBoot mode):No pkg mgr errors this time ([_unlike the first time_]("http://ubuntuforums.org/showpost.php?p=12374267&postcount=17") I tried to tried Boot-Repair's new SecureBoot option), but the BIOS still returns:
[INDENT]No boot device available.
Strike the F1 key to retry boot, F2 to run the setup utility[/INDENT] as it did the 1st time I tried generating SecureBoot files, even though EFI/Boot/bootx64.efi is there.
(Incidentally, bootx64.efi and bootx64.efi.grb are both 1357480 bytes.)

_[Boot-Repair output]("http://paste.ubuntu.com/1410835")_
> **YannBuntu said:**
> firmware in UEFI **(Non-Secure)** mode.Same -- no boot device.

---

### Post by YannBuntu on 2012-12-04
ok. I have no more idea for UEFI at the moment, sorry.

Until we find another idea, you can install and use Ubuntu+Windows in Legacy mode  (first create a [BIOS-boot partition]("https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29"), then run Boot-Repair --> Adv options --> ""GRUB location" tab --> untick "Separate /boot/efi" --> Apply).

---

### Post by oldfred on 2012-12-04
Some UEFI have the shell, others do not but it can be added. 
Do you have a shell and does it give any useful info? 

       Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)


[       ]("http://software.intel.com/en-us/articles/efi-shells-and-scripting/")
 [https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)

---

### Post by mouling on 2012-12-19
Hi,

I bought this Dell Inspiron 2330 too, and I was highly interested in this thread. I wish here to report my own successfull experience on this machine, hoping it can be helpfull.

Like you, I wanted to keep the pre-installed Windows 8 and to have a dual win/ubuntu boot, and I managed to do so in UEFI mode with secure boot activated. 
I'll just give you an overview of my experience and mention what could explain, at first glance, why my installation went fine while yours didn't.

The first thing I have done with this computer after unpacking is upgrading it. It included, of course, windows and dell software, but also BIOS upgrade to version A09 (release date : 21 Nov. 2012) from the Dell website ([http://www.dell.com/support/drivers/fr/fr/frdhs1/Product/inspiron-one-23-2330-aio](http://www.dell.com/support/drivers/fr/fr/frdhs1/Product/inspiron-one-23-2330-aio) for my French installation). This might be a first important point.
After all this updating process, I ran the C: drive disk scan & defrag windows utilies to get prepared for partition shrinking.

Secondly, the installation. I followed the instructions from the UEFI ubuntu help page ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)), so I used Ubuntu secured remix 12.10 64bit.
At first, I burned a DVD, but it seems that it was not recognized as a bootable UEFI drive - I am not quite sure, because I tried the DVD in legacy mode at first (worked fine, but windows was therefore unbootable), and afterwards unsuccessfully in UEFI mode but I did not insist. DVD is so slow compared to USB, so I prepared a bootable USB key from windows with Linux Live USB Creator.
In the Bios, I selected the UEFI + activated secure boot option, and booted the USB key. When booting, pressing F12 provides a list where the USB key is indeed recognized. I launched it, then choosed "try ubuntu".

I the "trial" desktop, I used GParted to shrink the big windows partition to ~60Go, and made two new ones : 1) swap, and 2) a 50 Go ext4 to be mounted on / (I keep all the rest for data). I did not create any efi partition, although I was a bit confused by the documentation on that point ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)).
Then, "install ubuntu", choosed "something else" to set up partitioning by myself, then choosed the previously mentioned for swap and / ; and the install went through.
After install, I rebooted, just to see what happens; the boot went fine, but as I expected, the windows partition was made unaccessible. So I ran boot-repair, choosed the "recommended repair", and now it works fine: the computer boots on grub, letting me choose win or ubuntu.

For information: I did not run any extensive test so far, but at first glance ubuntu runs fine on this computer except the video card (damn hybrid Intel / AMD Radeon HD 7650, only the intel part works so far!), but this is not the place to talk about that.

Hope this might help, and do not hesitate to ask for further information if needed.

---

### Post by cboling on 2012-12-20
> **mouling said:**
> BIOS upgrade to version A09
That did the trick!  When I first had trouble, I checked for available updates, but there were none.  I hadn't thought to check since, and this one was published a few days later.

**I upgraded the BIOS from A05 to A09, and everything works** as advertised!  I am able to boot the LiveCD/USB in UEFI mode.  I used boot-repair to convert my MBR-mode install to UEFI, and it works fine -- secure-mode and unsigned versions.

Thanks for sharing your successful experience, and thanks to Yann and everyone else who worked on this.

Slightly off-topic note regarding the remix CD: While I could convert the standard Ubuntu 12.10 desktop image to USB, when I run Ubuntu 11.04's "Startup Disk Creator" on ubuntu-secure-remix-12.10-64bits.iso it instantly says "Installation Failed".

---

### Post by smegthelight on 2013-01-29
I wish they would spread the info about what they did in the bios that made it work.  I am having the same symptoms on a MSI GT70-0ND laptop (a Windows 8 UEFI model).

---

