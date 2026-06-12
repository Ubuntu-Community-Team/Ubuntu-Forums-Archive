---
title: "Compaq Presario 1200 and Ubuntu 9.04 - Graphics Card Problems"
date: 2009-05-02
forum: Hardware
---

### Post by mediate on 2009-05-02
Hello.

I recently installed Windows ME and Ubuntu 9.04 on an old crap Presario 1200 in the hopes that it will work as new. I had problems with the bootloader, but those were fixed. Now, I finished installing my wireless usb card. Now, the desktop looks ugly as it is shrunk due to the wrong display driver being installed. Can I install a new grapincs card driver on this computer? If so, can someone please guide me through it (either through a wiki page or step-by-step instruction in the forums, please.)? Thanks in advance.

Mediate

Laptop Specs (if they are needed):
Laptop: Presario 12XL323 (1200 series model)
Processor: Intel                     ®   Celeron ™ processor - 633 MHz
Memory: 174 MB Memory
Hard Disk: IBM Travelstar 10GB (5.5 GB for WinME, 4.6 for Ubuntu)
Graphics Card: Integrated Trident CyberBlade 3D Graphics with 4 MB shared video memory
OSes: Windows Millenium (Fresh Install) and Ubuntu 9.04 (Running with LILO instead of GRUB as I'm more used to LILO than GRUB)
Wireless Card: TRENDNet TEW-424UB

---

### Post by overdrank on 2009-05-02
> **mediate said:**
> Hello.

I recently installed Windows ME and Ubuntu 9.04 on an old crap Presario 1200 in the hopes that it will work as new. I had problems with the bootloader, but those were fixed. Now, I finished installing my wireless usb card. Now, the desktop looks ugly as it is shrunk due to the wrong display driver being installed. Can I install a new grapincs card driver on this computer? If so, can someone please guide me through it (either through a wiki page or step-by-step instruction in the forums, please.)? Thanks in advance.

Mediate

Laptop Specs (if they are needed):
Laptop: Presario 12XL323 (1200 series model)
Processor: Intel                     ®   Celeron ™ processor - 633 MHz
Memory: 174 MB Memory
Hard Disk: IBM Travelstar 10GB (5.5 GB for WinME, 4.6 for Ubuntu)
Graphics Card: Integrated Trident CyberBlade 3D Graphics with 4 MB shared video memory
OSes: Windows Millenium (Fresh Install) and Ubuntu 9.04 (Running with LILO instead of GRUB as I'm more used to LILO than GRUB)
Wireless Card: TRENDNet TEW-424UB

Hi and welcome, you may have some issues with the Trident CyberBlade graphics as they are not supported very well in linux.
I am surprised that you were able to install Ubuntu with only 174 MB Memory but at any rate

You may try and boot into recovery mode, which is usually the second choice from the grub when booting the system. Then you can choose the xfix option to help correct graphical issues. When xfix it complete you should be given the choice to boot normally.

---

### Post by mediate on 2009-05-02
Hello and thank you. Unfortunately, xfix did not fix this problem. Is there any way I could manually choose the driver to use for the xserver (similar to the setup process of Red Hat 7.3, where you could choose the driver, from a long list. I'm sure that Ubuntu has a list for graphics card driver). Thank you again.

---

### Post by overdrank on 2009-05-03
> **mediate said:**
> Hello and thank you. Unfortunately, xfix did not fix this problem. Is there any way I could manually choose the driver to use for the xserver (similar to the setup process of Red Hat 7.3, where you could choose the driver, from a long list. I'm sure that Ubuntu has a list for graphics card driver). Thank you again.

Hi and I have no experience with Red Hat nor with Trident CyberBlade in Ubuntu. You may find some help on the forums with a good search. 

You may wish to try Hardy 8.04 as it was before the xorg change for auto detection of graphics. It is also long term support and had a great tool for graphics witch was [displayconfig-gtk]("https://wiki.ubuntu.com/DisplayConfigGTK")

---

### Post by mediate on 2009-05-05
> **overdrank said:**
> Hi and I have no experience with Red Hat nor with Trident CyberBlade in Ubuntu. You may find some help on the forums with a good search. 
 
You may wish to try Hardy 8.04 as it was before the xorg change for auto detection of graphics. It is also long term support and had a great tool for graphics witch was [displayconfig-gtk]("https://wiki.ubuntu.com/DisplayConfigGTK")
 Thank you very much. That did the trick as the monitor itself wasn't seen properly by Ubuntu. Thank you for the help.

---

### Post by vgarcias on 2009-05-06
Hi mediate,

Did you go back to 8.04? if so, How did you use the displayconfig-gtk?

I also have a Compaq Presario 1200 which was using ubuntu 7.04, but when I tried to use 9.04... I had to use the 800x600 resolution.

Thanks...

---

### Post by mediate on 2009-05-06
> **vgarcias said:**
> Hi mediate,

Did you go back to 8.04? if so, How did you use the displayconfig-gtk?

I also have a Compaq Presario 1200 which was using ubuntu 7.04, but when I tried to use 9.04... I had to use the 800x600 resolution.

Thanks...

Hello, vgarcias.

Yes, I had to go back to 8.04 as 9.04 does not have displayconfig-gtk. Also, in 8.04, it's messed up since you can't use it (at least on my laptop) from the screen resolution settings window. If you have 8.04 or lower, open a terminal and type
```
sudo displayconfig-gtk
```
then wait. Once it opens, click on the bar next to model, then select the generic lcd panel with 1024x768. Then use resolution on 1024x768, as that's the max the monitor accepts.

---

### Post by vgarcias on 2009-05-07
mediate,

Before I went back to 8.04, I tried the solution posted in [http://ubuntuforums.org/showthread.php?t=806835&page=2](http://ubuntuforums.org/showthread.php?t=806835&page=2)
And fortunally, it worked. I'm now working with 9.04 on my old Compaq Presario 1200  at 1024x768
;)

---

