---
title: "Ubuntu 15.10  - Problem with Intel HD 4000 graphics card driver"
date: 2016-03-31
forum: Hardware
---

### Post by cchance_25 on 2016-03-31
Hello all, how are you all doing?

I'm new to GNU/Linux systems :D. former windows user :). and I'm having problems with the graphics driver.
On windows, I could run the screen resolution on 1600x900_60Hz with no problems, but I can't do that now on Ubuntu.

My machine:

Intel i7-3770 Ivy bridge with integrated intel HD 4000 graphics card.

I searched every page, site, and I read every article on the web but couldn't find the solution. My screen stuck on 1024x768(4:3).

I found some solutions, but it wasn't permanent, here's some of them:

```
$ cvt 1600 900 60

# 1600x900 59.95 Hz (CVT 1.44M9) hsync: 55.99 kHz; pclk: 118.25 MHz
Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync

```

Then:

```
$ xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
$

$ xrandr --addmode VGA1 1600x900_60.00

```

And after typing this:

```
 $ xrandr --output VGA1 --mode 1600x900_60.00
```


the resolution changes to 1600x900, but as soon as I logout/restart the computer it restores the default (1027x768).


Any solution to this problem? 



Additional information: 

```
$ glxinfo | grep OpenGL

OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Desktop 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 11.0.2
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 11.0.2
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 11.0.2
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:
```




```
$ xrandr
Screen 0: minimum 8 x 8, current 1024 x 768, maximum 32767 x 32767
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VGA1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by grahammechanical on 2016-03-31
> VGA1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm

You are using VGA and from my experience that limits the screen resolution. You should switch to HDMI. That is what I did and now I get

> graham@sdb7-Dev:~$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080     60.05*+  60.00    59.94    50.00    23.97    60.00    50.04  
   1920x1200     59.88  
   1440x480      60.05  
   1400x1050     84.96  
   1280x1024     75.02  
   1280x800      84.88  
   1280x720      60.00    59.94    50.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   720x576       50.00    50.08  
   720x480       59.94    60.05  
   640x480       75.00    72.81    59.94    59.93

Regards

---

### Post by cchance_25 on 2016-03-31
Thanks for replying [**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323").

first of all I don't have an HDMI port in my screen, neither my computer. 

I mentioned that it's works with the full resolution in Windows 7.. What's the difference? 

Is it possible for this problem to occur for any other reason than VGA cable?

---

### Post by RobGoss on 2016-04-01
Hello and welcome, I was reading this post it might be worth taking a look.[http://askubuntu.com/questions/37411/screen-resolution-stuck-at-1024x768]("http://askubuntu.com/questions/37411/screen-resolution-stuck-at-1024x768")

---

### Post by buzzingrobot on 2016-04-01
Different monitors support different resolutions via differerent ports, and the results can vary with OS and driver. VGA typically delivers the lowest resolution. If Display Port is an option, try that.

---

### Post by him610 on 2016-04-01
Normally when the computer boots, the GFXMODE=auto (default); however, sometimes the auto setting is not what is desired. The GFXMODE can be set to a resolution more in line with what the monitor can display. 

Caution: This may or may not work for you. Be careful when using root privileges.

1. Open this file with your editor as root (sudo) 
```
/etc/default/grub
```

2. Locate the line,
```
#GRUB_GFXMODE=640x480
```

3. Directly underneath, add this line...
```
GRUB_GFXMODE=1600x900
```

4. Save the file and exit

5. Execute
```
sudo update-grub
```

6. Reboot your system.

Observe the results, your monitor's resolution should be 1600x900.

---

### Post by cchance_25 on 2016-04-02
Thank you all for your help, unfortunately other ports are not available  since my video card is integrated and only provides a VGA port, my  monitor too.


> **hgh9mrp said:**
> Normally when the computer boots, the GFXMODE=auto (default); however, sometimes the auto setting is not what is desired. The GFXMODE can be set to a resolution more in line with what the monitor can display. 

Caution: This may or may not work for you. Be careful when using root privileges.

1. Open this file with your editor as root (sudo) 
```
/etc/default/grub
```

2. Locate the line,
```
#GRUB_GFXMODE=640x480
```

3. Directly underneath, add this line...
```
GRUB_GFXMODE=1600x900
```

4. Save the file and exit

5. Execute
```
sudo update-grub
```

6. Reboot your system.

Observe the results, your monitor's resolution should be 1600x900.

thank you, so I tried what yo said and unfortunately it didn't help, although I get this error message when I login.

```
Could not apply the stored configuration for monitors
none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 63
CRTC 63: trying mode 1024x768@60Hz with output at 1600x900@60Hz (pass 0)
CRTC 63: trying mode 1024x768@60Hz with output at 1600x900@60Hz (pass 1)
Trying modes for CRTC 64
CRTC 64: trying mode 1024x768@60Hz with output at 1600x900@60Hz (pass 0)
CRTC 64: trying mode 1024x768@60Hz with output at 1600x900@60Hz (pass 1)
Trying modes for CRTC 65
CRTC 65: trying mode 1024x768@60Hz with output at 1600x900@60Hz (pass 0)
CRTC 65: trying mode 1024x768@60Hz with output at 1600x900@60Hz (pass 1)
Trying modes for CRTC 66
CRTC 66: trying mode 1024x768@60Hz with output at 1600x900@60Hz (pass 0)
CRTC 66: trying mode 1024x768@60Hz with output at 1600x900@60Hz (pass 1)
```



My /etc/default/grub file: 
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=1600x900 // Added this line here

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by Bashing-om on 2016-04-02
cchance_25; Hello;

Let me poke my nose in here.
The edit :
> 
GRUB_GFXMODE=1600x900 // Added this line here

IF and IF that is the real edit made to the file,
That line in the config file should read:
```

