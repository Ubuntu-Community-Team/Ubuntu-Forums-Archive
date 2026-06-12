---
title: "Low Resolution with Ubuntu 9.10"
date: 2009-11-03
forum: Hardware
---

### Post by Sebastian Burch on 2009-11-03
Hello! I have just installed Ubuntu 9.10 on Toshiba satellite  SA20-S103. I am having problems with the resolution, System/Dislplay wont let me choose a higher resolution than 800x600, I would love to have my 1024×768 back. 

The graphics card is  a trident "ALi Cyberblade Aladdin Ai1.

If anyone could help me solve this problem.

---

### Post by RedSingularity on 2009-11-03
Look in system>Admin>Hardware Drivers.  See if you can load a propietary driver.  If not post the output of 

lspci | grep VGA

---

### Post by Sebastian Burch on 2009-11-04
1.- There isn't any proprietary drivers to load in system>Admin>Hardware Drivers

2.- The Output of lspci | grep VGA

01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)


Thank you!

---

### Post by RedSingularity on 2009-11-04
Post the output of 

cat /etc/X11/xorg.conf

---

### Post by Sebastian Burch on 2009-11-04
The output of  (cat /etc/X11/xorg.conf )  is:

cat: /etc/X11/xorg.conf: No such file or directory


Which doesn't makes sense to me, so I don't know what to do now. Thank you.

---

### Post by RedSingularity on 2009-11-04
Make sure you type it just like thiis.....

cat /etc/X11/xorg.conf

---

### Post by Sebastian Burch on 2009-11-04
I think I have. In the terminal I wrote exactly:

sebastian@sebastian-laptop:~$ **cat /etc/X11/xorg.conf**

and this is the output I get:

cat: /etc/X11/xorg.conf: No such file or directory


What can I be doing wrong? Thank you.

---

### Post by RedSingularity on 2009-11-04
Hmmm maybe you dont have a xorg file.  Thats odd.  Try......... gedit /etc/X11/xorg.conf

---

### Post by Sebastian Burch on 2009-11-04
It does open the Xorg.conf file:

[IMG]https://files.one.ubuntu.com/3fde524b-b20e-4329-a8b3-de2625664e6b[/IMG]

I guess I just need to write in it. thank you

---

### Post by Sebastian Burch on 2009-11-04
I did it and this is what I get:

sebastian@sebastian-laptop:~$ sudo apt-get install ubuntu-desktop
[sudo] password for sebastian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
sebastian@sebastian-laptop:~$ sudo apt-get reinstall ubuntu-desktop
E: Invalid operation reinstall
sebastian@sebastian-laptop:~$ 

thank you

---

### Post by dylan_newb on 2009-11-04
try 
```
cvt 1024 768 
```
 the output should look like 
```
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

```
copy whats after modeline
```
"1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

```
put it after xrandr --newmode
```
 xrandr --newmode"1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

```
then 
```
 xrandr --addmode lvcd1 1024x768_60.00

```
go to display and see if it worked

---

### Post by Sebastian Burch on 2009-11-04
I did every step, and its fine until the last command

Code:

 
 xrandr --addmode lvcd1 1024x768_60.00

Output:

xrandr: cannot find output "lvcd1"


Thank you.

---

### Post by RedSingularity on 2009-11-04
> **Sebastian Burch said:**
> I did it and this is what I get:

sebastian@sebastian-laptop:~$ sudo apt-get install ubuntu-desktop
[sudo] password for sebastian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
sebastian@sebastian-laptop:~$ sudo apt-get reinstall ubuntu-desktop
E: Invalid operation reinstall
sebastian@sebastian-laptop:~$ 

thank you


If you want to try reinstalling the ubuntu desktop software do it this way.........

sudo apt-get install --reinstall ubuntu-desktop

---

### Post by Sebastian Burch on 2009-11-04
I am going to try changing the Xorg.conf

