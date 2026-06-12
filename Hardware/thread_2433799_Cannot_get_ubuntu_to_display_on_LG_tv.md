---
title: "Cannot get ubuntu to display on LG tv"
date: 2019-12-25
forum: Hardware
---

### Post by glubbish on 2019-12-25
The TV is [FONT=Lato]LG 50UM7600PTA 50" UM7600 4K UHD SMART LED TV.

Tried running an existing  18.04.3 LTS install, saw the bios splash, then black screen.

Tried the usb boot for ubuntu, same issue black screen.

Has anyone got ubuntu working with this TV? 
Are there any tricks needed?
I have never had a problem with samsung tv's.

```
Partial Solution

```[/FONT]```
[FONT=Lato]export DISPLAY=:0
xrandr --output DP-1 --mode 1920x1080  --rate 60
This let me get a viewable screen
Still working out how to get it working with 4k[/FONT]
```[FONT=Lato]

[/FONT][FONT=Lato]Finally got a workaround for this by creating a file in ~/.config/autostart
containing 
[/FONT]xrandr --output DP-1 --mode 1920x1080  --rate 60
pactl set-card-profile 0  output:hdmi-surround[FONT=Lato] [/FONT]

---

### Post by CelticWarrior on 2019-12-25
Not enough information.

Which computer? With which graphics? If Nvidia have you installed the proprietary drivers?
How is it connected to the TV?
Is it detected in settings> Devices > Screens?

---

### Post by glubbish on 2019-12-25
It is a nuc, and using the intel cpu/gpu for graphics
Same install worked fine on samsung.

It is connected via HDMI. (same as with samsung).

Not sure how I can check settings, when the display is black.

---

### Post by glubbish on 2020-02-16
Perhaps this can help?

```
$ sudo get-edid | parse-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
No EDID on bus 4
No EDID on bus 5
1 potential busses found: 3
256-byte EDID successfully retrieved from i2c bus 3
Looks like i2c was successful. Have a good day.
Checksum Correct

Section "Monitor"
        Identifier "DENON-AVR"
        ModelName "DENON-AVR"
        VendorName "DON"
        # Monitor Manufactured week 0 of 2018
        # EDID version 1.3
        # Digital Display
        DisplaySize 1600 900
        Gamma 2.20
        Option "DPMS" "false"
        Horizsync 30-135
        VertRefresh 24-120
        # Maximum pixel clock is 300MHz
        #Not giving standard mode: 640x480, 60Hz
        #Not giving standard mode: 800x600, 60Hz
        #Not giving standard mode: 1024x768, 60Hz
        #Not giving standard mode: 1152x864, 60Hz
        #Not giving standard mode: 1280x1024, 60Hz
        #Not giving standard mode: 1920x1080, 60Hz

        #Extension block found. Parsing...
#WARNING: I may have missed a mode (CEA mode 95)
#DOUBLE WARNING: It's your first mode, too, so this may actually be important.
#WARNING: I may have missed a mode (CEA mode 93)
#WARNING: I may have missed a mode (CEA mode 94)
#WARNING: I may have missed a mode (CEA mode 98)
#WARNING: I may have missed a mode (CEA mode 99)
#WARNING: I may have missed a mode (CEA mode 100)
#WARNING: I may have missed a mode (CEA mode 63)
#WARNING: I may have missed a mode (CEA mode 64)
Segmentation fault


$ sudo lshw -c display
  *-display
       description: VGA compatible controller
       product: Iris Pro Graphics 580
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:125 memory:db000000-dbffffff memory:90000000-9fffffff ioport:f000(size=64) memory:c0000-dffff
$
```

---

### Post by wildmanne39 on 2020-02-16
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end, if you are editing a post to add code tags click the edit button then click the go advanced button, highlight the code then select the # symbol from the tool bar.

---

### Post by vidtek on 2020-02-16
glubbish-

What you are saying is that the setup you have now still works on your Samsung tv?

If that is the case then you need to investigate the settings in the menus of your new LG tv.

If it doesn't work on the Samsung either, try another HDMI cable, some are pretty awful quality.

See if it will work on another input, try an old VGA cable or a displayport cable for instance.

If it works on the Samsung but not the LG, maybe you have a problem with the socket on the LG tv?

HDMI can be a problematic interface.

Tony.

---

### Post by webaake on 2020-02-16
Yes, check the LG TV. Once after a Nvidia update I had to move the HDMI to an other port on the TV.

