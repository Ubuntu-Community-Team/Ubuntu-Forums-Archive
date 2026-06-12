---
title: "geforce2 MX200"
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by hiperactive on 2005-09-19
Hello
I have read some posts here and tried some things but I haven't succeed. I have downloaded the lastest Ubuntu(5.10) and worked fine untill I installed my video card drivers (geforce2 MX200 agp) using: 

$ sudo aptitude install nvidia-glx 
$ sudo aptitude install nvidia-settings 
$ sudo nvidia-glx-config enable

The installation was ok so I rebooted the X server but it never worked again. Since then I only get this:

------------------------------------------
(II) Setting vga for screen 0. 
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32 
(==) NVIDIA(0): RGB weight 888 
(==) NVIDIA(0): Default visual is TrueColor 
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0) 
(--) NVIDIA(0): Linear framebuffer at 0xE0000000 
(--) NVIDIA(0): MMIO registers at 0xEC000000 
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module! 
(EE) NVIDIA(0):  *** Aborting *** 
(II) UnloadModule: "nvidia" 
(EE) Screen(s) found, but none have a usable configuration. 

Fatal server error: 
no screens found
------------------------------------------

I have already tried
- Restore the previous config... cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf 
- Reconfigure using dpkg-reconfigure dpkg-reconfigure xserver-xorg
....... but none worked.

Besides, what happened next was strange too, there were 3 new options for booting in Grub. At first I have only:

-Linux  blabla kernel-2.6.12-8-386
-Linux  blabla kernel-2.6.12-8-386 (recovery mode)
-Winxp

But mysteriously were added:
-Linux  blabla kernel-2.6.XX-X-386 (I tried it but it hangs at the very beginning)
-Linux  blabla kernel-2.6.XX-X-386 (recovery mode) (hangs too)
-Memtest
 
I don't remember the exact version of the kernel but it was older than v2.6.12-8.

I don't what to do?  ](*,) 
Sorry for my English and I am a newbie here. 


Saludos

---

### Post by tseliot on 2005-09-19
Try to boot in recovery mode and type

nano /etc/X11/xorg.conf

find the line with "nvidia" and substitute it with "nv"

CTRL+O to save (overwrite the file)

CTRL+X to exit

type "startx" or Restart your computer

EDIT: oops! I didn't notice it doesn't boot in recovery mode too. Reinstall Ubuntu.

---

### Post by hiperactive on 2005-09-19
[QUOTE=tseliot]Try to boot in recovery mode and type

nano /etc/X11/xorg.conf

find the line with "nvidia" and substitute it with "nv"

CTRL+O to save (overwrite the file)

CTRL+X to exit

type "startx" or Restart your computer

EDIT: oops! I didn't notice it doesn't boot in recovery mode too. Reinstall Ubuntu.[/QUOTE]

Thanks, it worked... But still cant install the proper nvidia drivers  ](*,)

---

### Post by tseliot on 2005-09-27
QUOTE: hiperactive

Hello there
I am reading your HOWTO: Latest NVIDIA drivers
and trying to follow it the best as I can, I have problems with my video card, you answered my post here : [http://www.ubuntuforums.org/showthread.php?t=67036](http://www.ubuntuforums.org/showthread.php?t=67036)

Well my problem now is at this part:
Open either Synaptic or Kynaptic

press the "Search" button and put "header" in the search field

you will see a list of files, find "linux-headers-the name you got from uname -r"

for example if your kernel is "2.6.10-5-386", the headers will be "linux-headers-2.6.10-5-386"

my kernel is 2.6.12-8-386 and linux-headers-2.6.12-8-386 is not found on Synaptic. The strange thing was when I uninstalled nvidia-glx the package linux-headers-2.6.12-8-386 was present and had to be uninstalled too. . Now I dont know what to do, ignore that part or download another header??

thanks in advance
_________________________

I've got some questions for you:

1) Do you use Breezy or Hoary?

2) If you use Hoary I suppose you took the kernel from Breezy's repositories or you compiled the kernel yourself. Can you explain me what you did, please?

3) Check and post your "/etc/apt/sources.list" (copy the content and paste it to this page)

4) You might need kernel sources too.

5) Your graphic card is pretty old so maybe the drivers that you can find in Ubuntu repositories don't support it any more. I suggest you to do the following things:

Download this driver (version 6111)
[http://www.nvidia.com/object/linux_display_ia32_1.0-6111.html]("http://www.nvidia.com/object/linux_display_ia32_1.0-6111.html")

And follow my guide in order to install it (it's just a matter of copying and pasting commands from the guide):

[http://ubuntuforums.org/showthread.php?t=57368]("http://ubuntuforums.org/showthread.php?t=57368")

If you have problems about the installation of the drivers, please post them in that thread.

---