following this [http://ubuntuforums.org/showthread.php?t=269052](http://ubuntuforums.org/showthread.php?t=269052)

Because reinstalling the desktop software hasn't done any changes.

---

### Post by swilleyman on 2009-11-04
Try running

sudo Xorg -configure

to generate a completely filled out xorg.conf

It should detect the capabilities of your display and put the proper modes into the xorg.conf explicitly.

---

### Post by Sebastian Burch on 2009-11-04
This is what I get:

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log


I wonder?...

Thank you.

---

### Post by GuerreiroZ on 2009-11-04
I'm having the same problem and errors than Sebastian Burch. I followed the steps in the topic, but did not work.

---

### Post by irvin on 2009-11-04
I have a similar problem using 9.10 as a VM in Virtualbox

Any ideas how to get a higher Resolutuion without the Guest Additions ?
I'm asking because I use Ubuntu 9.10 as a guest and connect to them via x11vnc.
But when I install then GA I can't use "right mouse click" anymore.

I tried the xorg.conf but this won't work in 9.10 anymore. When I make this my Gnome crashes and I don't have a desktop anymore.
There's talk about a new monitors.xml file which keeps the settings, but i tried with this a lot and it doesn't take effect.
As I have 2 resolutions 640x480 and 800x600 from the start. Where's the file for this input ?
No one really seems to know.

---

### Post by RedSingularity on 2009-11-04
> **Sebastian Burch said:**
> It does open the Xorg.conf file:

[IMG]https://files.one.ubuntu.com/3fde524b-b20e-4329-a8b3-de2625664e6b[/IMG]

I guess I just need to write in it. thank you


Can you post the contents of xorg?

---

### Post by geoffree on 2009-11-04
[QUOTE=Sebastian Burch;8240958]

Since ver. 9.0 there have been problems with changing monitor resolution. The settings of 600x800 and 400x600 seem to be defaults in the instructions.  But it's possible to change things.

Check out this document: "HOWTO: change resolution/refresh rate in Xorg"

Also: Find your monitors manual (manufacturers website and Google are useful). Look for horizontal sync and vertical refresh rates, also if bandwidth or maximum dot clock / pixel clock is mentioned.

What I did was to follow suggestion of "fabricator4" who advised editing the xorg.conf file. I did the following:

"sudo gedit /etc/X11/xorg.conf"

In the monitor section, type in your own Horiz and Vert range. Mine was: 

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync     31-101
    VertRefresh    60-160
EndSection

Save.  Then, Ctrl-Alt-Fx to get a terminal. Enter your name and password. Type:  "sudo /etc/init.d/gdm stop".  Enter.  The GUI display will stop. Then type "sudo /etc/init.d/gdm start". And Ctrl-Alt-F7 to bring up the GUI display screen.  

I hope this is helpful.  If not check out the posts by searching for "monitor resolution".

geoffree

---

### Post by dylan_newb on 2009-11-05
> **Sebastian Burch said:**
> I did every step, and its fine until the last command

Code:

 
 xrandr --addmode lvcd1 1024x768_60.00

Output:

xrandr: cannot find output "lvcd1"


Thank you.

for me it was vga1 for some its dvi1 
but you said it was on a laptop right? 
maybe lvcd-0  
or put ```
 lspci
```
and put the output on here

---

### Post by Sebastian Burch on 2009-11-05
The Xorg.conf file is blank.

---

### Post by Sebastian Burch on 2009-11-05
sebastian@sebastian-laptop:~$  lspci
00:00.0 Host bridge: ALi Corporation M1672 Northbridge [CyberALADDiN-P4]
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:09.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 USB Controller: NEC Corporation USB (rev 43)
00:0c.1 USB Controller: NEC Corporation USB (rev 43)
00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)

---

### Post by trevelyan on 2009-11-05
apparently Karmic doesnt have a Xorg.conf file with settings by default but will use it if you create one (or for example if NVIDIA propietary driver install creates it) so do this...

