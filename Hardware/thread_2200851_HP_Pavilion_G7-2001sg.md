---
title: "HP Pavilion G7-2001sg"
date: 2014-01-21
forum: Hardware
---

### Post by timmay2 on 2014-01-21
Hello, I just recently switched from Windows to Ubuntu and the System works quite well, besides of my hybrid graphics card.  First off I better start with my system.  



 

 [PHP]

 HP Pavillion G7-2001sg Hardware [http://h20565.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay?javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken&javax.portlet.prp_ba847bafb2a2d782fcbb0710b053ce01=wsrp-navigationalState%3DdocId%253Demr_na-c02780857-1%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.tpst=ba847bafb2a2d782fcbb0710b053ce01&ac.admitted=1390315990850.876444892.492883150](http://h20565.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay?javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken&javax.portlet.prp_ba847bafb2a2d782fcbb0710b053ce01=wsrp-navigationalState%3DdocId%253Demr_na-c02780857-1%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.tpst=ba847bafb2a2d782fcbb0710b053ce01&ac.admitted=1390315990850.876444892.492883150)

 
Ubuntu 13.10 (Saucy Salamander)

 Kernel: 3.11.0-15-generic 


It seems that my Notebook is one of the few that uses a pure ATI Hybrid and not a ATI-Intel like in 99% of the other machines. The problem is that I cant change my grafics. Ubuntu does recognise the right cards, at least Ubuntu tells me the right hardware. 
[PHP]
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250] (prog-if 00 [VGA controller])
        Kernel driver in use: radeon
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] (prog-if 00 [VGA controller])
        Kernel driver in use: radeon
[/PHP]
Drivers 
[PHP]
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RS880
OpenGL core profile version string: 3.1 (Core Profile) Mesa 9.2.1
OpenGL core profile shading language version string: 1.40
OpenGL core profile context flags: (none)
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 9.2.1
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
[/PHP]

Screen resolutions
[PHP]
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
        load detection: 1 
                range: (0, 1)
LVDS connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 382mm x 215mm
        EDID: 
                00ffffffffffff0030e47a0200000000
                00130103802615780aa8c09d58509a26
                1c505400000001010101010101010101
                0101010101012f2640b860840c303030
                23007ed7100000190000000000000000
                00000000000000000000000000fe0000
                00004c47446973706c61790a000000fe
                004c503137335744312d544c433300c2
        scaling mode: Full 
                supported: NoneFullCenterFull aspect
   1600x900       60.1*+
   1440x900       59.9  
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 disconnected (normal left inverted right x axis y axis)
        underscan vborder: 0 
                range: (0, 128)
        underscan hborder: 0 
                range: (0, 128)
        underscan: off 
                supported: offonauto
        coherent: 1 
                range: (0, 1)
[/PHP]


 

Now If I try to switch between the cards with switcheroo I get some odd problems. The screen just keeps beeing black and I have to restart the system. Then the system starts normal again but uses the IGD Mobility Radeon HD 4225/4250 again. 

Switcheroo seems to be instelled correctly 

[PHP]
timmay@Lappy3000L:~$ sudo grep -i switcheroo /boot/config-3.* 
[sudo] password for timmay: 
/boot/config-3.11.0-12-generic:CONFIG_VGA_SWITCHEROO=y 
/boot/config-3.11.0-15-generic:CONFIG_VGA_SWITCHEROO=y 
/boot/config-3.2.0-23-generic:CONFIG_VGA_SWITCHEROO=y 
/boot/config-3.2.0-58-generic:CONFIG_VGA_SWITCHEROO=y 
timmay@Lappy3000L:~$ 
timmay@Lappy3000L:~$ sudo ls -l /sys/kernel/debug/vgaswitcheroo/switch 
-rw-r--r-- 1 root root 0 Jan 13 19:34 /sys/kernel/debug/vgaswitcheroo/switch 
timmay@Lappy3000L:~$ 
[/PHP]

This is how I do it. 

