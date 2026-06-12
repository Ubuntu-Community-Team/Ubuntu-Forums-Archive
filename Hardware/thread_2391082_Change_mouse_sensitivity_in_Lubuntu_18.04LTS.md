---
title: "Change mouse sensitivity in Lubuntu 18.04LTS"
date: 2018-05-05
forum: Hardware
---

### Post by alynur2 on 2018-05-05
Hi guys, I recently changed my old roller mouse to a cabled Logitech optical mouse and the sensitivity is extremely accelerated. I was able to make changes in 16.04LTS but can't find the instructions to try in 18.04LTS. My memory doesn't work as well as it used to. Any help would be appreciated.
```
albert@albert-desktop:~$ inxi -FzSystem:    Host: albert-desktop Kernel: 4.15.0-20-generic x86_64 bits: 64
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop Mobo: ASRock model: AM1B-M serial: N/A
           BIOS: American Megatrends v: P1.50 date: 04/29/2015
CPU:       Quad core AMD Athlon 5370 APU with Radeon R3 (-MCP-) 
           cache: 2048 KB
           clock speeds: max: 2200 MHz 1: 1050 MHz 2: 951 MHz 3: 922 MHz
           4: 887 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Cedar [Radeon HD 5000/6000/735
0/8350 Series]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
           Resolution: 1024x768@75.03hz, 1024x768@75.03hz
           OpenGL: renderer: AMD CEDAR (DRM 2.50.0 / 4.15.0-20-generic, LLVM 6.0
.0)
           version: 3.3 Mesa 18.0.0-rc5
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Cedar HDMI Audio [Radeon HD 5
400/6300/7300 Series]
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD] FCH Azalia Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 500.1GB (19.9% used)
           ID-1: /dev/sda model: WDC_WD5000AUDX size: 500.1GB
Partition: ID-1: / size: 26G used: 5.0G (21%) fs: ext4 dev: /dev/sda9
           ID-2: swap-1 size: 8.65GB used: 0.00GB (0%)
           fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 22.5C mobo: N/A gpu: 54.5
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 196 Uptime: 36 min Memory: 2036.5/7914.6MB
           Client: Shell (bash) inxi: 2.3.56 



```

---

### Post by #&amp;thj^% on 2018-05-05
You will first need xinput installed if not already there.
Then enter this into the terminal:
Mine shows as follows:
```
**xinput --list --short**
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech M510                           	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Logitech K780                           	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=12	[slave  keyboard (3)]
    &#8627; Logitech K780                  
```
So you need to enter:
```
xinput --list --short
```
Then we can continue changing the value. :)

---

### Post by alynur2 on 2018-05-05
```
 albert@albert-desktop:~$ xinput --list --short&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Generic USB K/B                         	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Generic USB K/B                         	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 Camera: USB2.0 Camera            	id=11	[slave  keyboard (3)]
    &#8627; Generic USB K/B                         	id=12	[slave  keyboard (3)]

```

```
albert@albert-desktop:~$ xinput --list-props 8
Device 'Logitech USB Optical Mouse':
	Device Enabled (141):	1
	Coordinate Transformation Matrix (143):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	libinput Natural Scrolling Enabled (278):	0
	libinput Natural Scrolling Enabled Default (279):	0
	libinput Scroll Methods Available (280):	0, 0, 1
	libinput Scroll Method Enabled (281):	0, 0, 0
	libinput Scroll Method Enabled Default (282):	0, 0, 0
	libinput Button Scrolling Button (283):	2
	libinput Button Scrolling Button Default (284):	2
	libinput Middle Emulation Enabled (285):	0
	libinput Middle Emulation Enabled Default (286):	0
	libinput Accel Speed (287):	0.000000
	libinput Accel Speed Default (288):	0.000000
	libinput Accel Profiles Available (289):	1, 1
	libinput Accel Profile Enabled (290):	1, 0
	libinput Accel Profile Enabled Default (291):	1, 0
	libinput Left Handed Enabled (292):	0
	libinput Left Handed Enabled Default (293):	0
	libinput Send Events Modes Available (263):	1, 0
	libinput Send Events Mode Enabled (264):	0, 0
	libinput Send Events Mode Enabled Default (265):	0, 0
	Device Node (266):	"/dev/input/event2"
	Device Product ID (267):	1133, 49271
	libinput Drag Lock Buttons (294):	<no items>
	libinput Horizontal Scroll Enabled (295):	1



```