```

press ctrl+alt+F1

```
to start in a console. log in with your user name and password. then do this:
```

sudo service gdm stop

```
to stop the gdm service. then this:
```

sudo Xorg -configure

```
to create a new xorg.conf with your settings. onces this is created, karmic will use it.then to go back to your normal session:
```

sudo service gdm start

```

after this you will have your xorg.conf file in the usual directory. then if you need to add settings to it you can and Karmic will use those settings.

hope this helps. let us know.

---

### Post by Sebastian Burch on 2009-11-05
Thank you_ _treleyan that was very helpful!

The problem persists. I cant get System/preferences/Display to show a 1024x768 resolution.

Thank you.

---

### Post by DarthBrady on 2009-11-05
I installed 9.10 on a friend's PC who wants to switch from windows. All is great, except I am having the exact same problem as Sebastian. The highest resolution is 800x600. My screen (vizio P50 HD20A) has a native res of 1366x768, but 1024x768 would also work great. 

I have followed all the instructions given on this thread just as Sebastian, with the same results as he posted.  I would be glad to help if I can as I obviously have the same problem. Also, I tried the tip on stopping the gdm and the 'Xorg -configure' command, but still don't have a Xorg.conf file.

---

### Post by gabak on 2009-11-05
follow this instruction

sudo gedit /etc/X11/xorg.conf


Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	HorizSync    30-63
	VertRefresh  56-71
	#UseModes     "Modes0" #monitor0usemodes
	Option      "PreferredMode" "1024x768"
	EndSection

Section "Modes"
	Identifier "Modes0"
	#modes0modeline0
EndSection

Section "Device"
	### Available Driver options are:-
	### Values: i: integer, f: float, bool: "True"/"False",
	### string: "String", freq: "f Hz/kHz/MHz"
	### [arg]: arg optional
	#Option     "NoAccel"            	# [bool]
	#Option     "SWcursor"           	# [bool]
	#Option     "ColorKey"           	# i
	#Option     "CacheLines"         	# i
	#Option     "Dac6Bit"            	# [bool]
	#Option     "DRI"                	# [bool]
	#Option     "NoDDC"              	# [bool]
	#Option     "ShowCache"          	# [bool]
	#Option     "XvMCSurfaces"       	# i
	#Option     "PageFlip"           	# [bool]
	Identifier  "Card0"
	Driver      "intel" #card0driver
	VendorName  "Intel Corporation"
	BoardName   "82865G Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
   Identifier "Screen0"
   Device     "Card0"
   Monitor    "Monitor0"
   DefaultDepth 24
   Subsection "Display"
      Depth       24
      Modes       "1024x768"
   EndSubsection
EndSection

---

### Post by gabak on 2009-11-05
make that new file
then write copy and paste all i have wrote.
plz let me know if it worked for you

---

### Post by dylan_newb on 2009-11-06
do all the steps i told before but the last one.
do this one instead 
```
xrandr --addmode AGP1 1024x768_60.00
```

---

### Post by Sebastian Burch on 2009-11-06
sebastian@sebastian-laptop:~$ xrandr --addmode AGP1 1024x768_60.00
xrandr: cannot find output "AGP1"

---

### Post by Sebastian Burch on 2009-11-06
I added the changes to wrote on  Xorg, but it didnt work. That isn't my graphic card or drivers.

---

### Post by Heretical on 2009-11-06
Sebastian do what gabak said. I had exactly the same problem with you. I am trying to solve it for a month now... and finally I can change my resolution! Gabak I love you. :D. And may I ask you something else. How can I have one more choice of 1280x1024 ? Thank you.

---

### Post by quintas on 2009-11-07
> **Sebastian Burch said:**
> I did every step, and its fine until the last command

Code:

 
 xrandr --addmode lvcd1 1024x768_60.00

Output:

