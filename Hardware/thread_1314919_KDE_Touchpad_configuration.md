---
title: "KDE Touchpad configuration"
date: 2009-11-04
forum: Hardware
---

### Post by patsissons on 2009-11-04
I just installed kubuntu karmic the other night and the only thing that i can't figure out so far is the touchpad.  I seem to remember earlier kubuntu releases (possibly even 9.04) allowing configuration of the touchpad on a laptop.  Mostly i just want to disable the touchpad's tap-to-click feature.  So if there is another way to do this outside of the system settings in kde, that is fine too.

thanks for any help.

---

### Post by Sefianix on 2009-11-05
[http://ubuntuforums.org/showthread.php?t=1046677](http://ubuntuforums.org/showthread.php?t=1046677)

Unfortunately, at this time it seems there's no GUI to set touchpad options.  create the fdi file in the post and fill it with the xml listed.  It worked for me.

---

### Post by edd07 on 2009-11-05
There is a GUI, but it's GTK+ (it will still run on Kubuntu,though)
It's called gsynaptics:
```
sudo apt-get install gsynaptics
```
Run the command to configure your touchpad and then add gsynaptics-init to your Autostart programs in System Settings.

Hope this helps

---

### Post by patsissons on 2009-11-05
yea i had read about gsynaptics, but unfortunately, my problem runs deeper than this, it is actually and issue with the ALPS touchpad not being recognized.

as for this particular issue, i also discovered the following programs:

[http://bitbucket.org/lunar/synaptiks/wiki/Home](http://bitbucket.org/lunar/synaptiks/wiki/Home)

[http://www.kde-apps.org/content/show.php/kcm_touchpad?content=113335](http://www.kde-apps.org/content/show.php/kcm_touchpad?content=113335)

obviously i cannot test these out, but it they look pretty solid.

---

### Post by patsissons on 2009-12-07
finally some new info on this topic.  I finally managed to get my touchpad properly recognized (it only took modifying the alps part of the psmouse kernel module, so it would recognize the updated e7 signature).  So now gsynaptics finally works, but unfortunately, only partially.  It will disable the touchpad, but i really wanted to disable the tap to click.  Or even better, disable the tap to click while typing.  i will have to check on the kubuntu add ons that i posted earlier to see if they will work.  i guess i will report back once i have given them a go.

for reference, this is to disable the tap-to-click (and maybe configure some other multi-touch gestures on an alps touchpad for an hp mini 311).  If anyone is interested in how i got the driver working properly just let me know and i will go into details.  I have read that this driver mod will work with gnome (although on an hp dm1, not a mini 311, same touchpad tho).  so there might be some light left at the end of the tunnel.

---

### Post by Zorael on 2009-12-08
I'm unfamiliar with ALPS pads. Once you modified the module to make it register as a touchpad properly, does xinput offer any options? Synaptics pads have lots of them that you can toggle in userspace, without having to enable shared memory or any of its ilk.
```
$ xinput list-props 8
Device 'SynPS/2 Synaptics TouchPad':
        Device Enabled (97):    1   
        Synaptics Edges (243):  1752, 5192, 1620, 4236
        Synaptics Finger (244): 24, 29, 255           
        Synaptics Tap Time (245):       180           
        Synaptics Tap Move (246):       221           
        Synaptics Tap Durations (247):  180, 180, 100 
        Synaptics Tap FastTap (248):    0             
        Synaptics Middle Button Timeout (249):  75    
        Synaptics Two-Finger Pressure (250):    280   
        Synaptics Two-Finger Width (251):       7     
        Synaptics Scrolling Distance (252):     100, 100
        Synaptics Edge Scrolling (253): 1, 0, 0         
        Synaptics Two-Finger Scrolling (254):   0, 0    
        Synaptics Move Speed (255):     0.400000, 0.700000, 0.009952, 40.000000
        Synaptics Edge Motion Pressure (256):   29, 159                        
        Synaptics Edge Motion Speed (257):      400, 800                       
        Synaptics Edge Motion Always (258):     0                              
        Synaptics Button Scrolling (259):       1, 1                           
        Synaptics Button Scrolling Repeat (260):        1, 1                   
        Synaptics Button Scrolling Time (261):  100                            
        Synaptics Off (262):    0                                              
        Synaptics Guestmouse Off (263): 0                                      
        Synaptics Locked Drags (264):   0                                      
        Synaptics Locked Drags Timeout (265):   5000                           
        Synaptics Tap Action (266):     0, 3, 0, 0, 1, 2, 3                    
        Synaptics Click Action (267):   1, 1, 1                                
        Synaptics Circular Scrolling (268):     0                              
        Synaptics Circular Scrolling Distance (269):    0.100000               
        Synaptics Circular Scrolling Trigger (270):     0                      
        Synaptics Circular Pad (271):   0                                      
        Synaptics Palm Detection (272): 1                                      
        Synaptics Palm Dimensions (273):        10, 199                        
        Synaptics Coasting Speed (274): 45.000000                              
        Synaptics Pressure Motion (275):        29, 159
        Synaptics Pressure Motion Factor (276): 1.000000, 1.000000
        Synaptics Grab Event Device (277):      1
        Synaptics Gestures (278):       1
        Synaptics Capabilities (279):   1, 1, 1, 1, 1
        Synaptics Pad Resolution (280): 110, 100
        Synaptics Area (281):   0, 0, 0, 0
```

I mean, even a standard mouse has options to a certain extent.
```
$ xinput list-props 7
Device 'Macintosh mouse button emulation':
        Device Enabled (97):    1
        Evdev Axis Inversion (232):     0, 0
        Evdev Axis Calibration (233):
        Evdev Axes Swap (234):  0
        Evdev Middle Button Emulation (235):    2
        Evdev Middle Button Timeout (236):      50
        Evdev Wheel Emulation (237):    0
        Evdev Wheel Emulation Axes (238):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (239):    10
        Evdev Wheel Emulation Timeout (240):    200
        Evdev Wheel Emulation Button (241):     4
        Evdev Drag Lock Buttons (242):  0
```
(In this case it's the "Macintosh mouse button emulation" device, but a standard Logitech USB mouse has the same options.)

---

### Post by patsissons on 2009-12-09
yes xinput does list a bunch of props for the (now recognized) device:

```
xinput list-props 2                                                                                                                      
Device 'ImPS/2 ALPS GlidePoint':                                                                                                                     
        Device Enabled (93):    1                                                                                                                    
        Synaptics Edges (226):  40, 983, 41, 726                                                                                                     
        Synaptics Finger (227): 12, 14, 127                                                                                                          
        Synaptics Tap Time (228):       180                                                                                                          
        Synaptics Tap Move (229):       56
        Synaptics Tap Durations (230):  180, 180, 100
        Synaptics Tap FastTap (231):    0
        Synaptics Middle Button Timeout (232):  75
        Synaptics Two-Finger Pressure (233):    139
        Synaptics Two-Finger Width (234):       7
        Synaptics Scrolling Distance (235):     25, 25
        Synaptics Edge Scrolling (236): 1, 0, 0
        Synaptics Two-Finger Scrolling (237):   0, 0
        Synaptics Move Speed (238):     0.400000, 0.700000, 0.039124, 40.000000
        Synaptics Edge Motion Pressure (239):   14, 79
        Synaptics Edge Motion Speed (240):      1, 102
        Synaptics Edge Motion Always (241):     0
        Synaptics Button Scrolling (242):       1, 1
        Synaptics Button Scrolling Repeat (243):        1, 1
        Synaptics Button Scrolling Time (244):  100
        Synaptics Off (245):    0
        Synaptics Guestmouse Off (246): 0
        Synaptics Locked Drags (247):   0
        Synaptics Locked Drags Timeout (248):   5000
        Synaptics Tap Action (249):     0, 3, 0, 0, 1, 2, 3
        Synaptics Click Action (250):   1, 1, 1
        Synaptics Circular Scrolling (251):     0
        Synaptics Circular Scrolling Distance (252):    0.100000
        Synaptics Circular Scrolling Trigger (253):     0
        Synaptics Circular Pad (254):   0
        Synaptics Palm Detection (255): 0
        Synaptics Palm Dimensions (256):        10, 99
        Synaptics Coasting Speed (257): 0.000000
        Synaptics Pressure Motion (258):        14, 79
        Synaptics Pressure Motion Factor (259): 1.000000, 1.000000
        Synaptics Grab Event Device (260):      1
        Synaptics Area (261):   0, 0, 0, 0
        Synaptics Capabilities (262):   1, 1, 1, 0, 0
        Synaptics Jumpy Cursor Threshold (263): 0
```

im currently looking at touchfreeze and will try to modify it to work with the 311.  It doesn't seem to disable the tap-to-click stuff, but it is able to disable the touchpad, so i may just change it to do that while typing.

---

### Post by Zorael on 2009-12-09
I'm not sure how it'll work with your modified driver, but as for disabling taps, you can either disable tapping completely or set the tap time to 0.
```
Synaptics Tap Action (249):     0, 3, 0, 0, 1, 2, 3   # I think; top right, bottom right, bottom left, top left, one finger, two fingers, three fingers
Synaptics Tap Time (228):       180 
```
```
$ xinput set-int-prop "ImPS/2 ALPS GlidePoint" "Synaptics Tap Action" 8 0 0 0 0 0 0 0

$ xinput set-int-prop "ImPS/2 ALPS GlidePoint" "Synaptics Tap Time" 32 0
```
If you just modified the Synaptics driver to recognize your ALPS pad as a Synaptics device, this may just plain not work at all. YMMV.

---

### Post by rinseaid on 2009-12-10
> **patsissons said:**
> finally some new info on this topic.  I finally managed to get my touchpad properly recognized (it only took modifying the alps part of the psmouse kernel module, so it would recognize the updated e7 signature).  So now gsynaptics finally works, but unfortunately, only partially.  It will disable the touchpad, but i really wanted to disable the tap to click.  Or even better, disable the tap to click while typing.  i will have to check on the kubuntu add ons that i posted earlier to see if they will work.  i guess i will report back once i have given them a go.

for reference, this is to disable the tap-to-click (and maybe configure some other multi-touch gestures on an alps touchpad for an hp mini 311).  If anyone is interested in how i got the driver working properly just let me know and i will go into details.  I have read that this driver mod will work with gnome (although on an hp dm1, not a mini 311, same touchpad tho).  so there might be some light left at the end of the tunnel.

I've got a 311, I'd love to know how you got this to work. Would this help with two finger scrolling/clicking also?

Thanks

---

### Post by curiousphil on 2012-09-24
Hello all, 

in Ubuntu 12.04 and Mint13 (and maybe before) gsynaptics has been replaced by gpointing-device-settings .

So, if you install gsynaptics with :

```
sudo apt-get install gsynaptics
```the gsynaptic executable is not installed, which you can verify by 

```
which gsynaptics
```, which gives no result. 

The solution now is: 

- First, remove gsynaptics with 

```
sudo apt-get purge gsynaptics
```or, if you are uncertain about "purge", you can just use the conventional remove :  

```
sudo apt-get remove gsynaptics
```(purge just additionally removes the configuration files of the package)

- and now simply install gpointing-device-settings

```
sudo apt-get install gpointing-device-settings
```- and then just simply start it with 

```
gpointing-device-settings
```Done !!

Explanation : gpointing-device-settings is the new tool to configure the touchpad- and the mouse-details. It has a beautiful functionality and far more options then gsynaptics and most important of all: IT IS UNDER CURRENT DEVELOPMENT !!

TwoNotes to the more senior KDE Developers and Users :

- Could anybody post a solution on how to include "gpointing-device-settings" into the "KDE System Settings" at the right place?

- Is anybody working on a KDE - equivalent of "gpointing-device-settings" ?  What is the status there?

---

### Post by overdrank on 2012-09-24
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

