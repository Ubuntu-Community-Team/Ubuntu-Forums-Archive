---
title: "Wiping Data from Hard Drive"
date: 2013-11-09
forum: Hardware
---

### Post by Mohammed_Ibrahim on 2013-11-09
Hello,

Finally, I'm getting rid of Windows 8. I have both Ubuntu and Windows 8 in a dual boot environment (UEFI).
Is there a way to completely wipe all the data from the hard drive? I have access to Ubuntu, but not to Windows as I always get an error.

I'd like to wipe everything including Ubuntu itself from the hard drive and make a clean install of Ubuntu again.

Thank you.

---

### Post by Bucky Ball on 2013-11-09
Boot from the Ubuntu install CD, get to a desktop (try ubuntu), launch Gparted, right click partitions to make sure they are unmounted, delete everything. You might just be able to kill the Win partition and shrink/expand the existing partitions without having to reinstall Ubuntu. If you want to go another way ...

Clearing the hard drive can also be done when you are actually installing Ubuntu. Choose 'Something Else' when you get to the partitioning section of the install and you will see the partitions there. Kill them. Set up for your Ubuntu install, install.

---

### Post by david98 on 2013-11-09
Boot from live disk launch g parted all the tool's necessary are there

---

### Post by Mohammed_Ibrahim on 2013-11-09
But, if I deleted the Windows partition, will Ubuntu boot automatically?

Also, should I delete the EFI and other partitions too?

---

### Post by sudodus on 2013-11-09
Before wiping the EFI partition etc, you should check that your computer can boot in non-UEFI mode, sometimes called CSM. Browse the BIOS-UEFI menus for such settings!

It might be easier to give relevant advice if you specify your computer

- Brand name and model
- cpu, ram (size), graphics card ...
- BIOS-UEFI name and version.

---

### Post by Mohammed_Ibrahim on 2013-11-09
> **sudodus said:**
> Before wiping the EFI partition etc, you should check that your computer can boot in non-UEFI mode, sometimes called CSM. Browse the BIOS-UEFI menus for such settings!

It might be easier to give relevant advice if you specify your computer

- Brand name and model
- cpu, ram (size), graphics card ...
- BIOS-UEFI name and version.

Brand and Model: HP Pavilion p6-2420sem
CPU: Intel Core i7-3770 Processor
RAM: 8GB DDR3 RAM
Graphics Card: NVIDIA GeForce GT 630 (2GB DDR3)

How can I know the BIOS-UEFI name and version?

Thanks again.

---

### Post by Bucky Ball on 2013-11-09
Get into the BIOS at boot and you'll find all the details. You need to press a key right at boot. It varies with the machine. You will find the correct key in the manual (hardcopy or online), or you might see it on the screen just after you boot.

You could try del, esc, F10. It varies.

---

### Post by Mohammed_Ibrahim on 2013-11-09
System BIOS: JOS_815.rom v8.15

---

### Post by Bucky Ball on 2013-11-09
> **sudodus said:**
> Before wiping the EFI partition etc, you should check that your computer can boot in non-UEFI mode, sometimes called CSM. Browse the BIOS-UEFI menus for such settings!
.

Like sudodus says. You are going to need to get into the BIOS itself to do this. Some clues in my last post.

---

### Post by Mohammed_Ibrahim on 2013-11-09
> **Bucky Ball said:**
> Like sudodus says. You are going to need to get into the BIOS itself to do this. Some clues in my last post.

I got into the BIOS but I can't find CSM.

I have Legacy Support Disabled, and Secure Boot Enabled.

---

### Post by sudodus on 2013-11-09
Can you find any entry in the BIOS menus about

- system configuration
- boot mode
- UEFI or
- secure boot or 
- fast boot?

---

### Post by Mohammed_Ibrahim on 2013-11-09
> **sudodus said:**
> Can you find any entry in the BIOS menus about

- system configuration
- boot mode
- UEFI or
- secure boot or 
- fast boot?

I can only found these from the following:
Secure Boot: Enabled
Fast Boot: Enabled

---

### Post by Bucky Ball on 2013-11-09
You are getting this from the BIOS? If not, try one of these options at boot:

