---
title: "&quot;coasting&quot; in karmic"
date: 2009-11-14
forum: Hardware
---

### Post by treesurf on 2009-11-14
Hi all.  In Jaunty coasting was enabled by default for vertical scrolling with my synaptics touchpad.  It is not enabled in karmic and I'd like to figure out how to turn it back on.  

Anyone know how?

Thanks!

---

### Post by treesurf on 2009-11-15
Wow, threads sure do get buried quickly here sometimes.  

Bump. :D

---

### Post by SushiR on 2009-11-15
Have you looked in gnome-control-center to configure your touchpad (it's mouse settings). You can enable vertical scrolling there. If it doesn't work for you, you can still install "gpointing-device-settings".

---

### Post by treesurf on 2009-11-15
Thanks for the reply.  Unfortunately, neither the Mouse settings or gpointing-device-settings have an option for coasting.

---

### Post by SushiR on 2009-11-15
What exactly is coasting? I just thought you want to enable vertical scrolling...

---

### Post by treesurf on 2009-11-15
Coasting is when you quickly swipe the vertical scrolling area on the touchpad and the screen continues scrolling quickly for a moment, depending on how vigorously you swipe the touchpad.  Kind of like how scrolling works on an iPhone and other touchscreen devices.  

This worked by default in Jaunty, but not in Karmic.

---

### Post by treesurf on 2009-11-17
Last bump, and then I'm giving up.

---

### Post by Zorael on 2009-11-17
The Synaptics driver supports it (granted your pad does), but you'll likely have to enable the feature manually with a xinput command. I don't know if there exists a graphical xinput "browser". The command would have to be run once per session, so you could make a script of it and set it to autostart upon login.

See [http://ubuntuforums.org/showpost.php?p=7643273&postcount=2](http://ubuntuforums.org/showpost.php?p=7643273&postcount=2).

I see that coasting isn't listed in the example there, but I know for a fact I have it enabled on my netbook. So it's probably a new driver feature that wasn't present when I made that post.

Just browse the list that '**xinput list-props "SynPS/2 Synaptics TouchPad"**' outputs and you'll find it.


edit: Right, so I hobbled over to the netbook to give some concrete examples.

```
$ xinput list-props "SynPS/2 Synaptics TouchPad"
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
        **Synaptics Coasting Speed (274): 45.000000**
        Synaptics Pressure Motion (275):        29, 159
        Synaptics Pressure Motion Factor (276): 1.000000, 1.000000
        Synaptics Grab Event Device (277):      1
        Synaptics Gestures (278):       1
        Synaptics Capabilities (279):   1, 1, 1, 1, 1
        Synaptics Pad Resolution (280): 110, 100
        Synaptics Area (281):   0, 0, 0, 0
```
My autostarted script;
```
#!/bin/bash

echo Setting preset Synaptics options

echo [*] palm detection...
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Palm Detection" 8 1

echo [*] two-finger scrolling...
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 0 0

echo [*] edge motion speed...
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Motion Speed" 32 400 800

echo [*] coasting speed...
xinput set-float-prop "SynPS/2 Synaptics TouchPad" "Synaptics Coasting Speed" 45

# Template:
# xinput set-int-prop "SynPS/2 Synaptics TouchPad" "
```
It enables palm detection, disables two-finger scrolling, raises edge motion speed a bit (the speed at which it keeps moving when you drag something and hit the pad edge), and enables coasting. 

I find a coasting speed of 45 to be my sweet spot. Setting it to 1 makes it coast when I don't want to, and much higher than 50 makes it difficult to make it coast at all.

---

### Post by treesurf on 2009-11-18
Thanks!

---