By the way, if the screen is a bit off on the TV, set "Just scan" on the TV picture settings.

---

### Post by glubbish on 2020-02-17
Updated the NUC to dual boot, ubuntu and windows 10.
Windows display's fine on the LG, all the same ports and hardware.

The old samsung was 1080 not 4k, but also works with ubuntu (same ports/hardware).

As the LG screen is black, I cannot check any menu settings, I'm restricted to what I can enter in a putty session.

Summary:
Nuc/ubuntu/hdmi -> denon avr/hdmi -> LG tv. (black screen)
Nuc/windows/hdmi -> denon avr/hdmi -> LG tv. (works).
Nuc/windows/hdmi -> denon avr/hdmi -> Samsung tv (works)

---

### Post by webaake on 2020-02-18
If your LG TV normal menus don't work, there's your problem. Start there.

---

### Post by mastablasta on 2020-02-18
can you boot to text mode form grub. just curious... output is output, and getting text through would tell that at least something is getting to TV

had something similar with Samsung monitor. then i tried different HDMI cable than the one provided. and it all worked. then i took the cable that wasn't working to a computer shop. it worked well there. so i took it back and tried it again and it worked. very strange.

back to your issue - my LG TV has mutiple inputs and they can be set manually. can you do that in TV menu with remote? do you still get blank screen?

intel nuc has intel GPU and these are well supported. if you have a newer one perhaps getting a newer kernel might help. 

i do remember a user having issues with NUC when i also wanted to get one. i forgot what the solution was, bt i remember it was a simple one.