*    Press the F1, F10, or F11 key after restarting the computer.
*    HP Tablet PCs may use F10 or F12.
*    Other HP computers may allow access to BIOS using the F2 or Esc keys.

---

### Post by Mohammed_Ibrahim on 2013-11-09
> **Bucky Ball said:**
> You are getting this from the BIOS? If not, try one of these options at boot:

*    Press the F1, F10, or F11 key after restarting the computer.
*    HP Tablet PCs may use F10 or F12.
*    Other HP computers may allow access to BIOS using the F2 or Esc keys.

Yes, I am getting this from BIOS, I used (ESC).

---

### Post by Bucky Ball on 2013-11-09
> **Mohammed_Ibrahim said:**
> Yes, I am getting this from BIOS, I used (ESC).

Just checking. ;)

---

### Post by sudodus on 2013-11-09
> **Mohammed_Ibrahim said:**
> I can only found these from the following:
Secure Boot: Enabled
Fast Boot: Enabled

Please search once more if you can find something that might switch UEFI mode on/off!

If there is no such menu entry, you'll have to live with UEFI, and you should keep the UEFI partition that is already there. Install Ubuntu and use the methods described in the following links to make it work (if it does not work at once). It is usually easier to make Ubuntu work with

Secure Boot: Disabled
Fast Boot: Disabled

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2013-11-09
Even if converting to BIOS/CSM boot, I would stay with gpt partitioning and leave an efi partition at beginning of drive. You then could later convert to UEFI if desired. If you use MBR(msdos) partitioning you would have to totally reformat drive to gpt if you ever wanted to convert.
With gpt partitioning:
Ubuntu will boot in BIOS mode if you have a 1MB unformatted partition with the bios_grub flag.
Ubuntu or Windows will boot in UEFI mode from the efi partition which is formatted FAT32 and has boot flag.
You can have both an efi and bios_grub partition on the gpt partitioned drive.

Some computers have modified UEFI to only boot the Windows folder and/or the Windows efi file. Boot-Repair converts grub2's shim to be that file for those computers, so if yours is one of those and you use UEFI you may need the Windows efi file. Boot-Repair does rename this file to actually be grub2's shim file.
 /EFI/Microsoft/Boot/bootmgfw.efi

---

### Post by Mohammed_Ibrahim on 2013-11-09
> **sudodus said:**
> Please search once more if you can find something that might switch UEFI mode on/off!

If there is no such menu entry, you'll have to live with UEFI, and you should keep the UEFI partition that is already there. Install Ubuntu and use the methods described in the following links to make it work (if it does not work at once). It is usually easier to make Ubuntu work with

Secure Boot: Disabled
Fast Boot: Disabled

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Is it that to disable UEFI?
When I go to Storage > Boot Order, I found the following:
UEFI Boot Sources
- ubuntu
- Windows Boot Manager
- USB Floppy/CD
- USB Hard Drive
- UEFI: IPv4 Realtek PCIe GBE Family Controller
- UEFI: IPv6 Realtek PCIe GBE Family Controller
Legacy Boot Sources : Disabled

If I enabled Legacy Boot Sources, does it mean that everything will be fine and it disabled UEFI?

---

### Post by Bucky Ball on 2013-11-09
Posted in error.

---

### Post by Mohammed_Ibrahim on 2013-11-09
> **oldfred said:**
> Even if converting to BIOS/CSM boot, I would stay with gpt partitioning and leave an efi partition at beginning of drive. You then could later convert to UEFI if desired. If you use MBR(msdos) partitioning you would have to totally reformat drive to gpt if you ever wanted to convert.
With gpt partitioning:
Ubuntu will boot in BIOS mode if you have a 1MB unformatted partition with the bios_grub flag.
Ubuntu or Windows will boot in UEFI mode from the efi partition which is formatted FAT32 and has boot flag.
You can have both an efi and bios_grub partition on the gpt partitioned drive.

Some computers have modified UEFI to only boot the Windows folder and/or the Windows efi file. Boot-Repair converts grub2's shim to be that file for those computers, so if yours is one of those and you use UEFI you may need the Windows efi file. Boot-Repair does rename this file to actually be grub2's shim file.
 /EFI/Microsoft/Boot/bootmgfw.efi

