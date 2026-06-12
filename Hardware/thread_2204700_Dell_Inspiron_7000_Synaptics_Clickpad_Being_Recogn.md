---
title: "Dell Inspiron 7000 Synaptics Clickpad Being Recognized as a Touchpad"
date: 2014-02-09
forum: Hardware
---

### Post by Carpentr on 2014-02-09
Hi everyone,

I have a new Dell Inspiron 7000 that I'm looking to run Ubuntu 12.04 64-bit on full time.

Everything works great except the clickpad (touchpad with no buttons). 

I've tried following this guide:
[http://www.theorangenotebook.com/2012/02/call-for-testing-clickpad.html](http://www.theorangenotebook.com/2012/02/call-for-testing-clickpad.html)

However, it seems this is already included in the latest release of 12.04. Everything besides clicking and dragging works (right-click and two-finger right-clicking works fine).

When I try to click and drag, the item I'm dragging starts to get very erratic and cannot be controlled.

Here is my xinput:
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; La-VIEW Technology SteelSeries          	id=10	[slave  pointer  (2)]
&#9116;   &#8627; ELAN Touchscreen                        	id=13	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; La-VIEW Technology SteelSeries          	id=11	[slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                    	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=16	[slave  keyboard (3)]

```

Any help would be greatly appreciated.

---

### Post by Carpentr on 2014-03-06
I've been playing with this some more on a live CD of 13.10 and after running:
```

xinput list-props "SynPS/2 Synaptics TouchPad" | grep Capabilities

```

I get the following output:
```

1, 0, 0, 1, 1, 1, 1

```

The first 1 means that my system thinks the ClickPad has a physical left button to click with, which it does not. There is only one button and it is underneath the touchpad, invisible to the eye. Is there any way to change the first 1 to a 0? This seems to be the problem as to why I cannot click and drag without the window jumping all around the screen. Tap and drag works fine, just not physically clicking down on the ClickPad and dragging.

---

### Post by peter103 on 2014-04-21
Had the same problem using Ubuntu 12.04LTS on a Dell Inspiron 7537. Solution was as described in [http://askubuntu.com/questions/250336/disable-mouse-movement-in-tap-zones-on-synaptics-trackpad](http://askubuntu.com/questions/250336/disable-mouse-movement-in-tap-zones-on-synaptics-trackpad) . Fixed with 'synclient AreaBottomEdge=4200'.

---

### Post by tinga90 on 2014-05-16
Same problem here, Dell inspiron 7000 and clickpad makes me insane.
Detailed solution here:

```
sudo mkdir /etc/X11/xorg.conf.d
sudo cp /usr/share/X11/xorg.conf.d/50-synaptics.conf /etc/X11/xorg.conf.d/50-synaptics-modified.conf

```

Then open 50-synaptics-modified.conf:

```
sudo gedit /etc/X11/xorg.conf.d/50-synaptics-modified.conf
```

and append the following text:

```

# Clickpad fix
Section "InputClass"
        Identifier "touchpad border config"
        MatchIsTouchpad "on"
        Driver "synaptics"
        Option "BottomEdge" "4416"
        Option "AreaBottomEdge" "4000"
EndSection
```

Then reboot

---

### Post by andrew133 on 2014-07-12
Unfortunately those settings do not fix it for me on a Dell Inspiron 15 7000 series. Setting AreaBottomEdge does indeed disable touch events but ONLY when I put my finger down within that area. If I drag my finger into the excluded area from elsewhere it continues to register as pointer movement. If I click in the excluded area and then drag with my other finger then excluded area "re-activates" and I end up with the window I am dragging jumping to the corner where my clicking finger is located as soon as I remove my dragging finger from the pad.

This is incredibly frustrating because otherwise the clickpad works great, multitouch scrolling and all, but the laptop is pretty much unusable if I can't effectively drag items. It seems like it must be a bug with the driver. Who maintains the synaptics drivers and how might I report this bug to them?

Edit: just checked the behavior of the pad under windows. It registers both the clicking and dragging finger's movements but does not jump the cursor to the location of the clicking finger if the dragging finger is lifted. In windows I can click, drag with another finger, lift the dragging  finger, and then drag further with the clicking finger and it treats the  movement as if it comes from the same location where I lifted the  dragging finger instead of jumping to the corner where I clicked. This seems like the correct behavior that the linux driver is not implementing.

---

### Post by zetarancio on 2014-09-07
Please, confirm this bug here about the drag bug.
[https://bugzilla.kernel.org/show_bug.cgi?id=82361](https://bugzilla.kernel.org/show_bug.cgi?id=82361)

---

### Post by tinga90 on 2014-11-09
[COLOR=#000000]**@andrew133**
The solution described above allows me to left click with a finger while moving with an other finger on the touchpad (so that I can drag and drop items, or select some text, holding left touchpad button). 
In my case when I move outside the excluded area and left button is pressed, it results with a selection or dragging, with no cursor-jumping
[/COLOR][COLOR=#000000]I don't know why but it works fine for me, probably different notebook configurations... [/COLOR][COLOR=#000000]

I'm on Dell 7537 15.6" Full HD Touch screen, Ubuntu 14.04 (now updated to 14.04.1) 64bit

A problem that I'm facing is cursor jumping but not related to touchpad, even if I do not click anything it starts switching windows and jumping/pressing in some areas, and so it is impossible to work...
Now I made a clean install, if problems come again I will try installing windows to see if it is a notebook problem or an ubuntu problem[/COLOR]

---

### Post by adam101 on 2014-11-11
I also have a Dell 7537 (15 7000 series, 16 GB RAM, GeForce video card).  I'm running Linux Mint 17 Cinnamon on it.  I had this same exact issue, where the button areas are seen as part of the surface, making clicking and dragging difficult.  The above fix by tinga90 made the touchpad liveable.  Now it works a bit like my old Gateway circa 2007.  No multitouch, no problem.  In Windows with all the multipoint crap, using this touchpad feels a bit like trying to write with cooked spaghetti.
It was possible to click and drag; the WHOLE touchpad seems to click in like a mechanical button.  So you had to put the cursor where you wanted, apply LOTS of pressure to the touchpad to click the button, and drag.  It's about as unideal as you can get.  It's much better now, Thanks tinga90!

I do see the cursor jump every now and again, but I think it's because I strike the touchpad with my palm while typing.  It doesn't otherwise do it.  Unfortunately, no amount of typing in the console can shink the touchpad to a reasonable size.  sudo apt-get install reasonable-sized-touchpad didn't work, and now I'm out of ideas.

---

### Post by walshbp on 2015-01-24
After fighting with this a bit I was able to get the right clickpad button working properly.

The clickpad section on this page helped me out quite a bit:  [https://wiki.archlinux.org/index.php/Touchpad_Synaptics](https://wiki.archlinux.org/index.php/Touchpad_Synaptics)

I created a file to modify the synaptic xorg setup to manual configure the clickpad.   Create a file called /usr/share/X11/xorg.conf.d/52-mymods.conf with the following contents.

Section "InputClass"
        Identifier "Force Clickpad Config"
        MatchDriver "synaptics"
        Option "ClickPad"         "true"
        Option "EmulateMidButtonTime" "0"
        Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
        Option "SecondarySoftButtonAreas" "58% 0 0 15% 42% 58% 0 15%"
EndSection

---

