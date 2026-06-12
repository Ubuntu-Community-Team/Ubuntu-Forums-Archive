---
title: "2 problems with ATI Mobility 9000 IGP"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by marktechey on 2007-07-09
Hi,
     I have a couple of problems with my video card, an ATI Mobility Radeon 9000 IGP . The first one is, it is incorrectly reported as Ati Mobility Radeon 9200 IGP and ATI Mobility 9100 IGP  here are the results from 

lspci | grep ATI . 
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7831
* 00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP PCI/AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 1a)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
* 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility 9200 IGP

My second problem is I can´t get 3d acceleration or direct rendering to work. I´ve tried the fglrx driver and the ati open source driver, with no luck. This is what I get from 
 LIBGL_DEBUG=verbose glxinfo | grep vendor
    libGL error: XF86DRIQueryDirectRenderingCapable returned false
    server glx vendor string: SGI
    client glx vendor string: SGI
    OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)

Can anyone help?

---

### Post by marktechey on 2007-07-09
here is this if it helps

---

### Post by Kubunteando on 2007-07-09
Some questions some we can help:

1- are you using Feisty?
2- what version of the fglrx driver did you try?
3- what version of mesa (Open Source drivers) are you using?

---

### Post by marktechey on 2007-07-09
Thanks for the reply,
     I´m using Gusty, although I´ve had both these problems in Feisty, I´ve tried the 8.28.8 driver have fglrx because later versions don´t support my video card. Now I´m trying to use the open-source ati driver with AIGLX. The version of the ati open source driver i have is 1:6.6.3-2ubuntu6 . My Mesa version is 6.2, should I´ll try installing 7.0

Thanks

---

### Post by marktechey on 2007-07-09
I think I found my problem, but i´m not sure what to do 
[http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting)

under the AGP section, the second point. So how do I change this.

---

### Post by ~~Tito~~ on 2007-07-09
Hey same problem with me (wrong card showing up), but 3d acceleration and rendering works. Do you have a Hp Pavilion zv5000?

---

### Post by qamelian on 2007-07-09
I have the same GPU in my Compaq Presario R3000 laptop and it works flawlessly with the default open-source ATI Driver, including direct rendering. I doubt you'll get the FGLRX driver working as the last version to support this card doesn't work well with the current version of Xorg.

---

### Post by ~~Tito~~ on 2007-07-09
go here assuming u have an x86:
[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)

---

### Post by marktechey on 2007-07-09
No, I have a Toshiba Satellite A85-S107. Those of you with the same video cards as me, can you post your xorg.conf and how you used the open source driver. I think this might be a problem 

lspci | grep ATI
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7831           <- This line
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP PCI/AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 1a)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility 9200 IGP

I think i have to change intel-agp.ko to ati-agp.ko
    * If it complains about an unsupported chipset/bridge, make sure you included your chipset-specific AGP support when you configured the kernel. This chipset support is for your motherboard, not for your video card, so if you have a Radeon on an Intel motherboard, you need intel-agp.ko, not ati-agp.ko. 

This is from [http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting)

How do you do this?

---

### Post by ~~Tito~~ on 2007-07-09
> **marktechey said:**
> No, I have a Toshiba Satellite A85-S107. Those of you with the same video cards as me, can you post your xorg.conf and how you used the open source driver. I think this might be a problem 

lspci | grep ATI
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7831           <- This line
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP PCI/AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 1a)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility 9200 IGP

I think i have to change intel-agp.ko to ati-agp.ko
    * If it complains about an unsupported chipset/bridge, make sure you included your chipset-specific AGP support when you configured the kernel. This chipset support is for your motherboard, not for your video card, so if you have a Radeon on an Intel motherboard, you need intel-agp.ko, not ati-agp.ko. 

This is from [http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting)

How do you do this?
I meant x86 by the ubuntu version. (Ubuntu 7.04 Feisty Fawn x86 **Normal Version**)

---

### Post by marktechey on 2007-07-09
I got that, I have tried using that version of fglrx before, and it hasn´t worked

---

### Post by marktechey on 2007-07-09
I´m also using gusty, and so I have xorg 7.2 and fglrx won´t install correctly

---

### Post by ~~Tito~~ on 2007-07-09
Try the xorg version on that site?

---

### Post by marktechey on 2007-07-10
So I have now tried both fglrx (closed-source) and aiglx (open-source) for 3d accelleration. My problem with fglrx v. 8.28.8
      When running command sudo m-a build I get and error message, log attached
My problem with the open-source driver
      I think I need the module intel-agp to load instead of ati-agp . But I´m not sure how to do this. This is because I supposively have and ünsupported chip .

Also what version of xorg on what site are you talking about

---

### Post by Kubunteando on 2007-07-10
I think the issue with the 8.28.8 drivers is that they are not compatible with the newer kernels, starting with Feisty. I installed fine in Edgy, but I get also errors when installing them in Feisty.

So I go for the Open Souce drivers for the ATI Radeon Mobility 9000 I use. The only issue is I don't use TV-out.

The MESA 7.0 should work fine. I am using MESA 6.5.3 and it also seems to work fine.

---

### Post by marktechey on 2007-07-10
Ok, so we will try the open source dirver. However, I can´t get that to work because of this
mark@mark:~$ dmesg | grep agp
[   20.828000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.028000] agpgart: Unsupported Ati chipset (device id: 7831)
[  636.652000] agpgart: Unsupported Ati chipset (device id: 7831)

the fact that thinks the chips are unsupported, I have found a way to fix this at the following website
[http://dri.freedesktop.org/wiki/DriTroubleshooting#head-a4a5724fbf4d99874b6556d5153a7a89a06dc773](http://dri.freedesktop.org/wiki/DriTroubleshooting#head-a4a5724fbf4d99874b6556d5153a7a89a06dc773)
under the AGP section, under linux, the second bullet point, however, I don´t know how to do that. How to use intel-agp.ko instead of ati-agp,ko . Could you tell me how

---

### Post by marktechey on 2007-07-10
I did it!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
What I had to do was add 
Option 		"BusType" "PCI"
Option 		"UseFBDev" "false"

to my xorg.conf under device . I know get 
mark@mark:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

mark@mark:~$ glxinfo | grep "direct rendering"
direct rendering: Yes

Thanks for your help

---

### Post by jthg on 2007-12-25
I seem to be running into the same problem on the same laptop model.  Mark's fix did not work for me.  Mark, did you do anything else?

I think the problem stems from the fact that the ATI AGP bridge is not being recognized by the ati-agp kernel module.  When I modprobe ati-agp, I get
[INDENT]agpgart: Unsupported Ati chipset (device id: 7831)[/INDENT]
Is there a way to force the ati-agp module to load the radeon 9000 IGP driver?

Thanks,
Jacob

---

### Post by mistlur1 on 2008-05-12
> **marktechey said:**
> I did it!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
What I had to do was add 
Option 		"BusType" "PCI"
Option 		"UseFBDev" "false"

to my xorg.conf under device . I know get 
mark@mark:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

mark@mark:~$ glxinfo | grep "direct rendering"
direct rendering: Yes

Thanks for your help

Thank you Mark!!!
I know this is an old thread, but in case anyone with an old laptop runs into this issue Marks simple fix might do the trick.
Been fiddling with this for a while and your fix made my old Acer travelmate 2000 stop flickering and now redraws soundly. I also have a Mobility radeon 9000 igp, recognized as 9100 igp.
Mark, once again, thank you!

/mistlur

---

