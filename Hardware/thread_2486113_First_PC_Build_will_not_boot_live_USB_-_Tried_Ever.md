---
title: "First PC Build will not boot live USB - Tried Everything"
date: 2023-04-20
forum: Hardware
---

### Post by lart33 on 2023-04-20
I've spent the last four days trying to troubleshoot what I thought should otherwise be the easiest part of my whole build process: booting with a live USB to ubuntu. I have setup laptops in legacy bios with live USB sticks dozens of times, but I cannot for the life of me get anything to work on this PC (desktop) build


Hardware:


CPU: AMD TR Pro 5955WX


M/B: ASUS Pro WS WRX80E-SAGE SE WIFI


Mem: (2x) Crucial 2x32GB kit (CT2K32G4DFD832A) DDR4 UDIMM


GPU: NVIDIA A4500


SSD: Samsung NVMe M.2 980 Pro 1TB


PSU: Seasonic Titanium 80+ 1600W


ISO: Ubuntu 22.04.2 LTS (sha256sum matches)



I haven't done anything particularly irregular with my build: I know all of my hardware/software is at least in theory compatible, because I can see the same hardware being sold with Ubuntu 22.04 on the lambda labs website.


I have tried with and without safe graphics (and manually setting nomodeset kernel option), with Pop!_OS (NVIDIA driver version), and in both cases on multiple different flash drives and with different methods and bootloaders (dd command vs mkusb-nox vs. ventoy)