xrandr: cannot find output "lvcd1"


Thank you.

Hey Seb,
Same problem here. Instead of LDVSs VGAs DVIs or whatever I used "default" and it recognized the output. Thing this happened afterwards:
"Failed to change the screen configuration!"
Hope u get better luck than mine...

---

### Post by Yan_Suryana on 2009-11-07
I just Install Ubuntu 9.10 and got the same problem with my Screen Resolution to 800X600.

It works fine now after create xorg.conf using the intruction by GABAK.

Thank You GABAK . .

but now I have another problem, I can't create root password as I did when using Ubuntu 9.04.

Please advise.

---

### Post by Yan_Suryana on 2009-11-07
> **gabak said:**
> make that new file
then write copy and paste all i have wrote.
plz let me know if it worked for you

It Works fine now to get more than 800 X 600  
Bravo Gabak . . .

But I still can't set the Root Password , even Generate Random Password . .

---

### Post by zman58 on 2009-11-07
> **Yan_Suryana said:**
> It Works fine now to get more than 800 X 600  
Bravo Gabak . . .

But I still can't set the Root Password , even Generate Random Password . .

Why do you want to set the root password? I never have needed to do that on any system. If you want to run as root, then use sudo. You should never need the root password or a root desktop. If you want a root shell then use:
[INDENT]sudo bash[/INDENT]

---

### Post by zman58 on 2009-11-07
I installed Ubuntu 9.10 on an older system with a multi-sync monitor--a Viewsonic "PF790". I had an older nvidia adapter on that system. For some reason the nvidia install did not give me a monitor section in the xorg.conf file. The resolution was very low and I could not bump it up to 1280x1024. As a solution I had to add a monitor section and display subsection into my xorg.conf. Now I have the desired 1280x1024 resolution. I included the xorg.conf from that system below.

I added the Monitor line within the Section "Screen"
I added the entire Subsection "Display" in Section "Screen"
I added the entire Section "Monitor" to define the monitor.
Edit as you need for you monitor and system.
The HorizSync and VertRefresh settings came from the PF790 monitor specifications.
This worked perfectly for me.

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
	Monitor "PF790"
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Monitor"
	Identifier "PF790"
	Vendorname "Viewsonic"
	Modelname "PF-790"
	HorizSync 30-97
	VertRefresh 50-160
EndSection

