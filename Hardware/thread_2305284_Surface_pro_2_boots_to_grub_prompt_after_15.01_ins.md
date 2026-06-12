---
title: "Surface pro 2 boots to grub prompt after 15.01 install..."
date: 2015-12-04
forum: Hardware
---

### Post by Virus692 on 2015-12-04
I managed to install Ubuntu on my pro 2 however I can only get Ubuntu to boot to the grub prompt... I ran boot repair ( [http://paste2.org/1gb24Hcp](http://paste2.org/1gb24Hcp) ) but it did not fix the issues I can get to boot windows and once it does it repeatedly works however I really would like to have Ubuntu running on it.

please help me out I cannot make hid nor hair of the boot repair report.

Tim

---

### Post by oldfred on 2015-12-04
Is sdb an external drive?

You have sdb as MBR(msdos) partitioned which normally is for BIOS boot, not UEFI.
But since sda is UEFI, grub will install in UEFI mode to boot from sda.
Windows only boots from gpt drives with UEFI.
Windows only boots from MBR partitioned drives with BIOS. 
Ubuntu is more flexible, but still best to always use gpt partitioning if your system is UEFI.

If you get to grub prompt, it is booting, but then may need extra boot parameters to finish booting Ubuntu.

 Surface Pro Ubuntu install:
[http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu)
[http://ubuntuforums.org/showthread.php?t=2183946](http://ubuntuforums.org/showthread.php?t=2183946)
[http://ubuntuforums.org/showthread.php?t=2209247](http://ubuntuforums.org/showthread.php?t=2209247)

If an external drive, you probably need to have an ESP - efi system partition on the external drive. And you must repartition with gpt to have that. Then you may need to copy /EFI/ubuntu from sda's ESP to sdb's ESP and copy again into a new folder as /EFI/Boot on sdb and rename shimx64.efi to bootx64.efi. External drives boot from /EFI/Boot/bootx64.efi in UEFI.

      
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning. Then use Something Else to choose / (root) partition and install. It will still install grub to the ESP on sda, I have tried multiple times and it just defaults to sda, so you have to copy files to sdb.

---

### Post by Virus692 on 2015-12-08
Thank you for your help... yes I was trying to install on sdb(a sd card) however I found that the surface would not recognize it at all. grub only was seeing sda. I am now trying to do this via your 1st link I was hoping to be able to not shrink the HD.

guess that is what i get for trying to think outside the box.

V

---