When I am lucky, I am able to get to the GRUB menu (which doesn't always happen and takes ~20min when it does work), but I basically always end up with some form of the following error: "Error: failure to read sector 0x0 from `cd0'... you need to load the kernel first"


If I open a grub command line, I try ls I can see (depending on the drive I'm using) options like (hd0) or (hd0,1) etc. but ls (hd0) gives me the same failure to read error.


I have used Memtest86 to confirm that my RAM works (no errors), but the dashboard says that it failed to detect SPD for RAM in channels A-D (whichever sticks I use and whichever of A-D they are in). E-H appear to show up fine. ASUS support suggested that this was fine (?) and suggested I use only E-H (??), but I struggle to imagine this doesn't matter.


I have found that the only way I even get into the GRUB menu is with the following BIOS UEFI settings:


Fastboot disabled


Secure boot keys cleared


AMI native NVMe driver disabled


With CSM enabled, I get no grub menu but see the Ubuntu splash screen, some printouts, then it just hangs with a bunch of identical lines pairs (example below) in a row


[ 16.304042] nvme 0000:2b:00.0: AER: aer_status: 0x00000001, aer_mask: 0x0000000

[ 16.304466] nvme 0000:2b:00.0: AER: aer_layer=Physical Layer, aer_agent=Receiver ID


Any advice would be massively helpful. I got on the phone with some helpful people at some local computer shops and at Puget Systems, but nothing has solved the problem completely. I saw some forum posts about RAM compatibility issues with this M/B failing to boot (or POST), but often the users with similar errors simply ended by saying they gave up ([https://www.reddit.com/r/ASUS/comments/108yb7v/wrx80sage_boot_issues/](https://www.reddit.com/r/ASUS/comments/108yb7v/wrx80sage_boot_issues/))


Thanks!

---

### Post by yancek on 2023-04-21
Does this failure occur only on that specific computer?  You indicate you have tried different methods to write the iso to the USB and they all fail with that error.  Do you have another computer you can try to boot the USB to verify that the USB can boot?  Do you get the same error with Legacy/CSM disabled?

---

### Post by oldfred on 2023-04-21
Have you updated UEFI firmware?
Have you updated SSD firmware?
Often new systems still have an update available.

Be sure to select UEFI boot.
Boot in safe graphics mode.
Does not show UEFI or BIOS boot screens and shows LVM or erase entire drive screens
[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)
Install third party software for graphics
Some is proprietary (Which is referring to nVidia and possibly others).

---

### Post by lart33 on 2023-04-23
I haven't tested *every* live USB on another computer, but I have tested several (dd method and ventoy, iirc) on another computer to confirm that it successfully boots. So, to the extent that this issue has to do with my USB, I was thinking it might be some kind of compatibility issue: like GPT vs MDOS partition tables, ext4 vs fat32 filesystems, etc.

CSM gives me as similar/the same error about either loading the kernel first or being unable to read a sector (or, I think it may have been not finding '/boot/'

---

### Post by lart33 on 2023-04-23
motherboard BIOS is up to date, if that's the same thing as UEFI firmware... I am not familiar with what SSD firmware means or would be.

I have tried both UEFI and legacy boot, safe-graphics mode and normal (as well as normal with the "nomodeset" option added manually in the grub menu)

I also tried using Pop!_OS with NVIDIA drivers built-in to see if the drivers were the issue

What I am not quite understanding is what the 'hd0' or 'cd0' drives refer to when I get the error message attempting to load the linux kernel: are those drives my flash drive? Or are they loaded into system memory (RAM) and then it is trying to read from there? I have sometimes gotten (i think in CSM/legacy mode) an error about running out of memory, which seems weird since (in my most minimal tests on a single DIMM) I have 32GB of RAM.

---

### Post by lart33 on 2023-04-23
[https://access.redhat.com/solutions/3600941](https://access.redhat.com/solutions/3600941)

looks like this might have info on my error, but I don't have redhat... anyone know how to view this?

---

### Post by oldfred on 2023-04-23
Your hd0 is first drive(may be sda or nvme0n1), cd0 is first CD/DVD drive. But sometimes the live installer on flash drive is seen as cd drive as when written with dd, it is a combination DVD/flash drive format.

Just to be pedantic, it has been UEFI since about 2012 when Microsoft required vendors to install in UEFI boot mode to gpt partitioned drives. But many vendors still call it BIOS. BIOS mode in UEFI is CSM.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
Some vendors now are releasing systems that are UEFI only, no CSM mode at all. Motherboards will probably be the last to eliminate CSM.

I only know how to update SSD by checking firmware & model in Ubuntu and then going to vendor site to see if firmware is newer. Once booted you can see firmware version. 
udisksctl status
How to update Samsung:
[https://wiki.archlinux.org/index.php/Solid_state_drive](https://wiki.archlinux.org/index.php/Solid_state_drive) & 
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)
I downloaded ISO & created bootable flash drive & ran it. It was tiny, looked more like an old DOS screen and only offered update.
Do not try to use the Windows app Magician unless you have Windows. 

With new hardware do not turn on CSM/BIOS/Legacy mode. Only use UEFI.
Most systems setting in UEFI only controls the boot once installed. You still select UEFI or BIOS in UEFI boot menu when booting flash drive. Always select the UEFI option.

Have you tried 23.04? I normally suggest the LTS versions like 22.04, but very new hardware often needs the newest kernel & drivers in the latest short term release.


How are you creating flash drive?
Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by lart33 on 2023-04-23
So when it says that there was a failure to read sector 0x... from 'hd0', is it referring to the first drive on my pc (as opposed to a partition on my flash drive? My only storage drive is the samsung m.2, so does that mean it may be defective? I'd assumed it wasn't used at all during the boot process, since I'm booting from the live USB... Is there a way to test whether my SSD is corrupted without first booting into the OS (which I can't do), similar to memtest (which I was able to do)? How did you create the bootable flash drive for the samsung update ISO (and can it be booted into with UEFI)?

I haven't yet but will try 23.04 next

I've tried creating the flash drive with dd (after reformatting it with fdisk and mkfs) as well as mkusb-nox, ventoy, and (on another machine with windows) balena. None seemed to work (though I worry some of my tests weren't controlled well). I see your advice about just formatting a flash drive with fat32 and setting the boot flag on... not sure how to do that, but I'll pursue that/figure it out as soon as I'm back at my computer!

Thank you for the advice! This is all much deeper than I've ever had to dive to get ubuntu running.

---

### Post by yancek on 2023-04-24
>  So when it says that there was a failure to read sector 0x... from  'hd0', is it referring to the first drive on my pc (as opposed to a  partition on my flash drive?

(hd0) should be referring to the first hard drive on the computer and not the USB.

Your internal drive should not be used when booting from the USB until you get to the point of installing to it.  If the internal hard drive has a Linux filesystem on it you can do a filesystem check with the fsck command.  Just do an online search to run fsck on Linux and you will find many sites explaining it in detail.  Your partition on the SSD needs to be unmounted to run fsck.

---

### Post by lart33 on 2023-04-24
Then i'm confused as to why I'm getting that error -- why is my bootloader even trying to read from hd0? I haven't gotten to the point of attempting an installation, since I haven't even gotten the live USB with Ubuntu to boot.

I have been able to read `ls (memdisk)/` to see a `grub.cfg` file, but that's the only option I've been able to run `ls` on without a failure to read error.

---

### Post by tea for one on 2023-04-24
As an experiment:-
Power off completely
Remove all peripheral devices (except monitor, keyboard, mouse)
Also, remove all internal drives 
Attach bootable USB
Power on (the PC should find the only bootable device)
What happens?

---

### Post by yancek on 2023-04-25
> why is my bootloader even trying to read from hd0?  

From the information you have posted, the only time you get that error in reference to hd0 is when you run the ls command from Grub which is then trying to detect all hard drives and partitions.  The attempt to boot shows an error referring to cd0 which would be a reference to the USB.  I don't have any other suggestions, the hardware may be too new and not have necessary drivers so as suggested above, you might test a more recent Ubuntu release.

---

### Post by oldfred on 2023-04-25
I did see one user who had CD/DVD turned on in UEFI/BIOS. So system was looking for a CD drive that did not exist.
Did you look in UEFI for version and verify at vendor's web site that you have newest version.

With motherboards, you typically have multiple ways to update UEFI. Some even directly from UEFI.
Most have you download a file into a FAT32 partition (why I make my ESP larger & read/write, but may be a secuity issue) or to a flash drive that has a FAT32 partition. Some have a downloadable DOS bootable disk with DOS and update file.

---

### Post by lart33 on 2023-04-25
I think I've solved it: @yancek 's comment about hd0 referring to my SSD confused me, because it seemed like the SSD should have no impact on the bootloader process (since it doesn't show up in my UEFI boot priority sequence and has no boot info), but when I removed the SSD (my only persistent memory) entirely, I was able to boot the exact same flash drive (which had previously not worked) with no problem. Of course, now I can't save the operating system anywhere, but I know what the blocker appears to have been. I ordered a new SSD (another Samsung NVMe M.2 drive), and I'll try that once it arrives. I'm assuming the other one must have been bunk (I tried reinstalling it, in case it was just poorly attached, but that didn't help). If the new SSD doesn't work, I'll be a bit concerned, but as of now my thesis is basically that the bootloader is just attempting another read of the drives available and the error on read attempts to my SSD caused it to panic, even though the read operation itself was not critical to the bootloading process. Thanks for all the help everyone! Fingers crossed for thursday when the SSD gets in...

---

### Post by oldfred on 2023-04-25
Do you have latest firmware for UEFI/BIOS?
Did you update SSD firmware from Samsung?

How to update Samsung:
[https://wiki.archlinux.org/index.php/Solid_state_drive](https://wiki.archlinux.org/index.php/Solid_state_drive) & 
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)
Look at firmware, not Magician which is Windows.

If you can see drive in any boot. This shows firmware version to compare to what Samsung has available.
udisksctl status

I downloaded Samsung ISO & made bootable drive. It looked basic like an old DOS disk, but updated firmware.

---

### Post by lart33 on 2023-04-26
Yes, I downloaded and installed the latest UEFI firmware from ASUS. However, I had difficulty updating the SSD firmware: I couldn't seem to get the Samsung firmware (for the 980, from the link you provided) to boot on my machine. I followed their exact recommended method for creating the USB ([https://semiconductor.samsung.com/resources/user-manual/Firmware_Update_Utility_UserManual.pdf](https://semiconductor.samsung.com/resources/user-manual/Firmware_Update_Utility_UserManual.pdf)) with unetbootin as well as with dd. Since I couldn't boot into any OS while it was installed, i also couldn't run "udisksctl status" to see existing firmware -- my only hope would be to find the current firmware version in UEFI or something, though I was hoping the Samsung ISO would show me (again, I couldn't get it to run).

I would be curious to see if I can boot the Samsung ISO while the SSD is removed, since that would seem to indicate a more serious problem with the SSD. I wanted to upgrade to a larger SSD anyways, so I ordered a 990 2TB, which I'm hoping will work out of the box. Otherwise, I'll follow your advice for troubleshooting further!

---

### Post by oldfred on 2023-04-26
Use of dd to create bootable ISO only works for those ISO designed as both DVD/CD & flash drive.
Since instructions did not mention dd, I would be surprised dd would work.

I used grub2's loopmount which I use for all my Ubuntu ISO & it worked. I was a bit surprised as loopmount does not always work, either.

---

### Post by lart33 on 2023-04-28
Update: new SSD worked immediately and with no trouble! The hard-drive must have been bad.

Thank you all so much for the help/advice!

---

### Post by stevermann on 2023-04-28
Silly question - is the USB drive the first boot in the BIOS?

---

