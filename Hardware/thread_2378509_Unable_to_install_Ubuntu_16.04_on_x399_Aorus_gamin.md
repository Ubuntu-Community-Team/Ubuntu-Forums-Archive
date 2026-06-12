---
title: "Unable to install Ubuntu 16.04 on x399 Aorus gaming 7 Motherboard"
date: 2017-11-23
forum: Hardware
---

### Post by irshaduetian2 on 2017-11-23
[COLOR=#070F14][FONT=Verdana]I need to install the Ubuntu (in a dual boot mode) on my system. When I tried to boot from the Ubuntu Live USB stick. I get the following error.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana][Firmware Bug]: AMD-Vi: IOAPC[130] not in IVRS table[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]AMD-VI: Disabling interrupt remapping[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]and just stay stuck there. [/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]I have checked the Live USB stick on another system, it is working fine there.[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Checked my bios it was already latest version (F3g).[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]**Solution I have tried**[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]After reading relevant question on this[/FONT][/COLOR][ forums]("https://forum.giga-byte.co.uk/index.php?topic=18930.0")[COLOR=#070F14][FONT=Verdana] I enabled "SVM Mode" under M.I.T -> Advanced Frequency Settings -> Advanced CPU Core Settings, and enabled the "IOMMU" under "Chipset", [/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]Now when I try Boot from Ubuntu Live USB it doesn't show the above error but after Aorus Welcome Screen it stays stuck at the blank screen.[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]This is the first time I put gigabyte motherboard in my system. Counting on you guys for support.[/FONT][/COLOR]


[COLOR=#070F14][FONT=Verdana]**Other System Details**[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Processor: AMD Ryzen™ Threadripper™ 1950X[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Graphics Card: EVGA 1080Ti Hybrid FTW3[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]RAM: Ballistix Sports LT 64GB Kit BLS4K16G4D26BFSB[/FONT][/COLOR]

---

### Post by oldfred on 2017-11-23
UEFI or BIOS install.
IF UEFI press escape key several times at and just after UEFI screen to get grub menu.
IF BIOS hold shift key from BIOS/UEFI until grub menu appears.

With new nVidia you will need nomodeset boot parameter.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by irshaduetian2 on 2017-11-24
Hi, 
Thank you very much for your help. I was able to solve the problem by your instruction. 
I was using the UEFI.

**Listing down the exact steps that worked for others **
I took it all from [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

1. Boot from Live USB/CD. On the grub menu when "Try Ubuntu without installing" is highlighted" press "e".
2. Find the words "*quiet splash*" and add word "*nomodeset*" between them such that it looks like this "*quiet **nomodeset** splash*"
3. Press F10, the system will boot fine. 
4. Install the Ubuntu
5. Reboot
6. When you see the grub menu and first-row "Unbuntu" is highlighted press "e" and repeat the step 2 and 3.
7. To make the boot option permanent do the step under heading "[SIZE=3][COLOR=#000000]**How to permanently set kernel boot options on an installed OS (not **[/COLOR][/SIZE][SIZE=4][COLOR=#000000]**[SIZE=3]wubi[/SIZE]**[/COLOR][/SIZE][SIZE=3][COLOR=#000000]**)" **[SIZE=2] from here [/SIZE][/COLOR][/SIZE] [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
8. Reboot

System should work fine now.

Regards, 
Muhammad Irshad

---

### Post by oldfred on 2017-11-24
You should not need nomodeset as a permanent boot setting.
Once you install the proprietary nVidia driver it should then just boot and nomodeset may interfere with nVidia driver.

 Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 
      
 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
    
      
 # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 
   [https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition to those before adding ppa.
ubuntu-drivers devices 

            sudo apt-get install nvidia-XXX

---

