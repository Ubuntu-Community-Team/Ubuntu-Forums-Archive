---
title: "Trouble reinstalling Ubuntu with a UEFI laptop (having worked the first time)"
date: 2013-10-29
forum: Hardware
---

### Post by coeg2 on 2013-10-29
I recently got a new Windows 8 laptop (Asus X502C) which I would like to set up as a dual boot machine. The thing is, I initially had Ubuntu running OK on it. What I did was disable secure boot, enabled CSM and set my USB stick with Ubuntu 12.04 on it to boot preference. I installed Ubuntu onto what was drive D and all went well. I was able to boot up into it when I disabled secure boot and was able to boot up into Windows 8 when I enabled it. No problems so far. 

The reason I chose Ubuntu initially was that I understood it worked with UEFI (12.04.3 is supposed to support this). My laptop didn't want to boot into Ubuntu with secure boot enabled. It did show up a grub menu but wouldn't load up when I selected to boot into Ubuntu. Neither did the install option work. At this stage, I disabled secure boot and decided to install it without it. Success! It worked. 

I had initially wanted to install Debian Wheezy but wasn't sure if it would work but having gone through the process and seeing that Ubuntu installed and ran when secure boot was disabled, I thought I would try installing Debian instead. When I did this and rebooted, I was greeted by the grub prompt (similar to this - [http://i.stack.imgur.com/BLbvW.jpg)]("http://i.stack.imgur.com/BLbvW.jpg%29"). I thought if I reinstalled Ubuntu, as I had done initially, that this would be a simple way around the grub issue and that I’d instead use Ubuntu, as I assumed at the time it would work better with the UEFI issue. I reinstalled Ubuntu but once again came across the grub prompt. I have since not been able to work around this. I am not sure why. 

Seeing as I can't boot up with secure boot enabled, I think CSM is my only option? If so, how do I once again get my computer to load up grub correctly so I can boot into my installations? I'm wondering what the install of Debian might have done? If I recall correctly, It asked me if I wanted to install to the MBR, and that if other operating systems were showing up, which they were, that it should be safe to do so. I'm wondering if allowing it to do this has caused these grub issues?

Also, with Ubuntu, if I try to install it since this issue arose, I get this message after manually setting up the install and swap partitions (I didn't get this message on the first successful install) -

“The partition table format in use on your disks normally requires you to create a separate partition for boot loaded code. This partition should be marked for use as a “Reserved BIOS boot area" and should be at least 1MB in size. Note that this is not the same as a partition mounted on /boot.

If you do not go back to the partitioning menu and correct this error, boot loader installation may fail later, although it may still be possible to install the boot loaded to a partition.”

So, in summary, I can't boot up from a live USB/install Linux with secure boot enabled. I have decided that if I can do it in CSM mode and keep Windows 8, that would be the preferable option. How do I get back to this happening? Where should I install grub to? Any other input would be helpful. Thank you

---

### Post by oldfred on 2013-10-29
With gpt partitioning you need an efi partition if booting in UEFI mode or a bios_grub partition if booting in BIOS/CSM mode. The installer for Ubuntu now creates the bios_grub, but did not used to.
The bios_grub should be a tiny 1MB unformatted partition with the bios_grub flag. You can use gparted from live installer to create it and set flag. It can be any where on drive where efi partition is supposed to be first or near beginning of drive as Microsoft does not comply with UEFI standard of efi partition first, but it still is near beginning of drive.

What video chip? Often nomodeset or other boot parameters are needed for either CSM or UEFI boot. 

Some UEFI have been modified by vendor to only boot the Windows efi boot file. They hard code the name into the UEFI which is against the UEFI standard. Boot-Repair does have a work around where it renames grub2's shim file to have the Windows name as shim also has the Microsoft signing key. Then from grub you can booot the renamed Windows file.

See also link in my signature.

---

### Post by coeg2 on 2013-10-29
> **oldfred said:**
> With gpt partitioning you need an efi partition if booting in UEFI mode or a bios_grub partition if booting in BIOS/CSM mode. The installer for Ubuntu now creates the bios_grub, but did not used to.
The bios_grub should be a tiny 1MB unformatted partition with the bios_grub flag. You can use gparted from live installer to create it and set flag. It can be any where on drive where efi partition is supposed to be first or near beginning of drive as Microsoft does not comply with UEFI standard of efi partition first, but it still is near beginning of drive.

What video chip? Often nomodeset or other boot parameters are needed for either CSM or UEFI boot. 

Some UEFI have been modified by vendor to only boot the Windows efi boot file. They hard code the name into the UEFI which is against the UEFI standard. Boot-Repair does have a work around where it renames grub2's shim file to have the Windows name as shim also has the Microsoft signing key. Then from grub you can booot the renamed Windows file.

See also link in my signature.

Video chip is intel. I have tried creating a 1MB unformatted partition with the bios_grub flag during installation but I am still getting the grub prompt when I reboot. Is there any obvious reason as to why it was working but now any installation is resulting in the grub prompt?

---

### Post by oldfred on 2013-10-29
Did you install in UEFI mode or BIOS grub. 
And did you boot Boot-Repair in UEFI mode or BIOS mode?

How you boot installer is how it installs. This shows both the BIOS purple screen and the grub menu for installing.
       Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

One of may work better than nomodeset for Intel, not sure which works for which chips.

 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

   Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor

---

