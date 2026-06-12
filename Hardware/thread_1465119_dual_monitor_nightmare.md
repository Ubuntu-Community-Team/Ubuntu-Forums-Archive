---
title: "dual monitor nightmare"
date: 2010-04-29
forum: Hardware
---

### Post by samzie on 2010-04-29
Hi everyone, im new to ubuntu and will never go back to the darkside!

My problem is this.  I've tried to get two monitors working for the past week but am unable to. ive followed other threads, carrying out their instructions and nothing seems to get close to solving this.  i can turn either monitors off and on from the nvidia X server display configuration so i am guessing i cant be far off but unable to get both running using twinning or any other mode for that matter. also when i start  system/preferences/display i can only see one monitor. but on x server i can see both. im not sure if theres an issue there.  I've even tried installing envyNG but that never gets past the downloading drivers stage so i give up with that. 

ive got the latest drivers but no luck, still getting.

Failed to set MetaMode (1) 'CRT-0: nvidia-auto-select @1280x1024 +1920+0, DFP-0: nvidia-auto-select @1920x1080 +0+0' (Mode 3200x1080, id: 50) on X screen 0.

ive tried changing the monitor settings on both but but nothing helps, 
also ive tried changing the Xorg.conf but when i do that and restart i usually have to reinstall the orginal the original xorg.conf. because the driver refuses to load. heres my original conf.

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
    Disable    "dri2"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Option    "NoLogo"    "True"
    Driver    "nvidia"
EndSection


im using the latest 173 nvidia driver and this very morning i carried out the latest update ubuntu 9.10 karmic koala, still no luck.  can anyone help me?

Many thanks

Samzie

---

### Post by P4man on 2010-04-29
Which version of ubuntu and which (nvidia) videocard?

BTW, "system/preferences/display" is no longer functional after installing nvidia's proprietary driver, you have to use the nvidia tool instead, that at least is normal.

---

### Post by samzie on 2010-04-29
nvidia Geforce fx agp 5600  173.14.20 and 9.10 karmic koala

---

### Post by Grenage on 2010-04-29
Twinview does often struggle with a couple of screens, but it can usually be rectified bf specifying an EDID file.  At the bottom of this [page]("http://www.grenage.com/xorg.html") (fair warning, that's my site), have a quick look.

---

### Post by Wimz3n on 2010-04-29
I have some issues too with dual screen, so i just got a single q: 
Why can't i use another resolution on my HD-ready TV than on my laptop. If i want another, it's just set to panning the TV (=no movies). 

And samzie: I had a few issues with karmic, so from my point of view, go back to jauntry.

A toss to developers & helpers out there:
Newbies like me wants some info. There are everywhere, but often at a point of level that is pretty uneasy to understand, Which make it hard to actually stick to Linux. It took me one month to actually use Linux on my laptop (celebrating one year Linuxuser tomorrow).

Why is it so hard to make a prog dealing with xorg.conf?

---

### Post by samzie on 2010-04-29
still no luck, i aquired edid file 

i noticed this on the terminal

samzie@main:~$ gksudo nvidia-settings

PARSE ERROR:  Parse error on line 39 of section Module in file /etc/X11/xorg.conf.
"Disable" is not a valid keyword in this section.
 ummm now im stuck

also, if i press "detect settings" nothing happends for either of the selected monitors

Failed to set MetaMode (1) 'CRT-0: nvidia-auto-select @1280x1024 +0+56, DFP-0: nvidia-auto-select @1920x1080 +1560+0' (Mode 3480x1080, id: 51) on X screen 0.

still hapening and my conf is now
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Option    "TwinView"    "1"
    Option    "TwinViewXineramaInfoOrder"    "CRT-0"
    Option    "metamodes"    "CRT-0: 1440x900_75 +0+0, CRT-1: 1440x900_75 +1440+0"
    Option    "CustomEDID"    "CRT-1:/etc/X11/edid.bin"

EndSection

Section "Module"
    Load    "glx"
    Disable    "dri2"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Option    "NoLogo"    "True"
    Driver    "nvidia"
EndSection

added just like it said on your page. any thoughts?

---

### Post by Grenage on 2010-04-29
Hi again.

What is the purpose of this section:

> Section "Module"
Load "glx"
Disable "dri2"
EndSection

Additionally, have you tried using *nvidia-settings*?  The metamode in your config is exactly the same as mine, were you after those exact resolutions?

---

### Post by samzie on 2010-04-29
ok i took section out of the config, now im getting 
samzie@main:~$ gksudo nvidia-settings
       file '/root/.nvidia-settings-rc' (the currently enabled display
       devices are CRT-0 on main:0.0).


ERROR: Invalid display device DFP-0 specified on line 46 of configuration
       file '/root/.nvidia-settings-rc' (the currently enabled display
       devices are CRT-0 on main:0.0).


ERROR: Invalid display device DFP-0 specified on line 47 of configuration
       file '/root/.nvidia-settings-rc' (the currently enabled display
       devices are CRT-0 on main:0.0).


ive just altered my settings to my monitors (not yours) and am gonna restart,  lol wish me luck ...

---

### Post by samzie on 2010-04-29
Failed to set MetaMode (1) 'CRT-0: 1280x1024_75 @1280x1024 +0+0, DFP-0: nvidia-auto-select @1920x1080 +1280+0' (Mode 3200x1080, id: 50) on X screen 0.

tried this too
1)  open a terminal
2)  sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2)  sudo touch /etc/X11/xorg.conf  
3)  sudo nvidia-settings
4)  hit "save configuration"