```

---

### Post by anujv73 on 2009-11-07
hi i have live CD for ubuntu and its resolution is 640x340 due to that i cant installation manual properly, i have change in live cd /etc/x11/xorg.conf file but i dont know how to restart xorg ,i try alt+ctrl+bkspace but it wont work, pls anyone how to restart from command prompt any else soultion

---

### Post by DarthBrady on 2009-11-07
Well, this problem is solved, for me!

I am really busy at the moment so I will post my solution's details later, but until then I can say:

-the 'xrandr' fix works as listed in the first page of this thread. just make sure you have a space between your mode name and the --addmode and --newmode commands. BUT, these changes will not be present after to reboot.

to fix it permanently, i used the Ctrl+Alt+F1 method to stop the gdm and use the xorg -configure command to create a Xorg.conf file.
NOTE: this method creates a "Xorg.conf.new" in your home directory with 9.10 karmic. to make it work, open this file as sudo with gedit, paste in gabak's code over the default code to replace it. then, save and rename to Xorg.conf, and move the file to /etc/X11/ -after I did this and rebooted I have all resolutions I needed.

the only thing I did different really was change the "1024x768" in gabak's code to "1366x768." now I have 648x480/800x600/1024x768/1368x768. all work perfect.

---

### Post by Yan_Suryana on 2009-11-08
> **zman58 said:**
> Why do you want to set the root password? I never have needed to do that on any system. If you want to run as root, then use sudo. You should never need the root password or a root desktop. If you want a root shell then use:
[INDENT]sudo bash[/INDENT]

I can set my root password using: sudo passwd root.
Thanks anyway . .

---

### Post by Cheltspy on 2009-11-08
I had the same problem with a LCD television have found a work around with the following steps. 

1. use xrandr to return your adaptor

xrandr
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 8192 x 8192
VGA1 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3  
   640x480        59.9  
   1920x1200_60.00   59.9* 
DVI1 disconnected (normal left inverted right x axis y axis)

2. get your mode with cvt

cvt 1920 1200 60
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
 
3. using xrandr add this mode.
xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync 
xrandr --addmode VGA1 "1920x1200_60.00"

4. change to this mode using System>Preferences>Display


5.Once you are happy then start Terminal and logon with

sudo bash (then your password)

cd / 

cd /etc/gdm/Init

gedit Default

Insert line the xrandr lines before initctl

xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync 
xrandr --addmode VGA1 "1920x1200_60.00"


here are some generic modes for LCD televisions that could be added (use with care!!!)
  

#modes for VGA/HDMI Televisions/ Generic
# VGA modes
xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --newmode "1600x1200_60.00"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync
# 1920x1200 16x10 will display as 1600x1200 on many LCD panels
xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync

# DVI1 modes
xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync


#VGA1 Out
xrandr --addmode VGA1 "1024x768_60.00"   
xrandr --addmode VGA1 "1280x1024_60.00"  
xrandr --addmode VGA1 "1600x1200_60.00"  
xrandr --addmode VGA1 "1920x1200_60.00"
#DVI1 out 720p and 1080p
xrandr --addmode DVI1 "1280x720_60.00" 
xrandr --addmode DVI1 "1920x1080_60.00"

---

### Post by Phoenix23GF on 2009-11-27
Ok, so I tried everything recommended by gabak and the other users here.  I tried one version where Xorg created my xorg.conf file and another where nvidia created the xorg.conf file.  Both times I made the appropriate edits and nothing is working out.

I have an LG-W3000H monitor (2560x1600 native res) and I'm currently stuck at 1280x800.  If anyone has any suggestions please let me know.  I'll post my current xorg.conf file below in case there's a seriously stupid error I made and it's easily correctable.

One final note, I am running the video through a KVM switch but it is a DVI port.  The other computer (running windows vista) recognizes the 2560x1600, but I didn't have the KVM switch installed when I installed windows.  Think it's a problem with the detection? i.e. plug the monitor directly into the computer, create the xorg.conf file then hook the KVM switch up?  I didn't think it would matter but it might.

[xorg.conf]

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Fri Aug 14 17:54:58 PDT 2009

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath      "/usr/lib/xorg/modules"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "built-ins"
EndSection

Section "Module"
    Load           "glx"
    Load           "dbe"
    Load           "extmod"
    Load           "record"
    Load           "dri2"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"    
    Identifier "Monitor0"
    VendorName "Monitor Vendor"
    ModelName "Monitor Model"
    HorizSync 30-63
    VertRefresh 56-71
    #UseModes "Modes0" #monitor0usemodes
    Option "PreferredMode" "2560x1600"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "FlatPanel"              # [<bool>]
        #Option     "FPDither"               # [<bool>]
        #Option     "CrtcNumber"             # <i>
        #Option     "FPScale"                # [<bool>]
        #Option     "FPTweak"                # <i>
        #Option     "DualHead"               # [<bool>]
    Identifier     "Card0"
    Driver         "nvidia"
    VendorName     "nVidia Corporation"
    BoardName      "NV40 [GeForce 6800 Ultra]"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Card0"
    Monitor "Monitor0"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "2560x1600"
    EndSubsection
EndSection
```

---

### Post by rizalbrandan on 2009-12-08
Hello Sebastian

I have same problem with you, and same machine, mine toshiba dynabook satellite 1800

i used to ubuntu 8.04 and with some trick i have 1024x768 resolution but when i switch to karmic, i have same problem with u 

