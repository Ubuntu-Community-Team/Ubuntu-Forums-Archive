---
title: "Touchpad &amp; other keyboard related issues"
date: 2011-06-11
forum: Hardware
---

### Post by tuomasholopainen on 2011-06-11
Hi there,
First things first
My english is vary bad so excuse all errors!
I recently bought a notebook, asus a53e to be precise. Tech spec &#8594; [http://www.asus.co.nz/Notebooks/Versatile_Performance/A53E/#specifications](http://www.asus.co.nz/Notebooks/Versatile_Performance/A53E/#specifications)
[http://imageshack.us/photo/my-images/28/61666076.jpg/](http://imageshack.us/photo/my-images/28/61666076.jpg/)
Lets go to technical informations
```
$ xinput list 
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)] 
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)] 
&#9116;   &#8627; PS/2 Logitech Wheel Mouse               	id=11	[slave  pointer  (2)] 
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)] 
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)] 
    &#8627; Power Button                            	id=6	[slave  keyboard (3)] 
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)] 
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)] 
    &#8627; USB 2.0 UVC VGA WebCam                  	id=9	[slave  keyboard (3)] 
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)] 
```

As you can see Fn+F9 should enable/disable touchpad but it doesn't! I also tried touchpad-indicator which doesn't work.
The only thing that works is:
```
xinput set-prop 11 "Device Enabled" 0/1
```
Here are various settings from /usr/share/x11/xorg.conf.d:
keyboard config just in case:
```
Section "InputClass"
    Identifier             "Keyboard"
    MatchIsKeyboard        "yes"
    Option                 "XkbModel" "asus_laptop"
    Option                 "XkbLayout" "pl, us"
	Option		"XkbOptions"	"grp:alt_ctrl_toggle"
EndSection
```
module:
```
Section	"Module"
	Load	"synaptics"
EndSection
```
synapyic:
```
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
EndSection
```
plus
```
Section "InputClass"
	Identifier "Dell Inspiron embedded buttons quirks"
	MatchTag "inspiron_1011|inspiron_1012"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
	Option "JumpyCursorThreshold" "90"
	Option "AreaBottomEdge" "4100"
EndSection

Section "InputClass"
	Identifier "Dell Inspiron quirks"
	MatchTag "inspiron_1120"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
	Option "JumpyCursorThreshold" "250"
EndSection

Section "InputClass"
	Identifier "HP Mininote quirks"
	MatchTag "mininote_1000"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
	Option "JumpyCursorThreshold" "20"
EndSection
```
Here is the question.
How can I configure fn+f9 to enable/disable touchpad when xev doesn't return anything when I press fn or combination fn+f9?
How can I get fn+f11 and fn+f12 to set volume level?

Since fn+f5/f6/f7 work properly I can't understand why others combinations won't.
Is it something wrong with ```
Option                 "XkbModel" "asus_laptop"

``` or it's something elese?
As you can see touchpad was detected as some kind of virtual core pointer.
Don't get me wrong, touchpad works perfect I'm only looking some way to disable it.

---

### Post by Abi79 on 2011-06-14
Ubuntu 11.04 here, on an [Asus K52DE]("http://www.asus.com/Notebooks/Versatile_Performance/K52DE/").

Just for reference, I have the same problem related to the touchpad toggle as you do.

```
$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Avago USB LaserStream(TM) Mouse             id=10    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                              id=11    [slave  keyboard (3)]
    &#8627; Asus Laptop extra buttons                   id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
```They keyboard model is Asus Laptop, layout USA. The functions keys that work are sleep, screen brightness, turning the screen off, the three sound keys, the insert button and the shortcut for the calculator. What doesn't work is the touchpad toggle, wireless and scroll lock (Fn+NumLK). Would greatly appreciate any help, as well. :)

**Edit:** The post at [http://ubuntuforums.org/showthread.php?t=1460790](http://ubuntuforums.org/showthread.php?t=1460790) has helped fix the wireless button. Trying the touchpad now.

---