and got this
ERROR: Cannot open display 'main:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 20 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 21 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 22 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 23 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 24 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 25 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 26 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 27 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 28 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 29 of configuration
       file '/home/samzie/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 30 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GammaCorrectedAALines specified on line 31 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 34 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 35 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 36 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 37 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 38 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 39 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 40 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 41 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 42 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 43 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 44 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 45 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 46 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       47 of configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       48 of configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 49 of
       configuration file '/home/samzie/.nvidia-settings-rc' (no Display
       connection).

lol help!!!

---

### Post by Grenage on 2010-04-29
I've never seen an issue with .nvidia-settings-rc - to be honest I didn't even know it existed!  The references to CRT/DFP will obviously have to match those for your system.

Move .nvidia-settings-rc, call it .nvidia-settings-rc.bak or something.  Then clear out your xorg.conf and try *gksu nvidia-settings* again.

Something has obviously gone horribly wrong, and it's trying to set conditions that aren't there.  After clearing .nvidia-settings-rc and xorg.conf, I imagine your steps 1-4 woud sort it out.  I hope, anyhow.

---

### Post by P4man on 2010-04-29
Sonething else to throw in: in lucid (10.04) the opensource nvidia drivers seemed  quite usable if you dont need too much 3d. It works a treat for compiz and enabled dual monitor automatically on my PC. Then again, my card is a  bit newer (7900) and I did install the proprietary drivers, so its not like I tested extensively. I also seem to recall the opensource drivers causing issues with suspend, not sure if that is fixed meanwhile.

Anyway, im sure you'll get it fixed with Grenage's help, but just a FYI.

---

### Post by Objekt on 2010-04-29
I think the OP probably needs to nuke his xorg config from orbit & start over.

A first step would be to back up the current xorg.conf file, just in case.

If he just renames his existing xorg.conf file to something like xorg.conf.backup, the system should automagically generate a fresh xorg.conf on the next Xserver restart, or prompt him to do so.  

At least that's what I can recall off the cuff.  I'm not sitting in front of my Ubuntu system now, so I can't go into more detail.

---

### Post by samzie on 2010-04-29
i give up,
what ever i do leads to something bigger and badder, im new to unix so its a bit of a struggle, im learning fast but dont understand what im doing right now, perhaps in a few months or somthing or i'll buy a better card, thanks for all the help much appreciated.