here try this :

1.  use and run ubuntu livecd that your machine can display 1024x768 mode (mine 8.04 with some tricks) 

2. copy xorg.conf file from /etc/X11 to flashdisk

3. shutdown livecd and run ubuntu 9.10

4. copy xorg.conf from flashdisk to /etc/X11

5.  restart GDM   sudo /etc/init.d/gdm restart

6. and try to set system>preference>display and change to 1024x768 mode


it work for me .... try yours .......

---

### Post by umair4a11 on 2009-12-14
> **gabak said:**
> follow this instruction

sudo gedit /etc/X11/xorg.conf


Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync    30-63
    VertRefresh  56-71
    #UseModes     "Modes0" #monitor0usemodes
    Option      "PreferredMode" "1024x768"
    EndSection

Section "Modes"
    Identifier "Modes0"
    #modes0modeline0
EndSection

Section "Device"
    ### Available Driver options are:-
    ### Values: i: integer, f: float, bool: "True"/"False",
    ### string: "String", freq: "f Hz/kHz/MHz"
    ### [arg]: arg optional
    #Option     "NoAccel"                # [bool]
    #Option     "SWcursor"               # [bool]
    #Option     "ColorKey"               # i
    #Option     "CacheLines"             # i
    #Option     "Dac6Bit"                # [bool]
    #Option     "DRI"                    # [bool]
    #Option     "NoDDC"                  # [bool]
    #Option     "ShowCache"              # [bool]
    #Option     "XvMCSurfaces"           # i
    #Option     "PageFlip"               # [bool]
    Identifier  "Card0"
    Driver      "intel" #card0driver
    VendorName  "Intel Corporation"
    BoardName   "82865G Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
   Identifier "Screen0"
   Device     "Card0"
   Monitor    "Monitor0"
   DefaultDepth 24
   Subsection "Display"
      Depth       24
      Modes       "1024x768"
   EndSubsection
EndSection


Hi Gapak.
Thanx alot Dear..
It Works for me. now i have my fav resolution. 
advise to all newbies, try mentioned above trick and thy will find every thing right then :)
Once again thanks ;)

---

### Post by omgurindanger on 2009-12-19
I have the same problem here as well with the max res. I can get is 800x600

I have tried following the steps below
1) cvt 1280 800
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync

2) xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
2) xrandr --addmode default 1280x800_60.00
3) xrandr -s 1280x800
Failed to change the screen configuration

I also have tried Gabak's method, which I have seen couple reply here it worked for them.  But I could not get them to work too.

I checked the log file, it shows
Fatal server error:
no screens found

My video card is 
lspic | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

I have tried finding the SIS driver, I found one here in this forum, but was not working as well.

