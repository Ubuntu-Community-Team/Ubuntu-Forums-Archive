---
title: "How can I disable Two-Finger Scrolling with xinput?"
date: 2009-04-30
forum: Hardware
---

### Post by Rubicon_82 on 2009-04-30
How can I disable Two-Finger Scrolling on a Synaptics Touchpad in Kubuntu 9.04?

This is a fresh install of 9.04 at the Beta release, with current updates.  There is no mention of a touchpad in xorg.conf; xserver-xorg-input-synaptics reports version 0.99.3-2ubuntu4.               

I have tried following the instructions at [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad), but I cannot enable SHMConfig to get gsynaptics to work.  Instead, I've tried doing this through xinput, but I can't seem to figure out the correct syntax.                                      

Output from '$ xinput list-props 5'
```
                             
Device 'SynPS/2 Synaptics TouchPad':
        Device Enabled (89):            1
        Synaptics Edges (233):          1632, 5312, 1575, 4281
        Synaptics Finger (234):         24, 29, 255           
        Synaptics Tap Time (235):               180           
        Synaptics Tap Move (236):               221           
        Synaptics Tap Durations (237):          180, 180, 100 
        Synaptics Tap FastTap (238):            0             
        Synaptics Middle Button Timeout (239):          75    
        Synaptics Two-Finger Pressure (240):            280   
        Synaptics Scrolling Distance (241):             100, 100
        Synaptics Edge Scrolling (242):         1, 0, 0         
        Synaptics Two-Finger Scrolling (243):           1, 0    
        Synaptics Edge Motion Pressure (244):           29, 159 
        Synaptics Edge Motion Speed (245):              1, 401  
        Synaptics Edge Motion Always (246):             0       
        Synaptics Button Scrolling (247):               1, 1    
        Synaptics Button Scrolling Repeat (248):                1, 1
        Synaptics Button Scrolling Time (249):          100         
        Synaptics Off (250):            0                           
        Synaptics Guestmouse Off (251):         0                   
        Synaptics Locked Drags (252):           0
        Synaptics Locked Drags Timeout (253):           5000
        Synaptics Tap Action (254):             2, 3, 0, 0, 1, 2, 3
        Synaptics Click Action (255):           1, 1, 1
        Synaptics Circular Scrolling (256):             0
        Synaptics Circular Scrolling Trigger (257):             0
        Synaptics Circular Pad (258):           0
        Synaptics Palm Detection (259):         0
        Synaptics Palm Dimensions (260):                10, 199
        Synaptics Pressure Motion (261):                29, 159
        Synaptics Grab Event Device (262):              1

```I assume that I should be altering the "Synaptics Two-Finger Scrolling" property.  However, attempting the command '$ xinput set-atom-prop 5 "Synaptics Two-Finger Scrolling" 0 0' results in an error such as:
```

X Error of failed request:  BadAtom (invalid Atom parameter)
  Major opcode of failed request:  17 (X_GetAtomName)
  Atom id in failed request:  0x0
  Serial number of failed request:  15
  Current serial number in output stream:  15

```Can anyone advise on the correct syntax for this command?

EDIT:

I was able to disable the Two-Finger Scrolling option by using the information in this post:
[http://ubuntuforums.org/showpost.php?p=7217419&postcount=4](http://ubuntuforums.org/showpost.php?p=7217419&postcount=4)

---

