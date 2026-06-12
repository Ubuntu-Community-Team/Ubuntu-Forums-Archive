---
title: "New LCD screen"
date: 2019-06-01
forum: Hardware
---

### Post by eka55 on 2019-06-01
[COLOR=#242729][FONT=Arial]I bought a new LCD screen and now my computer's screen goes black for 1 second randomly. I am using dual boot and windows 8.1 works without any error, also my old LCD screen didn't have any kind of this problem. I have tried another new LCD screen and it had the same issue. Should I renew driver or something?[/FONT][/COLOR]

---

### Post by Autodave on 2019-06-01
Please give us some info:

1. What are your machine specs?
2. What is the make and model of new monitor?
3. How is monitor connected to PC: what cables and adapters (if any)?

---

### Post by eka55 on 2019-06-02
1. Laptop is Asus X555LDB.
2. I do not know exactly what is the model. 
3. It is connected with 16 pin screen cable.

If model of the monitor can be the reason of the problem, I'll try to take it apart and find it out, but as windows works fine, I think that the new model fits well.

---

### Post by Autodave on 2019-06-02
Ok.  That machine supposedly has a NVIDIA® GeForce® 820M with 2GB DDR3  VRAM.  Have you installed any drivers for the Nvidia crad?  If so, what one and where did you get it from?

What version of 'buntu are you running?

---

### Post by eka55 on 2019-06-02
After changing a monitor, I haven't installed anything. Ubuntu 18.04 is running.

---

### Post by Autodave on 2019-06-02
Go into Settings -> Additional Drivers.  See what is installed or what installs.

---

### Post by eka55 on 2019-06-02
"No additional drivers available."

---

### Post by Autodave on 2019-06-02
Under Settings: do you have an Nvidia control panel?

---

### Post by oldfred on 2019-06-02
post these:
       #To see video:
lspci -vnn | grep VGA -A 12
sudo lshw -c display
lspci | grep VGA
#Resolution:
xwininfo -root
xrandr -q
xrandr --q1
#What is installed
dkms status

---

### Post by eka55 on 2019-06-03
[IMG]https://ibb.co/pxmn1hs[/IMG]https://ibb.co/pxmn1hs 
Do you mean this setting? There is no Nvidia control panel.

---

### Post by eka55 on 2019-06-03
**lspci -vnn | grep VGA -A 12**
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 5500 [8086:1616] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. HD Graphics 5500 [1043:236a]
	Flags: bus master, fast devsel, latency 0, IRQ 50
	Memory at f5000000 (64-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	[virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915


00:03.0 Audio device [0403]: Intel Corporation Broadwell-U Audio Controller [8086:160c] (rev 09)
	Subsystem: ASUSTeK Computer Inc. Broadwell-U Audio Controller [1043:19ad]

**sudo lshw -c display**
  *-display                 
       description: VGA compatible controller
       product: HD Graphics 5500
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:50 memory:f5000000-f5ffffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff
  *-display
       description: 3D controller
       product: GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:49 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:d000(size=128) memory:f7000000-f707ffff



**lspci | grep VGA**
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 5500 (rev 09)



**xwininfo -root**


xwininfo: Window id: 0x17c (the root window) (has no name)


  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1366
  Height: 768
  Depth: 24
  Visual: 0x41
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x40 (installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1366x768+0+0

**xrandr -q**
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
eDP-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
   1366x768      59.99 +  40.00* 
   1360x768      59.80    59.96  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)



**xrandr --q1**
 SZ:    Pixels          Physical       Refresh
*0   1366 x 768    ( 345mm x 194mm )   60  *40  
 1   1360 x 768    ( 345mm x 194mm )   60  
 2   1280 x 720    ( 345mm x 194mm )   120  60  
 3   1024 x 768    ( 345mm x 194mm )   120  60  
 4    960 x 720    ( 345mm x 194mm )   120 
 5    928 x 696    ( 345mm x 194mm )   120 
 6    896 x 672    ( 345mm x 194mm )   120 
 7   1024 x 576    ( 345mm x 194mm )   120  60  
 8    960 x 600    ( 345mm x 194mm )   120 
 9    960 x 540    ( 345mm x 194mm )   120  60  
 10   800 x 600    ( 345mm x 194mm )   120  60   56  
 11   840 x 525    ( 345mm x 194mm )   120 
 12   864 x 486    ( 345mm x 194mm )   60  
 13   800 x 512    ( 345mm x 194mm )   120 
 14   700 x 525    ( 345mm x 194mm )   120 
 15   800 x 450    ( 345mm x 194mm )   120 
 16   640 x 512    ( 345mm x 194mm )   120 
 17   720 x 450    ( 345mm x 194mm )   120 
 18   700 x 450    ( 345mm x 194mm )   120 
 19   640 x 480    ( 345mm x 194mm )   120  60  
 20   720 x 405    ( 345mm x 194mm )   60   59  
 21   684 x 384    ( 345mm x 194mm )   120 
 22   680 x 384    ( 345mm x 194mm )   120 
 23   640 x 400    ( 345mm x 194mm )   120 
 24   576 x 432    ( 345mm x 194mm )   120 
 25   640 x 360    ( 345mm x 194mm )   120  60   59  
 26   512 x 384    ( 345mm x 194mm )   120 
 27   512 x 288    ( 345mm x 194mm )   120 
 28   480 x 270    ( 345mm x 194mm )   119  120 
 29   400 x 300    ( 345mm x 194mm )   121  113 
 30   432 x 243    ( 345mm x 194mm )   120  119 
 31   320 x 240    ( 345mm x 194mm )   120 
 32   360 x 202    ( 345mm x 194mm )   119  118 
 33   320 x 180    ( 345mm x 194mm )   120  119 
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - X Axis Y Axis

**dkms status **is empty

---

### Post by oldfred on 2019-06-03
You have Intel internal graphics & nVidia card. If 620 the Intel is better, if 720 then nVidia slightly better.
[URL="https://www.videocardbenchmark.net/compare/Intel-HD-5500-vs-GeForce-GT-720/2908vs2896"]https://www.videocardbenchmark.net/compare/Intel-HD-5500-vs-GeForce-GT-720/2908vs2896
https://www.videocardbenchmark.net/compare/Intel-HD-5500-vs-GeForce-GT-720-vs-GeForce-GT-620/2908vs2896vs1429[/URL]

But you are using nVidia with nouveau open source driver. Often better to install & use nVidia driver.
If you install or reinstall a nVidia driver, you must purge the old one first or you have conflicts and major issues.

       If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by eka55 on 2019-06-03
**sudo ubuntu-drivers autoinstall**
No drivers found for installation.

I have manually installed **nvidia, 410.104, 4.15.0-47-generic, x86_64: installed. **I am not sure whether I did right or not, but the problem still exists :(

---

### Post by oldfred on 2019-06-03
How did you install, from Ubuntu repository?

---

### Post by eka55 on 2019-06-04
At first I was following [https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946) this link. And on final step, I tried to install latest version of nvidia with following command:
sudo apt install nvidia-driver-410

---

### Post by oldfred on 2019-06-04
Did you only install one driver? Or purge before installing second?
Mine is an older card so 390 is newest I can use.

product: GF108 [GeForce GT 620]
configuration: driver=nvidia latency=0

```
fred@bionic-z97:~$ dkms status
nvidia, 390.116, 4.15.0-48-generic, x86_64: installed
nvidia, 390.116, 4.15.0-50-generic, x86_64: installed

```
Does yours now show installed?

You can search on what is best driver for your card. And then add ppa so you can install that version.
       nVidia install, purge if installing newer driver.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

---

### Post by eka55 on 2019-06-05
Yes, I have installed only one.

elene@elenes-asus:~$ dkms status
nvidia, 410.104, 4.15.0-47-generic, x86_64: installed

I was trying to install best match with:
sudo ubuntu-drivers autoinstall
but as I have mentioned, it gives me ** No drivers found for installation**.
Is there any other way to find the best driver for my card?

---

### Post by oldfred on 2019-06-05
If you add the ppa this should then show more/newer drivers.
       [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
# make sure system is up to date
sudo apt-get update
sudo apt-get upgrade 
   sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update 
    
 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 


# should show newest versions available in addition
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX  

    
 # If later you do not want ppa, how to uninstall ppa
sudo add-apt-repository --remove ppa:graphics-drivers/ppa

---

### Post by drvshrm on 2019-06-06
Are you connecting it with USB cable or HD Cable??

---

### Post by eka55 on 2019-06-06
I have already tried these commands and finally installed nvidia-410 manually, I was not able to find any better match.

---

### Post by eka55 on 2019-06-06
It is connected with 16 pin screen cable.

---

### Post by oldfred on 2019-06-06
HDMI, DVI, displayport, VGA?
Some connectors work better than others. 
Most video cards have two different connectors and most displays have two inputs.

---

