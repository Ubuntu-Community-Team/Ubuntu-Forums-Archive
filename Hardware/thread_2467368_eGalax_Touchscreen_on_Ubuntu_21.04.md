---
title: "eGalax Touchscreen on Ubuntu 21.04"
date: 2021-09-24
forum: Hardware
---

### Post by bbasbagill on 2021-09-24
**Introduction**
 I spent the last few days rebuilding a car pc using an eGalax touch screen and Ubuntu 21.04.  These touch display controllers have been used for over a decade by a variety of manufacturers.  Anyone who has worked with these can tell you they can be a struggle to get up and running.  There are hundreds of posts across the internet about setting these up but much of the information is fragmented or outdated.  I post this information both as a set of notes to my future self but also in an effort to assist others who may be struggling with the same problems.
 
 **Scope**
 While this information may help troubleshoot other touch screen devices with Ubuntu, I am specifically working with a 7&#8221; eGalax in-dash unit:
 
 ```
lsusb
```
> Bus 003 Device 004: ID 0eef:0001 D-WAV Scientific Co., Ltd Titan6001 Surface Acoustic Wave Touchscreen Controller [eGalax] 
 
 Also I have not been able to get this to work with Wayland, so make sure you are using X11 by selecting &#8220;Ubuntu on Xorg&#8221; instead of &#8220;Ubuntu&#8221; at the login screen by clicking on the little gear icon in the lower right corner (tab and arrows will navigate without a mouse).
 
 **Driver**
 Out of the box with a fresh install of Ubuntu hirsute hippo, this touch panel does nothing.  The HDMI port gives a good display but when you tap on it there is no cursor movement or click action.  From what I can tell, this D-Wav Scientific Co., Ltd is owned by a company called EETI.  Their website can be found at [http://www.eeti.com]("http://www.eeti.com/") and as of this writing they are still actively developing linux drivers for eGalax panels.  If you visit their site, go to the downloads section, accept their license, then navigate to the Linux section you will see a variety of linux driver packages available based on kernel version and architecture.  If you don&#8217;t know what you are running, you can find out with a couple quick commands:
 
 ```
uname -r
```
> 5.11.0-36-generic 
 ```
uname -i
```
> x86_64 
 
 Hover your mouse over the appropriate link on the page to see the direct link to the driver package then you can download it like this:
 
 ```
wget https://www.eeti.com/touch_driver/Linux/20210716/eGTouch_v2.5.10206.L-x.tar.gz 
``` 
 
 After you download the package, unpack it like this (press tab after a few letters of eGTouch to autocomplete):
 
 ```
tar zxvf eGTouch_v2.5.10206.L-x.tar.gz
``` 
 
 Change into the unpacked directory (again use tab to autocomplete):
 
 ```
cd eGTouch_v2.5.10206.L-x
``` 
 
 Now install the driver:

 ```
sudo ./setup.sh
``` 
 
 Agree to the patent declaration, pick USB for the controller, confirm the controller is connected, don&#8217;t bother with monitor rotation or multimonitor, only set up 1 controller, if you are prompted to blacklist a usbtouchscreen module blacklist the module, then reboot the system
 
 ```
sudo shutdown -r now
``` 
 
 **Daemon**
 The latest version of the driver installed the eGTouchD service for me without a problem but many other posts indicate this was a problem in the past.  Verify the eGTouch daemon is running like this:
 
 ```
sudo service eGTouchD status
```
> [COLOR=#000000]&#9679; eGTouchD.service[/COLOR]
 [COLOR=#000000]     Loaded: loaded (/usr/bin/eGTouchD; enabled; vendor preset: enabled)[/COLOR]
 [COLOR=#000000]     Active: active (running) since Fri 2021-09-24 08:16:37 EDT; 4min 56s ago[/COLOR]
 [COLOR=#000000]    Process: 564 ExecStart=/usr/bin/eGTouchD start (code=exited, status=0/SUCCESS)[/COLOR]
 [COLOR=#000000]   Main PID: 584 (eGTouchD)[/COLOR]
 [COLOR=#000000]      Tasks: 2 (limit: 4327)[/COLOR]
 [COLOR=#000000]     Memory: 5.8M[/COLOR]
 [COLOR=#000000]     CGroup: /system.slice/eGTouchD.service[/COLOR]
 [COLOR=#000000]             &#9492;&#9472;584 /usr/bin/eGTouchD start[/COLOR]
[COLOR=#000000]
You should see a green dot, &#8220;loaded&#8221; and &#8220;active&#8221; to indicate that the daemon service is running without a problem, otherwise search online for detailed instructions on how to rebuild it.[/COLOR]
 
 [COLOR=#000000]**Swap Axes**[/COLOR]
 [COLOR=#000000]At this point the driver and daemon load and we can tap on the screen for a click event but the X and Y of the mouse movement is reversed.  The included eGTouchU app is fairly worthless and modern linux no longer uses a single xorg.conf file.  I tried messing around with &#8220;SwapAxes&#8221;&#8220;SwapXY&#8221; and "InvertX""InvertY" options in a variety of other .conf files but had no luck so lets go deeper down the rabbit hole.[/COLOR]
 
 [COLOR=#000000]We can interact with the driver using the command &#8220;xinput&#8221;.  This wasnt included with my default install so I added it like this:[/COLOR]
 
 ```
[COLOR=#000000]sudo apt install xinput[/COLOR]
``` 
 
 [COLOR=#000000]The first thing we need to do is get the ID number for our eGalaxTouch device so we can talk to it.  Just run the command with no options to get a list of devices:[/COLOR]
 ```
[COLOR=#000000]xinput[/COLOR]
```
  > [COLOR=#000000]&#9121; Virtual core pointer                                id=2    [master pointer  (3)][/COLOR]
 [COLOR=#000000]&#9116;   &#8627; Virtual core XTEST pointer                      id=4    [slave  pointer  (2)][/COLOR]
 [COLOR=#000000]&#9116;   &#8627; eGalaxTouch Virtual Device for Single       id=13    [slave  pointer  (2)][/COLOR]

 
 [COLOR=#000000]From this list we can see that the eGalaxTouch device is ID number 13.  Your number will likely be different but you&#8217;ll need to remember it for the following commands. Now we can ask what properties it supports:[/COLOR]
 
 ```
[COLOR=#000000]xinput --list-props 13[/COLOR]
```
>  [COLOR=#000000]Device 'eGalaxTouch Virtual Device for Single':[/COLOR]
 [COLOR=#000000]    Device Enabled (151):    1[/COLOR]
 [COLOR=#000000]    Coordinate Transformation Matrix (153):    0.000000, 1.000000, 0.000000, -1.000000, 0.000000, 1.000000, 0.000000, 0.000000, 1.000000[/COLOR]
 [COLOR=#000000]    libinput Natural Scrolling Enabled (288):    0[/COLOR]
 [COLOR=#000000]    libinput Natural Scrolling Enabled Default (289):    0[/COLOR]
 [COLOR=#000000]    libinput Calibration Matrix (290):    1.200000, 0.000000, -0.050000, 0.000000, 1.090000, -0.050000, 0.000000, 0.000000, 1.000000[/COLOR]
 [COLOR=#000000]    libinput Calibration Matrix Default (291):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000[/COLOR]
 [COLOR=#000000]    libinput Left Handed Enabled (292):    0[/COLOR]
 [COLOR=#000000]    libinput Left Handed Enabled Default (293):    0[/COLOR]
 [COLOR=#000000]    libinput Send Events Modes Available (271):    1, 0[/COLOR]
 [COLOR=#000000]    libinput Send Events Mode Enabled (272):    0, 0[/COLOR]
 [COLOR=#000000]    libinput Send Events Mode Enabled Default (273):    0, 0[/COLOR]
 [COLOR=#000000]    Device Node (274):    "/dev/input/event11"[/COLOR]
 [COLOR=#000000]    Device Product ID (275):    3823, 1[/COLOR]
 [COLOR=#000000]    libinput Drag Lock Buttons (294):    <no items>[/COLOR]
 [COLOR=#000000]    libinput Horizontal Scroll Enabled (295):    1[/COLOR]
 
 [COLOR=#000000]The property we are interested in is the &#8220;Coordinate Tansformation Matrix&#8221;.  You can read about transformation matrices at [https://wiki.ubuntu.com/X/InputCoordinateTransformation](https://wiki.ubuntu.com/X/InputCoordinateTransformation).  [/COLOR][COLOR=#000000]Try different matrices on the fly until you find something that works for you.  For me, using the &#8220;Right Rotate&#8221; matrix solved my swap axes problem:[/COLOR]
 
 ```
[COLOR=#000000]xinput --set-prop 13 &#8220;Coordinate Transformation Matrix&#8221; 0 1 0 -1 0 1 0 0 1[/COLOR]
``` 
 
 [COLOR=#000000]Once you find the Coordinate Transformation Matrix that works for you, we can make it permanent by adding it to the file *52-egalax-virtual-libinput.conf* that was created by the driver installation:[/COLOR]

 ```
[COLOR=#000000]sudo nano /usr/share/X11/xorg.conf.d/52-egalax-virtual-libinput.conf[/COLOR]
```
 
 [COLOR=#000000]Look for the section that has the same name as the device we saw in the xinput list and add a &#8220;TransformationMatrix&#8221; option using the matrix numbers we just discovered:[/COLOR]

 >  [COLOR=#000000]Section "InputClass"[/COLOR]
    [COLOR=#000000]Identifier "eGalax virtual class"[/COLOR]
    [COLOR=#000000]MatchProduct "eGalaxTouch Virtual Device"[/COLOR]
    [COLOR=#000000]MatchDevicePath "/dev/input/event*"[/COLOR]
    [COLOR=#000000]Driver "libinput"[/COLOR]
    **[COLOR=#000000]Option "TransformationMatrix" "0 1 0 -1 0 1 0 0 1"[/COLOR]**
 [COLOR=#000000]EndSection[/COLOR] 
 
 [COLOR=#000000]**Calibration**[/COLOR]
 [COLOR=#000000]At this point we can tap on the display and generate click events as well as move our cursor in the right direction.  However the further we move away from the center of the screen the more inaccurate the mouse movement becomes.  We need to calibrate the panel however the included eGTouchU app is fairly worthless and modern linux no longer uses a single xorg.conf file.  I tried messing around with &#8220;MinX&#8221;&#8221;MaxX&#8221; and &#8220;MinY&#8221;&#8221;MaxY&#8221; options in a variety of other .conf files but had no luck.  We can use the xinput tool again to calibrate our panel, lets jump back down the rabbit hole:[/COLOR]
 
 [COLOR=#000000]This time the property we are interested in is the &#8220;libinput Calibration Matrix&#8221;.  There are some complicated formulas floating around the internet to calculate these matrices however they follow this general format:[/COLOR]
 
 > [COLOR=#000000][x width] 0 [x offset] 0 [y height] [y offset] 0 0 1[/COLOR] 
 
 [COLOR=#000000]It&#8217;s also important to remember that since we rotated everything 90&#8217; in the previous step x becomes vertical and y becomes horizontal.  You can adjust these settings on the fly and experiment until you find something that works for you.  Use increments of 0.1 or -0.1 for small adjustments then smaller numbers to be more exact.  Pay special attention to the mouse position when you tap toward the edges of your screen, I suggest using a stylus instead of your finger for more accurate results:[/COLOR]
 
 ```
[COLOR=#000000]xinput --set-prop 13 &#8220;libinput Calibration Matrix&#8221;  1.2 0 -0.05 0 1.09 -0.05 0 0 1[/COLOR]
```
 
 [COLOR=#000000]Once you find the Calibration Matrix that works for you, we can make it permanent by adding it to the file *52-egalax-virtual-libinput.conf*:[/COLOR]
 
 ```
[COLOR=#000000]sudo nano /usr/share/X11/xorg.conf.d/52-egalax-virtual-libinput.conf[/COLOR]
``` 
 
 [COLOR=#000000]Again, look for the section that has the same name as the device we saw in the xinput list and this time add a &#8220;CalibrationMatrix&#8221; option using the matrix numbers we just discovered:[/COLOR]
 
 > [COLOR=#000000]Section "InputClass"[/COLOR]
 [COLOR=#000000]    Identifier "eGalax virtual class"[/COLOR]
    [COLOR=#000000]MatchProduct "eGalaxTouch Virtual Device"[/COLOR]
    [COLOR=#000000]MatchDevicePath "/dev/input/event*"[/COLOR]
    [COLOR=#000000]Driver "libinput"[/COLOR]
    [COLOR=#000000]Option "TransformationMatrix" "0 1 0 -1 0 1 0 0 1"[/COLOR]
    **[COLOR=#000000]Option "CalibrationMatrix" "1.2 0 -0.05 0 1.09 -0.05 0 0 1"[/COLOR]**
 [COLOR=#000000]EndSection[/COLOR]

Reboot and enjoy your working touch screen.

Edit: formatting cleanup

---

