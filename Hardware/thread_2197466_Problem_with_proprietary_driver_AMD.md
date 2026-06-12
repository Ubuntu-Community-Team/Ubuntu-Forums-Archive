---
title: "Problem with proprietary driver AMD"
date: 2014-01-03
forum: Hardware
---

### Post by scogiam95 on 2014-01-03
Hello everyone, today after some time I decided to reinstall Ubuntu installation performed without errors.
Because with the open driver pc gets too hot, I decided to install the drivers AMD owners following the tutorial included in the official Ubuntu documentation:

```
[COLOR=#555555][FONT=Monaco]Save a backup copy of xorg.conf in case this doesn't work.[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Remove/purge current fglrx and fglrx-amdcccle (If you have used a method outside of aptitude, apt, Software Center or Synaptic, follow the other party's instructions for removal):[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]sudo apt-get remove --purge fglrx fglrx-amdcccle[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]For some users, the fglrx-updates and fglrx-amdcccle-updates packages do not work. If you attempted to install them, also do:[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]sudo apt-get remove --purge fglrx-updates fglrx-amdcccle-updates[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Reboot.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]If you are running 12.04.2 to 13.04, you must install the linux generic headers[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]sudo apt-get install linux-headers-generic[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Install the driver:[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]sudo apt-get install fglrx fglrx-amdcccle[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Generate a fresh xorg.conf BEFORE REBOOTING![/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]sudo aticonfig --initial[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]or:[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]sudo amdconfig --initial[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]If you are using multiple AMD graphics cards or AMD dual graphics (i.e.: notebook users), use:[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]sudo aticonfig --adapter=all --initial[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]or:[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]sudo amdconfig --adapter=all --initial[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Reboot again.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]To confirm the drivers are working open a terminal and type:[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]fglrxinfo[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]You should get an output similar to the following:[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]fglrxinfo [/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]display: :0  screen: 0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]OpenGL vendor string: Advanced Micro Devices, Inc.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]OpenGL renderer string: AMD Radeon HD 6300M Series[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]OpenGL version string: 4.2.11733 Compatibility Profile Context[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Use the Catalyst Control Center to make final adjustments to your monitor setup. If, after rebooting, you are presented with the message "Could not apply the stored configuration for monitors", do not be alarmed. It simply means that you will have to use the Catalyst Control Center to configure your monitors as you should even in the case where this warning is not shown. This most likely to happen with multiple monitor applications (particularly if the monitors are of different sizes) and multiple graphics card applications. ][/FONT][/COLOR]
```

When restart i get a black screen (no backlight), connect a second monitor to the HDMI and it works.




Now you might tell me the solution to get the laptop screen?


fglrxinfo say:

```
[COLOR=#555555][FONT=Monaco]giamma1295@giamma1295-K54HR:~$ fglrxinfo[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]display: :0  screen: 0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]OpenGL vendor string: Advanced Micro Devices, Inc.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]OpenGL renderer string: AMD Radeon HD 6400M Series[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]OpenGL version string: 4.2.12337 Compatibility Profile Context 13.101[/FONT][/COLOR]
```


My xorg.conf:

```
[COLOR=#555555][FONT=Monaco]Section "ServerLayout"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Identifier     "aticonfig Layout"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Screen      0  "aticonfig-Screen[0]-0" 0 0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]EndSection[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]Section "Module"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]EndSection[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]Section "Monitor"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Identifier   "aticonfig-Monitor[0]-0"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "VendorName" "ATI Proprietary Driver"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "ModelName" "Generic Autodetecting Monitor"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "DPMS" "true"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]EndSection[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]Section "Monitor"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Identifier   "0-LVDS"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "VendorName" "ATI Proprietary Driver"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "ModelName" "Generic Autodetecting Monitor"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "DPMS" "true"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "PreferredMode" "1366x768"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "TargetRefresh" "60"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "Position" "1366 0"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "Rotate" "normal"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "Disable" "false"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]EndSection[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]Section "Monitor"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Identifier   "0-DFP1"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "VendorName" "ATI Proprietary Driver"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "ModelName" "Generic Autodetecting Monitor"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "DPMS" "true"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "PreferredMode" "1366x768"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "TargetRefresh" "60"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "Position" "0 0"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "Rotate" "normal"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "Disable" "false"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]EndSection[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]Section "Device"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Identifier  "aticonfig-Device[0]-0"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Driver      "fglrx"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "Monitor-LVDS" "0-LVDS"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "Monitor-DFP1" "0-DFP1"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  BusID       "PCI:1:0:0"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]EndSection[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]Section "Device"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Identifier  "amdcccle-Device[1]-1"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Driver      "fglrx"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Option       "Monitor-LVDS" "0-LVDS"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  BusID       "PCI:1:0:0"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Screen      1[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]EndSection[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]Section "Screen"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Identifier "aticonfig-Screen[0]-0"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Device     "aticonfig-Device[0]-0"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  DefaultDepth     24[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  SubSection "Display"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]     Viewport   0 0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]     Virtual   2966 2966[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]     Depth     24[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  EndSubSection[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]EndSection[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]Section "Screen"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Identifier "amdcccle-Screen[1]-1"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Device     "amdcccle-Device[1]-1"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  DefaultDepth     24[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  SubSection "Display"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]     Viewport   0 0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]     Depth     24[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  EndSubSection[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]EndSection[/FONT][/COLOR]
```

