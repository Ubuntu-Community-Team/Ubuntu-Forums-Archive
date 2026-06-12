---
title: "fullscreen videos intel graphics"
date: 2011-02-06
forum: Hardware
---

### Post by migrate from windows on 2011-02-06
Hi
I have ubuntu 10.10   installed in my old pc withIntel 82845g/gl  (brookdale chipset) it works well with VESA driver .but cannot run  fullscreen videos. When i try to enable intel driver I get this message  in the xorg log " 

(EE) Intel(0): No kernel modesetting drivers detected

unloading module intel 

Then boots to text mode 
can anyone help

adding i915.modeset=1 in grub did not work

apt update,upgrade everything done

please help.......Trying to wean of from microsoft..this issue is pushing me back to its feet

---

### Post by ronnielsen1 on 2011-02-06
I suffer from this card and you have a few options

Use an older Ubuntu or manually change to the intel driver or use vesa (no 3D)

> [X freezes]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze")  (GPU lockups) are still being experienced on i830, i845, and i855  chips.  Although there have been various attempts to fix these for  Ubuntu 10.10 we have not managed to produce an acceptable fix. 
To  ensure that users with these cards get a stable graphical environment  by default we no longer automatically load the Intel driver on these  cards.  This results in the fbdev driver loading, which does not provide any ability to change resolution, video acceleration, or 3D. 
There are couple of options to re-enable these missing features with various trade-offs: 

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

Go to the link above and see how it works for you. I'm using the intel driver which allows me to play 3d games but any attempts to run compiz locks me up. Personally, I'm thinking of loading an extra install of 9.04

---

### Post by migrate from windows on 2011-02-07
> **ronnielsen1 said:**
> I suffer from this card and you have a few options

Use an older Ubuntu or manually change to the intel driver or use vesa (no 3D)



[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

Go to the link above and see how it works for you. I'm using the intel driver which allows me to play 3d games but any attempts to run compiz locks me up. Personally, I'm thinking of loading an extra install of 9.04

I have no problems with VESA except for fullscreen video. 

How did you manage to get the intel driver running ..the above link doesnt help I get the no kernel modesetting driver error. What is the version of intel driver.pls specify. and a copy of your xorg.conf pls.

---

### Post by ronnielsen1 on 2011-02-07
> I have no problems with VESA except for fullscreen video. 

Well, you won't - unless you try to play a 3D game

> Like the fbdev driver the vesa driver provides no 3D acceleration or video acceleration.  It does, however, support changing resolutions. 

> How did you manage to get the intel driver running ..the above link  doesnt help I get the no kernel modesetting driver error. What is the  version of intel driver.pls specify. and a copy of your xorg.conf pls. 	

Just like on the link:

> Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Go to synaptic and make sure that xserver-xorg-video-intel is installed. I didn't have any trouble after doing this and restarting

---

### Post by migrate from windows on 2011-02-07
Which kernel are you using....are you using ubuntu 10.10?

---

### Post by migrate from windows on 2011-02-08
Thnx everybody after weeks of sleepless nights and dreams about kernels...driver $%$*&$   

finally fixed it ...the problem was with ACPI  

Had to add 
GRUB_CMDLINE_LINUX="acpi=force"

to etc/default/grub  
seems like enabling  kms is dependent on ACPI indirectly 


Finally smiling

---

### Post by HendyIrawan on 2011-03-07
> **migrate from windows said:**
> finally fixed it ...the problem was with ACPI  

Had to add 
GRUB_CMDLINE_LINUX="acpi=force"

to etc/default/grub  
seems like enabling  kms is dependent on ACPI indirectly

THANK YOU 'migrate from windows' !!! You are a savior !!

I also had similar problem (Ubuntu 10.10 Maverick Meerkat) but now works fine after adding to GRUB2:
 

  acpi=force
  

 :guitar:

 

 My hardware:
 
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
  
Similar problem in Launchpad Bug #661645 :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661645](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661645)

---

### Post by migrate from windows on 2011-03-08
Welcome! happy to be of help inspite being ubuntu newbie myself!!

---