---

### Post by #&amp;thj^% on 2018-05-05
Sorry I have been away with another scheduled event today.
But have a look here it is pretty straight forward and allows you to add it to auto start for each reboot: [http://humpty.drivehq.com/promotes/linux/lubuntu-mouse-speed.html](http://humpty.drivehq.com/promotes/linux/lubuntu-mouse-speed.html)
If you have any problems just post back here and I will try to help you sort through it. NOTE: Before you add it to auto start make sure you are happy with the change you make adjusting the Values till you are satisfied.
Good Luck :)

---

### Post by alynur2 on 2018-05-07
Hi 1fallen, this site was more confusing than anything. Here is the script I thought they were suggesting I make:

```
sudo xed MouseConfig.sh

#!/bin/bash
clear
# xset m <acc> <threshold>
  xset m 15/10 0
  xset q | grep acceleration
#xinput --set-ptr-feedback $ID 0 18 10    #(an alternative to xset m)


#Name=Logitech
NAME='Logitech USB OPtical Mouse'


ID=`8 | grep -i $NAME | cut -f2 | cut -c4-| head -n1 `
echo $NAME Mouse ID is 8


xinput --set-prop 8 "Device Accel Profile" 0
xinput --set-prop 8 "Device Accel Constant Deceleration" 2
xinput --set-prop 8 "Device Accel Adaptive Deceleration" 1
xinput --set-prop 8 "Device Accel Velocity Scaling" 5
xinput --list-props 8 | grep Accel



```

When I run it, I get this:
```
albert@albert-desktop ~ $ ./MouseConfig.sh
  acceleration:  15/10    threshold:  0
./MouseConfig.sh: line 11: 8: command not found
grep: USB: No such file or directory
grep: OPtical: No such file or directory
grep: Mouse: No such file or directory
Logitech USB OPtical Mouse Mouse ID is 8
property 'Device Accel Profile' doesn't exist, you need to specify its type and format
property 'Device Accel Constant Deceleration' doesn't exist, you need to specify its type and format
property 'Device Accel Adaptive Deceleration' doesn't exist, you need to specify its type and format
property 'Device Accel Velocity Scaling' doesn't exist, you need to specify its type and format
	libinput Accel Speed (287):	0.000000
	libinput Accel Speed Default (288):	0.000000
	libinput Accel Profiles Available (289):	1, 1
	libinput Accel Profile Enabled (290):	1, 0
	libinput Accel Profile Enabled Default (291):	1, 0


 
```

If I try running xinput --set-prop 8 287  1.0, it has no noticeable effect. If I run xinput --set-prop 8 287 2.0, I get this:

```
albert@albert-desktop ~ $ xinput --set-prop 8 287 2.0
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  131 (XInputExtension)
  Minor opcode of failed request:  57 ()
  Value in failed request:  0x11f
  Serial number of failed request:  19
  Current serial number in output stream:  20



```

---

### Post by #&amp;thj^% on 2018-05-08
Well starting from scratch then, when I begin to set this up I run:
```
xinput --short
```
This shows for my devices:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech K780                           	id=10	[slave  pointer  (2)]
&#9116;   &#8627; [COLOR="#FF0000"]Logitech M510                           	id=14	[slave  pointer  (2)][/COLOR]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=12	[slave  keyboard (3)]
    &#8627; Logitech K780                           	id=13	[slave  keyboard (3)]

