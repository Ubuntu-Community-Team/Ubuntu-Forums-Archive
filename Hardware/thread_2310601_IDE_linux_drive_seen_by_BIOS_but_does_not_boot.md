---
title: "IDE linux drive seen by BIOS but does not boot"
date: 2016-01-20
forum: Hardware
---

### Post by dvkantor on 2016-01-20
Hello,

I have an ASUS laptop with dual boot (Win10 and Ubuntu 14.04.3). I am trying to transfer the drives to a new ASUS laptop. I enabled IDE in BIOS for controller and disabled Secure Boot. BIOS does see both drives, but can only boot up from the Win10. When I remove Win10 Drive, BIOS cannot boot from the Linux drive. When I place the linux drive back into the old ASUS, it comes up right away. Any suggestions as to what I might be doing wrong?

---

### Post by oldfred on 2016-01-20
Why would you enable IDE? That is for compatibility with 15 year old or more old drives. Or is old system that old?
UEFI needs AHCI or defaults to it.

Are these just old BIOS/MBR drives you want to boot in BIOS mode on new UEFI based hardware?

Best to see details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by dvkantor on 2016-01-20
Yes, I am trying to make BIOS/mbr hard drives work on new UEFI hardware. I also enabled CSM. BIOS does see the drive, but it is not listed as a bootable option. I just tried booting up with AHCI and it says to insert boot media, just as it did in IDE mode.

---

### Post by oldfred on 2016-01-20
Do you have secure boot off, and you may specially have to allow boot with some settings in UEFI.
How new is new Asus? What model & video chip?
Very new Skylake have some additional issues.

Some other Asus, may have clues somewhere?
 Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Installing 15.04 on Asus N550JX, boot parameters required
[http://ubuntuforums.org/showthread.php?t=2293394](http://ubuntuforums.org/showthread.php?t=2293394)
Asus ROG G75VW  with Windows 7 in UEFI boot mode.
[URL="http://ubuntuforums.org/showthread.php?t=2251167"]http://ubuntuforums.org/showthread.php?t=2251167

[/URL]

---

### Post by dvkantor on 2016-01-20
[COLOR=#333333][FONT=Helvetica neue]**Yes, I have secure boot off. ASUS G751JT-CH71 with NVIDIA 970M which I cannot make work with Live CD because Nouveau does not support this chipset.**[/FONT][/COLOR]

---

### Post by dvkantor on 2016-01-20
But, fdisk does see all of the partitions on the Linux drive. So this leads me to believe that the issue is purely BIOS based.

---

### Post by oldfred on 2016-01-20
With nVidia you will need nomodeset.
Can you set which video you use to boot with or is it just default. Or does it boot with Intel and auto switch to nVidia if required?

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

      
 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

If UEFI, you should get grub menu on boot not accessibility purple BIOS boot screen.
      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

I have seen many posts with Asus, but it seems like not one is the same model. Do they have a different model for every sale?
But UEFI is similar for all models, see above for possible additional boot parameters.

---

### Post by dvkantor on 2016-01-23
Oldfred, it is in fact a skylake model. Sorry I have been preoccupied with work so have not replied. Is there some forum that you can recommend?

---

### Post by oldfred on 2016-01-23
Some info, you may need to update kernel, support software, and video drivers.

 ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)

 Xeon Skylake Users May Run Into Display Problems With Current Distributions Dec 2015
[http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset](http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset)
Intel's Skylake Audio Firmware Lands
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Skylake-Audio-Firmware](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Skylake-Audio-Firmware)
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-BXT-Firmware-Blobs](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-BXT-Firmware-Blobs)
Skylake Intel Core i5 6500: A Great Skylake CPU For $200, Works Well On Linux, 4.3 kernel  for best graphics
[http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1)
Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)

---

### Post by yoshii on 2016-01-23
I'm not sure about Linux partitions, but Windows partitions won't boot until you set the "boot" flag to on.  You can do this using gParted from a gParted LiveCD, or any other LiveCD that has pParted on it.  
I know that it doesn't hurt the Linux partitions, but maybe it will help if the BIOS is looking at the flags.

---

### Post by oldfred on 2016-01-24
Only if BIOS/MBR does Windows have to have boot flag on the NTFS primary partition with Windows boot files.

If UEFI, the boot flag is on the ESP - efi system partition. And boot flag in UEFI is not the same as a boot flag in BIOS. With UEFI parted/gparted are using boot flag to set the correct GUID for UEFI to find the partition with the efi boot files. If you use gdisk the code is ef00 which again assigns the correct GUID for the ESP.

---