PS:Use ubuntu 13.10

---

### Post by Bashing-om on 2014-01-03
scogiam95; Hi !

Show us what we are working with; Post the out put of terminal codes:
To see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
As we are looking at "AMD Radeon HD 6400M Series" - hybrid graphics (??)  and what driver is loaded.
And will see what can be done.

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

### Post by kaldor on 2014-01-03
Since Fglrx is a terrible mess (and won't likely improve) I recommend you use the open source Radeon driver with DPM enabled. In kernel 3.11, experimental support for Radeon power management has been added. Assuming you remove fglrx and revert to the open source driver, add the following line as a kernel parametre when booting:

```
**radeon.dpm=1**
```

The Radeon driver is much more stable than fglrx. With the new DPM support in kernel 3.11, there's pretty much no reason to bother with the proprietary fglrx anymore.

Some reading material on the topic:

[http://askubuntu.com/questions/324733/how-to-enable-the-radeon-dynamic-power-management-feature-in-ubuntu-13-04](http://askubuntu.com/questions/324733/how-to-enable-the-radeon-dynamic-power-management-feature-in-ubuntu-13-04)

[http://www.phoronix.com/scan.php?page=news_item&px=MTQyNDE](http://www.phoronix.com/scan.php?page=news_item&px=MTQyNDE)

---

### Post by hal8000b on 2014-01-05
Forum is a little slow to load.
Another way to check current driver with inxi :

sudo apt-get install inxi


inxi -Gx


Sample output from Ubuntu 13.10 x64   running on AMD HD5770   PCIe card :

Graphics:  Card: Advanced Micro Devices [AMD/ATI] Juniper XT [Radeon HD 5770] bus-ID: 01:00.0 
           X.Org: 1.14.3 drivers: [COLOR=#0000ff]ati,radeon[/COLOR] (unloaded: fbdev,vesa) Resolution: 1280x1024@60.0hz 
           GLX Renderer: Gallium 0.4 on AMD JUNIPER GLX Version: 3.0 Mesa 9.2.1 Direct Rendering: Yes


Ati or Radeon is the open source driver,  fglrx is the proprieatry or Catalyst driver

---

### Post by scogiam95 on 2014-01-05
Thanks guys for reply!

@[COLOR=#000000]kaldor [/COLOR]with your solution, I got lower temperatures of 10'-15' !


```
giamma1295@giamma1295-K54HR:~$ sensorsacpitz-virtual-0
Adapter: Virtual device
temp1:        +60.0°C  (crit = +88.0°C)


asus-isa-0000
Adapter: ISA adapter
temp1:        +60.0°C  


coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +60.0°C  (high = +80.0°C, crit = +85.0°C)
Core 0:         +60.0°C  (high = +80.0°C, crit = +85.0°C)
Core 1:         +60.0°C  (high = +80.0°C, crit = +85.0°C)


pkg-temp-0-virtual-0
Adapter: Virtual device
temp1:        +61.0°C  


radeon-pci-0100
Adapter: PCI adapter
temp1:        +57.5°C  

```

[COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -C display:
[/FONT][/COLOR]
```
giamma1295@giamma1295-K54HR:~$ sudo lshw -C display
[sudo] password for giamma1295: 
  *-display               
       description: VGA compatible controller
       product: Seymour [Radeon HD 6400M/7400M Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0

       resources: irq:53 memory:c0000000-cfffffff memory:dfe20000-dfe3ffff ioport:d000(size=256) memory:dfe00000-dfe1ffff

```

[COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep -iA3 vga:[/FONT][/COLOR]

```
giamma1295@giamma1295-K54HR:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] [1002:6760]
    Subsystem: ASUSTeK Computer Inc. Radeon HD 7470M [1043:2002]
    Kernel driver in use: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series] [1002:aa98]
```





[COLOR=#000000]inxi -Gx:
[/COLOR]```
giamma1295@giamma1295-K54HR:~$ inxi -GxGraphics:  Card: Advanced Micro Devices [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] bus-ID: 01:00.0 
           X.Org: 1.14.3 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1366x768@60.0hz 
           GLX Renderer: Gallium 0.4 on AMD CAICOS GLX Version: 3.0 Mesa 9.2.1 Direct Rendering: Yes

```

---

### Post by Wizard.Semfe on 2014-02-10
I love you guys! :D
I'm going to try the solution NOW!

---

### Post by ppjdee on 2014-02-10
i think im going to give this a try... im giving up on fglrx until next release.

---

### Post by Bashing-om on 2014-02-10
Wizard.Semfe; ppjdee;

Let us know how it goes, all info is great to have.

[INDENT][INDENT]if at first you do not succeed
[/INDENT][/INDENT]

---

### Post by daniel128 on 2014-03-13
I'm going to try the solution. Thanks.

---