``` 
My Mouse is the "Logitech M510                           	id=14"
So now I have the mouse and name also the id# mine is "id=14"
So now I need to make the script via:
```
xed fixmouse.sh
```
I use "xed" as a gui text editor you can use your preferred text editor.
Now I input in the newly opened text editor the needed settings.
Mine are:
```
#!/bin/bash
clear
# xset m <acc> <threshold>
  xset m 15/[COLOR="#FF0000"]14[/COLOR] 0
  xset q | grep acceleration
#xinput --set-ptr-feedback $ID 0 18 [COLOR="#FF0000"]14[/COLOR]    #(an alternative to xset m)

#Name=Logitech
NAME='Logitech M510'

ID=`xinput list --short | grep -i $NAME | cut -f2 | cut -c4-| head -n1 `
echo $NAME Mouse ID is $ID

xinput --set-prop $ID "Device Accel Profile" 0
xinput --set-prop $ID "Device Accel Constant Deceleration" 2
xinput --set-prop $ID "Device Accel Adaptive Deceleration" 1
xinput --set-prop $ID "Device Accel Velocity Scaling" 5
xinput --list-props $ID | grep Accel
```
You see my id's in red, and don't use my id's use what you see with "xinput --short" for your mouse.
Now to be sure the needed permission is set i now run:
```
chmod 775 fixmouse.sh
```
Then I make sure it works with:
```
 ./fixmouse.sh
```
And if all is good I then add the new file to autostart.
BTW: you used "287" as value?? not valid:
```
xinput --set-prop 14 287 2.0
property '287' doesn't exist, you need to specify its type and format
```
I see you was confused, hopefully now it is a bit more clear.

---

### Post by alynur2 on 2018-05-08
I think the confusion may be due to the xinput data in 16.04 and 18.04 are different, like a different format. Here is my xinput --list-props 8 of 16.04

[CODE]albert@albert-desktop ~ $ xinput --list-props 8Device 'Logitech USB Optical Mouse':
	Device Enabled (142):	1
	Coordinate Transformation Matrix (144):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (272):	0
	Device Accel Constant Deceleration (273):	2.500000
	Device Accel Adaptive Deceleration (274):	1.000000
	Device Accel Velocity Scaling (275):	10.000000
	Device Product ID (262):	1133, 49271
	Device Node (263):	"/dev/input/event2"
	Evdev Axis Inversion (276):	0, 0
	Evdev Axes Swap (278):	0
	Axis Labels (279):	"Rel X" (152), "Rel Y" (153), "Rel Vert Wheel" (271)
	Button Labels (280):	"Button Left" (145), "Button Middle" (146), "Button Right" (147), "Button Wheel Up" (148), "Button Wheel Down" (149), "Button Horiz Wheel Left" (150), "Button Horiz Wheel Right" (151), "Button Side" (266), "Button Extra" (267), "Button Forward" (268), "Button Back" (269), "Button Task" (270), "Button Unknown" (265), "Button Unknown" (265), "Button Unknown" (265), "Button Unknown" (265)
	Evdev Scrolling Distance (281):	1, 1, 1
	Evdev Middle Button Emulation (282):	0
	Evdev Middle Button Timeout (283):	50
	Evdev Middle Button Button (284):	2
	Evdev Third Button Emulation (285):	0
	Evdev Third Button Emulation Timeout (286):	1000
	Evdev Third Button Emulation Button (287):	3
	Evdev Third Button Emulation Threshold (288):	20
	Evdev Wheel Emulation (289):	0
	Evdev Wheel Emulation Axes (290):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (291):	10
	Evdev Wheel Emulation Timeout (292):	200
	Evdev Wheel Emulation Button (293):	4
	Evdev Drag Lock Buttons (294):	0

---

### Post by alynur2 on 2018-06-10
It's been a while and nobody seems to be able to solve this problem, so if xinput is requesting a certain format, I guess I need to know what exactly is being requested, which I haven't a clue. Anybody understand this format they are asking for?
Usage: xinputset-prop <device> [--type=atom|float|int] [--format=8|16|32]<property> <val> [<val> ...]

---

### Post by alynur2 on 2018-06-10
Thanks to Binary Java, who solved his own problem, gnome tweaks has the solution.

---