Samzie

---

### Post by Grenage on 2010-04-29
Don't give up!  This kind of headache sucks; we know, we've all been there.

Did you try removing the nvidia.rc and xorg files, then following steps 1-4 again?

---

### Post by P4man on 2010-04-29
Consider yourself lucky! some people install ubuntu and everything just works, these poor buggers never learn a thing :p

on a serious note, try the above suggestions.

---

### Post by samzie on 2010-05-06
sorry for the extended delay i installed lynx and it killed my computer,
so ive reinstalled everything and here is my brand new conf.  also. i cant aquire a edid file file from anywhere? do i need one for both monitors or do i acquire from just one?
also same issues as before with :- Failed to set MetaMode (1) 'CRT-0: nvidia-auto-select @1280x1024 +0+0, DFP-0: nvidia-auto-select @1920x1080 +1280+0' (Mode 3200x1080, id: 50) on X screen 0.

config -------------------------
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"Option    "TwinView"    "1"
Option    "TwinViewXineramaInfoOrder"    "CRT-0"
Option    "metamodes"    "CRT-0: 1440x900_75 +0+0, CRT-1: 1440x900_75 +1440+0"
Option    "CustomEDID"    "CRT-1:/etc/X11/edid.bin"

    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "@@@ L7AK2A"
    HorizSync       31.0 - 80.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5600"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"Option    "TwinView"    "1"
Option    "TwinViewXineramaInfoOrder"    "CRT-0"
Option    "metamodes"    "CRT-0: 1440x900_75 +0+0, CRT-1: 1440x900_75 +1440+0"
Option    "CustomEDID"    "CRT-1:/etc/X11/edid.bin"

    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

i cant be far off surely

---

### Post by Grenage on 2010-05-06
If you can't acquire an EDID file, what are you referencing in the xorg.conf?

> Option "CustomEDID" "CRT-1:/etc/X11/edid.bin"

What are your monitor models?

---

### Post by samzie on 2010-05-06
theres is no edid file in /x11 so im guessing i need to make one and put it iin there?  my monitors are

  LG w2343 dfp-0 1920x1080 and l7ak2a crt-0 1280x1024

also get this  if i try to add metamode
&#8226; MetaMode 2 of Screen 0 is the same as MetaMode 1.  All MetaModes must be unique.

this is what my x server settings look like

1Linux-x86
NVIDIA Driver Version:173.14.20
Display Name:samzie-desktop:0Display Name:
Server Version Number:11.0
Server Vendor String:The X.Org 
FoundationServer Vendor Version:1.6.4 (10604000)
---------------------------Resolution:Depth:24GeForce FX 5600 (GPU 0)
x screen 0 information -------------
screen number 0
samzie-desktop:0.0Dimensions1280x1024 pixels (342x271 millimeters)
NV-Control Version:1.16 GPU Errors: 0
X Screens:195x96 dots per inch Recovered GPU errors 0:
Displays:LG W2343 (DFP-0),
 @@@ L7AK2A (CRT-0)

---

### Post by samzie on 2010-05-06
ive search my pc for an edid file without any luck. can i generate one? if so how?

---

### Post by samzie on 2010-05-06
oh well, i lived in hope!

---

### Post by Grenage on 2010-05-06
Hi Samzie!

Sorry for the delay in getting back to you, it's been a bit of day!  I think the best thing I can do, is give you my xorg.conf from work; I'm back in there tomorrow morning.

I'll make the appropriate resolution adjustments to it, and if that doesn't work, I'll explain how best to get the EDID file in place (if required).

Gren.

---

### Post by Grenage on 2010-05-07
The below config is what I imagine it might need to be like.  I was a little surprised that you mentioned both DFP _and_ CRT in your earlier post; normally if two monitors are on one card, they will both be DFP (0 and 1) or CRT (0 and 1).

