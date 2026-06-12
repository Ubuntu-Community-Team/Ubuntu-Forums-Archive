---
title: "[SOLVED] NVIDIA driver causes colored lines."
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by chrisruls00 on 2007-09-09
when I try to install the NVIDIA driver that Is need to use desktop effects it makes a bunch of colored lines appear whenever i boot up ubuntu, I just re-installed, but I still cant get Desktop Effects and my 3D games are slow. Is there any fix for this? I would really like to use the desktop effects. I also kinda want to do this stuff too:[http://www.youtube.com/watch?v=ZD7QraljRfM&mode=related&search=](http://www.youtube.com/watch?v=ZD7QraljRfM&mode=related&search=)

---

### Post by chrisruls00 on 2007-09-09
Help? I Tried to install the Bryel program but when it activated my Nvidia driver the colored lines re-appeared! Is there any way I can un-activate them from the recovery mode?

EDIT: I re-installed anyways, but could someone help me get this driver working?

---

### Post by chrisruls00 on 2007-09-10
Can someone please help me?

---

### Post by Soybean on 2007-09-10
I suspect that nobody is answering because nobody knows the answer. ;) 

Some suggestions:
-Post more information about your computer. I assume you have an Nvidia card, but which card is it? What other hardware do you have? What have you got for a monitor?
-What exactly did you do? How did you go about installing the Nvidia driver? 
-Add a screenshot of the problem. This will help people to determine where the problem is occuring -- if I look at your screenshot and see the same colored lines, then we can tell that the problem is not with your monitor, for example.

I don't actually have any idea why you'd be getting colored lines; these are just general troubleshooting suggestions for this sort of problem.

---

### Post by chrisruls00 on 2007-09-10
ok, well this is a hand down TOSHIBA Laptop from my Dad, Ill have to do research to find out about what hardware is in it. I Am activating the Driver by going to Desktop Effects and when It asks to activate it If I say yes it downloads and installs. Then If I restart the colored lines appear. Actually at first the screen is white and then it kinda does a fog effect where the white seems to be blown away to reveal the lines.

---

### Post by nick_h on 2007-09-10
To find out what card you have type:
```
lspci | grep -i nv
```

---

### Post by chrisruls00 on 2007-09-10
Ok I get:

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)


so I guess I do have an nVidia Card... I wonder why the driver breaks it?

---

### Post by nick_h on 2007-09-10
Check that you are using nvidia-glx rather than nvidia-glx-new or nvidia-glx-legacy.  You could also try downloading the driver from the [nvidia website](http://www.nvidia.com/object/linux_display_ia32_1.0-9639.html).

---

### Post by chrisruls00 on 2007-09-10
I downloaded the driver and tried to install it but It says:


ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).


whats an X server?

---

### Post by nick_h on 2007-09-11
The X server is the graphical interface.  Switch to a virtual terminal by typing CTRL-ALT-F1.  Log out of the graphical interface and then stop X by typing:
```
sudo /etc/init.d/gdm stop
```
I suggest you backup your xorg.conf file.
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Change directory where you have downloaded the driver.  To install type:
```
sudo sh NVIDIA-Linux-x86-1.0-9639-pkg1.run
```
You can restart X by typing:
```
sudo /etc/init.d/gdm start
```

---

### Post by chrisruls00 on 2007-09-11
I get an error:

No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel...etc.

So I say YES, then...

No Matching Kernel found...etc...this means the installer will need to compile a kernel interface for your kernel.

I say OK.

ERROR: You do not appear to have libc header files installed on your system. Please install your distribution's libc development package.

How do I get this libc development package?

---

### Post by nick_h on 2007-09-11
You will need to install the build-essential package.  Type:
```
sudo apt-get install build-essential
```

---

### Post by chrisruls00 on 2007-09-11
I installed it but I get the same colored lines. Luckily you told me to back up that config file i didn't know about before! I just copied it over again and it works again. Still, I wonder why It didn't work.

---

### Post by nick_h on 2007-09-11
When you install the nvidia driver are these lines permanent? Do they make the GUI unusable?

I assume that when you get this problem you can switch to a virtual terminal which looks OK.  (and from the terminal you can restore your original xorg.conf)

As far as debugging is concerned you may find some error messages in /var/log/Xorg.0.log - either view it using System->Administration->System Log or type:
```
cat /var/log/Xorg.0.log
```
You can check the nvidia module has loaded by typing:
```
lsmod | grep nvidia
dmesg | grep NV
```