I can leave that, but the problem is that I can't even boot to Windows 8, there is always an error (Your PC ran into a problem) and then it takes me back to grub!

---

### Post by sudodus on 2013-11-09
> **Mohammed_Ibrahim said:**
> Is it that to disable UEFI?
When I go to Storage > Boot Order, I found the following:
UEFI Boot Sources
- ubuntu
- Windows Boot Manager
- USB Floppy/CD
- USB Hard Drive
- UEFI: IPv4 Realtek PCIe GBE Family Controller
- UEFI: IPv6 Realtek PCIe GBE Family Controller
Legacy Boot Sources : Disabled

If I enabled Legacy Boot Sources, does it mean that everything will be fine and it disabled UEFI?

It's hard to know exactly what it means, but in my newest computer (a Toshiba), there is a clear entry '***boot mode***' where I can switch between UEFI and CSM mode.

If your computer can boot Ubuntu in UEFI mode, maybe you should stay there, and just clear the partitions. Now that *oldfred* has found this thread, you will get the best available support, so you will manage to get a good system, whichever boot mode you choose :-)

---

### Post by Mohammed_Ibrahim on 2013-11-09
Is there a way to just fix Windows 8 from that "Your PC ran into a problem" error? Because if I fixed it, I'll be able to do all the UEFI work from there.

---

### Post by oldfred on 2013-11-09
How are you trying to boot Windows? If you left fast boot on, then it will not boot from a grub menu. And if you ran Boot-Repairs rename function, you may be booting grub2's shim from the Windows entry in the UEFI menu. You need to be able to boot Windows directly from UEFI. 

Post the link this gives from Ubuntu or live installer.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mohammed_Ibrahim on 2013-11-09
I'm booting Windows from the Grub menu (Windows UEFI Boot Loader), and yes Fast Boot is enabled, should I disable it?

Boot-Info:
[http://paste.ubuntu.com/6389954/](http://paste.ubuntu.com/6389954/)

---

### Post by oldfred on 2013-11-09
Fast boot is one of the first things you have to turn off when dual booting. It is always on hiberation which causes issues.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)
User who fixed Windows 8
[http://ubuntuforums.org/showthread.php?t=2171156s](http://ubuntuforums.org/showthread.php?t=2171156s)

---

### Post by oldfred on 2013-11-09
Boot-Repair ran the buggy UEFI rename function. So the Windows boot file is really grub2's shim file.

 Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

You may have to un-rename so you can directly boot Windows from the UEFI menu.
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

There also is a backup of the efi file, but if you have fast boot on you probably cannot get to it:

 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

---

### Post by Mohammed_Ibrahim on 2013-11-09
Hello,

I went to Boot Repair and did the "Restore EFI Backups" option, and booted again to Windows, the same error still appeared.

Should I turn of Fast Boot now?
Do you need the Boot-Info again?


Thanks in advance :)

---

### Post by oldfred on 2013-11-09
I really do not know all the ways to fix Windows 8. My last Windows was XP and I stopped using it 2 years ago.

       [URL="http://www.eightforums.com/"]http://www.eightforums.com/

[http://jp-andre.pagesperso-orange.fr/advanced-ntfs-3g.html#windows8](http://jp-andre.pagesperso-orange.fr/advanced-ntfs-3g.html#windows8)

      [/URL]
 Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)
User who fixed Windows 8
[http://ubuntuforums.org/showthread.php?t=2171156s](http://ubuntuforums.org/showthread.php?t=2171156s)

    [URL="http://www.eightforums.com/"]
[/URL]

---

### Post by Bucky Ball on 2013-11-10
> **Mohammed_Ibrahim said:**
> 
Should I turn of Fast Boot now?
 :)

oldfred has already said fast boot is one of the first things that should be switched off a few posts ago. Please read replies. ;)

---

### Post by Mohammed_Ibrahim on 2013-11-10
> **Bucky Ball said:**
> oldfred has already said fast boot is one of the first things that should be switched off a few posts ago. Please read replies. ;)

I'm still getting the Windows error, I think I have to ask this in a Windows forum.

---