If the below doesn't work, I'd quite like to see what nvidia-settings gives you as an xorg.conf.

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "LG"
    ModelName      "W2343"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5600"
    Option "VideoOverlay"  "on"
    Option "OpenGLOverlay" "off"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "**CRT-0**"
    Option         "metamodes" "**CRT-0**: 1920x1080_60 +0+0, **CRT-1**: 1280x1024_60 +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by samzie on 2010-05-07
thank you for getting back and helping me, ive your added your config still getting 

Failed to set MetaMode (1) 'CRT-0: nvidia-auto-select @1280x1024 +1920+0, DFP-0: nvidia-auto-select @1920x1080 +0+0' (Mode 3200x1080, id: 50) on X screen 0.

do you wonder if my card is capable of dual view? im starting to wonder? what do you think?

---

### Post by Grenage on 2010-05-07
It does seem rather odd.  If you were to delete the old xorg.conf, recreate it, then run nvidia-settings - can you activate both monitors?

```
sudo rm /etc/X11/xorg.conf
sudo touch /etc/X11/xorg.conf
gksu nvidia-settings
```

---

### Post by samzie on 2010-05-07
i can select each on x server and turn them on or off and set the display res, but obviously not at the same time. i have to select off on one of them to get the other to come on.

i'll try what you have asked and get back right now

---

### Post by samzie on 2010-05-07
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "@@@ L7AK2A"
    HorizSync       31.0 - 80.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5600"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: NULL, DFP: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by samzie on 2010-05-07
i also had a look on a few web pages and they all say it has dual monitor capability. i done a system check to ensure every thing was ok using $sudo lshw
it all looks ok to me

samzie@samzie-desktop:~$ sudo lshw -html > your-file-name.html
[sudo] password for samzie: 
samzie@samzie-desktop:~$ sudo lshw 
samzie-desktop            
    description: Desktop Computer
    product: PCV-RS346(CE)
    vendor: Sony Corporation
    version: To Be Filled By O.E.M.
    serial: 28004250-5000223
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=6029A845-2AF8-D711-BA02-000C6EE2C729
  *-core
       description: Motherboard
       product: P4SD-VX
       vendor: ASUSTek Computer Inc.
       physical id: 0
       version: To be filled by O.E.M.
       serial: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 2002 (09/19/2003)
          size: 64KiB
          capacity: 448KiB
          capabilities: acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: CPU 1
          size: 3GHz
          capacity: 3GHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 8KiB
             capacity: 8KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 2a
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 256MiB
             width: 64 bits
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 512MiB
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f8000000-fbffffff(prefetchable)
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: memory:fc900000-fe9fffff memory:dff00000-efefffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: NV31 [GeForce FX 5600]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list rom
                configuration: driver=nvidia latency=64 maxlatency=1 mingnt=5
                resources: irq:16 memory:fd000000-fdffffff memory:e0000000-e7ffffff(prefetchable) memory:fe9e0000-fe9fffff(prefetchable)
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:e000(size=32)
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:e400(size=32)
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:e800(size=32)
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ec00(size=32)
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:febffc00-febfffff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:a000(size=4096) memory:fea00000-feafffff memory:eff00000-f7efffff(prefetchable)
           *-network:0
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 02
                serial: 00:0c:6e:e2:c7:29
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.69 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
                resources: irq:20 memory:feaff000-feafffff ioport:ac00(size=64)
           *-network:1
                description: Wireless interface
                product: RT2500 802.11g Cardbus/mini-PCI
                vendor: RaLink
                physical id: 9
                bus info: pci@0000:02:09.0
                logical name: wlan0
                version: 01
                serial: 00:13:d3:6e:d0:2c
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2500pci latency=64 multicast=yes wireless=IEEE 802.11bg
                resources: irq:21 memory:feafc000-feafdfff
           *-multimedia
                description: Multimedia video controller
                product: iTVC16 (CX23416) MPEG-2 Encoder
                vendor: Internext Compression Inc
                physical id: a
                bus info: pci@0000:02:0a.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ivtv latency=64 maxlatency=8 mingnt=128
                resources: irq:22 memory:f0000000-f3ffffff(prefetchable)
           *-firewire
                description: FireWire (IEEE 1394)
                product: uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr
                vendor: NEC Corporation
                physical id: e
                bus info: pci@0000:02:0e.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=44 mingnt=20
                resources: irq:18 memory:feafe000-feafefff
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16) memory:40000000-400003ff
           *-disk
                description: ATA Disk
                product: ST3160021A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.04
                serial: 3JS1G76D
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=6f1e15ad
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 1dbb1733-132c-4728-8c2c-bcdf4670a5a5
                   size: 146GiB
                   capacity: 146GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2010-05-06 09:52:10 filesystem=ext3 modified=2010-05-06 12:14:58 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2010-05-07 11:48:51 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2933MiB
                   capacity: 2933MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2933MiB
                      capabilities: nofs
           *-cdrom:0
                description: DVD writer
                product: DVD-RW  DVR-106D
                vendor: PIONEER
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: DVD reader
                product: DVD-ROM GDR8162B
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 0015
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:d400(size=256) ioport:d000(size=64) memory:febff800-febff9ff memory:febff400-febff4ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: ioport:d800(size=256) ioport:dc00(size=128)
     *-scsi
          physical id: 1
          bus info: usb@1:5
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: UMH-U HS-MS
             vendor: Sony
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 2.12
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: UMH-U HS-CF
             vendor: Sony
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdc
             version: 2.12
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             product: UMH-U HS-SM
             vendor: Sony
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdd
             version: 2.12
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
samzie@samzie-desktop:~$ sudo lshw -html > your-file-name.html