does this page help in any way?: [https://www.intel.com/content/www/us/en/support/articles/000030985/intel-nuc.html](https://www.intel.com/content/www/us/en/support/articles/000030985/intel-nuc.html)

is the install UEFI? it should be according to this. : [https://forums.intel.com/s/question/0D50P0000490DzfSAE/i-have-a-nuc6i3syh-that-boots-up-with-a-blackblank-screen-what-the-heck-is-going-on?language=en_US](https://forums.intel.com/s/question/0D50P0000490DzfSAE/i-have-a-nuc6i3syh-that-boots-up-with-a-blackblank-screen-what-the-heck-is-going-on?language=en_US)

---

### Post by glubbish on 2020-02-18
This is a problem a friend of mine has, he knows even less ubuntu than I do.
But I did the original install for him and tried to boot ubuntu via usb.
It may take variable amounts of time to get requested info.

I have tried ctlr/alt f1 etc but could not get a prompt, still just the blank screen.

I found the inputs on the LG tv somewhat mystifying. They appear to be set up for specific devices. 
However, I believe that part is setup correctly as the windows boot works fine (same NUC, avr, tv etc).

I will try "Disable **Intel iGD** in the BIOS." from the link above. It may be a LG specific issue, that the samsung does not have.
I will get him to check /ect/fstab to check if it was I eufi install (I can't remember, but its likely).

---

### Post by vidtek on 2020-02-18
Glubbish-

You need to use the LG remote control, in the menus you will find a setting for display modes on the various inputs.

The auto setting only works for Windows now, you will have to play around with the settings of ***the TV*** when in Ubuntu.

I VERY much doubt you will get any satisfaction from playing around in the Ubuntu settings, even if you could see them!

It seems to be a refresh rate or horizontal frequency mode problem, the screen will just blank if the tv is unable to display them.

---

### Post by glubbish on 2020-02-23
More info:

nuc:
NUC6i7KYK
BIOS Version: 0066 (Latest) Date: 12/5/2019

There was no option for intel idg in the bios

I tried using the menus on the LG, what a difficult mess that is.
This tv seems to insist that you choose between certain devices, none of which work
I could not find any way to change any setting for the device. 
The manual is next to useless :(

---

### Post by vidtek on 2020-02-24
> **glubbish said:**
> More info:

nuc:
NUC6i7KYK
BIOS Version: 0066 (Latest) Date: 12/5/2019

There was no option for intel idg in the bios

I tried using the menus on the LG, what a difficult mess that is.
This tv seems to insist that you choose between certain devices, none of which work
I could not find any way to change any setting for the device. 
The manual is next to useless :(

My next suggestion would be to return the tv from where you purchased it.  If it is that difficult to operate it is not fit for purpose.

If that is not an option, try this forum: [HTML]https://www.avforums.com/forums/[/HTML]  Post your questions there, maybe someone else has that model and can give you some guidance. 

Sounds like it is quite a dud.

Cheers Tony.

---

### Post by glubbish on 2020-02-29
Managed to get it to display after:
export DISPLAY=:0
xrandr --output DP-1 --mode 1920x1080  --rate 60

so its working for 1080

Prior to this xrandr showed:

chris@kodi:~$ export DISPLAY=:0
chris@kodi:~$ xrandr
Screen 0: minimum 320 x 200, current 3840 x 2160, maximum 8192 x 8192
DP-1 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   3840x2160     30.00*+  25.00    24.00    29.97    23.98
   4096x2160     30.00    25.00    24.00    29.97    23.98
   1920x1080    120.00   100.00   119.88    60.00    50.00    59.94    30.00    25.00    24.00    29.97    23.98
   1920x1080i    60.00    50.00    59.94
   2880x576      50.00
   2880x480      60.00    59.94
   1280x1024     60.02
   1152x864      59.97
   1280x720      60.00    50.00    59.94
   1440x576      50.00
   1024x768      60.00
   1440x480      60.00    59.94
   800x600       60.32
   720x576       50.00
   720x480       60.00    59.94
   640x480       60.00    59.94
   720x400       70.08
DP-2 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
chris@kodi:~$

---

### Post by vidtek on 2020-02-29
> **glubbish said:**
> Managed to get it to display after:
export DISPLAY=:0
xrandr --output DP-1 --mode 1920x1080  --rate 60

so its working for 1080

Prior to this xrandr showed:

chris@kodi:~$ export DISPLAY=:0
chris@kodi:~$ xrandr
Screen 0: minimum 320 x 200, current 3840 x 2160, maximum 8192 x 8192
DP-1 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   3840x2160     30.00*+  25.00    24.00    29.97    23.98
   4096x2160     30.00    25.00    24.00    29.97    23.98
   1920x1080    120.00   100.00   119.88    60.00    50.00    59.94    30.00    25.00    24.00    29.97    23.98
   1920x1080i    60.00    50.00    59.94
   2880x576      50.00
   2880x480      60.00    59.94
   1280x1024     60.02
   1152x864      59.97
   1280x720      60.00    50.00    59.94
   1440x576      50.00
   1024x768      60.00
   1440x480      60.00    59.94
   800x600       60.32
   720x576       50.00
   720x480       60.00    59.94
   640x480       60.00    59.94
   720x400       70.08
DP-2 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
chris@kodi:~$

If this is now solved please mark it so; glad you got it going, where did you get the idea for the solution?
Tony

---

### Post by glubbish on 2020-02-29
not quite solved.
It still does not work with 4k.
Got the idea from the kodi forum
[https://forum.kodi.tv/showthread.php?tid=352003](https://forum.kodi.tv/showthread.php?tid=352003)

---

### Post by vidtek on 2020-02-29
> **glubbish said:**
> not quite solved.
It still does not work with 4k.
Got the idea from the kodi forum
[https://forum.kodi.tv/showthread.php?tid=352003](https://forum.kodi.tv/showthread.php?tid=352003)

It is really helpful for others who may encounter these issues if you write out the steps you have taken to (partially) resolve the situation.  
When they do an internet search this thread will appear in it.
It is all about helping each other.:)
Cheers Tony.

---

### Post by glubbish on 2020-04-25
Still not having a lot of luck with this issue.

Found that running:
xrandr --output DP-1 --mode 1920x1080  --rate 60
from a remote terminal does make the session visible on the tv

But this also changes the sound (pulseaudio) from hdmi to analog and does not work.

I created a script called set_screen_resolution.sh

```
#!/bin/bash
xrandr --output DP-1 --mode 1920x1080  --rate 60
pactl set-card-profile 0  output:hdmi-surround
```

and running this after boot fixes both the display and the sound

I tried to automate this script using crontab -e including
```
@reboot sleep 90 && /home/chris/set_screen_resolution.sh
```

But it does not do anything and xrandr shows the wrong resolution
but if I do ```
$./set_screen_resolution.sh
```
it works fine.

---

### Post by glubbish on 2020-05-10
Finally got a workaround for this by creating a file in ~/.config/autostart
containing 
xrandr --output DP-1 --mode 1920x1080  --rate 60
pactl set-card-profile 0  output:hdmi-surround

---

