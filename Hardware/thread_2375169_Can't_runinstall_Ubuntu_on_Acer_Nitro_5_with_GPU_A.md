---
title: "Can't run/install Ubuntu on Acer Nitro 5 with GPU AMD RX550"
date: 2017-10-22
forum: Hardware
---

### Post by thrwya on 2017-10-22
Tried installing the 16.04 64bit version from a USB stick on my new Acer Nitro 5 laptop. When I chose the "start" option in the boot menu, the screen went black, and two horizontal lines of randomly colored pixels appeared. I'm guessing the GPU isn't supported or something? The same thing happened with Linux Mint 18.2.Any idea how I should proceed?Had no issues when trying to run the Debian graphical installer.

---

### Post by ajgreeny on 2017-10-22
When booting the USB try the nomodeset boot option from F6, I think.
That will hopefully get you to a GUI though it may be at low resolution, and allow you to go to Additional Drivers once installed to install whatever is recommended for your graphic card.

---

### Post by gsahli on 2017-10-22
Refer to this:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by oldfred on 2017-10-23
You want an UEFI install and then have to manually add nomodeset on the Linux line.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Note that once installed Acer has a unique requirement of setting an UEFI supervisory password( never lose that or reset when done) and enabling "trust" on the .efi boot files from within UEFI.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

---

### Post by thrwya on 2017-10-30
Adding the nomodeset parameter worked. Thanks guys, and thanks for the links.

---

### Post by mörgæs on 2017-10-30
Please read the signature under the posts above, thanks.

---

### Post by thrwya on 2017-10-30
Update: Just installed it, and Ubuntu freezes at the purple boot screen, even after adding nomodeset to the grub thingy. This page [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver) says I need the AMDGPU-Pro driver. Will post results.

---

### Post by oldfred on 2017-10-30
I thought even with AMD, you should be able to boot with nomodeset.
Does recovery mode, under advanced options let you at least boot to command line/terminal?

---

### Post by thrwya on 2017-10-31
> **oldfred said:**
> I thought even with AMD, you should be able to boot with nomodeset.Does recovery mode, under advanced options let you at least boot to command line/terminal?Tried it a second time, and now I was able to boot to the OS. Maybe I mistyped it there before or something?Thank you guys.

---