GRUB_GFXMODE=1600x900

```
in it's simplest form, and could be that nothing else is required. I have made that exact edit, and works well for me.

However, did you read the caution above the line ?
grub's command `vbeinfo'; does it say that 1600x900 is a viable resolution ? Your monitor MUST support this resolution.

[INDENT][INDENT]we look'n for that way
[/INDENT][/INDENT]

---

### Post by cchance_25 on 2016-04-02
> **Bashing-om said:**
> cchance_25; Hello;

Let me poke my nose in here.
The edit :

IF and IF that is the real edit made to the file,
That line in the config file should read:
```

GRUB_GFXMODE=1600x900

```
in it's simplest form, and could be that nothing else is required. I have made that exact edit, and works well for me.

However, did you read the caution above the line ?
grub's command `vbeinfo'; does it say that 1600x900 is a viable resolution ? Your monitor MUST support this resolution.[INDENT][INDENT]we look'n for that way
[/INDENT]
[/INDENT]



Hello and welcome, 

I did exactly what  [**[COLOR=#000000]hgh9mrp[/COLOR]**]("http://ubuntuforums.org/member.php?u=248298")       said, and updated grub.. 

When I login after rebooting I get this message: 

[[IMG]http://store2.up-00.com/2016-04/145962382540281.png[/IMG]]("http://www.up-00.com/") 



And yeah my monitor fully supports the resolution since it works totally fine for me now, and when using windows.

---

### Post by him610 on 2016-04-03
I believe in your situation the capabilities of the GPU/monitor are being exceeded and it reverts to a default (safe) resolution that will not stress you equipment.

What it does in Windows is not relevant to solving your issue.

Please provide make, model, and year of manufacture of your monitor.

Please post the results of
```
inxi -F
```

Please post results of
```
cat /boot/grub/grub.cfg | grep gfxmode
```

Did you actually heed the advice of Bashing-om -
> grub's command `vbeinfo'; does it say that 1600x900 is a viable resolution ? Your monitor MUST support this resolution.

Which means that when you get to the grub menu, you enter "c" which will bring up the real grub screen with 
a grub prompt, 'grub>'...
then you enter ```
vbeinfo
```

It will list all of the resolutions your monitor is capable of. Find the highest resolution, use that in the line GFXMODE=9999x999
Do not add "// some comment" afterwards. If you want to add a comment, add a line above with a preceding crunch "#some comment"

@grahammmechanical - I have connected a couple of different monitors (1440x900 and 1680x1050) to my system using a VGA cable and suffered no limitations; although, reducing the 1680x1050 to 1600x1200 seems to look better.

---

### Post by cchance_25 on 2016-04-03
Here's the inxi -F:
```

$ inxi -F
System:    Host: linux-pc Kernel: 4.2.0-34-generic x86_64 (64 bit)
           Desktop: Unity 7.3.3  Distro: Ubuntu 15.10 wily
Machine:   System: Dell product: OptiPlex 9010 v: 01
           Mobo: Dell model: 0M9KCM v: A01 Bios: Dell v: A22 date: 12/21/2015
CPU:       Quad core Intel Core i7-3770 (-HT-MCP-) cache: 8192 KB 
           clock speeds: max: 3900 MHz 1: 1709 MHz 2: 1659 MHz 3: 1697 MHz
           4: 1749 MHz 5: 1777 MHz 6: 1768 MHz 7: 2133 MHz 8: 1843 MHz
Graphics:  Card: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
           Display Server: X.Org 1.17.2 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1600x900@59.95hz
           GLX Renderer: Mesa DRI Intel Ivybridge Desktop
           GLX Version: 3.0 Mesa 11.0.2
Audio:     Card Intel 7 Series/C210 Series Family High Definition Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.2.0-34-generic
Network:   Card-1: Intel 82579LM Gigabit Network Connection driver: e1000e
           IF: eno1 state: down mac: 90:b1:1c:8c:1d:91
           Card-2: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express)
           driver: ath9k
           IF: wlp2s0 state: up mac: 60:e3:27:c1:03:e8
Drives:    HDD Total Size: 1500.3GB (6.6% used)
           ID-1: /dev/sda model: WDC_WD5000AAKX size: 500.1GB
           ID-2: /dev/sdb model: WDC_WD10EZRZ size: 1000.2GB
Partition: ID-1: / size: 46G used: 6.6G (16%) fs: ext4 dev: /dev/sda5
           ID-2: swap-1 size: 3.68GB used: 0.00GB (0%) fs: swap dev: /dev/sda6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 247 Uptime: 1 day Memory: 1659.3/7870.4MB
           Client: Shell (bash) inxi: 2.2.16

```

```
$ cat /boot/grub/grub.cfg | grep gfxmode
  set gfxmode=1600x900
function gfxmode {
    gfxmode $linux_gfx_mode
        gfxmode $linux_gfx_mode
        gfxmode $linux_gfx_mode
        gfxmode $linux_gfx_mode
        gfxmode $linux_gfx_mode

```

for the grub>vbeinfo; I can't execute the command, I get this message: 
```
grub> vbeifno
vbeifno

Error 27: Unrecognized command
grub> 

```


Thank you

---

### Post by Bashing-om on 2016-04-03
cchance_25; Hey;

What we are asking of you:
> 
for the grub>vbeinfo; I can't execute the command, I get this message: 

The command is not a bash terminal command, rather a 'grub' command. To be executed from the grub prompt ( grub >) .

To get this grub prompt, reboot the machine, and get to the grub menu ( bios is a shift key - EFI the escape key) and press the 'c' key.
With a linux kernel selected as the booting kernel.

You are now at the grub prompt; what returns:
```

vbeinfo

```

We do want to insure that " gfxmode=1600x900 " is an acceptable resolution.

[INDENT][INDENT]all in the right process
[/INDENT][/INDENT]

---

### Post by him610 on 2016-04-03
You neglected to provide the information requested below. It is needed to compare the monitor specs with those of your graphics processor.

> Please provide make, model, and year of manufacture of your monitor.

You used the wrong term from grub, it should have been ```
grub> vbeinfo
```

You do not have Intel HD 4000 Graphics.
Your graphics card > Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller is not a normal consumer grade graphics card; although, Ubuntu lists it in some of its certified systems so there should be a way to get it to work. 
[http://www.ubuntu.com/certification/catalog/component/pci/8086%3A0152]("http://www.ubuntu.com/certification/catalog/component/pci/8086%3A0152")

There are reported issues with this graphics controller that you may want to refer to...
[https://answers.launchpad.net/ubuntu/+question/266765]("https://answers.launchpad.net/ubuntu/+question/266765")

You may have better luck searching for > Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller

My shallow well of knowledge on setting graphics resolution has dried up. Please keep us posted as to your progress. Good luck.

---

### Post by him610 on 2016-04-03
Here is another page you may want to review...
[https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_commands_in_kdm.2BAC8-gdm_startup_scripts]("https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_commands_in_kdm.2BAC8-gdm_startup_scripts")

---

### Post by cchance_25 on 2016-04-04
> **hgh9mrp said:**
> You neglected to provide the information requested below. It is needed to compare the monitor specs with those of your graphics processor.



You used the wrong term from grub, it should have been ```
grub> vbeinfo
```

You do not have Intel HD 4000 Graphics.
Your graphics card  is not a normal consumer grade graphics card; although, Ubuntu lists it in some of its certified systems so there should be a way to get it to work. 
[http://www.ubuntu.com/certification/catalog/component/pci/8086%3A0152](http://www.ubuntu.com/certification/catalog/component/pci/8086%3A0152)

There are reported issues with this graphics controller that you may want to refer to...
[https://answers.launchpad.net/ubuntu/+question/266765](https://answers.launchpad.net/ubuntu/+question/266765)

You may have better luck searching for 

My shallow well of knowledge on setting graphics resolution has dried up. Please keep us posted as to your progress. Good luck.


[[img]http://store1.up-00.com/2016-04/145977847748571.png[/img]](http://www.up-00.com/)[]("http://www.up-00.com/")

Make: Fujistu
Model: L20T-2 LED
Manufacturer Date:  08/08/2010. 


about the graphics card, the computer specs sheet says it has Intel HD 4000

```

             Feature:         9010MT Technical specification: 
             Graphics Card: Integrated Intel® HD Graphics 2500/4000 (3rd generation Core i3/i5/i7 CPUs)


```


vbeinfo is taking a long time, so i'm waiting for the results to come. 



Hopefully i'm not inconveniencing you. 

Thank you for your help.

---

### Post by Bashing-om on 2016-04-04
cchance_25; Hello;

this:
> 
Hopefully i'm not inconveniencing you. 
 
Nope; help is what we do .

Do we have a problem ?
> 
vbeinfo is taking a long time, so i'm waiting for the results to come. 

Should only take a matter of moments .

To address the installed graphic's card; well what the spec sheet says and what is actually installed may be different. Let's see what is:
Post also the result of terminal command:
```

lspci -k | grep -EA2 'VGA|3D'

``` which will explicitly list the graphic's hardware.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by cchance_25 on 2016-04-04
Since I faced a problem with the vbeinfo command, I did little searching  and I found that I could use hwinfo and getting the same output. So I  installed it and ran: 

 ```
sudo hwinfo --framebuffer
```
 I got the following output: 

```

02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.459]
  Unique ID: rdCR.QgFYtsmQZBC
  Hardware Class: framebuffer
  Model: "Intel(R) Sandybridge/Ivybridge Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(R) Sandybridge/Ivybridge Graphics Controller"
  SubVendor: "Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 63 MB + 960 kB
  Memory Range: 0xe0000000-0xe3feffff (rw)
  Mode 0x0360: 848x480 (+896), 8 bits
  Mode 0x0361: 848x480 (+1728), 16 bits
  Mode 0x0362: 848x480 (+3392), 24 bits
  Mode 0x033c: 1920x1440 (+1920), 8 bits
  Mode 0x034d: 1920x1440 (+3840), 16 bits
  Mode 0x035c: 1920x1440 (+7680), 24 bits
  Mode 0x033a: 1600x1200 (+1600), 8 bits
  Mode 0x034b: 1600x1200 (+3200), 16 bits
  Mode 0x035a: 1600x1200 (+6400)  [Created at bios.459]
  Unique ID: rdCR.QgFYtsmQZBC
  Hardware Class: framebuffer
  Model: "Intel(R) Sandybridge/Ivybridge Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(R) Sandybridge/Ivybridge Graphics Controller"
  SubVendor: "Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 63 MB + 960 kB
  Memory Range: 0xe0000000-0xe3feffff (rw)
  Mode 0x0360: 848x480 (+896), 8 bits
  Mode 0x0361: 848x480 (+1728), 16 bits
  Mode 0x0362: 848x480 (+3392), 24 bits
  Mode 0x033c: 1920x1440 (+1920), 8 bits
  Mode 0x034d: 1920x1440 (+3840), 16 bits
  Mode 0x035c: 1920x1440 (+7680), 24 bits
  Mode 0x033a: 1600x1200 (+1600), 8 bits
  Mode 0x034b: 1600x1200 (+3200), 16 bits
  Mode 0x035a: 1600x1200 (+6400), 24 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x037d: 1024x768 (+1024), 8 bits
  Mode 0x037e: 1024x768 (+2048), 16 bits
  Mode 0x037f: 1024x768 (+4096), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown, 24 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x037d: 1024x768 (+1024), 8 bits
  Mode 0x037e: 1024x768 (+2048), 16 bits
  Mode 0x037f: 1024x768 (+4096), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown



```

---

### Post by slickymaster on 2016-04-04
*Moved to the ***Hardware ***sub-forum*

---

### Post by cchance_25 on 2016-04-11
Hello everybody, 

I really thank you guys for helping and sticking with me through my problem. 

After trying every possible solution, every driver and update.. 

I checked on my VGA cable.. there were missing pins on one end, probably two or three broken pins. I replaced the cable and it worked perfectly. Plus, the system now detects the monitor brand.

Thank you all very very much.

---

### Post by Bashing-om on 2016-04-11
cchance_25; Great !

Pleased you found the source of the problem.
Them silly little pins !

[INDENT]just goes to prove
[INDENT][INDENT]software not always at fault
[/INDENT][/INDENT][/INDENT]

---

### Post by cchance_25 on 2016-04-11
> **Bashing-om said:**
> cchance_25; Great !

Pleased you found the source of the problem.
Them silly little pins !
[INDENT]just goes to prove[INDENT][INDENT]software not always at fault
[/INDENT]
[/INDENT]
[/INDENT]


Haha yeah, never expected that!

Thank you <3

---