---

### Post by Grenage on 2010-05-07
Without both monitors at least being enabled, we're going to have problems.  Were there different revisions of that GFX card, perhaps some without dual-head support?

---

### Post by samzie on 2010-05-07
i think its time to call it a day, i'll invest in a new card soon, im in the middle of moving house so it will have to wait for a couple of months.  thank you for being so helpful though. it was fun trying. again many thanks and all the best.

Samzie

---

### Post by brian11 on 2010-05-07
If you haven’t taken the plunge into doubling up on monitors, you have a few options for doing so, from adding a second video card to your computer, to replacing the old one with a dual card, or just plugging a monitor into your laptop and using its screen as a second monitor. Here’s a primer on how to set up dual monitors. If your boss won’t approve the purchase order for your second monitor at work? Tell her studies show it will increase your productivity.
 Once you’ve got the two screens hooked up, go to your system’s display settings to configure their arrangement. One of the screens will be your “primary” monitor (numbered 1) and then the secondary. Hit the “Identify” button to throw up numbers on each screen letting you know which is which. If one of your monitors is smaller than the other, drag and drop it to align to the top or bottom of its comrade in the same way the screens are physically aligned on your desk, to ensure the smoothest window and mouse movement between the two. In my case, my MacBook Pro is the primary monitor to the bottom right of my widescreen, as pictured (click to enlarge).

---

### Post by samzie on 2010-05-07
thanks Brian! :lolflag:

---

### Post by Iowan on 2010-05-07
Warn or 1-point sig violation. It's too commercial

---

### Post by P4man on 2010-05-07
Iowan, its a bot.

Look here:
[http://www.google.com/search?client=ubuntu&channel=fs&q=If+you+haven%E2%80%99t+taken+the+plunge+into+doubling+up+on+monitors%2C+you+have+a+few+options+for+doing+so%2C+from+adding+a+second+video+card+to+your+computer%2C+t&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=If+you+haven%E2%80%99t+taken+the+plunge+into+doubling+up+on+monitors%2C+you+have+a+few+options+for+doing+so%2C+from+adding+a+second+video+card+to+your+computer%2C+t&ie=utf-8&oe=utf-8)

---