---

### Post by chrisruls00 on 2007-09-11
Ok, it says:

[    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[  886.780000] nvidia: module license 'NVIDIA' taints kernel.
[  886.792000] NVRM: The NVIDIA GeForce4 420 Go GPU installed in this system is
[  886.792000] NVRM:  supported through the NVIDIA 1.0-96xx Legacy drivers. Please
[  886.792000] NVRM:  visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
[  886.792000] NVRM:  information.  The 100.14.09 NVIDIA driver will ignore
[  886.792000] NVRM:  this GPU.  Continuing probe...
[  886.796000] NVRM: No NVIDIA graphics adapter found!
[ 3380.228000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007


What does it mean it will ignore the GPU?

---

### Post by chrisruls00 on 2007-09-11
ok I found an installation help thread on the nVidia and it told me to uninstall specific packages so I uninstalled them. Ill try a re-installation soon.

---

### Post by TNakos on 2007-09-11
Just don't use it. It help for me. I found that the OS ran faster...


-Tim

---

### Post by chrisruls00 on 2007-09-11
I want to install the driver for various reasons, Im not giving up unless someone can prove it will not work. Anyways I tried installing again but it still caused the colored lines. So i switched to the terminal using Ctrl+Alt+F1 and once again used the backup to restore the driver. Mabey there is a different driver for my card... I have:

GNOME:2.18.1 (Ubuntu 2007-04-10)
Kernel:2.6.20-16-generic (#2 SMP Fri Aug 31 00:55:27 UTC 2007)
GCC:4.1.2 (i486-linux-gnu)
Xorg:7.2.0 (04 April 2007)
CPU:Intel(R) Pentium(R) 4 CPU 2.40GHz
nVidia Corporation [GeForce4 420 Go](rev a3)(prog-if 00[VGA])
Subsystem:Toshiba America Info Systems Unknown device 0010

---

### Post by dafyre on 2007-09-11
When you go to NVIDIA's website, click on the Download Drivers at the top of the screen, and then click on the Linux, FreeBSD, and Solaris link.

Under the Graphics Drivers section, you want to get the LATEST Legacy GPU Version which is 1.0-9639, click that link.

On the next page, download the NVIDIA-Linux-x86-1.0-9639-pkg1.run file.

Follow the instructions given by nick_h above again, only using *this* file.  That should get you going.

:popcorn:

---

### Post by chrisruls00 on 2007-09-11
I found this error in my Xorg.0.log file:
Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

What does it mean?

---

### Post by chrisruls00 on 2007-09-11
Thats the same file. BUT i looked at nVidia's forums And looked at a thread for helping Ubuntu users and according to it I was missing a package called xserver-xorg-dev. Anyways I downloaded it and then re-installed the driver and It actually loaded back up! But, I cant tell if it worked right or not...

---

### Post by chrisruls00 on 2007-09-12
ugg...nevermind. For whatever reason it didnt write to the xorg.conf file and when I made the changes it broke again.

---

### Post by dafyre on 2007-09-12
You may want to try the Older Legacy GPU Release (Try the 7xxx one rather than the 9639 one), and see if that works.

---

### Post by chrisruls00 on 2007-09-12
It might have worked!!! It didnt show the colored lines, AND an nVidia Logo Poped up as I booted up!!! I hope it worked!!!

---

### Post by chrisruls00 on 2007-09-12
well i think it worked but it says the GLX is not supported by the X server OR there was a problem retrieving GLX info.

---

### Post by nick_h on 2007-09-12
If it works then the command
```
glxinfo
```
should show a line "direct rendering: Yes".
There is also the test program,
```
glxgears
```
It may help if you post your */var/log/Xorg.0.log* if you are still having problems.

---

### Post by chrisruls00 on 2007-09-12
```
chrisruls00@chrisruls00-laptop:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 16 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x23 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x24 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x25 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x26 16 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x27 16 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x28 16 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x79 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault (core dumped)
chrisruls00@chrisruls00-laptop:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
chrisruls00@chrisruls00-laptop:~$ 

```
This is what I get, guess it dosent work right...
My Log:
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux chrisruls00-laptop 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep 12 18:06:43 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation NV17 [GeForce4 420 Go]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,1a30 card 1179,0001 rev 11 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1a31 card 0000,0000 rev 11 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 1179,0001 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1179,0001 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1179,0001 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1179,0001 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 82 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 1179,0001 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1179,0203 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 1179,0001 rev 02 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0175 card 1179,0010 rev a3 class 03,00,00 hdr 00
(II) PCI: 02:07:0: chip 104c,8023 card 1179,0001 rev 00 class 0c,00,10 hdr 00
(II) PCI: 02:09:0: chip 10ec,8139 card 1179,0002 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:0b:0: chip 1179,0617 card c000,0000 rev 32 class 06,07,00 hdr 82
(II) PCI: 02:0b:1: chip 1179,0617 card c800,0000 rev 32 class 06,07,00 hdr 82
(II) PCI: 02:0d:0: chip 1179,0805 card 1179,0001 rev 03 class 08,80,00 hdr 00
(II) PCI: 03:00:0: chip 1814,0201 card 1432,0c54 rev 01 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xdbf00000 - 0xdfffffff (0x4100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,8), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfce00000 - 0xfcefffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x60000000 - 0x67ffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:11:0), (2,3,4), BCTRL: 0x0500 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x60000000 - 0x63ffffff (0x4000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 5: bridge is at (2:11:1), (2,5,8), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[1] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0x64000000 - 0x67ffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV17 [GeForce4 420 Go] rev 163, Mem @ 0xfd000000/24, 0xdc000000/26, 0xdbf80000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xefffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0x6c000000 - 0x6c001fff (0x2000) MX[B]
	[1] -1	0	0xfcefff00 - 0xfcefffff (0x100) MX[B]
	[2] -1	0	0xfce00000 - 0xfce03fff (0x4000) MX[B]
	[3] -1	0	0xfce06000 - 0xfce067ff (0x800) MX[B]
	[4] -1	0	0x68000a00 - 0x68000aff (0x100) MX[B]
	[5] -1	0	0x68000800 - 0x680009ff (0x200) MX[B]
	[6] -1	0	0x68000400 - 0x680007ff (0x400) MX[B]
	[7] -1	0	0x68000000 - 0x680003ff (0x400) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdbf80000 - 0xdbffffff (0x80000) MX[B](B)
	[10] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[13] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[14] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[15] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[23] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[24] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfce06800 - 0xfce069ff (0x200) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x6c000000 - 0x6c001fff (0x2000) MX[B]
	[1] -1	0	0xfcefff00 - 0xfcefffff (0x100) MX[B]
	[2] -1	0	0xfce00000 - 0xfce03fff (0x4000) MX[B]
	[3] -1	0	0xfce06000 - 0xfce067ff (0x800) MX[B]
	[4] -1	0	0x68000a00 - 0x68000aff (0x100) MX[B]
	[5] -1	0	0x68000800 - 0x680009ff (0x200) MX[B]
	[6] -1	0	0x68000400 - 0x680007ff (0x400) MX[B]
	[7] -1	0	0x68000000 - 0x680003ff (0x400) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xdbf80000 - 0xdbffffff (0x80000) MX[B](B)
	[10] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[13] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[14] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[15] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[23] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[24] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfce06800 - 0xfce069ff (0x200) MX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x6c000000 - 0x6c001fff (0x2000) MX[B]
	[5] -1	0	0xfcefff00 - 0xfcefffff (0x100) MX[B]
	[6] -1	0	0xfce00000 - 0xfce03fff (0x4000) MX[B]
	[7] -1	0	0xfce06000 - 0xfce067ff (0x800) MX[B]
	[8] -1	0	0x68000a00 - 0x68000aff (0x100) MX[B]
	[9] -1	0	0x68000800 - 0x680009ff (0x200) MX[B]
	[10] -1	0	0x68000400 - 0x680007ff (0x400) MX[B]
	[11] -1	0	0x68000000 - 0x680003ff (0x400) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xdbf80000 - 0xdbffffff (0x80000) MX[B](B)
	[14] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0xfce06800 - 0xfce069ff (0x200) MX[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[20] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[21] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[22] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[23] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[24] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[25] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[30] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[31] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7185
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7185
	Module class: XFree86 Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA dlloader X Driver  1.0-7185  Mon Apr  2 18:31:01 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x6c000000 - 0x6c001fff (0x2000) MX[B]
	[5] -1	0	0xfcefff00 - 0xfcefffff (0x100) MX[B]
	[6] -1	0	0xfce00000 - 0xfce03fff (0x4000) MX[B]
	[7] -1	0	0xfce06000 - 0xfce067ff (0x800) MX[B]
	[8] -1	0	0x68000a00 - 0x68000aff (0x100) MX[B]
	[9] -1	0	0x68000800 - 0x680009ff (0x200) MX[B]
	[10] -1	0	0x68000400 - 0x680007ff (0x400) MX[B]
	[11] -1	0	0x68000000 - 0x680003ff (0x400) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xdbf80000 - 0xdbffffff (0x80000) MX[B](B)
	[14] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0xfce06800 - 0xfce069ff (0x200) MX[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[20] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[21] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[22] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[23] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[24] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[25] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[30] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[31] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x6c000000 - 0x6c001fff (0x2000) MX[B]
	[5] -1	0	0xfcefff00 - 0xfcefffff (0x100) MX[B]
	[6] -1	0	0xfce00000 - 0xfce03fff (0x4000) MX[B]
	[7] -1	0	0xfce06000 - 0xfce067ff (0x800) MX[B]
	[8] -1	0	0x68000a00 - 0x68000aff (0x100) MX[B]
	[9] -1	0	0x68000800 - 0x680009ff (0x200) MX[B]
	[10] -1	0	0x68000400 - 0x680007ff (0x400) MX[B]
	[11] -1	0	0x68000000 - 0x680003ff (0x400) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xdbf80000 - 0xdbffffff (0x80000) MX[B](B)
	[14] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0xfce06800 - 0xfce069ff (0x200) MX[B]
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[23] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[24] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[25] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[26] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[27] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[28] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[29] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[30] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[33] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[34] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xDC000000
(--) NVIDIA(0): MMIO registers at 0xFD000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce4 420 Go
(--) NVIDIA(0): VideoBIOS: 04.17.00.59.f9
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): VideoRAM: 32768 kBytes
(II) NVIDIA(0): Connected display device(s): DFP-0, TV-0
(WW) NVIDIA(0): Multiple displays connected, but only one display allowed;
(WW) NVIDIA(0):      using boot display
(--) NVIDIA(0): Display device DFP-0: maximum pixel clock at  8 bpp: 350 MHz
(--) NVIDIA(0): Display device DFP-0: maximum pixel clock at 16 bpp: 350 MHz
(--) NVIDIA(0): Display device DFP-0: maximum pixel clock at 32 bpp: 350 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(WW) NVIDIA(0): Unresolved symbol: xf86ExecX86int10
(EE) NVIDIA(0): Unable to initialize the X Int10 module; the console may not
(EE) NVIDIA(0):      be restored correctly on your TV.
(II) NVIDIA(0): Generic Monitor: Using hsync range of 28.00-51.00 kHz
(II) NVIDIA(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(II) NVIDIA(0): Not using default mode "640x350" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x175" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x400" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "720x400" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "360x200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "512x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "832x624" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "416x312" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1440x900" (hsync out of range)
(II) NVIDIA(0): Not using default mode "720x450" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1680x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "840x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x768" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "640x400" (height 800 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 768)
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device DFP-0:
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): Display dimensions: (310, 230) mm
(--) NVIDIA(0): DPI set to (83, 84)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdbf80000 - 0xdbffffff (0x80000) MX[B]
	[1] 0	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B]
	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0x6c000000 - 0x6c001fff (0x2000) MX[B]
	[8] -1	0	0xfcefff00 - 0xfcefffff (0x100) MX[B]
	[9] -1	0	0xfce00000 - 0xfce03fff (0x4000) MX[B]
	[10] -1	0	0xfce06000 - 0xfce067ff (0x800) MX[B]
	[11] -1	0	0x68000a00 - 0x68000aff (0x100) MX[B]
	[12] -1	0	0x68000800 - 0x680009ff (0x200) MX[B]
	[13] -1	0	0x68000400 - 0x680007ff (0x400) MX[B]
	[14] -1	0	0x68000000 - 0x680003ff (0x400) MX[B]
	[15] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[16] -1	0	0xdbf80000 - 0xdbffffff (0x80000) MX[B](B)
	[17] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[19] -1	0	0xfce06800 - 0xfce069ff (0x200) MX[B]
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000ce00 - 0x0000ceff (0x100) IX[B]
	[26] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[27] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[28] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[29] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[30] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[31] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[32] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[33] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[36] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[37] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBGLXVisuals" is not used
(WW) NVIDIA(0): Option "DisableGLXRootClipping" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) GLX is not supported with the Composite extension
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
ProcXCloseDevice to close or not ?
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
```

---

### Post by nick_h on 2007-09-12
In the log file the lines starting "(EE)" are errors.  Your problem looks to be the line:

*(EE) GLX is not supported with the Composite extension*

Is there a line something like,

*Load "Composite"*

in your /etc/X11/xorg.conf ?

If there is I suggest you comment it out (with a #) and then restart X (CTRL-ALT-Backspace).

---

### Post by chrisruls00 on 2007-09-12
didnt help. The line was there and I removed it but it still loaded it for some reason.

EDIT: I changed the line to Disable instead of Enable and now my nVidia X server Settings can detect it but it dosent work with compiz.

---

### Post by angryfirelord on 2007-09-12
Ok, first, uninstall the generic nvidia driver you downloaded (it would be something like sh blah blah blah.sh --uninstall) if you managed to install it.

Next, do:
```
sudo apt-get install nvidia-glx
```
Then, run:
```
sudo dpkg-reconfigure xserver-xorg
```
Choose nvidia as your driver. You can keep the default settings unless you know what to change them to.

---

### Post by chrisruls00 on 2007-09-12
isn't that the same driver that causes my colored lines issue? I've finaly found a driver that doesn't do that so im weary of changing...

---

### Post by munozdj on 2007-09-12
Have you tried Envy? It should detect your card and automatically install the right drivers from nVidia. It worked for me!
[HTML]http://albertomilone.com/nvidia_scripts1.html[/HTML]

---

### Post by JC Casiano on 2007-09-12
I have a 420 Go on my old Sony GRT100.  You should be able to use the nvidia-glx package (9631), but for my machine there is a caveat - you need the following option line in order to get the chip to use the LCD display:

Section "Device"
  identifier "nVidia Corporation NV17 [GeForce4 420 Go]"
...
  driver "nvidia"
  screen 0
  option "UseDisplayDevice" "DFP"
...

The other problem, where the screen goes hazy white, may be caused by an invalid resolution or sync parameter, but it's been a while since I've seen that problem so I don't remember how I fixed it. It may even be caused by the missing DFP option.  

If you switch to a console screen you can change the xorg.conf driver to "nv" and restart X (I usually have to "killall kdm") and you will be able to get the system to go back to the non-GL NVidia driver, which would then allow you to use the GUI to reinstall any packages.  I'm using Adept to install my packages, but it seems everyone has their bias.

This chip is capable of doing Beryl, I have it running right now on a 1400x1050 screen.  Had to manually add a number of parameters to xorg.conf to make it work, and I also have a shell script that allows me to toggle Beryl without the manager.  I can tell you more about that later, first you need to get the video stabilized.  

You will probably have to tweak down the Beryl configuration to get acceptable performance, but it's still impressive.  I have an occasional problem where I will lose the background image or some windows will not redraw, but that is usually fixed by launching the toggler script.  I'll get that figured out later.

---

### Post by angryfirelord on 2007-09-12
> **chrisruls00 said:**
> isn't that the same driver that causes my colored lines issue? I've finaly found a driver that doesn't do that so im weary of changing...
Now I'm confused, did the driver install successfully from nvidia's site & did you change your Driver in your xorg.conf to say "nvidia"?

---

### Post by chrisruls00 on 2007-09-13
I downloaded This driver:

[http://www.nvidia.com/object/linux_display_ia32_1.0-7185.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7185.html)

and it installed succesfuly, but Im having problems with glx.

---

### Post by chrisruls00 on 2007-09-13
Hey cool, those changes to the xorg.conf file you suggested worked! I just installed the 9639 version here:
[http://www.nvidia.com/object/linux_display_ia32_1.0-9639.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9639.html)

Edit: Awsome! Now the compiz I installed earlier works too! The only problem is that the top of my windows seems to be gone (the 3 buttons used to close and minimize) and when I opened a terminal it was white, otherwise GREAT progress. Ill have to go to bed soon (Gotta wake up early for Band)

---

### Post by nick_h on 2007-09-13
I'm glad to read that you got it working. The 1.0.9639 driver is the latest for your card and is probably the best to use.

If you update the kernel in the future then you will also have to reinstall the driver.  This is easy to do but you might not have expected the GUI to stop working.

I suggest that you take another bakup of your working xorg.conf now.

---

### Post by JC Casiano on 2007-09-14
With Beryl, initially I had problems like that because the engine would crash and take the window decorations with it; this generally amounted to removing the frames from all the windows.  As I got further along in the Beryl configuration I learned that I needed to set up and Emerald theme to get frames, as well as enable window decorations in Beryl.  In addition I had to select specific rendering parameters for Beryl.  I don't remember exactly how I did it, but I'll be you will have to do something similar with Compiz.  However...

There are a number of additional options that I added to xorg.conf to help stabilize my Beryl configuration.  You will probably also need them for Compiz.  I didn't include them with my last reply because I wanted to make certain you could get 9639 up and running first.  I just installed it, and so far it is working well, but I will have to load up a bunch of windows to try to screw it up before I'll be happy with it.

Here is the entire Device section from my xorg.conf:

Section "Device"
  identifier "nVidia Corporation NV17 [GeForce4 420 Go]"
  boardname "nv"
  busid "PCI:1:0:0"
  driver "nvidia"
  screen 0
  option "UseDisplayDevice" "DFP"
  option "XAANoOffscreenPixmaps"
  Option "AddARGBVisuals" "True"
  Option "AddARGBGLXVisuals" "True"
  Option "AllowGLXWithComposite" "true"
  Option "backingstore" "true"
  Option "TripleBuffer" "true"
EndSection

I don't know which options are actually required except the DFP option, but the TripleBuffer option appeared to reduce the frequency that my system dropped the desktop background image.  I read somewhere that "backingstore" is not necessary, and I advise putting the options two at a time in case they cause problems with Compiz.

In addition I have the following:

Section "DRI"
  Mode 0666
EndSection
Section "Extensions"
  Option "Composite" "Enable"
EndSection

I haven't gone through various permutations to determine what really was needed, but having all of these parameters has stabilized my desktop somewhat, and I'm even able to run the "14-day Trial Edition" of "World of Warcraft" in Wine without having to deactivate Beryl.  GoogleEarth doesn't like Beryl, and the GL screen savers weren't working at all, hopefully one or both will work with this latest NVidia update.

Oh, BTW, if you hate touch-tapping as much as I do, add the option "TapButton1" "0" to the Synaptics sections of xorg.conf.  Took me a while to find that, and I'm much happier as a result.

---

### Post by chrisruls00 on 2007-09-15
whats touch mapping? Also my sister thought I still had windows and tried to do some stuff while I was logged on... So i had to re-install. So ill have to start from scratch.

---

### Post by JC Casiano on 2007-09-15
Touch tapping is that dubiously useful feature that allows you to double click by tapping on a notebook's touch pad.  While it sounds charming, those of us who don't dig our fingers into the touch pad will often inadvertently trigger events because the pad double-clicks for us.

---

### Post by chrisruls00 on 2007-09-15
Ok, I got everything re-installed. I tried adding those things to my xorg.conf file and nothing changed. Mabey if I tried this Emerald program it would work? Im still getting white boxes when I launch certian applications, including a Terminal and the default Text editor along with some games, including Kolf which was a game I had fun playing.Also what Is this WINE program you where talking about?

---

### Post by JC Casiano on 2007-09-17
I think that you need to load at least one theme manager, and since you're using Compiz I can't make a recommendation for you.  But I do know that at least for Beryl I have to have a theme manager to get the window decorations to show up corretly.  Are you absolutely "married" to Compiz?  Have you tried running Beryl?  I'll see if I can get Compiz running on my VAIO, maybe I'll be able to see what you're experiencing.

Wine allows you to run some Windows applications in Linux without having to run a virtual machine or an emulator.  In my own definition, Wine acts as a translation layer between the Windows app and Linux.  Not everything works, and WoW broke after several patches were applied.  So now I have to find a way to downgrade Wine.

---

### Post by chrisruls00 on 2007-09-17
I'll Try Beryl if I can somehow save my compiz settings in case I have to come back to compiz-fusion.

---

### Post by chrisruls00 on 2007-09-17
Nope... Didn't work. And I liked compiz-fusion better, so im staying with it. The border windows I dont miss much.

---