[PHP]
PRE.ctl { font-family: "Lohit Hindi",monospace; }P { margin-bottom: 0.21cm; }   root@Lappy3000L:~# cat /sys/kernel/debug/vgaswitcheroo/switch 
0:IGD:+:Pwr:0000:01:05.0 
1:DIS: :Pwr:0000:02:00.0 
root@Lappy3000L:~# 
[/PHP]

both cards do have power and both of them seem the be recognised. Now if I try to switch to the DIS card “nothing” happens. The Plus is still located at the IGD Card 

[PHP]
PRE.ctl { font-family: "Lohit Hindi",monospace; }P { margin-bottom: 0.21cm; }   root@Lappy3000L:~# echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch 
root@Lappy3000L:~# cat /sys/kernel/debug/vgaswitcheroo/switch 
0:IGD:+:Pwr:0000:01:05.0 
1:DIS: :Pwr:0000:02:00.0 
[/PHP]

maybe this is just because I have to restart the x-server/ log out and in again before the change is performed. But if I do that my screen just keeps beeing black and I have to restadt the system.  
Now I tried to use Prime to test if it works that way. I Installed Steam on my system and tried it with a sourceengine (HalfLife2 engine) game (No more room in hell).  So I entered the “DRI_PRIME=1 %command%” command in the start property’s of the game. The screen turns black when I start the game but I can still see the courser. The game itself works, I can hear the sound of the gamemenu ect. 
When I force to close the game the desktop appears again – system works fine. 



There is also another “bug” that may help to find the problem. When I use my Laptop as it is intended (working without direct power supply, using the battery) I swith the power for the DIS card off to save erngery and also reduce heat. If my Laptop switches then into the sleep-mode and I “wake it up” again I get a strange error message. The screen stays black for 1 or 2 minutes and it tells me this. Than the desktops starts normal.

> 
[905.328578][FirmwareBug]:cpu1. Try to use APIC500 (LVT offset 0) for vector 0x400, but the register is already in use for Vector 0xf9 on the other CPU. 
[905.341968][FirmwareBug]:cpu2. Try to use APIC500 (LVT offset 0) for vector 0x400, but the register is already in use for Vector 0xf9 on the other CPU. 
[905.355264][FirmwareBug]:cpu3. Try to use APIC500 (LVT offset 0) for vector 0x400, but the register is already in use for Vector 0xf9 on the other CPU. 
[1263 XXXX][FirmwareBug]:cpu1. Try to use APIC500 (LVT offset 0) for vector 0x400, but the register is already in use for Vector 0xf9 on the other CPU. 
[1263 XXXX][FirmwareBug]:cpu2. Try to use APIC500 (LVT offset 0) for vector 0x400, but the register is already in use for Vector 0xf9 on the other CPU. 
[1263 XXXX][FirmwareBug]:cpu3. Try to use APIC500 (LVT offset 0) for vector 0x400, but the register is already in use for Vector 0xf9 on the other CPU. 
[1408 XXXX][FirmwareBug]:cpu1. Try to use APIC500 (LVT offset 0) for vector 0x400, but the register is already in use for Vector 0xf9 on the other CPU. 
[1408 XXXX][FirmwareBug]:cpu2. Try to use APIC500 (LVT offset 0) for vector 0x400, but the register is already in use for Vector 0xf9 on the other CPU.
[1408 XXXX][FirmwareBug]:cpu3. Try to use APIC500 (LVT offset 0) for vector 0x400, but the register is already in use for Vector 0xf9 on the other CPU.  
[1502 XXXX][FirmwareBug]:cpu1. Try to use APIC500 (LVT offset 0) for vector 0x400, but the register is already in use for Vector 0xf9 on the other CPU. 
[1502 XXXX][FirmwareBug]:cpu2. Try to use APIC500 (LVT offset 0) for vector 0x400, but the register is already in use for Vector 0xf9 on the other CPU. 
[1502 XXXX][FirmwareBug]:cpu3. Try to use APIC500 (LVT offset 0) for vector 0x400, but the register is already in use for Vector 0xf9 on the other CPU. 



The XXX is just a placeholder, I couldn’t write it down fast enough but you get idea. Thanks for ideas an help.

---