EDIT:
the driver I found is in this thread, [http://ubuntuforums.org/showthread.php?t=1135091](http://ubuntuforums.org/showthread.php?t=1135091)

problem SOLVED:
[http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads](http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads)
choose this one, [xorg-driver-sisimedia_0.9-1_i386.deb]("http://ncc-1701a.homelinux.net/%7Elinux-sis/downloads/xorg-driver-sisimedia_0.9-1_i386.deb")
install, then everything is OK.

---

### Post by chandra on 2009-12-25
Thank you, Cheltspy, for your post at [http://ubuntuforums.org/showpost.php?p=8271792&postcount=41](http://ubuntuforums.org/showpost.php?p=8271792&postcount=41)

I am running Kubuntu 9.10 with a GeForce4 MX 440 card and a Philips 190 S7 LCD monitor.

The monitor has a preferred mode of 1280 by 1024 at 60 Hz.

I have had to use the line 

xrandr --addmode default "1280x1024_60.00"

to get the vertical refresh rate to 59.5 Hz on the KDE RandR tool.

My difficulty is that I do not have an Init file like you do in GNOME as stated below.

> **Cheltspy said:**
> 
5.Once you are happy then start Terminal and logon with

sudo bash (then your password)

cd / 

cd /etc/gdm/Init

gedit Default

Insert line the xrandr lines before initctl

xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync 
xrandr --addmode VGA1 "1920x1200_60.00"


How may I do the equivalent in KDE 4.3.2 on Kubuntu so tht my system wakes up with a vertical refresh rate of 60 Hz rather than 50 Hz as at present.

As an aside, I might add that X and the nvidia driver seem to think it is a CRT rather than an LCD monitor. Any hints on how to set this correctly are most appreciated as well.

Many thanks for your help.

---

### Post by Lemuel111 on 2010-03-29
> **rizalbrandan said:**
> Hello Sebastian

I have same problem with you, and same machine, mine toshiba dynabook satellite 1800

i used to ubuntu 8.04 and with some trick i have 1024x768 resolution but when i switch to karmic, i have same problem with u 

here try this :

1.  use and run ubuntu livecd that your machine can display 1024x768 mode (mine 8.04 with some tricks) 

2. copy xorg.conf file from /etc/X11 to flashdisk

3. shutdown livecd and run ubuntu 9.10

4. copy xorg.conf from flashdisk to /etc/X11

5.  restart GDM   sudo /etc/init.d/gdm restart

6. and try to set system>preference>display and change to 1024x768 mode


it work for me .... try yours .......

Does anybody have a read out for xorg.conf file from 8.04 to save doing all the above?? Then I could just work from point 4. onwards. Cheers.

---

### Post by Lemuel111 on 2010-03-29
I've downloaded 8.04 & can see several folders titled X11 but which one will have the appropriate file in?

---

### Post by Lemuel111 on 2010-05-24
Does anyone know if the latest ubuntu will solve this low resolution problem?

---

### Post by drubdrub on 2010-10-17
These steps worked perfectly on 10.10.
[LIST]
[*]Sceptre X24WG, 1920 x 1200
[*]Intel 82865G
[/LIST]


> **Cheltspy said:**
> I had the same problem with a LCD television have found a work around with the following steps. 

1. use xrandr to return your adaptor

xrandr
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 8192 x 8192
VGA1 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3  
   640x480        59.9  
   1920x1200_60.00   59.9* 
DVI1 disconnected (normal left inverted right x axis y axis)

2. get your mode with cvt

cvt 1920 1200 60
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
 
3. using xrandr add this mode.
xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync 
xrandr --addmode VGA1 "1920x1200_60.00"

4. change to this mode using System>Preferences>Display

5.Once you are happy then start Terminal and logon with

sudo bash (then your password)
cd / 
cd /etc/gdm/Init
gedit Default

Insert line the xrandr lines before initctl

xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync 
xrandr --addmode VGA1 "1920x1200_60.00"

... stuff deleted ...


---

### Post by Lemuel111 on 2010-10-21
> **drubdrub said:**
> These steps worked perfectly on 10.10.
[LIST]
[*]Sceptre X24WG, 1920 x 1200
[*]Intel 82865G
[/LIST]

Have tried the above and got as far as point number 4 and the error message "could not be applied CRTC 263" came up. 

Any suggestions?

Thanks.

---

### Post by stallinux on 2011-02-09
The solution of dylan_newb (#11) works perfectly. This way I adjusted the resolution of my Ati 9600XT graphics card to 1280x1024 (my monitor does not take higher res). Thanks. Just to summarise:
(BTW: Also works with Ubuntu 10.10; hope a Google search brings you here: Ati 9600 Ubuntu low resolution problem fixed)

cvt 1280 1024

which replied with:
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

then (cut and paste)

xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

xrandr --addmode VGA-0 1280x1024_60.00

(VGA-0 was found by xrandr without options)

after which the resolution could be changed in the menu System > Preferences > Display (Ubuntu 9.10, or Monitors in Ubuntu 10.10)

---

